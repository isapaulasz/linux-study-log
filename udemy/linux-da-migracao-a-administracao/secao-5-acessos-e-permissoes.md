# Seção 5 - Acessos e permissões

## Tornando-se administrador

- Para se tornar usuário administrador e conseguir instalar programas, é necessário usar o comando `su`
- `su`: substitute user (ou switch user)
- É usado para trocar de usuário ou se tornar administrador (root)
- Fluxo: `su` → Enter → digitar a senha do root → o usuário passa a ser root
- Ao trocar para root dessa forma, o terminal se mantém na pasta em que estava e com o ambiente do usuário anterior
- Para trocar de usuário já carregando as variáveis de ambiente do novo usuário, é necessário escrever:
  - `su -`
  - ou `su - root`
  - (Enter, senha, etc)
- Para trocar para outros usuários, pode-se usar `su - nomeusuario`
- `sudo comando`: executa um único comando com privilégios de administrador, sem trocar de usuário (exige que o usuário tenha permissão no `sudo`)

## Saindo do usuário

- `exit`
- ou `Ctrl + D`

## Limpando a tela

- `Ctrl + L`
- ou `clear`
