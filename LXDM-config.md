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

# Guia #3: Configurando LXDM (Tela de Login)
#### CUIDADO! Qualquer configuração feita de forma equivocada pode comprometer a instalação. Tenha sempre um backup e uma saída de emergência.
Alterar o background do arquivo `lxdm.config`:
```
$ sudo leafpad /etc/lxdm/lxdm.conf
```
Altere a linha abaixo de `## background of the greeter`, retirando o caractere de comentário `#` no início da linha alterada e escrevendo assim:
```
bg='./src/lxdm-background.jpg' #Imagem sugerida, encontra-se no repositório no diretório relacionado.
```

Para alterar a imagem de Login, ícones e outras questões gráficas, modificar diretamente no tema existente (Industrial), através do diretório:
```
/usr/share/lxdm/themes/Industrial
```
Para alterar cor, tamanho e fonte dos textos:
```
$ sudo nano /usr/share/lxdm/themes/Industrial/gtk.css
```

[Voltar ao Topo](#sumário)