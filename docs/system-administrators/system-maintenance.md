# System Maintenance

## Add Survey Images

If **Scout** is running, it automatically checks this folder periodically for new images and copies them for internal storage and processing. Images added to this folder disappear from the Ubuntu desktop folder as **Scout** imports them.
 
Note: Anyone who has access to the **Scout** Server or the NAS remotely can copy aerial survey images into the `/data/scout/images` folder.
 
An alert bar displays in **Scout** when image ingestion is in progress, warning users that new images are being added and therefore not all images may be available for task creation.

## NAS Disconnection and Reconnection

```{warning}
Ensure the Ubuntu user account has write permissions for all folders and is the same account used to start the Scout container.
```

The following process is useful if you need to disconnect and reconnect the NAS while Scout is running and are unable to start or restart Scout.

1. Delete the file `data/scout/tmp/config/settings.json` from the Ubuntu Terminal
    * Using the terminal, the command would be `rm data/scout/config/settings.json`
    * Using the Files utility, go to the home directory and look for the folder `data/scout/tmp/config`, then manually delete the `settings.json` file.
2. Restart Scout.
