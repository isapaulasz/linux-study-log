# Seção 16 - Comandos para leitura e edição de texto

## Aula 28 - Leitura de arquivos de texto via linha de comando

- `cat`: lê arquivo de texto
  - `cat -n`: enumera as linhas
- O `cat` não foi feito para a leitura de arquivos binários
- `strings`: extrai e exibe as sequências de caracteres legíveis de um arquivo, útil para arquivos binários
- `head`: lê as primeiras linhas do arquivo (10 por padrão)
  - `head -n 30 nomearquivo`: `-n` permite definir a quantidade de linhas que aparecerão, nesse caso 30
- `tail`: lista as últimas linhas do arquivo (10 por padrão); também permite usar `-n`
  - `tail -f nomearquivo`: acompanha o arquivo em tempo real, útil para logs
- `tac`: lista todo o arquivo invertido, da última linha para a primeira
- `more`: mostra o arquivo aos poucos, carregando conforme o terminal é rolado para baixo, porém não permite retorno para cima
- `less`: versão mais rica do `more`, permitindo subir e descer
  - permite busca dentro do arquivo usando `/`
  - `h` mostra as opções disponíveis
  - `q` sai
- `strings arquivo | less`: permite uma leitura mais completa das informações
- `wc` (word count): permite ver o número de linhas, o número de palavras e a quantidade de caracteres (bytes)

## Aula 29 - Filtrando informações em arquivos

- `grep`: busca informações
- Exemplos:
  - `grep ext4 /etc/fstab`: retorna as linhas que contêm `ext4`
  - `grep -v ext4 /etc/fstab`: retorna tudo, menos as linhas que contêm `ext4`
- `-E`: permite buscar vários conteúdos em uma só busca
  - `grep -E "ext4|btrfs" /etc/fstab`: nesse caso, retorna tudo que contém `ext4` e tudo que contém `btrfs`
- `--color`: é possível incluir para ajudar visualmente
  - `grep -E --color "ext4|btrfs" /etc/fstab`
- `-i`: torna o comando case insensitive (ignora maiúsculas e minúsculas)
  - `grep -i User arquivo`: retorna as linhas que contêm `user` e `User`
- `-n`: mostra o número de cada linha encontrada
- É possível acumular as opções, como `--color -iE -n` (ou `-iEn --color`)

## Aula 30 - Editores de texto em linha de comando

- `nano`: editor de texto simples
  - a barra de ferramentas usa comandos `Ctrl + tecla` (representados por `^`)
- `vim`: editor de texto
  - `vim.tiny` é uma versão mais enxuta
  - `i`: entra no modo de inserção para digitar o texto
  - `Esc`: volta ao modo de comandos
- `nvim`: fork do `vim` (Neovim) com recursos adicionais
- Comandos do `vim`, executados no modo de comandos:
  - `:syntax on` e `:syntax off`: incluem e removem as cores do editor
  - `:w`: salva
  - `:wq`: salva e sai
  - `:q!`: sai sem salvar
