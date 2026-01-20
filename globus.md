# Moving large files with Globus

## Installs
[Download Globus personal connector](https://www.globus.org/globus-connect-personal).

## Logging in to Globus
Type `app.globus.org` in a browser or open the Globus application (globus.app) if you have it installed locally. 

If moving files from your laptop, you must first launch the personal connector (it will run in the background).

## Confirm your laptop is a Collection

Launch the personal connector if you haven't already.

Select Collections. You should see your Laptop if the endpoint is setup correctly.

## Additional Endpoints
Click the following links to access the endpoints for HTCF and RIS.

[HTCF @ CGSSB](https://app.globus.org/console/endpoints/73a4842d-9bd4-41ab-9fe4-1b826bebf43f/overview)

[WashU RIS Research Storage](https://app.globus.org/console/endpoints/6f79e659-fa99-4fdc-aa56-1d7076296b72/overview)
This can't be bookmarked. 
```
# Lab files on RIS
/storage1/dbaldri/Active/
```
GTAC transfers will also occur on this endpoint.

## Moving Files

Select the split pane button.

On one pane, enter the path to the files and/or directories you will move. 
In the other pane, enter the path to the destination path.

Select the Transfer & Timer Options dropdown and check the following options.
- preserve source file modification times
- Fail on quota errors

Click the boxes next to the files to move. Select Start to begin the transfer.

## Recommended bookmarks
### HTCF
Inputs /lts/yourlab/yourproject/data/input/
Results /lts/yourlab/yourproject/data/results/

### Personal Computer
Downloads (mac) /Users/yourusername/Downloads/
Project folders

### Notes for Windows users
Use forward slashes for your paths.

## View Status of Transfer
Select the activity tab to see a history of transfers, and their status. 
Globus will check file integrity and transfer progress and alert you to issues. 
