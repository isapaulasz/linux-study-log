# Seção 7 - Obtendo ajuda pelo próprio terminal

## Aula 9 - Comandos para a obtenção de ajuda

- bash
  - `help`: lista os comandos internos do terminal
  - `help nomedocomando` ou `nomedocomando --help`: dá informações mais precisas sobre o comando
- zsh
  - `run-help`: ajuda para os comandos internos do zsh
- Dica: usar `alias` para padronizar comandos em diferentes terminais
  - `alias help=run-help`
  - o alias vale apenas para a sessão atual; para torná-lo permanente, inclua-o no arquivo de configuração do terminal (`~/.bashrc` ou `~/.zshrc`)

## Aula 10 - Comandos de busca e manpages

- Podemos consultar manuais (manpages) para cada comando
- `apropos palavra`: retorna tudo que existe no sistema com aquela palavra nas descrições, preferencialmente em inglês
- `man`: abre o manual de um comando
  - `man man`: manual do próprio manual
- O manual possui seções numeradas, que aparecem no `apropos` e de forma mais detalhada no `man`
  - ex: `man 1 passwd` (comando) e `man 5 passwd` (arquivo de configuração)
- `man -k palavra`: equivale ao `apropos`
- `man -w programa`: mostra o caminho do arquivo do manual no sistema
- `whatis programa`: retorna uma descrição curta do programa e as seções em que ele existe
- O `whatis` não funciona da mesma forma que o `apropos`: o `whatis` busca pelo nome do comando, enquanto o `apropos` busca a palavra nas descrições
