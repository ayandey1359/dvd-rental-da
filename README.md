# DVD Rental Data Analysis
## Over View  

## Platform
To complete this Data Analyse project I had used  
 * **SQL language**  
 * **pgAdmin4**  
 * **Apache Superset**  
 * **R programming**  
 * **R Studio**  
 * **LibreOffice Base**(RDBMS)  
 * **LibreOffice Calc**(Spread-Sheet)  
 *This all platform are use simultaneously*  
 **OS :** **Lubuntu 22.04**
 ---
## Environment Set-Up

---
### Apache Superset
* To Set up apache superset make sure python3.9 version should avaliable.As I am using Lubuntu 22.04 i had python3.10.That need to install python3.9 but make sure the defult python3.10 should not affected.  
Lets start by open the Terminal
```
# to confirm python version  
python3 --V
```
```
# intall python3.9  
$ sudo add-apt-repository ppa:deadsnakes/ppa  
$ sudo apt-get update  
$ sudo apt-get intall python3.9
```
- **goal**: to set python3.9 as defult also python3.10 as back , depending on dependency which verision are utilized.  
program_A need python3.9  
program_B need python3.10  
both will be used as per required.
for that to set up------>
```
# set python3.9 as option -1  
$ sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.9 1
```
```
# set python3.10 as option -2  
$ sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 2
```
```
# to set as per requirement  
$ sudo update-alternatives --config python3
```
After this set-up need to install Apache-Superset  
```
# to see all the dependancy  
$ sudo apt-get install build-essential libssl-dev libffi-dev python3-dev python3-pip libsasl2-dev libldap2-dev default-libmysqlclient-dev
```
```
# install the python3.9 virtual environment  
$ sudo apt install python3.9-venv python3.9-dev
```
```
# create a python3.9 virtual environment  
$ python3.9 -m venv my_project_venv
```
```
# active and enter in the virtual environment  
$ . venv/bin/activate
```
```
# install the Apache Superset  
$ pip install apache-superset
```
```
# active flask key  
$ export FLASK_APP=superset
```
```
# generate strog SSl key by:  
$ openssl rand -base64 42
```
```
# export that key
export SUPERSET_SECRET_KEY= "key-string"
```
```
# upgrade superset defult database
$ superset db upgrade
```
```
$ ls -a  
$ ls .superset/
```
```
# initialize the superset
superset init
```
```
# starting and deploy the superset server  
superset run -p 8099 --with-threads --reload --debugger
```
superset will open on firefox or any.  
every time to open superset need to run this followings  
```
$ . venv/bin/activate
$ export FLASK_APP=superset
$ superset init
$ export SUPERSET_SECRET_KEY= "key-string"  
$ superset run -p 8099 --with-threads --reload --debugger
```
![Apache Superset](img/superset_login_screen.jpg)  
now connect with database by SQL-Alchemy URL  
```
# URL syntax
$ rdbms://username:password@host_name or url / database_name
# example
postgresql://postgres:*********@localhost/my_database
```  
**Apache Superset + database**  

---
### R Set-Up

It is important to connect R with datadase.Because all work going inside the database.  
**Connect RStudio with data-base**---->  
As I use Lubuntu 22.04 A **Linux Distribution** need to innstall **unixODBC** driver  
**R--> ODBC --> Database** (connection)  
```
## install the unixODBC Driver (system driver )
$ sudo apt-get install unixodbc unixodbc-dev
```
```
# install PostgreSQL ODBC Drivers
$ sudo apt-get install odbc-postgresql
```
```
# to see details ( file )
$ odbcinst -j
```  
Now go to R Studio  
in R console  
```
# install the ODBC packages
$ install.packages("odbc")
```
```
# importing libraries
library(odbc)
library(DBI)

# connection code
con <- dbConnect(odbc::odbc(),
                 uid = "username",
                 server = "localhost",
                 pwd = "data base password")
                 port = 5432,
                 driver = "PostgreSQL Unicode",
                 database = "database_name",
```
**connection established**  
![RDatabase](img/r_connection_screen.png)
**RStudio + database**  


___

## Setting up packages in R
before install packages need to install packages depandacies..then the packages will be installed.  
```
# install dependencies
$ sudo apt-get install libcurl4-openssl-dev libssl-dev libxml2-dev
$ sudo apt-get install libharfbuzz-dev libfribidi-dev
$ sudo apt-get install libcairo2-dev
```
open terminal -> type **sudo R** -> R console  
```
#update R
> update.packages(ask = FALSE, checkBuilt = TRUE)
```
```
# install packages
> install.packages("textshaping")
> install.packages("ragg")
```
now all depandencies and supported pacakes are installed  
#### installing important packges
```
# install tidyverse
>install.packages("tidyverse")
```
```
# install R-Markdown
> install.packages("rmarkdown")
```
***********************************************************

## Importing Data
---
* This data set is avaliable in the official postgres learning platfrom and the database link is [here]()  





# Analytics
---
*
