# Introduction to Automation for Digital Preservation Practitioners

This repository contains files needed for the "Introduction to Automation for Digital Preservation Practitioners" workshop.

This lesson will cover methods for automating the following tasks:

- Moving images to a new folder for images on the desktop
- Getting rid of 'junk' files
- Fixing broken extensions by bulk-renaming files
- Seeing what's inside all text files that have been modified in the last five minutes

## Initial Setup

1. Download this repository, as a ZIP (click the green 'Clone or download' button, then click 'Download ZIP') 
2. Extract the repository from its ZIP file. You should have two folders: exercise_files and BooostNote_import.
3. Drag exercise_files to your desktop
4. Drag BoostNote_import to your desktop

## Setting up Boostnote ##

Now, you need to import the organize-tool clippings into Boostnote. We will be using these clippings for automation, and you can re-use them later if needed (and hopefully add your own eventually!)

1. Open Boostnote
2. Click the ellipsis (it is to the left of the search bar at the top of the screen) - this will open Preferences
3. To the right of "My Storage" you will see three icons - click the middle one (the hover text should say 'Open Storage Folder')
4. Open the Boostnote folder
5. Open the notes folder
6. Drag and drop all of the files from the 'Boostnote_Import' folder (on your desktop) into the 'notes' folder
7. Go back to Boostnote
8. Go to View > Reload (or ctrl+r)
9. In "My Storage" on the left there should be a new folder called "Unknown 1"; right click this and rename it "Organize"

## Common error messages

### ERROR! while parsing a block mapping

#### Cause 1: Indentation

If you got this error after you copied and pasted a rule into the config.yml file, highlight the rule that you just added and press ctrl (or command) + \] to indent. This should properly align the rule, as YAML files are very finicky about formatting!

You can use ctrl + \[ to unindent.

#### Cause 2: Forgot to add the 'filters:' line

The following rule will not work.

```code

rules:

  - folders: '~/Desktop'
      - filename:
          startswith: A
          contains: hole
          case_sensitive: false
    actions:
      - echo: 'Found a match.'
      
```
This is because 'filters:' is missing from beneath 'folders'. Don't forget to add the 'filters:' line!

### ERROR! Unacceptable pattern: ''

You have entered a folder that doesn't exist.

### ERROR! No rules found in configuration file

Did you remember to save your config file after adding Rules?

### ERROR! 'NoneType' object is not iterable

You added the header declaring variables, and 'rules:' but did you add the rules themselves?

### ERROR! __init__() missing 1 required positional argument

Did you list your actions?

Remember to indent your actions properly! The below action will fail because 'dest' and 'overwrite' are not indented.

```code
    actions:
      - Move:
        dest: '~/Documents/Invoices/'
        overwrite: false
```

This action will work because they were indented.

```code
    actions:
      - Move:
          dest: '~/Documents/Invoices/'
          overwrite: false
```

### ERROR! while parsing a block collection

If you see this error message, organize is upset by an indent. It will give you a list of lines that it is upset by. Try un-indenting the first line that it found a problem with (highlight it and press ctrl/command + \[ on your keyboard).

### ERROR! 'str' object has no attribute 'get'

Did you accidentally add the rules twice?

```code
rules:

  rules:

  - folders: ~/Desktop/challenge
```
### ERROR! 'module' object is not callable

I've only seen this error when organize itself is corrupted. Uninstall with the following command at the command line if you're on Mac:

```code
sudo pip3 uninstall organize-tool
```

Or this command if you're on Windows:

```
pip uninstall organize-tool
```

Then follow the installation instructions for re-installation.

### ERROR: Please specify your filters as a YAML list

You may have included your filter but forgotten to include what you were actually filtering ON.

```code
    filters:
          startswith: A
```

In the above example, you might have meant to filter on files that start with the letter A, but you forgot to include the type of filter. The below solution will work.

```code
    filters:
      - filename:
          startswith: A
```          

### ERROR! 'PosixPath' object has no attribute 'items'

This error occurs for Mac users in Organize version 1.61 when you attempt to rename a file. To fix this error, simply upgrade your version of Organize by entering the following command into your command line.

```bash
sudo pip install organize-tool --upgrade
```

Once installation is complete, try running the rename command again.


### ERROR! 'WindowsPath' object has no attribute 'items' 

This error occurs for Windows users in Organize version 1.61 when you attempt to rename a file. To fix this error, simply upgrade your version of Organize by entering the following command into your command line.

```bash
pip install organize-tool --upgrade
```

Once installation is complete, try running the rename command again.

### Nothing to do.

This message will appear if:

* Your filter doesn't match any files
* You have already run the rules and have forgotten
* You're pointing your rules at the wrong folder
* You haven't indented one of your filters, so Organize is ignoring it
