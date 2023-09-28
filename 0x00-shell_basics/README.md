#!/bin/bash
pwd prints the absolute path name of the current working directory
ls Display the contents list of your current directory
ls -l List all the files in the working directory in long format
ls -la . Display current directory contents, including hidden files (starting with .). Use the long format
ls -lan Display current directory contents in Long format with user and group IDs displayed numerically And hidden files (starting with .)
mkdir Create a script that creates a directory named my_first_directory in the /tmp/ directory
mv Move the file betty from /tmp/ to /tmp/my_first_directory
rm delete the file
rm -r delete directories with all its content
cd - changes the working directory to the previous one
ls -la . .. /boot script that lists all files (even ones with names beginning with a period character, which are normally hidden) in the current directory and the parent of the working directory and the /boot directory (in this order), in long format
file /tmp/iamafile script that prints the type of the file named iamafile. The file iamafile will be in the /tmp directory when we will run your script.
ln -s /bin/ls __ls__  Create a symbolic link to /bin/ls, named __ls__. The symbolic link should be created in the current working directory.
cp -u *.html ..Create a script that copies all the HTML files from the current working directory to the parent of the working directory, but only copy files that did not exist in the parent of the working directory or were newer than the versions in the parent of the working directory.
