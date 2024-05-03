# Rake Tab Completion
Integrating this will allow for tab completion of rake commands.

# Setup
## Add source target to your bash profile
* Use `rake_tab_completion_profile` for base functionality.
* Use `rake_tab_completion_profile_time_analysis` for time analysis wrapped functions.
    * MacOS users should validate installation of coreutils for gdate
        * The boiler plate date command does not go beyond seconds like GNU versions.  
```
source ~/path/to/file
```
## Update Profile
```
source ~/path/to/.bash_profile
```
## Add Global .gitignore for cache files.
This step may require additional configuration steps and location may vary by device.
* Open ~/.config/git/ignore
* Add the following:
```
.rake_*_cache
```
