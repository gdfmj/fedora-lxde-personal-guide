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

# Guia #2: Configurando o Menu LXDE
## ATENÇÃO!
PARA CADA ARQUIVO A SER MODIFICADO, CRIE UMA CÓPIA DE BACKUP COM O COMANDO:
```
$ sudo cp <origem> <destino>
```

##### DICA: Não exclua menus ou submenus padrões, visto que eles podem ser necessários para aplicativos posteriormente instalados. Você poderá alterar as categorias dos aplicativos para encaixar nas suas classificações, e os Menus que ficarem vazios não aparecerão.
-----------------------------
## Instruções
Arquivo para Adicionar (ou Excluir) os menus e submenus:
```
/etc/xdg/menus/lxde-applications.menu
```
Diretório onde cada menu e submenu tem seus arquivos de configurações `.directory`:
```
/usr/share/desktop-directories/
```
A estrutura destes arquivos obedece o padrão `Desktop Entry`, como no seguinte exemplo:
```
[Desktop Entry]
Name=Favoritos
Name[pt-BR]=Favoritos
Comment=Aplicativos Favoritos
Comment[pt-BR]=Aplicativos Favoritos
Icon=
Type=Directory
```
Para selecionar um ícone, acesse o diretório
`/usr/share/icons/`. Procure por um arquivo com o icone desejado e coloque o caminho. Cada aplicativo precisa ser configurado pelo seu `Desktop Entry` para se associar a um ou mais Menus ou Submenus. Em geral estes se encontram nos diretórios:


* Para os aplicativos compartilhados entre os usuarios do PC
```
/usr/share/applications/
```
* Para os aplicativos de um único usuario
```
/usr/local/share/applications/
```
ou
```
~/.local/share/applications/
```
O menu ao qual o aplicativo se associa deve estar escrito na linha de `Categories`, como no exemplo de `Desktop Entry` abaixo[¹](#dica-não-exclua-menus-ou-submenus-padrões-visto-que-eles-podem-ser-necessários-para-aplicativos-posteriormente-instalados-você-poderá-alterar-as-categorias-dos-aplicativos-para-encaixar-nas-suas-classificações-e-os-menus-que-ficarem-vazios-não-aparecerão):
```
[Desktop Entry]
Version=1.0
Name=Galculator
Comment=Perform simple and scientific calculations
Comment[pt_BR]=Executa cálculos simples e científicos
Exec=galculator
Icon=galculator
Terminal=false
Type=Application
Categories=Utility;Calculator;GTK;
StartupNotify=true
X-Desktop-File-Install-Version=0.26
```

[Voltar ao Topo](#sumário)