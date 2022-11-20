## GitTemplates

This Template contains useful command blocks for Git setup and configuration.
  
### <Repo> Setup from CLI:

```
git init
git add -A
git commit -m "add project to existing repo"
git remote add origin https://github.com/<UserID>/<Repo>.git
git push -u -f origin master
```

### Enable and Setup Python Env on VsCode:

```
- On Windows:
  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process 
  py -3 -m venv .venv    
  .venv\scripts\activate

- On Linux:
  python3 -m venv .venv    
  source .venv/bin/activate

- To install a package in the workspace:
  python -m pip install <package-name>
```

### START/STOP MS SQL SERVICE (CMD or PowerShell):

```
- Open CMD in Administrator mode:
  net start SQLServerAgent
  net stop SQLServerAgent    

- Open PowerShell:
  Get-Service -Name MSSQLSERVER
  Set-Service -Name MSSQLSERVER -Status Running -PassThru
  Get-Service -Name MSSQLSERVER

```
  
### Connect to MySQL DB from CLI:

```
In CLI Type the command:
  mysql -u <username> -p -h <end-point>
  mysql -h <mysql-instance-dns> -P 3306 -u <username> -p
  
```

### Create and Run REACT app

```
npx create-react-app@5.0.0 my-app

npm start
```

### Building ThreeJS Project in VS Code:

* Download and extract Three JS package from: https://threejs.org/
* Create a folder called CGLabs
* Open that folder in vscode and create a subfolder called 'js'
* Copy 'three.js' from the 'ThreeJS/build' folder into 'js'
* Create index.html in CGLabs [by default vscode uses emmet to generate html snipets]
* Download 'Live Server extension' in vs code [live server provides local server live-runtime for static apps]
* Download Javascript ES6/ES7 extension
* Download Javascript Babel extension
* Create lab for each lab to develop threejs apps inside the labs folder
* Insert the labs js scripts into index.html and load using live server


### Enable ThreeJS autocomplete in VS Code:

* Install nodejs for your operating system [https://nodejs.org/en/download/]
* In the vscode terminal run the commands:
```
sudo apt install node
sudo apt install npm
sudo apt update
sudo apt upgrade
```
* In the vscode terminal run the command:  
```
npm init -y
[This command will generate the package.json file for your project]
```
* In the vscode terminal run the command:  
```
npm install @types/three 
[This command will install the ThreeJS definition module in vscode]
```
### Netbeans Fix Script:
```
#!/bin/bash

cd ~
rm -rf .netbeans*
rm -rf /tmp/`whoami`
```

### Compile and Run C Script:
```
#!/bin/bash

gcc -Wall $1 $2 -lm -o $3

./$3
echo
```
### Setting Grep output coloring
```
add: alias grep='grep --color=auto' to the .bashrc in home directory

or (bad fix)
export GREP_OPTIONS='--color=auto'
export GREP_COLOR='1;33'
echo
```

### Find and Kill Process Windows
```
netstat -pant | grep "8080"

taskkill /F /PID <process ID>
```


### MySQL Localhost Configuration:
*Database name: bookstoredb*
*Update: application.properties in the resources directory with your SQL parameters*
```
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5Dialect
spring.datasource.url=jdbc:mysql://${YOUR_HOSTNAME:localhost}:<SQL-PORT></SQL-PORT>/bookstoredb?serverTimezone=UTC
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.username=<SQL-Username>
spring.datasource.password=<SQL-Password>
```
## Hide DB Credentials

There are two ways to hide the DB credentials in the application.properties file
  
### Store the Credentials in the System Environment Variables

The dbuser and dbpassword are system variables that store the real credential in the System

```
spring.datasource.username=${dbuser}
spring.datasource.password=${dbpassword}
```

### Encrypt the Credentials using Jasypt (Java Simplified Encryption)

Jasypt (Java Simplified Encryption), provides encryption support for property sources in Spring Boot Applications.

#### Step 1: Add maven dependency of jasypt in pom.xml 

```
<!-- https://mvnrepository.com/artifact/com.github.ulisesbocchio/jasypt-spring-boot-starter -->
<dependency>
    <groupId>com.github.ulisesbocchio</groupId>
    <artifactId>jasypt-spring-boot-starter</artifactId>
    <version>3.0.4</version>
</dependency>

<plugin>
  <groupId>com.github.ulisesbocchio</groupId>
  <artifactId>jasypt-maven-plugin</artifactId>
  <version>3.0.4</version>
</plugin>
```

#### Step 2: Update the application.properties
Add the following Jasypt properties

```

spring.datasource.username=DEC(your-username)
spring.datasource.password=DEC(your-password)
jasypt.encryptor.iv-generator-classname=org.jasypt.iv.NoIvGenerator
jasypt.encryptor.algorithm=PBEWithMD5AndDES
jasypt.encryptor.password=techjava
jasypt.encryptor.keyObtentionIterations=1000
jasypt.encryptor.poolSize=1
jasypt.encryptor.providerName=SunJCE
jasypt.encryptor.saltGeneratorClassname=org.jasypt.salt.RandomSaltGenerator
jasypt.encryptor.stringOutputType=base64
```

DEC(your-username)
DEC(your-password)

Will be encrypted using the Jasypt algoritm by running the following command:

```
mvn jasypt:encrypt -Djasypt.encryptor.password=techjava
```

And change to:

spring.datasource.username=ENC(OQU5p/cR6Sw946szK78WWQ==)
spring.datasource.password=ENC(4oGwVGAp1KtoOSMkez70/vnm4m5u2H7L)

### ERRATA: CORS policy: No 'Access-Control-Allow-Origin':
*In case the CORS block requests to resources in local host*

* Option 1 (Easy Fix): Add the proper annotation in the back-end for the mapping functions
```
 @CrossOrigin(origins = "http://localhost:3000")

```

* Option 2 (Lazy Fix): Add CORS extension to your browser
```
https://mybrowseraddon.com/access-control-allow-origin.html

```
