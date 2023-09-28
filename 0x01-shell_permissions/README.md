#!/bin/bash
su betty a script that switches the current user to the user
whoami a script that prints the effective username of the current user
groups Write a script that prints all the groups the current user is part of
chown betty hello a script that changes the owner of the file hello to the user betty.
touch hello a script that creates an empty file called hello
chmod u+x hello a script that adds execute permission to the owner of the file hello
chmod u+x,g+x,o+r hello a script that adds execute permission to the owner and the group owner, and read permission to other users, to the file hello
chmod ugo+x hello a script that adds execution permission to the owner, the group owner and the other users, to the file hello
chmod 007 hello a script that sets the permission to the file hello as follows: Owner: no permission at all, Group: no permission at all, other users: all the permissions
chmod 753 hello a script that sets the mode of the file hello to this:The file hello will be in the working directory, you are not allowed to use commas for this script
chmod --reference olleh hello a script that sets the mode of the file hello the same as olleh’s mode. The file hello will be in the working directory, The file olleh will be in the working directory
chmod -R ugo+X . a script that adds execute permission to all subdirectories of the current directory for the owner, the group owner and all other users. Regular files should not be changed.
mkdir -m 751 my_dir a script that creates a directory called my_dir with permissions 751 in the working directory.
chgrp school hello a script that changes the group owner to school for the file hello, The file hello will be in the working directory
