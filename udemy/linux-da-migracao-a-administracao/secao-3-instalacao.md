# Seção 3 - Instalação do Linux

- Links para download:
  - Debian: https://www.debian.org/
  - VirtualBox: https://www.virtualbox.org/
- O VirtualBox permite criar uma máquina virtual para instalar o Linux sem alterar o sistema principal do computador
- Na aula é feito o download da versão 9.8 do Debian, porém, na data desta anotação, a versão mais atual era a 13.7 (confira a versão vigente no site oficial)

## Versões de instalação do Debian

- Existem diversas versões do Debian para download:
  - versão de instalação (CD/DVD ou netinstall)
  - versão live CD (imagem live), que permite rodar o sistema sem instalar; outras distros oferecem o mesmo recurso
  - versão torrent
  - computadores com Debian pré-instalado, entre outras
- A versão indicada pelo professor é a netinstall
- Na versão de CD, a instalação vem do conteúdo gravado no próprio CD
- Na versão netinstall, os pacotes são baixados direto da rede, de algum servidor

## Processo de instalação

- Menu do carregador de boot: existe a opção de instalação com e sem interface gráfica; é opcional, mas a interface gráfica oferece um instalador mais agradável
- Durante a instalação é necessário selecionar:
  - idioma
  - rede
  - nome da máquina
  - senha do usuário root (administrador)
  - criação de um usuário comum
  - fuso horário (horário local)
- Em seguida inicia o particionamento de disco, que pode ser feito de duas formas:
  - manualmente
  - assistido, em que o instalador sugere o esquema e podemos personalizá-lo
- O Linux precisa, no mínimo, de uma partição raiz (`/`), onde fica o sistema; normalmente cria-se também uma partição de swap, usada como memória virtual
- O particionamento usando o disco inteiro formata o disco e apaga tudo que há nele
- Existe a opção de espelho de rede (mirror), que escolhe um servidor de origem para baixar os pacotes e disponibiliza opções de programas para instalar
