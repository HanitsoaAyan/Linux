# Linux
EXERCICE  D’INSTALLATION A PARTIR D’UN CODE SOURCE 

INSTALLATION MYSQL :
	Commande utilisée : 
-Télécharger le code source de mysql 
-Entrer dans sudo su root 
-Entrer dans /usr/local
-Décompresser et désarchiver le code source : tar -xvf mysql-8.3.0-linux-glibc2.28-x86_64.tar.xz (code source)
-Dépendance à installer : apt install libaio1 (comme on est déjà dans root pas besoin de sudo)
-Créer un lien symbolique rattacher à l’installation créer par tar : ln -s mysql-8.3.0-linux-glibc2.28-x86_64 mysql  
-Déplacer dans mysql : cd mysql 
-Créer un dossier mysql et data : mkdir mysql-files data 
 Changement de groupe propiétaire d’un fichie : chown mysql:mysql mysql-files
-Changement de droit et permission : chmod 750 mysql-files
-Ouvrir le fichier <<my.cnf>> dans /etc/ : nano /etc/my.cnf
-Copier 4 lignes dans le fichier : 
	-[mysql]
	-basedir=/usr/local/mysql
	-datadir=/usr/local/mysql/data
	-user=mysql
-Initialize le data :dans  cd/usr/local/mysql  	bin/mysql –initialize –user=mysql
-Copier le mot de passe trouver dans l’initialisation 
-Commencer l’installation de la sécurité : bin/mysql_secure_installation (copier le mot de passe dans le fichier avant)
-Entrer un nouveau mot de passe 
-Répondre oui au question 
-bin/mysql -u root -p 
-Entrer cd 
-Entrer la commande ls -a (pour regarder si il y a .profil )
-Entrer nano .profil : copier 
	-PATH=$PATH:/usr/local/mysql/bin



INSTALLATION APACHE :
	Commande utilisée :
-Téléchargement du code source d’apache 
-Pour installer l‘apache il faut des dépendances 
-Décompresser et désarchiver le contenu de chaque dépendance 
	1)Premier dépendance :
	-Entrer dans cd Documents
	-Décompresser et désarchiver : tar -zxf apr-1.7.4.tar.gz 
	-Entrer dans cd apr-1.7.4/
	-lister pour voir le makefile 
	-Puis ./configure 
	-sudo make 
	-sudo make install 
	2)Deuxieme dépendance :
	-Entrer dans cd Documents
	-Décompresser et désarchiver : tar -zxf apr-util-1.6.3.tar.gz
	-Entrer dans cd apr-util-1.6.3/
	-lister pour voir le makefile 
	- ./configure : ERREUR
		-On fait ./configure –with-apr=/usr/local/apr
		-Télécharge expat : sudo apt install libexpat-dev
	-sudo make ou make 
	-sudo make install 
	3)Troisième dépendance :  
	-Entrer dans cd Documents
	-Décompresser et désarchiver : tar -jxf pcre-8.00.tar.bz2 
	-Entrer dans cd pcre-8.00/
	-lister pour voir makefile
	-./configure 
	-sudo make 
	-sudo make install 
	4)Dernier dépendance :
	-Entrer dans cd Documents 
	-Décompresser et désarchiver : tar -jxf httpd-2.4.59.tar.bz2
	-Entrer dans cd htpp-2.4.59/
	-lister pour voir le makefile 
	-./configure : ERREUR 
		-j’ai tous recommencer les dépendances et changer le make en make clean puis 
		-puis j’ai réécris après ./configure un make 
	-make install 


 
INSTALLATION PHP : 
	Commande utilisée :
-Télécharger le code source de php 
-Décompresser et désarchiver le code source : tar -zxf php 8.2.18.tar.gz
-Entrer dans cd php 8.2.18/
-lister pour voir makefile : ERREUR 
	-No package libxml-2.0 et ‘sqlite3’ 
	-Télécharger la dépendance demandé dans ./configure :
		-Entrer dans sudo su root 
		-apt install libxml2-dev
		-apt install sqlite3
		-apt install libsqlite3-dev
	-Refaire le ./configure pour voir si elle a bien été installer 
	-cmake 
	-make 
	-make test 
	-sudo make install 



