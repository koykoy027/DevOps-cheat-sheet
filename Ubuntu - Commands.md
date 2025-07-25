# Ubuntu Commands

## SSH Commands
- `ssh -T git@github.com`: Test handshake

## Navigation and File Management
- `cp source destination`: Copy files or directories.
- `mv source destination`: Move or rename files or directories.
- `rm file_name`: Remove files or directories.
- `rm -r directory_name`: Remove folders and subfolders.
- `mkdir directory_name`: Create a new directory.
- `ls`: List files and directories in the current location.
- `cd directory_path`: Change the current directory.
- `df -h` check storage.

## Package Management
- `sudo apt-get install package_name`: Install a new package.
- `sudo apt-get update`: Update the package list.
- `sudo apt-get upgrade`: Upgrade installed packages.
- `sudo apt-get remove package_name`: Remove a package.
- `dpkg -l`: List all installed packages.
- `apt-cache search search_term`: Search for packages matching a keyword.
- `sudo apt-get autoremove`: Remove unused dependencies.
- `sudo apt-get clean`: Clear the local repository of retrieved package files.
- `sudo systemctl restart package_name | sudo service package_name restart`: restart package

## APACHE2 Commands
- `sudo a2ensite`: enable configuration
- `sudo a2dissite`: disable configuration

