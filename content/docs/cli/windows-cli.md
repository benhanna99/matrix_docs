---
title: "Windows CLI"
description: "Basics of Windows Command Line"
lead: "Basics of Windows Command Line"
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "cli"
weight: 110
toc: true
---


## Open command prompt

Open windows>run and type **cmd**

## Show a List of All Available Commands

Enter **help** into the CLI and hit enter

## Open Help / List of possible commands using Switch

type the command followed by forward slash question mark

EG:

```

copy /?

dir /?

```

## Paste in a Command

Hit shift + insert keys to paste in a command you copied 

## List Files & Folders

```

dir

```

## Change One Directory Back

CD, space and two dots


```

cd ..

```

## Switch to a specific folder in the directory

cd and folder name

```

cd XXX_XXX

```

## Navigate Through Previous Commands

To Instantly view your command history, hit the up arrow on your keyboard a few times until the command you used appears, you can press enter again to reuse it.

## Use the Listing Tree

To display the file names as well add **f** after the **tree** command. 

Best used in sub folders.

```

tree

```

## Clear the screen

```

cls

```


## Copy a file

we need to take a copy and name the copy.

EG: copy index_old.php index_new.php

```

copy SOURCE_FILE_NAME.extension COPIED_FILE_NAME.extension


```

We could also use the full path here

```

copy C://desktop/folderName/file.txt

```

## Copy the entire folder and its contents

Copy an entire folder to another location

xcopy slash S then the folder we want to copy followed by what the copied folders name will be

```

xcopy /s SOURCE_FOLDER_NAME DESTINATION_FOLDER_NAME

```

## Delete a file

del followed by the file name with extension name

```

del FILE_NAME.extension

```

## Rename a File

USe the **ren** command followed by the file we want to rename followed by what we will rename it to 

```

ren file_name.extension renamed_file.extension

```

## Open a file

Just type the name of the file and its extension when in its folder


## Create a Directory/Folder

```

mkdir FOLDER_NAME

```

## Create a Directory/Folder "With Name Spaces"

Same as a above but put the folder name in quotations

```

mkdir "FOLDER_NAME"

```

## Move a File to a Folder/ Directory

Type move followed by the file name (with extension) and then the folder name we will be moving it to, or the path to the folder

```

move FILE_NAME.extension FOLDER_NAME

```

## Move One Directory/Folder Back

Or we can move it similar to how we change directory by navigating back through the folders. By typing move followed by the file name followed by dot dot 

move file.txt ...

```

move FILE_NAME.extension ..

```

## Delete a Directory/Folder

Keep in mind the below command only removes directories and not files. So it will only remove folders that are empty.

```

rmdir FOLDER_NAME

```

To delete a folder that has files or folders within it, we need to use the **slash S**


```

rmdir /S

```

## View Hostname

Enter **hostname** into the CLI


## IP Config

View the I.P info by entering **ipconfig** into the CLI

## Ping a Server

Enter **ping** followed by the domain EG:

```

ping google.com

```

## Perform an NS Lookup

enter **nslookup** to enter into interactive mode.

Type a name of any website you want to lookup.

## Collect all The information about current System

enter **systeminfo**


## Shutdown Computer/ System

Enter **shutdown /s**