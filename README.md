# NFT-OpenSea-Auto-Upload version-1.5.0 
Python code to upload NFT's on OpenSea

Hey everyone, I created a Custom selenium python script borrowing bits and pieces from the Maxime OpenSea Auto Uploader script. I had tried using his script as it was, but I ran into many issues, probably mostly user error on my part (who knows)

Anyway, here it is... it only works with Json files currently because that's what i needed. This project was built more around my own needs and is uploaded to this repo in that way as well... It's NOT going to work for everyone, and you'll very highly likely need to modify the code to get it to work with your project. 
I'm sure that i could do some things to make it more user friendly... 

On the other hand, when i wrote it, it wasn't really designed to be the most user friendly or fully featured, its just a wham-bam thank you ma'am sorta "Git'er Done" kinda project. 

Changes might come down the road, but for the time being, if you're using multiple json files to upload to opensea, this should work for you (with a little elbow grease).

The way its supposed to work is, after setting up the folders and files, you add your Json files to the Data folder... you don't use the single Master Json file that's generated from say, the hashlips generator for instance... you would instead use the individual numbered json files. Add as many of those as you want to the data folder, and then run the script and once it starts it'll log into your metamask, go to to opensea, create an NFT (add properties, collection, set which blockchain, etc), it will then MINT that NFT and then LIST the NFT for whatever price set in the Json file... it will then go on to the next Json file in the data folder and do the same process for that until it has gone through all Json files.

Let me know what you think, and how i could improve my code. I'm open to hearing feedback and welcome changes.

# Automatically upload your NFTs on Opensea using Python Selenium.

* Sign up on [Opensea](https://opensea.io/).
* Sign up on [MetaMask](https://metamask.io/).

## What does this bot do?

This script allows you to upload and sell **as many NFTs as you want to Opensea**, all **automatically** and **quickly** (about 2 NFTs per minute) **with metadata integrated**, and **Ethereum** and **Polygon** Blockchains are supported.  

**You can decide whether you want to upload or sell your NFTs, or both**. Currently this code has a hard coded schedule of a 6 month sales listing (the old code was breaking at this point so i figured an easy fix was to just comment out that line of code and let the default value do its thing, since what I wanted was the default anyway)

## Instructions

* ### Basic installation of Python for beginners:
  * [Download this repository](https://github.com/Anubis-Society/NFT-OpenSea-Auto-Upload/archive/refs/heads/master.zip) or clone it by typing this command in your command prompt:
```
git clone https://github.com/kurtatwork/KurtAtWork-OpenSea-Auto-Uploader.git
```
  * It requires [Python](https://www.python.org/) 3.7 or a newest version - _developped with Python 3.9.7_.
  * Install [pip](https://pip.pypa.io/en/stable/installation/) to be able to have needed Python modules.
  * Open a command prompt in the repository folder and type:
```
pip install -r requirements.txt
```
* ### Configuration of the bot:
  * Extract the repository folder from the ZIP file, you should have a folder named  `KurtAtWork-OpenSea-Auto-Uploader-master`.
  * Download and install [Google Chrome](https://www.google.com/intl/en_en/chrome/).
  * Download the [ChromeDriver executable](https://chromedriver.chromium.org/downloads) that is compatible with the actual version of your Google Chrome browser and your OS (Operating System). To know your Google Chrome browser version, refer to: **_[What version of Google Chrome do I have?](https://www.whatismybrowser.com/)_**
  * Extract the executable file from the ZIP file and copy/paste it in the `assets/` folder of the repository.
  * Create your NFTs data files containing all details for each NFT. It currently MUST be JSON files. Examples provided in the 'data' foler in this project repo. 
  * Your NFT Json files must be located in the `data/` folder and the name of each one must be a number.
  * Make sure that your Json files match the formatting of the example Json sample files... if they do not match, i.e. you end up having to change the number of properties in the Json file, then changes may also need to be made to the main.py file in order to accomodate for those differences. 
  * Regardless of whether you changed the the formatting of the Json files, you will want to look into the code of the main.py file and see if you need to change things here or there to accomodate your particular project. there is a certain portion of the code that automatically spits out new Json files after the NFTs are minted and listed, and you may want to change some of the preset data there such as the 'tags' field, and other fields... There's probably a few other things you might want to change throughout for your project.
  * Feel free to reach out in a ticket request if you need assistance or if you have suggestions for ways to improve this script.
  * And again, if you enjoy this script or get some valuable use out of it, feel free to consider donating to my wallet, or purchasing an NFT from one of my collections.



## Data files structure

If you do not want to add details to the values not required, leave:

  * **an empty string** for JSON files: 
```json
"file_path": "....../Desktop/NFT/nft_0001.png",
"nft_name": "NFT #1",
"description": "",
```

<strong>Required values *</strong>  
  (Mandatory value in certain specified cases)


## Known issues and important things to know

* Make sure to **deposit Ethereum (ETH/WETH)** or **Polygon (MATIC)** on your wallet before proceeding to the sale. Otherwise the bot will cancel the sale.  
  Opensea needs an **Ethereum** wallet with more than **0.05 ETH** or a **Polygon** wallet with a deposit of **any amount**.

* The bot may crash at the beginning when loading the MetaMask extension (a Selenium module issue), An error like the one below should appear:  
```python
selenium.common.exceptions.WebDriverException:
Message: unknown error: failed to wait for extension background page to load:
chrome-extension://nkbihfbeogaeaoehlefnkodbefpgknn/background.html from timeout:
Timed out receiving message from renderer: 10.000
```
* When lauching the webdriver, Selenium can raise an exception:
```python
driver = webdriver.Chrome(service=Service( # DeprecationWarning using
TypeError: WebDriver.init() got an unexpected keyword argument 'service'
```
You must update your Selenium version to 4.1.0 or higher by typing in the command prompt:
```
pip install selenium --upgrade
```
You can now verify that a more recent version of Selenium is installed by typing:
```
pip show selenium
```  
