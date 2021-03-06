#### README FILE FOR TITAN ESPORTS GAME STATS (LEAGUE OF LEGENDS) ####

## LIST OF FILES ##

- **run.sh** - Main shell file to initalize stats process. The user must pass 2 arguments when running this file (the week and name of league). For example: ```./run.sh wk1 Divinity```
- **scripts/codes.js** - Javascript file where tournament codes will be placed. File contains valid tournament codes from Spring 2021 Invitational to utilize (need to be uncommented in document)
- **scripts/fetchGameData.js** - Javascript file handling data from Riot's API. These variables will need to be supplied by the user: ``tournament_key, verson``
- **scripts/credentials.json** - Json file to hold credentials for using Google's oauth. These variables will need to be supplied by the user: ```client_id, project_id, client_secret```
- **scripts/google_write.py** - Python script for writing to a specific Google Sheet's document (defined by ```code = ```)
- **scripts/GoogleSheetsAPI.py** - Python script for passing credentials to Google oauth (uses token.pickle, more below on this). Variables from **scripts/credentials.json** are passed to this script.
- **scripts/positions.csv** - Excel sheet that contains an ordered list of positions in League of Legends. This is a quick fix to Riot API listing both support and ADC as 'bottom lane' players as well as other issues where correct player positions were not recognized. 

## REQUIREMENTS ##
The following are required to run this script.

- [Node.js](https://nodejs.org/en/)
- [Google API Client](https://pypi.org/project/google-api-python-client/)
- [Python 3](https://www.python.org/downloads/)
- [PIP](https://pip.pypa.io/en/stable/reference/pip_install/) 

## ADDITIONAL FILE DETAILS ##
- **run.sh** - This document is the main handler. It calls files from ```scripts/``` as well as handles some of the formatting. The script utilizes simple native shell tools (*awk, cat, paste, tail*) to remove uncessary data, arrange columns in a specific order, and create formulas/columns to manipulate data.
- **scripts/codes.js** - This document is a container for tournament codes. Tournament codes are generated through [Riot's API](https://developer.riotgames.com/docs/lol) using the user's unique RGAPI key. Specifically for this program, codes should be included on a weekly basis (i.e., all codes for Week X will be placed in this file before running script).
- **scripts/fetchGameData.js** - This is the main logic file for handling Riot's API. User will need to create an [RGAPI developer key](https://developer.riotgames.com/docs/portal#product-registration_application-process) and include this key for variable ```tournament_key```. The current patch version should also be included in ```version```. The rest of the script handles what data we want to select from the Riot API. Since this is in a JSON format, the script also parses this data for easier output.
- **scripts/credentials.json** - This document holds all the necessary credentials for [Google OAuth](https://developers.google.com/identity/protocols/oauth2/javascript-implicit-flow). See link for specific details on how to handle this. 
- **scripts/google_write.py** - This document handles where to write the data to. Since TES runs multiple leagues, this document contains multiple leagues (and can easily be expanded). Parameters are passed from **run.sh** for specific league.
- **scripts/GoogleSheetsAPI.py** - This document handles the token and security credentials for Google OAuth as well as how the data will be written to the Google Sheet.

## ADDITIONAL INFORMATION ##
- A token.pickle file is required to store Google OAuth security and to access available services. This should be autogenerated when executing the script.

## CREDITS ##
Credit to Jetgorilla (https://github.com/broberts2), without his assistance this wouldn't have been possible. 
