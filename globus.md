# Moving large files with Globus

## Moving Files
[Transfering files with Globus tutorial.](https://docs.globus.org/guides/tutorials/manage-files/transfer-files/).

Select the split pane button.

On one pane, enter the path to the files and/or directories you will move. 
In the other pane, enter the path to the destination path.

Select the Transfer & Timer Options dropdown and check the following options.
- preserve source file modification times
- Fail on quota errors

Click the boxes next to the files to move. Select Start to begin the transfer.

## Installs
[Download Globus personal connector (if you need to transfer files to your laptop).](https://www.globus.org/globus-connect-personal).

## Logging in to Globus
Open [app.globus.org](https://app.globus.org/dashboard) in a browser or open the Globus application (globus.app) if you have it installed locally. 

If moving files from your laptop, you must first launch the personal connector (it will run in the background).

## Confirm your laptop is a Collection

Launch the personal connector if you haven't already.

Select Collections. You should see your Laptop if the endpoint is setup correctly.

## RIS Endpoints
Click the following links to access the endpoints.

[WashU RIS Research Storage](https://app.globus.org/console/endpoints/6f79e659-fa99-4fdc-aa56-1d7076296b72/overview)
This can't be bookmarked. 
```
# Lab files on RIS
/storage1/dbaldri/Active/
```
GTAC transfers will also occur on this endpoint.

## HTCF Endpoints
[oPool Sequencing Data](https://app.globus.org/file-manager?destination_id=d5e72d9a-ef3e-4253-a010-36f223db254a&destination_path=%2Flts%2Fdblab%2Fopool%2Fdata%2Finput%2F&two_pane=false)

### Notes for Windows users
Use forward slashes for your paths.

## View Status of Transfer
Select the activity tab to see a history of transfers, and their status. 
Globus will check file integrity and transfer progress and alert you to issues. 
