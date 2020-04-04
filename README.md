# AI-Powered-Image-Recognizers-from-Social-Media
Social Mapper is an Open Source Intelligence Tool that uses facial recognition to correlate social media profiles across different sites on a large scale. It takes an automated approach to search popular social media sites for targets' names and pictures to accurately detect and group a person’s presence, outputting the results into report that a human operator can quickly review.

Social Mapper has a variety of uses in the security industry, for example the automated gathering of large amounts of social media profiles for use on targeted phishing campaigns. Facial recognition aids this process by removing false positives in the search results, so that reviewing this data is quicker for a human operator.

Social Mapper supports the following social media platforms:

* LinkedIn
* Facebook
* Pinterest
* Twitter
* Google Plus
* Instagram
* VKontakte
* Weibo
* Douban

Social Mapper takes a variety of input types such as:

* An organisation's name, searching via LinkedIn
* A folder full of named images
* A CSV file with names and URL’s to images online

## Getting Started

These instructions will show you the requirements for and how to use Social Mapper.

### Prerequisites

As this is a Python3 based tool, it should theoretically run on Linux, ChromeOS ([Developer Mode](https://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/generic)) and macOS. The main requirements are Firefox, Selenium and Geckodriver. To install the tool and set it up follow these 4 steps:

1) Install the latest version of Mozilla Firefox for macOS here:

```
https://www.mozilla.org/en-GB/firefox/new/
```

Or for Debian/Kali (but not required for Ubuntu) get the non-ESR version of Firefox with:
```
sudo add-apt-repository ppa:mozillateam/firefox-next && sudo apt update && sudo apt upgrade
```

Make sure the new version of Firefox is in the path. If not manually add it.

2) Install the Geckodriver for your operating system and make sure it's in your path, on Mac you can place it in `/usr/local/bin`, on ChromeOS you can place it in `/usr/local/bin`, and on Linux you can place it in `/usr/bin`.

Download the latest version of Geckodriver here:

```
https://github.com/mozilla/geckodriver/releases
```

3) Install the required libraries:

On Linux install the following prerequisites:
```
sudo apt-get install build-essential cmake
sudo apt-get install libgtk-3-dev
sudo apt-get install libboost-all-dev
```

On Linux & macOS finish the install with:

```
git clone https://github.com/amir7587/AI-Powered-Image-Recognizers-from-Social-Media.git
cd social_mapper/setup
python3 -m pip install --no-cache-dir -r requirements.txt
```

On Mac look through the [setup/setup-mac.txt](setup/setup-mac.txt) file to view some additional xcode, brew and xquartz installation instructions.

4) Provide Social Mapper with credentials to log into social media services:

```
Open social_mapper.py and enter social media credentials into global variables at the top of the file
```

5) For Facebook, make sure the language of the account which you have provided credentials for is set to 'English (US)' for the duration of the run. Additionally make sure all of your accounts are working, and can be logged into without requiring 2 factor authentication. 

## Using Social Mapper

Social Mapper is run from the command-line using a mix of required and optional parameters. You can specify options such as input type and which sites to check alongside a number of other parameters which affect speed and accuracy.

### Required Parameters

To start up the tool 4 parameters must be provided, an input format, the input file or folder and the basic running mode:

```
-f, --format	: Specify if the -i, --input is a 'name', 'csv', 'imagefolder' or 'socialmapper' resume file
-i, --input	: The company name, a CSV file, imagefolder or Social Mapper HTML file to feed into Social Mapper
-m, --mode	: 'fast' or 'accurate' allows you to choose to skip potential targets after a first likely match is found, in some cases potentially speeding up the program x20
```

Additionally at least one social media site to check must be selected by including one or more of the following:

```
-a, --all		: Selects all of the options below and checks every site that Social Mapper has credentials for
-fb, --facebook		: Check Facebook
-tw, --twitter		: Check Twitter
-ig, --instagram	: Check Instagram
-li, --linkedin		: Check LinkedIn
-gp, --googleplus	: Check Google Plus
-vk, --vkontakte	: Check VKontakte
-wb, --weibo		: Check Weibo
-db, --douban		: Check Douban
```

### Optional Parameters

Additional optional parameters can also be set to add additional customisation to the way Social Mapper runs:

```
-t, --threshold		: Customises the facial recognition threshold for matches, this can be seen as the match accuracy. Default is 'standard', but can be set to 'loose', 'standard', 'strict' or 'superstrict'. For example 'loose' will find more matches, but some may be incorrect. While 'strict' may find less matches but also contain less false positives in the final report.
-cid, --companyid	: Additional parameter to add in a LinkedIn Company ID for if name searches are not picking the correct company.
-s, --showbrowser	: Makes the Firefox browser visible so you can see the searches performed. Useful for debugging.
-v, --version		: Display current version.
-e, --email		: Provide a fuzzy email format like "<f><last>@domain.com" to generate additional CSV files for each site with firstname, lastname, fullname, email, profileURL, photoURL. These can be fed into phishing frameworks such as Gophish or Lucy.
```

STEPS TO RUN THE PROGRAM(using linux commands):
1) git clone https://github.com/amir7587/AI-Powered-Image-Recognizers-from-SocialMedia.git   
2) cd social_mapper/setup
3) python3 -m pip install --no-cache-dir -r requirements.txt
4) Open social_mapper.py and enter social media credentials into global variables at the top of the file

To run The progran:

5) python social_mapper.py -f imagefolder -i /root/Desktop/social_mapper/Input-Examples/imagefolder/ -m fast -fb  

To view the profile link stored in csv file

6) cat SM-Results/results-social_mapper.csv

To view the profile link along with their images in html format

7) firefox SM-Results/results-social_mapper.html 

