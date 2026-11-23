# Seção 6 - Instalação de programas

## Aula 6 - Aplicações gráficas para instalação, atualização e remoção de programas

- É possível instalar e remover programas através da interface gráfica
- YaST: um dos pioneiros de instalação gráfica de programas no Linux; só está disponível para uma distro (openSUSE)
- Synaptic: fortemente utilizado no Debian
- Central de programas do Ubuntu: o mais popular por ser usado no Ubuntu
- Software Boutique: permite uma variedade de opções (presente no Ubuntu MATE)
- A diversidade de opções de interface gráfica pode tornar a escolha mais confusa, mas, no final, existem poucas diferenças

## Aula 7 - Gerenciador de pacotes (usando os repositórios)

- Gerenciadores de pacote: programas usados no terminal, que agem da mesma forma que os programas gráficos
- `apt`: advanced package tool
  - `apt-cache search`: descobrir um programa
  - `apt-cache show`: mostra a descrição do programa
  - `apt-get install`: instalar programas
  - `apt-get update`: atualiza a lista de pacotes disponíveis nos repositórios
  - `apt-get upgrade`: atualiza os programas instalados no sistema
  - `apt-get remove`: apagar apps
  - `apt-get purge`: apaga apps junto com seus arquivos de configuração
  - `apt-get source`: baixa o código-fonte do programa
- `aptitude`: permite fazer tudo, como `search`, `show`, `install` e `remove`
- Os comandos `apt-get` e `apt-cache` possuem versões unificadas no `apt`, como `apt search`, `apt show` e `apt install`
- Instalar, atualizar e remover programas exige privilégios de administrador

## Aula 8 - Instalação de programas utilizando gerenciadores de baixo nível

- `apt` e similares são gerenciadores de pacotes que buscam os programas nos servidores, junto com suas dependências
- Quem faz a instalação de fato são os gerenciadores de pacote de baixo nível, como o `dpkg`
- Download de teste: Skype (descontinuado em 2025, mas o procedimento vale para qualquer arquivo `.deb`)
- Passo a passo:
  - fazer o download do arquivo `.deb`
  - ler as informações do pacote: `dpkg -I skypeforlinux-64.deb`
  - instalar: `dpkg -i skypeforlinux-64.deb`
- O `dpkg` não resolve dependências automaticamente
  - `apt-get install -f`: corrige as dependências faltantes após a instalação
  - `apt install ./skypeforlinux-64.deb`: instala o `.deb` já resolvendo as dependências
