# Seção 19 - Usuários e grupos

## Aula 35 - Usuários e grupos

- `useradd`: cria usuários
- `adduser`: versão mais fácil de `useradd`, que guia a criação de forma interativa (específica do Debian e derivados)
- Ao criar um usuário é necessário definir uma senha, e é opcional adicionar mais informações do usuário, como nome completo, sala, telefone, etc
- `passwd usuario`: altera a senha
- `passwd -S usuario`: mostra o status da conta do usuário
- `passwd -l usuario`: trava a conta e não permite que o usuário faça login
- `chage -l usuario`: mostra as informações de expiração da senha e da conta
- `gpasswd -a usuario grupo`: adiciona o usuário a um grupo
- `groups usuario`: mostra os grupos em que o usuário está
- `deluser usuario`: exclui o usuário
  - usando `deluser --help` é possível ver as opções adicionais, como remover a home (`--remove-home`), fazer backup dos arquivos removidos (`--backup`), etc
- `delgroup grupo`: exclui o grupo
- `userdel` e `groupdel`: equivalentes presentes em todas as distribuições

## Aula 36 - Modificando informações dos usuários

- `sudo usermod -s /bin/zsh nomeusuario`: outra forma de mudar de terminal (nesse caso, para o zsh)
- `usermod --help`: mostra os outros parâmetros do `usermod`, que modifica o usuário
  - `-c`: comentários sobre o usuário
  - `-d`: novo diretório do usuário
  - `-e`: cria uma data de expiração do usuário
  - `-aG grupo`: adiciona o usuário a um grupo, mantendo os anteriores
  - entre outros
