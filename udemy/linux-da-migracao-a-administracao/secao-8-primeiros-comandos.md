# Seção 8 - Primeiros comandos

## Aula 11 - Listando diretórios e informações do sistema

- Comandos para listar diretórios e acessá-los
- `ls`: list, lista o conteúdo dos diretórios
- `dir` também funciona
- `ls -a`: mostra tudo, inclusive arquivos ocultos (os que começam com ponto)
- `ls -l`: lista em formato detalhado, com o total de blocos do diretório, permissões de acesso, dono, grupo, tamanho e data de modificação dos arquivos e diretórios (ex: `drwxr-xr-x`)
- `ls -ld diretorio`: mostra informações somente do diretório, sem incluir o que está dentro dele
- `ls -s`: mostra o tamanho de cada arquivo em blocos
- `ls -Z`: mostra o contexto de segurança (SELinux) de cada arquivo
- `ls` + `Tab` (duas vezes): mostra as opções de autocompletar
- `lsblk`: lista dispositivos de bloco (discos e partições)
- `lspci`: mostra informações de hardware
  - `lspci -v`: mostra os detalhes de cada hardware
  - `lspci -vv`: aumenta as informações
  - `lspci -k`: boa opção para visualizar os drivers em uso
- `lsusb`: mostra quais dispositivos estão conectados às portas USB
- `lsmod`: mostra quais módulos (drivers) estão sendo utilizados
- `lsb_release -a`: mostra as informações da versão atual do sistema

## Aula 12 - Navegando entre diretórios

- `cd`: comando de acesso a diretórios
- `cd ..`: retorna para o diretório anterior (diretório pai)
- `cd Do` + `Tab`: completa ou mostra os diretórios que iniciam com `Do`
- `pwd`: mostra o diretório atual
- `echo`: escreve uma mensagem no terminal
- `echo $OLDPWD`: mostra o diretório em que eu estava anteriormente
- `cd -`: retorna para o diretório em que eu estava anteriormente
- Todos os comandos a seguir levam para a home:
  - `cd ~nomeusuario/` + `Tab`
  - `cd /home/nomeusuario`
  - `cd ~`
