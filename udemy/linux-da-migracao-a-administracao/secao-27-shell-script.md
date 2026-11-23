# Seção 27 - Shell Script

## Aula 66 - O que é shell script

- Linguagem de automação de tarefas: um arquivo de texto com comandos, executados em sequência pelo shell
- Linguagem de extrema importância para o sistema, pois vários scripts compõem o sistema (por exemplo, os de inicialização)

## Aula 67 - Primeiros três scripts

- É necessário definir o bit de execução para que os scripts possam ser executados como programas
  - `chmod +x *.sh`: dá permissão de execução a todos os arquivos `.sh` da pasta
- Não é necessária a extensão `.sh` para funcionar, ela é apenas uma convenção
- Primeiro script:

```bash
#!/bin/bash
# Esse é um script simples, somente para demonstrar como funciona
echo "olá mundo"
```

- `#` denomina um comentário
- O primeiro comentário é um comentário especial chamado shebang (`#!/bin/bash`), com a finalidade de indicar qual programa vai executar o script
- `echo`: exibe uma mensagem na tela
- Para executar o script:
  - `./nomescript.sh`
  - ou `bash nomescript.sh`, que não exige o bit de execução
- Segundo script:

```bash
#!/bin/bash
# Vamos tratar aqui de variáveis
PESSOA=`whoami`
echo "olá $PESSOA"
```

- `PESSOA` é uma variável, que guarda o resultado do comando `whoami`
- Na atribuição não há espaços ao redor do `=`
- Para usar o valor da variável, é necessário o `$`
- Terceiro script:

```bash
#!/bin/bash
# Vamos fazer o script ler as informações digitadas pelo usuário e armazenar em uma variável
echo -n "olá. Como se chama?: "
read PESSOA
echo "tudo bem $PESSOA?"
```

- `echo -n`: exibe a mensagem sem pular a linha
- `read`: abre uma entrada para o usuário digitar e guarda o que foi digitado na variável

## Aula 68 - Isolamento de texto em um shell script

- Isolamento de texto:

```bash
#!/bin/bash
# Vamos conferir se a variável $PESSOA com os caracteres '' funciona
PESSOA='whoami'
echo "olá $PESSOA"
```

