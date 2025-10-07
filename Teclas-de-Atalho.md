# Guia #5: Configuração das teclas de atalho 'Fn'
Faremos a configuração das teclas de atalho Fn (Super/Menu, Áudio e Brilho).

Com os comandos `jgmenu`, `brightnessctl` e `alsamixer` [instalados](./Pós-instalação.md#softwares), verifique qual a saída de `keycode` do atalho a ser utilizado (p. e.: 'Fn' + 'F6' = `XF86MonBrightnessUp`). Para isso use o comando:
```
$ xev -1
```
Com o comando sendo reproduzido, aperte as teclas do atalho desejado, e note a parte da saída similar a `keycode ## (keysym #x#####, XF86NomedaAçãodoAtalho)`. Anote o código similar a `XF86NomedaAçãodoAtalho` para cada atalho desejado.

Após isso, edite o documento `~/.config/openbox/lxde-rc.xml`:
```
$ sudo nano ~/.config/openbox/lxde-rc.xml
```
Adicione as seguintes linhas, com a substituição dos códigos correspondentes (caso necessário), na seção de keybindings:
```
    <!-- Super to open Menu -->
    <keybind key="Super_L">
      <action name="Execute">
       	<command>jgmenu_run</command>
      </action>
    </keybind>
    <!-- Set Brightness Level Up -->
    <keybind key="XF86MonBrightnessUp">
      <action name="Execute">
          <command>brightnessctl s 10%+</command>
      </action>
    </keybind>
    <!-- Set Brightness Level Down -->
    <keybind key="XF86MonBrightnessDown">
      <action name="Execute">
          <command>brightnessctl s 10%-</command>
      </action>
    </keybind>
    <!-- Set Audio to Mute -->
    <keybind key="XF86AudioMute">
      <action name="Execute">
          <command>amixer set Master toggle</command>
      </action>
    </keybind>
    <!-- Set Audio level Up -->
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
          <command>amixer set Master 3500+</command>
      </action>
    </keybind>
    <!-- Set Audio level Down -->
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
          <command>amixer set Master 3500-</command>
      </action>
    </keybind>
```
Ao reiniciar a sessão, verifique se fez efeito. 

#### PS: em geral, o comando `amixer` vem instalado nas distribuições linux. Se esse não for o caso, é necessário instalar via `dnf`:
```
$ sudo dnf install amixer
```
Ou ainda, caso deseje, utilize outro comando que obtenha o resultado pretendido para mutar ou mudar o volume

-------------------
Segue a lista de documentação para navegação no repositório:
* [Índice](./README.md);
* [Guia #1: Pós-instalação](./Pós-instalação.md);
* [Guia #2: Configurando o Menu LXDE](./Menu-LXDE.md);
* [Guia #3: Configurando LXDM (Tela de Login)](./LXDM-config.md);
* [Guia #4: Instalação de Fontes](./Fontes.md);
* [Guia #5: Configuração das teclas de atalho 'Fn'](#guia-5-configuração-das-teclas-de-atalho-fn).