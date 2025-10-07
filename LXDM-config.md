<!-->
====================================Aterar aparência do LXDM(Tela de Login)====================================
	!CUIDADO! Alterar o background do arquivo lxdm.config:

$ sudo nano /etc/lxdm/lxdm.conf

	Altere a linha abaixo de '## background of the greeter', atentando para a ausência do caractere '#' no início da linha alterada, para:

bg='localização-do-arquivo'

	Para alterar a imagem de Login, ícones e outras questões gráficas, modificar diretamente no tema existente (Industrial), através do diretório:

/usr/share/lxdm/themes/Industrial

	Para alterar cor, tamanho e fonte dos textos:

$ sudo nano /usr/share/lxdm/themes/Industrial/gtk.css
