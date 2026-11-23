# Seção 17 - Terminais de comandos

## Aula 31 - Como alterar entre terminais

- Bash não é a unica opção disponivel de terminal em linux
- cat /etc/shells permite ver o terminais disponiveis no sistema
- echo $SHELL permite ver o terminal atual
- zshell possui seu proprio diretorio
- zsh .: para alternar para o zshell
- chsh: change shell
  - chsh -s /bin/zsh: torna zsh o terminal padrao, mas exige reiniciar o terminal

## Aula 32 - Utilizando zsh no Fedora

- zsh: inicia shell
- existe configurações iniciais que precisam ser seguidas
- outra forma de utilizar é su - usuario

## Aula 33 - Entendendo os recursos do zsh

- configuração manual
- autoload compinit
- compinit
- autoload promptinit
- promptinit
- autoload tem muitas opções
- setopt
- ls **/**(.x) mostra todos os executaveis no ramo
- é possivel escrever caminhos absolutos usando somente as 2 primeiras letras dos diretorios
