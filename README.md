# Introduction to Automation for Archivists

This repository contains files needed for the "Introduction to Automation for Archivists" workshop.

This lesson will cover methods for automating the following tasks:

- Moving images to a new folder for images on the desktop
- Getting rid of 'junk' files
- Fixing broken extensions by bulk-renaming files
- Seeing what's inside all text files that have been modified in the last five minutes

## Downloads

To get started, you will need to download the following:

1. [Python](https://www.python.org/downloads/)
2. [Organize-tool](https://pypi.org/project/organize-tool/)
3. [Sublime Text](https://www.sublimetext.com/download)
4. [BoostNote](https://boostnote.io/#download)
5. This repository, as a ZIP (click the green 'Clone or download' button, then click 'Download ZIP') 

## Initial Setup

First, extract the repository from its ZIP file. You should have two folders: exercise_files and BooostNote_import.

Next, you need to import the organize-tool clippings into BoostNote. We will be using these clippings for automation, and you can re-use them later if needed (and hopefully add your own eventually!)

1. Open BoostNote
2. Click the ellipsis - this will open Preferences
3. To the right of "My Storage" you will see three icons - click the middle one (the hover text should say 'Open Storage Folder')
4. Open the Boostnote folder
5. Open the notes folder
6. Drag and drop all of the files from the 'BoostNote_Import' folder into the 'notes' folder
7. Go back to BoostNote
8. Go to View > Reload
9. A new folder called "Unknown 1" would have appeared; right click this and rename it "Organize"

Now set Sublime Text as your default .yml editor.

1. In your command line (or terminal) type 'organize config'
2. You may be asked to choose a default editor; if so then pick Sublime Text

You are now ready to get started! Have fun, I will guide you through the rest.

## Common error messages

### ERROR! while parsing a block mapping

If you got this error after you copied and pasted a rule into the config.yml file, highlight the rule that you just added and press the TAB key. This should properly align the rule, as YAML files are very finicky about formatting!

### ERROR! Unacceptable pattern: ''

You have entered a folder that doesn't exist.
