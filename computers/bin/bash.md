# find processes (like postgres in this case)

`ps auxw | grep post`


## change permissions
* `chmod 400 file`	To protect a file against accidental overwriting.
* `chmod 500 directory`	To protect yourself from accidentally removing, renaming or moving files from this directory.
* `chmod 600 file`	A private file only changeable by the user who entered this command.
* `chmod 644 file`	A publicly readable file that can only be changed by the issuing user.
* `chmod 660 file`	Users belonging to your group can change this file, others don't have any access to it at all.
* `chmod 700 file`	Protects a file against any access from other users, while the issuing user still has full access.
* `chmod 755 directory`	For files that should be readable and executable by others, but only changeable by the issuing user.
* `chmod 775 file`	Standard file sharing mode for a group.
* `chmod 777 file`	Everybody can do everything to this file.
