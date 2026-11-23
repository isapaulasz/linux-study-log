# Seção 21 - Gerenciamento de serviços

## Aula 40 - Manipulando o systemd

- `systemd`: recebe o PID 1 e é o primeiro processo iniciado pelo kernel durante o boot; é responsável pelos serviços em execução no sistema operacional
- Se assemelha ao `services.exe` do Windows
- `systemctl`: comando para gerenciar o systemd
- `systemctl status`: mostra uma visão geral do sistema
- `systemctl status nomeservico`: mostra o status do serviço
- `systemctl stop nomeservico`: interrompe o serviço, exige login de administrador
- `systemctl start nomeservico`: inicia o serviço
- `systemctl restart nomeservico`: reinicia o serviço

## Aula 41 - Habilitando e desabilitando serviços, units

- `systemctl enable nomeservico`: habilita o serviço para iniciar junto com o boot
- `systemctl disable nomeservico`: desabilita o serviço
- Desabilitar não para o serviço: ele continua rodando até o próximo boot
- Para pará-lo imediatamente, é possível usar `systemctl stop`
- `systemctl cat nomeservico`: lê o arquivo de configuração (unit) do serviço
- Sockets são units associadas aos services: ficam escutando e acionam o serviço quando necessário
- O `systemd` possui diversos comandos próprios, que começam com `systemd-`
- `systemd-analyze`: apresenta quanto tempo levou para realizar o boot da máquina
- `systemd-analyze blame`: mostra o tempo que cada item levou para inicializar
- `systemd-cgtop`: equivalente ao `top` para o systemd

## Aula 42 - Caminho do diretório do systemd

- `ls /etc/init.d/`: mostra os arquivos de configuração dos serviços no SysV (System V)
- `ls /etc/systemd/`: mostra os arquivos de configuração dos serviços no systemd
- `ls /etc/systemd/system`: mostra as units configuradas pelo administrador; as units instaladas pelos pacotes ficam em `/usr/lib/systemd/system` (ou `/lib/systemd/system`)
