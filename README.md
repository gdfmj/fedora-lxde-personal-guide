# Guia #1: O QUE FAZER APÓS INSTALAR O FEDORA LXDE

## Softwares

Vamos rodar no terminal um código para limpar os aplicativos que não serão usados, pois serão substituidos por outros de nossa preferência:

```ruby
$ sudo dnf remove xpad abiword gnumeric pidgin midori sylpheed asunder brasero dnfdragora clipit
```

Após a limpeza de aplicativos, vamos atualizar os aplicativos restantes:

```ruby
$ sudo dnf update -y --allowerasing --best
```

Instalar os repositórios RPM Fusion Free & Nonfree:

```ruby
$ sudo dnf install -y --allowerasing --best https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm fedora-workstation-repositories
```

Agora vamos fazer a instalação dos pacotes rpm de aplicativos que serão melhor aproveitados em nossa curadoria:

```ruby
$ sudo dnf install -y --allowerasing --best git gtk4 ffmpeg ffmpeg-devel compton vlc gnome-screenshot evince libreoffice libreoffice-langpack-pt-BR sylpheed chromium cheese onedrive libreoffice-draw gimagereader-gtk gimp brightnessctl kolourpaint qlipper gxkb xev jgmenu-gtktheme jgmenu wmctrl
```

## Configurar o One Drive

Rode no terminal:

```ruby
$ onedrive --sync
```

Seguir as instruções impressas no terminal para vinculação da conta e esperar o download dos arquivos e diretórios do servidor. Ao finalizar, é necessário configurar a sincronização automática ao iniciar uma nova sessão com o usuário. Para isso, rode no terminal:

```ruby
$ sudo mkdir ~/.config/autostart/ && sudo leafpad ~/.config/autostart/OneDrive-autostart-synchronize.desktop
```

Na tela do leafpad, escreva o seguinte conteúdo:

```ruby
[Desktop Entry]

Type=Application
Exec=onedrive --synchronize
Name=OneDrive Autostart Synchronize
Comment=Execute a command to run an OneDrive synchronization at autostart session
Icon=./icons/cloud_icon.svg #Ícone sugerido, encontra-se no repositório no diretório relacionado
```

## Instalar Temas e Alterar Aparência:

### Temas

Remover os arquivos originais:

```ruby
$ sudo rm -r /usr/share/themes/Adwaita-dark
```

Baixar os repositórios:

```ruby
$ cd ~/Downloads && sudo git clone https://github.com/PapirusDevelopmentTeam/papirus-icon-theme.git /usr/share/themes/Papirus && sudo git clone https://github.com/kouros17/Adwaita-Maia-Dark.git /usr/share/themes/Adwaita-Maia-Dark && sudo git clone https://github.com/axxapy/Adwaita-dark-gtk2.git /usr/share/themes/Adwaita-Dark && sudo git clone https://github.com/shaggyz/openbox-tenebris.git /usr/share/themes/Tenebris
```

#### Ícones: 
* [Papirus](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)

#### Widgets:
* [Adwaita-dark (GTK-2 vem por padrão, mas falta o GTK-3)](https://github.com/axxapy/Adwaita-dark-gtk2);
* [Adwaita-Maia-dark (GTK-3 & GTK-2)](https://github.com/kouros17/Adwaita-Maia-Dark)

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

```ruby
$ sudo cp ./icons/system-log-out.png /usr/share/icons/Papirus-Dark/128x128/apps/ #Ícone sugerido, encontra-se no repositório no diretório relacionado
```

Alterar o arquivo de configuração do botão:

```ruby
$ sudo leafpad /usr/share/applications/lxde-logout.desktop
```

Nas linhas de nome, trocar `Name[pt_BR]` por:

```ruby
Name[pt_BR]=Opções de sessão
```

Na linha de Icon, trocar para:

```ruby
Icon=/usr/share/icons/Papirus-Dark/128x128/apps/system-log-out.png
```
