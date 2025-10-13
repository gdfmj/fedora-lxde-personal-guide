<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Raleway:ital,wght@0,100..900;1,100..900&display=swap" rel="stylesheet">
<link rel="stylesheet" href="./style.css">

## [Sumário](#sumário)

* [Ínício](./README.md);
* [Guia #1: Pós-instalação](#guia-1-o-que-fazer-após-instalar-o-fedora-lxde);
* [Guia #2: Configurando o Menu LXDE](./Menu-LXDE.md);
* [Guia #3: Configurando LXDM (Tela de Login)](./LXDM-config.md);
* [Guia #4: Instalação de Fontes](./Fontes.md);
* [Guia #5: Configuração das teclas de atalho 'Fn'](./Teclas-de-Atalho.md).

-------------------

# Guia #1: O QUE FAZER APÓS INSTALAR O [FEDORA LXDE](https://fedorabr.org/categories/lxde)

Sumário:

* [Softwares](#softwares);
* [Instalar Temas e Alterar Aparência](#instalar-temas-e-alterar-aparência);
* [Configuarar o OneDrive](#configurar-o-one-drive);
* [Configurando o JGMenu](#configurando-o-jgmenu);
* [WebApps e Sofwares Extras](#webapps-e-sofwares-extras);
* [Softwares de Inicialização](#softwares-de-inicialização);
* [Desligar/Reiniciar via Terminal](#desligarreiniciar-via-terminal).
## Softwares

Vamos rodar no terminal um código para limpar os aplicativos que não serão usados, pois serão substituidos por outros de nossa preferência:

```
$ sudo dnf remove xpad abiword gnumeric pidgin midori sylpheed asunder brasero dnfdragora clipit
```

Após a limpeza de aplicativos, vamos atualizar os aplicativos restantes:

```
$ sudo dnf update -y --allowerasing --best
```

Instalar os repositórios [RPM Fusion](https://rpmfusion.org/) Free & Nonfree:

```
$ sudo dnf install -y --allowerasing --best https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm fedora-workstation-repositories
```

Agora vamos fazer a instalação dos pacotes rpm de aplicativos que serão melhor aproveitados em nossa curadoria:

```
$ sudo dnf install -y --allowerasing --best git gtk4 ffmpeg ffmpeg-devel compton vlc gnome-screenshot evince libreoffice libreoffice-langpack-pt-BR sylpheed chromium cheese onedrive libreoffice-draw gimagereader-gtk gimp brightnessctl kolourpaint qlipper gxkb xev jgmenu-gtktheme jgmenu wmctrl
```

## Instalar Temas e Alterar Aparência

### Temas

Remover os arquivos originais:

```
$ sudo rm -r /usr/share/themes/Adwaita-dark
```

Baixar os repositórios:

```
$ cd ~/Downloads && sudo git clone https://github.com/PapirusDevelopmentTeam/papirus-icon-theme.git /usr/share/icons/Papirus && sudo git clone https://github.com/kouros17/Adwaita-Maia-Dark.git /usr/share/themes/Adwaita-Maia-Dark && sudo git clone https://github.com/axxapy/Adwaita-dark-gtk2.git /usr/share/themes/Adwaita-Dark && sudo git clone https://github.com/shaggyz/openbox-tenebris.git /usr/share/themes/Tenebris
```

#### Ícones: 

* [Papirus](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)

#### Widgets:

* [Adwaita-dark](https://github.com/axxapy/Adwaita-dark-gtk2) (GTK-2 vem por padrão, mas falta o GTK-3);
* [Adwaita-Maia-dark](https://github.com/kouros17/Adwaita-Maia-Dark) (GTK-3 & GTK-2)

#### Openbox(Borda da Janela): 

* [Tenebris](https://github.com/shaggyz/openbox-tenebris)

### Opções de Interface

#### Relógio digital:

* Formato do relógio: `%a %d de %b %R`; 
* Formato da dica: `%A, %d de %B de %Y - %X`

#### Monitor de Baterias: 

* Cor de fundo: `#4e4e4e`; 
* Cor de carregamento: `#00bfff`; 
* Cor de descarregamento: `#dfdfdf`

### Botão de Logout

Copiar o ícone personalizado para a pasta comum:

```
$ sudo cp ./src/system-log-out.png /usr/share/icons/Papirus-Dark/128x128/apps/ #Ícone sugerido, encontra-se no repositório no diretório relacionado
```

Alterar o arquivo de configuração do botão:

```
$ sudo leafpad /usr/share/applications/lxde-logout.desktop
```

Nas linhas de nome, trocar `Name[pt_BR]` por:

```
Name[pt_BR]=Opções de sessão
```

Na linha de `Icon`, trocar para:

```
Icon=/usr/share/icons/Papirus-Dark/128x128/apps/system-log-out.png
```

## Configurar o One Drive

Rode no terminal:

```
$ onedrive --sync
```

Seguir as instruções impressas no terminal para vinculação da conta e esperar o download dos arquivos e diretórios do servidor. Ao finalizar, é necessário configurar a sincronização automática ao iniciar uma nova sessão com o usuário. Para isso, rode no terminal:

```
$ sudo mkdir ~/.config/autostart/ && sudo leafpad ~/.config/autostart/OneDrive-autostart-sync.desktop
```

Na tela do leafpad, escreva o seguinte conteúdo (é recomendada a [instalação dos ícones Papirus](#ícones)):

```
[Desktop Entry]

Type=Application
Exec=onedrive --sync
Name=OneDrive Autostart Sync
Comment=Execute a command to run an OneDrive synchronization at autostart session
Icon=/usr/share/icons/Papirus/Papirus/128x128/apps/ms-onedrive.svg
```

## Configurando o [JGMenu](https://github.com/jgmenu/jgmenu)

Com o `jgmenu` instalado, criar o diretório de configuração - caso ainda não exista - e mudar as permissões de usuário:

```
$ mkdir ~/.config/jgmenu && sudo chmod -hR $USER ~/.config/jgmenu
```

São três arquivos que definem as configurações do `jgmenu`:

* [`jgmenurc`](#jgmenurc): configura os parâmetros gráficos do menu;
* [`prepend.csv`](#prependcsv): configura os aplicativos fixos do menu;
* [`schema`](#schema): configura as sessões de aplicativos do menu.

### jgmenurc

Agora com o `leafpad`, vamos criar um arquivo chamado `jgmenurc` dentro desse diretório com o seguinte comando:

```
$ sudo leafpad ~/.config/jgmenu/jgmenurc
```

O arquivo `jgmenurc` deve conter os parâmetros seguintes:

```
stay_alive           = 1
position_mode        = fixed
menu_width           = 360
menu_padding_top     = 0
menu_padding_right   = 0
menu_padding_bottom  = 0
menu_padding_left    = 0
menu_radius          = 10
menu_border          = 2
menu_halign          = left
sub_hover_action     = 1
item_margin_y        = 5
item_height          = 36
item_padding_x       = 8
item_radius          = 0
item_border          = 0
sep_height           = 1
font                 = Sans 16px
icon_size            = 32
icon_text_spacing    = 10
icon_theme           = Papirus
color_menu_bg = #2f2f2f 100
color_norm_bg        = #2b303b 0
color_norm_fg = #ffffff 100
color_sel_bg = #15539e 100
color_sel_fg = #ffffff 100
color_sep_fg         = #8fa1b3 40
color_title_fg = #ffffff 100
color_title_bg = #2f2f2f 100
color_title_border = #2f2f2f 100
```

### prepend.csv

Um segundo arquivo que deve ser criado no diretório é o `prepend.csv`, novamente utilizando o `leafpad`:

```
$ sudo leafpad ~/.config/jgmenu/prepend.csv
```

O conteúdo do arquivo `prepend.csv` depende da [instalação dos ícones Papirus](#ícones):

```
^sep(Menu de Aplicativos)
Terminal,lxterminal,/usr/share/icons/Papirus-Dark/128x128/apps/terminal.svg
Arquivos,pcmanfm,/usr/share/icons/Papirus-Dark/128x128/places/user-home.svg
Navegador,microsoft-edge,/usr/share/icons/Papirus-Dark/128x128/apps/microsoft-edge.svg
E-mail,sylpheed,/usr/share/icons/Papirus-Dark/128x128/apps/mailspring.svg
Office,libreoffice,/usr/share/icons/Papirus-Dark/128x128/apps/libreoffice.svg
^sep()
```

### schema

O último arquivo a ser adicionado no diretório é o `schema`,  mais uma vez via `leafpad`:

```
$ sudo leafpad ~/.config/jgmenu/schema
```

Mais uma vez é recomendada a [instalação dos ícones Papirus](#ícones):

```
Name=Acessórios
Icon=/usr/share/icons/Papirus-Dark/128x128/apps/administration.svg
Categories=Accessibility;Core;Utility;Development

Name=Internet e Aplicativos Web
Icon=/usr/share/icons/Papirus-Dark/128x128/apps/dhcpcd.svg
Categories=Network;Favoritos

Name=Multimídia
Icon=/usr/share/icons/Papirus-Dark/128x128/apps/media-player-48.svg
Categories=Game;Graphics;Audio;Video;AudioVideo

Name=Escritório e Estudos
Icon=/usr/share/icons/Papirus-Dark/128x128/apps/bookworm.svg
Categories=Education;Office

Name=Sistema
Icon=/usr/share/icons/Papirus-Dark/128x128/devices/cpu.svg
Categories=Emulator;System

Name=Configurações
Icon=/usr/share/icons/Papirus-Dark/128x128/apps/configurator.svg
Categories=Settings;SystemConfig
```

### Lançador do Menu

Para que o jgmenu tenha um funcionamento adequado, vamos criar um arquivo `.desktop` em `/usr/share/applications/`:

```
$ sudo leafpad /usr/share/applications/Apps.desktop
```

Preencher com a entrada a seguir:

```
[Desktop Entry]
Name=Apps
GenericName=Menu
Comment=Menu JGMenu
Exec=jgmenu_run
Categories=Settings;
Icon=/usr/share/icons/Papirus-Dark/32x32/apps/distributor-logo-fedora.svg
Type=Application
Terminal=false
```

Para finalizar esta etapa, criar via interface gráfica um lançador no local desejado para abrir o menu de aplicativos.

## WebApps e Sofwares Extras

No `Chromium`, acessar e instalar os seguintes sites como WebApps: ['Whatsapp'](https://web.whatsapp.com/); ['OneDrive'](https://onedrive.live.com/); ['Kindle'](https://ler.amazon.com.br); ['Google Tradutor'](https://translate.google.com/?sl=pt&tl=en&op=translate) e ['YouTube Music'](https://music.youtube.com/).

Alguns Softwares ainda precisam ser instalados de modo alternativo. É o caso do [JDownloader 2](https://jdownloader.org/jdownloader2), o qual pode ser instalado via terminal, a partir da pasta `~/Downloads`:

```
$ cd Downloads
```

Após entrar na pasta, execute:

```
$ wget -c http://installer.jdownloader.org/JD2Setup_x64.sh
```

Após o download, dê permissão de execução ao executável:

```
$ chmod +x JD2Setup_x64.sh
```

E execute-o com:

```
$ sh JD2Setup_x64.sh
```

Será exibido o instalador do JDownloader 2. É só seguir os passos e instalar o programa.

## Softwares de Inicialização

No LXSession, colocar para iniciar: `onedrive --sync`; `alsamixer`; `compton`

## Desligar/Reiniciar via Terminal

Para cada finalização é recomendado o uso do terminal. Para desligar o PC verificando atualizações, rodar sempre:

```
$ sudo dnf upgrade -y --allowerasing --best && onedrive --sync && poweroff
```

Para reboot, rode no terminal:

```
$ sudo dnf upgrade -y --allowerasing --best && onedrive --sync && reboot
```

[Voltar ao Topo](#sumário)
