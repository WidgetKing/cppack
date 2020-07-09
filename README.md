# Description
CpPack is a command line tool which allows you to write javascript for Adobe Captivate in .js files, rather than using Captivate's Execute Javascript dialog.

CpPack has the following four features:
1. Initialize your javascript project with a folder structure for writing, compiling and testing your Captivate javascript code.
2. Merge multiple javascript files into a single javascript file.
3. Package the javascript file into a Web Object so it can be imported into Captivate.
4. Run a local host server where you can place your Captivate project export to test. Every time you edit your javascript code, the server will update the Captivate project with the latest code and refresh the page so you can test immediately.

# Installation
1. Download and install the [node.js](www.nodejs.org) command line tool. The recommended version is fine.
2. Open up a command line window and enter the following command:

```
npm install cppack -g
```

# Useage
All CpPack's features are implemented in three commands:

## init
When starting a new Captivate javascript process, navigate your command line to your javascript project folder and enter the following command:

```
cppack init
```

The CpPack tool will then ask you if you want to use **recommended** settings or **custom** settings. If you are not an experienced javascript programmer, the recommended settings will work fine for you. If you are more experienced, the custom settings will allow you to tinker with your folder structure so it fits your preferences.

The recommended settings will generate the following folder structure:

```
- dist (The merged javascript file and Web Object will be saved here)
- server (Test how your code will work in your Captivate project by including the project export in this folder)
- src (Folder for your javascript code)
-- index.js (Start writing javascript here)
- cppack-config.json (File which records your CpPack settings. Can be edited to fit your needs)
- package.json (Standard javascript projects include this file to keep track of your project's details and dependancies)
```
## pack
When you want to merge your javascript files into a Web Object that can be imported into Captivate, run the following command:

```
cppack pack
```

A new Web Object file will be generated in the 'dist' folder.

## run
When you want to rapidly test your code in a working Captivate project, navigate the command line to your javascript project folder and enter the following command:

```
cppack run
```

CpPack will now watch your javascript files. Whenever a file is saved it will run the **pack** command. CpPack will then search through the **server** folder. When it finds an old version of your code it will replace it with the new version that was just built.

This command will also create a local host server which serves up the contents of the **server** folder. You can access this local host server by entering the following into your browser:

```
https://localhost:8080
```

On that page you will be shown a menu that allows you to navigate the folder structure of the **server** folder. If you navigate to a Captivate export's index.html, it will display that Captivate project in the browser. While this project is being viewed, when you make a change to the code in your javascript files, the page will automatically refresh to show you how your latest code works in this project.

# Configuration
The **init** command will generate a file called: **cppack-config.json**

This text file records how you've configured CpPack. Advanced users can use this to further configure the way CpPack works. Basic users should not need to edit this file.

# Update
To update to the latest version of CpPack, run the following in the command line (It will not matter what directory the command line is in):

```
npm update -g cppack
```

If you want to know what version of CpPack you have currently installed, run this command:

```
cppack version
```
