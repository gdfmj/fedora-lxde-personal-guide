<!-->
====================================Instalar as fontes MS e outras====================================
	Reúna o conjunto de fontes a serem instaladas em uma pasta. Usaremos no exemplo a Pasta '~/Downloads/Fontes'.
	Em seguida, crie via terminal uma pasta para abrigar as fontes no sistema:

$ sudo mkdir /usr/share/fonts/others

	Ainda no terminal, copie as fontes para a nova pasta sob o comando 'sudo':

$ sudo cp ~/Downloads/Fontes/* /usr/share/fonts/others

	Para definir as permissões dos arquivos, digite os seguintes comandos:

$ sudo chown -hR root:$USER /usr/share/fonts/others

$ sudo chmod 644 /usr/share/fonts/others/* -R

$ sudo chmod 755 /usr/share/fonts/others

	Por fim, para compilar os caches de informações de fonte via fontconfig, digite no terminal:

$ sudo fc-cache -fv

