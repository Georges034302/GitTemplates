## GitTemplates

This Template contains useful command blocks for Git setup and configuration.
  
### <Repo> Setup from CLI:

```
git init
git add -A
git commit -m "add project to existing repo"
git remote add origin https://github.com/Georges034302/<Repo>.git
git push -u -f origin master
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

gcc -Wall -ansi $1 $2 -lm -o $3

./$3
echo
```
### Acknowledgments

1. Hat tip to anyone whose code was used
2. Inspiration
3. etc

