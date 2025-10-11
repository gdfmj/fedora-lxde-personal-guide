<link rel="stylesheet" href="./style.css">
<style>
    /*body{
        background-color: #353535ff;
    }
    h1, h2, h3, h4 {
        color: #f7f7f7ff;
    }
    a {
        color: #e20000ff;
    }
    p, ul, ol {
        color: #ddddddff;
    }
    code {
        background-color: #000000;
        color: #ffffffff;
    }
    .highlight {
        background-color: #000000;
    }
    .markdown-body .highlight pre,
.markdown-body pre {
        background-color: #000000;
    }*/
</style>

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

-------------------
Segue a lista de documentação para navegação no repositório:
* [Índice](./README.md);
* [Guia #1: Pós-instalação](./Pós-instalação.md);
* [Guia #2: Configurando o Menu LXDE](./Menu-LXDE.md);
* [Guia #3: Configurando LXDM (Tela de Login)](#guia-3-configurando-lxdm-tela-de-login);
* [Guia #4: Instalação de Fontes](./Fontes.md);
* [Guia #5: Configuração das teclas de atalho 'Fn'](./Teclas-de-Atalho.md).