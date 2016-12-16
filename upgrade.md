<!-- TITLE: Upgrade -->
<!-- SUBTITLE: How to upgrade to the latest version of Wiki.js -->

# Before upgrading

# Upgrade
> **Glossary**  
> In the instructions below, the following terms refer to:
> 
> wiki folder: The folder where Wiki.js is located.  
> repo folder: The folder where the local Git repository is located, as defined in your config.yml file.  
> data folder: The folder where temporary files for Wiki.js are located, as defined in your config.yml file.  

1. **Download** the latest version from the [Releases](https://github.com/Requarks/wiki/releases) page.

2. **Stop** Wiki.js by running the command `pm2 stop wiki`

3. **Make a backup** of your `config.yml` file to a secure location.

4. If your **repo folder** is located inside your wiki folder, make a backup to a secure location as well.

5. **Delete** all files/folders contained in your wiki folder.

6. **Delete the data folder** if located in a different location than above.

7. **Extract** the contents of the .zip/tar.gz file you downloaded in step 1, to the wiki folder.

8. Inside the wiki folder, **run** the command: `npm install && npm rebuild`

9. **Copy** the `config.yml` back to its original location, in your wiki folder.

10. If your **repo folder** was located inside your wiki folder, copy it back to it's original location as well.

11. **Start** Wiki.js by running the command `pm2 start wiki`

12. **Verify** Wiki.js has started without errors by running the command `pm2 logs wiki`