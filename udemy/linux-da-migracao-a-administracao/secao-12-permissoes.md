# Seção 12 - Permissões de arquivos e bits especiais

## Aula 22 - Permissões de arquivos

- O primeiro caractere indica o tipo (`-` arquivo, `d` diretório, `l` link)
- Os três caracteres seguintes são referentes às permissões do dono do arquivo
- Os três seguintes são do grupo, que pode ou não incluir o dono
- Os três últimos referem-se às outras pessoas, que não sejam o proprietário nem o grupo
- `r` = Read: leitura
- `w` = Write: escrita (gravar ou salvar)
- `x` = Execute: executar o arquivo
- Ex: `drwxr-xr-x`
  - `d`: é um diretório
  - `rwx`: o dono tem acesso a leitura, escrita e execução
  - `r-x`: o grupo tem acesso a leitura e execução
  - `r-x`: outros têm acesso a leitura e execução
- `chmod`: change mode, altera permissões
- `chmod u=rwx,g=rwx,o=rwx nomedoarquivo`: altera as permissões de usuário (`u`), grupo (`g`) e outros (`o`) para o arquivo
- `chmod o-x nomedoarquivo`: retira a permissão de execução dos outros
- `chmod o+x nomedoarquivo`: devolve a permissão

## Aula 23 - Permissões de arquivos #2 (forma numérica)

- A forma numérica é a mais comum entre os usuários para alterar permissões
- Read: 4
- Write: 2
- Exec: 1
- As permissões se tornam valores acumulados
- Quem tem permissão total de leitura, escrita e execução tem 7 (4+2+1)
- Acesso somente a leitura e execução se torna 5 (4+1)
- Leitura e escrita se torna 6 (4+2)
- Sem permissão nenhuma é 0
- Cada dígito representa, na ordem: dono, grupo e outros
- 644 é uma permissão comum: o dono lê e escreve; grupo e outros apenas leem
- `chmod 777 nomearquivo`: permissão total a todos (evite usar, por ser inseguro)

## Atividade Complementar

- Qual é o valor octal padrão para binários, scripts e diretórios?
  - 755
- Qual é o valor octal padrão para arquivos comuns? Por quê?
  - 644; arquivos comuns não são programas executáveis, e a ausência de permissão de execução evita riscos
- Por que diretórios precisam possuir o bit de execução ativo?
  - Os usuários precisam da permissão de execução para entrar no diretório e acessar os itens dentro dele

## Aula 24 - Permissões especiais

- Permissões numéricas normalmente são antecedidas por um 0, que indica que nenhum bit especial está ativo (`0755`)
- Setuid (SUID): permissão para executar programas mesmo não sendo o proprietário
  - Um exemplo de programa é o `passwd`
  - No lugar do `x` do dono, aparece um `s`: `-rws`
  - `chmod u+` + `Tab`: permite ver as opções de privilégio do usuário
  - `chmod u+s nomearquivo`: dá a permissão de SUID ao arquivo
- Setgid (SGID): o programa é executado com os direitos do grupo dono; em diretórios, os novos arquivos herdam o grupo do diretório
  - `chmod g+s nomearquivo`
- Sticky bit: voltado para diretórios públicos, em que somente o proprietário do arquivo (ou o root) pode excluí-lo
  - `tmp` é um diretório com sticky bit; para "outros" aparece `rwt`
  - Para alterar, podemos usar `chmod o+t nomediretorio` ou `chmod 1777 nomediretorio`

## Atividade Complementar 2

- Fazendo uma revisão antes de iniciar a atividade: bits especiais servem para que determinado arquivo seja executado por outros usuários como se fossem seus proprietários
- SETUID: o executável (não funciona em scripts) é executado com os direitos do proprietário, ao invés de ser executado com os direitos de quem o está executando
- SGID: o mesmo vale para esse bit quando ele é definido no programa; a pessoa atual pode executá-lo como o dono do grupo
- Sticky bit: serve para dar permissão de exclusão de arquivos somente aos proprietários ou ao usuário root em diretórios públicos
- Valores numéricos:
  - 4 = setuid
  - 2 = sgid
  - 1 = sticky bit

### Perguntas dessa tarefa

1. Como descobrir se um diretório ou um binário possui bit especial ativado?
   - É possível usar o comando `ls -l`, que lista os diretórios e mostra suas permissões; os bits especiais aparecem como `s` ou `t` no lugar do `x`
   - `find /caminho/ -perm -4000`: lista os arquivos com SUID
2. Como você definiria o bit SETUID no comando `ping`? (muito cuidado: copie-o para um diretório e faça o teste nessa cópia)
   - Exemplo com um diretório de teste:
     - `mkdir ~/teste_suid`
     - `cp $(which ping) ~/teste_suid/ping_copia`
     - `cd ~/teste_suid`
     - `ls -l ping_copia`
     - `chmod u+s ping_copia` ou `chmod 4755 ping_copia`
     - `ls -l ping_copia`: confirma que aparece `rws` nas permissões do dono