- Retorna "olá whoami"
- Aspas simples (`''`) guardam o texto literalmente
- Crases (`` ` ``) guardam o resultado de um comando
- Para evitar a confusão entre crase e apóstrofo, foi criada a opção `$()`, que tem a mesma funcionalidade da crase:

```bash
#!/bin/bash
# Vamos conferir se a variável $PESSOA com a opção $() funciona
PESSOA=$(whoami)
echo "olá $PESSOA"
```

## Aula 69 - Funções

- Funções executam longos scripts como um comando:

```bash
#!/bin/bash
# Vamos usar função
pessoa_atual () {
    PESSOA=$(whoami)
    echo "olá $PESSOA"
}
pessoa_atual
```

- Ao chamar o nome da função, o comando é executado
- A função precisa ser definida antes de ser chamada
- Executar um programa enquanto observa a presença de erros:

```bash
#!/bin/bash
# Vamos usar a opção $() e a função
PESSOA=$(whoami)
listar_pasta () {
    ls
}
echo "olá $PESSOA. Vamos preparar para listar sua pasta atual."
sleep 2
listar_pasta
```

- Apresenta uma mensagem, faz uma pausa de 2 segundos (`sleep 2`) e executa a função, que usa o comando `ls`
- O nome usado na chamada deve ser igual ao da função (`listar_pasta`)

```bash
#!/bin/bash
PESSOA=$(whoami)
# Esta é uma variável somente para interação com o usuário e também no arquivo de log
DATA=$(date)
# Esta variável também será utilizada no arquivo de log dentro da função montar_dispositivo

# A função montar_dispositivo será responsável por realizar a montagem do dispositivo de armazenamento e gerar o log
montar_dispositivo () {
    echo -n "$DATA $PESSOA " &>> log; mount -t vfat UUID=34D8-539C /mnt/
}

echo "olá $PESSOA."
sleep 1
echo "vamos preparar o dispositivo para iniciar o backup."
sleep 1
montar_dispositivo
if [ $? = 0 ]; then
    echo "dispositivo pronto para iniciar o backup"
else
    echo "dispositivo não foi encontrado"
fi
```

- Mostra a data, gera um log e manda montar o dispositivo de armazenamento em `/mnt/`
- `&>> log`: acrescenta ao arquivo `log` a saída padrão e a de erro
- `mount -t vfat UUID=... /mnt/`: monta o dispositivo formatado em vfat, identificado pelo UUID (que pode ser consultado com `lsblk -f`)
- Nesse script, apenas o `echo` é gravado no `log`; para gravar também a saída do `mount`, adicione `&>> log` ao final do comando
- `$?`: guarda o código de saída do último comando executado (0 significa sucesso)
- A condicional é escrita usando `[ ]`, com espaços ao redor dos colchetes, e é encerrada com `fi`

## Aula 70 - Condicionais

- Último script:

```bash
#!/bin/bash
PESSOA=$(whoami)
# Esta é uma variável somente para interação com o usuário e também no arquivo de log
DATA=$(date)
# Esta variável também será utilizada no arquivo de log dentro da função montar_dispositivo

# A função montar_dispositivo será responsável por realizar a montagem do dispositivo de armazenamento e gerar o log
montar_dispositivo () {
    echo -n "$DATA $PESSOA " &>> log; mount -t vfat UUID=34D8-539C /mnt/ || mount -t vfat UUID=5698-D123 /mnt
}

echo "olá $PESSOA."
sleep 1
echo "vamos preparar o dispositivo para iniciar o backup."
sleep 1
montar_dispositivo
case "$?" in
    0)
        echo "dispositivo pronto para iniciar o backup"
    ;;
    *)
        echo "dispositivo não foi encontrado"
    ;;
esac
```

- `||`: se a montagem do primeiro dispositivo falhar, tenta montar o segundo
- `case` como alternativa ao `if`
- Caso `$?` seja zero, a primeira mensagem será exibida; caso contrário, a segunda
- Cada opção do `case` termina com `;;`
- O `*)` equivale ao `else`, valendo para qualquer outro valor
- O `case` é finalizado com `esac` (a palavra `case` invertida)
- Versão final, com o backup:

```bash
#!/bin/bash
PESSOA=$(whoami)
# Esta é uma variável somente para interação com o usuário e também no arquivo de log
DATA=$(date)
# Esta variável também será utilizada no arquivo de log dentro da função montar_dispositivo

# A função montar_dispositivo será responsável por realizar a montagem do dispositivo de armazenamento e gerar o log
montar_dispositivo () {
    echo -n "$DATA $PESSOA " &>> log; mount -t vfat UUID=34D8-539C /mnt/ || mount -t vfat UUID=5698-D123 /mnt
}

# A função BACKUP copia os arquivos para o dispositivo, registra o resultado e desmonta o dispositivo
BACKUP () {
    rsync -rv /home/user/Documentos/pasta/ /mnt/ &>> backup.log
    umount /mnt
}

echo "olá $PESSOA."
sleep 1
echo "vamos preparar o dispositivo para iniciar o backup."
sleep 1
montar_dispositivo
case "$?" in
    0)
        echo "dispositivo pronto para iniciar o backup"
        sleep 1
        echo "iniciado backup"
        sleep 1
        BACKUP
    ;;
    *)
        echo "dispositivo não foi encontrado"
    ;;
esac
```

- `rsync -rv origem/ destino/`: sincroniza os arquivos da pasta de origem com o dispositivo (ajuste o caminho para a pasta que deseja copiar)
- `&>> backup.log`: grava no arquivo `backup.log` o que o `rsync` exibir
- `umount /mnt`: desmonta o dispositivo ao final, para que possa ser removido com segurança
