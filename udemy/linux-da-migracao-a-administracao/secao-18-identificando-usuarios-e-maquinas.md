# Seção 18 - Identificando usuários e máquinas

- O terminal bash mostra usuário e máquina no prompt, mas outros terminais, como o dash, não mostram
- `whoami`: mostra o usuário
- `who am i`: versão alternativa que mostra mais informações
- `who`: mostra os usuários logados
- `w`: mostra mais informações sobre todos os usuários
- `loginctl`: gerenciador de sessões do systemd, mostra sessão, uid e usuário
  - `loginctl kill-session ID`: semelhante a encerrar a sessão pela interface
- `users`: mostra os usuários logados
- `id`: mostra o ID de cada usuário
- `hostname`: mostra o nome da máquina
- `uname`: mostra o nome do sistema operacional (kernel); `uname -a` mostra todas as informações
- `arch`: mostra a arquitetura da máquina
- `hostnamectl`: versão mais completa do `hostname`
- `lsb_release -a`: mostra informações semelhantes ao `hostnamectl`
