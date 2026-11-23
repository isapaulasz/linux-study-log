# Seção 9 - Hierarquia de diretórios Linux

## Aula 13 - Estrutura de diretórios

- `/` (root ou raiz) e todos os seus diretórios
- `bin` (binary): diretório de programas, onde eles estão instalados; aqui estão comandos que utilizamos, como `ls`, `cp`, etc
- `sbin`: outro diretório de comandos, mas direcionado à administração do sistema, de uso do usuário root
- `boot`: onde ficam o kernel Linux e o carregador de boot (GRUB)
- `dev` (device): os arquivos que representam os dispositivos ficam aqui, como CPU, teclado e dispositivos de bloco (HD, SSD, pendrive)
  - tudo no Unix é representado por arquivos, e o kernel carrega o driver a partir deles
- `etc`: equivalente ao painel de controle do Windows ou às preferências do sistema do Mac; guarda os arquivos de configuração do sistema e dos programas
- `home`: pastas dos usuários, equivalente à pasta Users no Windows e no Mac
- `root`: pasta pessoal do usuário root, separada da `home` por questões de segurança
- `lib` e `lib64`: bibliotecas necessárias aos programas de `bin` e `sbin`, além de módulos do kernel
- `lost+found`: arquivos recuperados pelo sistema após falhas no sistema de arquivos
- `media` e `mnt`: dois diretórios com propósito parecido
  - `media`: onde são montados dispositivos de armazenamento removíveis (pendrive, CD)
  - `mnt`: usado para montagens manuais, geralmente de dispositivos fixos
- `opt`: semelhante ao `bin`, porém para programas de fornecedores externos (navegadores, IDEs, players, etc)
- `usr`: outro diretório que contém seu próprio `bin`, `lib`, interface gráfica, etc
- `proc`: sistema de arquivos virtual, que roda na memória e mostra informações dos processos e do kernel
- `sys`: informações sobre o hardware e os drivers em execução
- `run`: dados voláteis do sistema criados desde o boot
- `srv`: dados dos serviços fornecidos pelo sistema, como sites e FTP
- `tmp`: arquivos temporários, como vídeos sendo assistidos, que são armazenados e depois deletados
- `var`: dados variáveis, como logs, filas de impressão, páginas de internet e cache
  - dica: usar `aptitude clean` para limpar o cache de pacotes baixados

## Aula 14 - Caminhos relativos e absolutos

- Caminho relativo: quando navegamos pelos diretórios a partir de onde estamos
- Caminho absoluto: quando percorremos o caminho desde a raiz
- Exemplos:
  - `cd /`: vai para a raiz, de onde `ls` mostra todos os diretórios disponíveis
  - `cd /usr/bin`: exemplo de caminho absoluto
  - `cd ../etc`: exemplo de caminho relativo (sobe um nível e entra em `etc`)
