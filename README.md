  # WatchDog project

_________________________________
^^^Info about WatchDog project^^^
_________________________________

!!! To start on this project you need to install all necessary tools like python3, sqlite3, pip etc. To do that you need to go on folder and run the command bellow:
chmod 755 UtilitiesInstall 


@python vs python3
The app works with python3. If you use python and not the python3, you will face issues !

@To add on infinite loop to execute every X mins we use linux's 'crontab -e' more specific we add the 
line bellow: (Before you enter script to crontab make sure that you have set data.csv)
* * * * * /path to file/shellScriptAggregator.sh
* * * * * /path to file/BackupProcess.sh


	
	&& Python Files &&
_________________________________

--emailBase.py
The script that takes the message.txt file from flatFilesUtil/ and send the text through an email. It need the data.csv file that contains an email address (with credentials) 
to use it as source and destinations addresses. If data.csv doesn't exist then it ask from user to insert these info. At this point on 'crontab -e' command, already exist this file 
to works automated.

--movieWatchDog.py
This script download the given page and extracts the data we need to store them in database

--watchDogUtilities.py
Common function we need in other files. Basically it contains functions for path of files

--CustomeModels.py
Classes with the models we need on scripts

--SqliteQueryTool.py
It's a python file that contains all functions needed to manipulate SQLite database.

--createMessage.py
This script BASED ON input argument either fetch all the data we want to send through an email, either mark all unread rows as sended to avoid sending any duplication of data. The project on which will make the changes
depend on the arguments user will impliment.
The script works only with this arguments:
	- 'tableName'
    - 'tableName' update
    - 'tableName' 'pathForMessage'
    - 'tableName' 'pathForDb' update
    - 'tableName' 'pathForMessage' 'pathForDb'
    - 'tableName' 'pathForMessage' 'pathForDb' update



	&& Bash Shell Scripts &&	
_________________________________

--shellScriptAggregator.sh
It the bash script that execute every py script we want on right order. If something go wrong, it notify the user with error message

--storageConfigure.sh
It init the tables we need in db from .sql files in sqlCommands

--UtilitiesInstall.sh
It has been created to run only one time, to init and install any necessary tool that project needs


	&& Directories &&
_________________________________

--flatFilesUtil
It contains all the data files project needs to run 	

--DBUtil
All about SQLite3 (files and folders)

--sqlCommads
The folder with all the .sql command (in file). Basically its the 'create table' and stuff like that


	&& Other files &&
_________________________________

--data.csv
The csv file that contain the destinations emails and the source email with its credentials. The first line contains the source email and the others is the destination emails

--message.txt 
The message that the emailBase.py will send through an email
	
--watchDogDB.sqlite
The Base of whole project