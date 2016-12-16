<!-- TITLE: Upgrade -->
<!-- SUBTITLE: How to upgrade to the latest version of Wiki.js -->

# Before upgrading

# Upgrade
1. **Download** the latest version from the [Releases](https://github.com/Requarks/wiki/releases) page.
2. **Stop** Wiki.js by running the command `pm2 stop wiki`
3. **Make a backup** of your `config.yml` file to a secure location.
4. If your **repo folder** is located inside your wiki folder, make a backup to a secure location as well.
4. **Delete** all files/folders contained in your wiki folder.
5. **Delete the data folder** if located in a different location than above.
6. **Extract** the contents of the .zip/tar.gz file you downloaded in step 1, to the wiki folder.
7. Inside the wiki folder, **run** the command: `npm install && npm rebuild`
8. **Copy** the `config.yml` back to its original location, in your wiki folder.
9. If your **repo folder** was located inside your wiki folder, copy it back to it's original location as well.
10. **Start** Wiki.js by running the command `pm2 start wiki`
11. **Verify** Wiki.js has started without errors by running the command `pm2 logs wiki`