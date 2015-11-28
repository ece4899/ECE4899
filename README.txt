Author: David Kalina

For senior seminar PANDa logger project ECE4899

Hopefully this will help install the necessary files/configurations needed...

Assumptions: Raspbian is installed and running

I	Install a local web Server -
sudo apt-get update

sudo apt-get install apache2 php5 libapache2-mod-php5

now you should allow overrides by editing the 000-default file, you can do that using the following comands..

sudo nano /etc/apache2/sites-enabled/000-default

now edit the following lines

change "AllowOverride None" -to "AllowOverride ALL".

now execute 

sudo service apache2 restart

to restart apache witht your new settings

now your site should be up and running u can go to /var/ and change the permissions on www, making it writable.

cd /var/
sudo chmod 777 /www

this will enable you to login upload HTML pages to your new site. open the browser on your PC and point to 192.168.xx.xx (ip address of you raspberry pi) to view the default page.


II	Install phpmyadmin - 
Many ways to do this, but this tutorial should be sufficient
http://raspipress.com/2012/09/tutorial-install-phpmyadmin-on-your-raspberry-pi/

III	Build the site -
using SFTP or UNIX install all the "WEBSITE" files into your new apache server. 

IV	Create the tables -
You will need tables for each sensor, listed are commands to create them in phpmyadmin
//Create table
USE DBNAME...;
CREATE TABLE TABLENAME...(
UserID int(10) NOT NULL AUTO_INCREMENT,
COLUMN1... varchar(255) NOT NULL,
COLUMN2... varchar(255) NOT NULL,
PRIMARY KEY (UserID)
)

V	Inserting values -
Once you feel the DB has been properly set up and is displaying correctly you can run
python BMP180.py

on the command line you will see....
Data Committed 

every two minutes to let you know of successful insertion. Refreshing the browser will show the new points on the graph.
