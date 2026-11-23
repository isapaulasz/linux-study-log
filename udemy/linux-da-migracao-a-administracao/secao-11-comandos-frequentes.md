# Seção 11 - Comandos frequentemente utilizados

## Aula 16 - Criação de diretórios (de pastas)

- `mkdir`: cria diretório
- `mkdir -p Diretorio/Subdiretorio/Subsubdiretorio`: permite criar diversos diretórios hierárquicos de uma vez
- Para criar diretórios com nomes por extenso, incluindo espaço:
  - `mkdir "Nome de diretório extenso"`
  - ou `mkdir Nome\ de\ diretorio\ extenso`

## Aula 17 - Criando múltiplos subdiretórios

- Criar um diretório com múltiplos subdiretórios
- Exemplo: criar o diretório `projeto` com os diretórios `publico` e `src`
  - dentro de `publico`, os subdiretórios `asset`, `img` e `pg`
  - dentro de `src`, os subdiretórios `sass` e `ts`
  - dentro de `asset`, os subdiretórios `css` e `js`
- Usamos chaves (`{}`) para criar múltiplos subdiretórios de uma só vez, separando os nomes por vírgula, sem espaços
- Resolução:
  - `mkdir -p projeto/{publico/{asset/{css,js},img,pg},src/{sass,ts}}`

## Aula 18 - Copiar, mover, renomear e apagar arquivos e diretórios

- `cp origem destino`: copia arquivos
  - `cp -v arquivo destino`: copia e retorna uma mensagem da ação
- Cuidado: se copiar um arquivo sobre um arquivo que já existe, ele será sobrescrito
- `cp -v arquivo1 arquivo2`: copia o conteúdo de um arquivo existente para um arquivo que ainda não existe
- `cp -rv init teste/`: copia um diretório para dentro de outro (`init` para `teste`); a flag `-r` copia recursivamente
- `cp -iv`: pede confirmação antes de sobrescrever
- `mv`: move e renomeia arquivos
  - `mv -v nomeatual novonome`: altera o nome do arquivo
  - `mv -v arquivo diretorio/`: move para o diretório de destino
- `rmdir`: apaga diretórios, porém não apaga se houver conteúdo dentro
- `rm`: apaga tanto arquivos quanto diretórios
  - `rm -rv teste`: apaga o diretório `teste` e todo o seu conteúdo, mostrando o que foi removido
- Cuidado: o `rm` não envia para a lixeira, a exclusão é permanente

## Aula 19 - Comparando e sincronizando arquivos e diretórios

- Comparar e sincronizar arquivos
- `diff init init2`: compara os diretórios, mostrando as diferenças
- `rsync -rv init2/ init`: sincroniza o conteúdo de `init2` para `init`, sobrescrevendo os arquivos diferentes e copiando os que faltam
- O `/` ao final de `init2/` indica que o conteúdo do diretório será sincronizado, e não o diretório em si

## Aula 20 - Links físicos e links simbólicos

- Criar links físicos e links simbólicos
- Links simbólicos se assemelham aos atalhos do Windows
- `ls /bin/`: dependendo do tema do terminal, os links simbólicos aparecem em cor diferente (no curso, verde escuro)
- `ln`: cria link
- `ln -s`: cria link simbólico
  - `ln -s ~usuario/caminhodiretorio`: executado dentro do diretório de destino, cria nele um link para o original
  - `ln -s original nomedolink`: forma completa, em que se define o nome do link
- `stat diretorio`: mostra informações detalhadas, como inode, tamanho, permissões, datas e número de links
- Ao remover o original, o link simbólico continua existindo, porém muda de cor (para vermelho) e vira um broken symbolic link ao usar `file`
- Link físico:
  - não pode ser criado para um diretório
  - `ln ~usuario/arquivo`: cria o link físico no diretório atual
  - aparece como um arquivo comum, e não como um link
  - ao remover o arquivo original, o link físico se mantém como um arquivo, se assemelhando a uma cópia
  - na verdade, é outro nome para os mesmos dados; eles só são apagados quando todos os links são removidos
  - `ls -li`: mostra o número do inode, que é igual entre o arquivo e seus links físicos

## Aula 21 - Localizando arquivos

- `mount`: mostra os sistemas de arquivos montados (também é usado para montar dispositivos)
- `btrfs filesystem show /dev/sdc`: mostra informações do sistema de arquivos Btrfs do dispositivo
- `find /caminho/ -name "nome"`: busca arquivos pelo nome
- `find /caminho/ -iname "nome"`: busca pelo nome, ignorando maiúsculas e minúsculas
- `find /run/media/usuario/ -name "padrao" -exec file '{}' \;`: busca arquivos e executa o `file` em cada um deles
- `find /caminho/ -type l -delete`: busca e deleta links simbólicos
- `find /caminho/ -type d -exec chmod 0755 '{}' \;`: define a permissão 755 em todos os diretórios
- `find /caminho/ -type f -exec chmod 0644 '{}' \;`: define a permissão 644 em todos os arquivos
- `find /caminho/ -user usuario`: busca arquivos que pertencem a um usuário
- `find /caminho/ -uid 1000`: busca arquivos pelo ID do usuário
  - `id usuario`: mostra o ID do usuário
- `whoami`: mostra o usuário atual
- `who`: mostra os usuários logados
- `find /caminho/ -size +10M`: busca arquivos maiores que 10 MB
- `find /caminho/ -mtime -7`: busca arquivos modificados nos últimos 7 dias
