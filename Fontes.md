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

# Guia #4: Instalação de Fontes
Reúna o conjunto de fontes a serem instaladas em uma pasta. Usaremos no exemplo o diretório `~/Downloads/Fontes`.

Em seguida, crie via terminal uma pasta para abrigar as fontes no sistema:
```
$ sudo mkdir /usr/share/fonts/others
```
Ainda no terminal, copie as fontes para a nova pasta sob o comando `sudo`:
```
$ sudo cp -R ~/Downloads/Fontes/* /usr/share/fonts/others
```
Para definir as permissões dos arquivos, digite os seguintes comandos:
```
$ sudo chown -hR root:$USER /usr/share/fonts/others
```
```
$ sudo chmod 644 /usr/share/fonts/others/* -R
```
```
$ sudo chmod 755 /usr/share/fonts/others
```
Por fim, para compilar os caches de informações de fonte via `fontconfig`, digite no terminal:
```
$ sudo fc-cache -fv
```

[Voltar ao Topo](#sumário)

