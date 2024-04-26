# Rake Tab Completion
Integrating this will allow for tab completion of rake commands.

# Setup
## Add source target to your bash profile
* Use main for base functionality.
* Use time_main for time analysis wrapped functions.
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
.rake_*
# Or
.rake_t_cache
.rake_md5_cache
```

# Possible Edge Cases
## validate_terminal_session():
Missing dependencies: Handle cases where either the rake or md5sum command is not available in the system PATH.
Permission issues: Consider scenarios where the user running the script lacks the necessary permissions to execute the required commands.
## _rake_cache_path():
No Rakefile found: Ensure the function handles the case where no Rakefile is found in any parent directory.
Empty Rakefile: Account for situations where the Rakefile exists but contains no tasks.
## rake_task_cache_store():
No tasks found: Handle scenarios where the rake --tasks command returns an empty list or encounters an error.
## rake_md5_cache_store():
Missing Gemfile or rakelib directory: Ensure the script gracefully handles cases where the Gemfile or the rakelib directory is missing.
Non-standard file locations: Account for scenarios where the Gemfile or Rakefile are located in non-standard directories.
## validate_cache():
Cache file corruption: Consider what happens if the cache files are corrupted or incomplete.
Concurrency issues: Guard against race conditions that may occur if multiple instances of the script try to validate or regenerate cache files simultaneously.
## _rakecomplete():
Invalid task names: Handle cases where rake tasks contain special characters, spaces, or other non-standard characters.
Concurrency issues: Ensure that multiple instances of the script don't interfere with each other's cache or calculations.
Interrupted execution: Test what happens if the script execution is interrupted, such as by a user pressing Ctrl+C or a system signal.


# Other
## How do we handle local development of the dev commands library?
* Do we care?
## Where does this live?
### fdp-devops
* This feels single use and is not what this is intended for. We could have it live here and another location.
### engineering-devops
* This feels better given the tool would be managed by devops. 
* Doesn't look like SBF has access.
  * Intended?
### dev_commands
* This directly enhances these commands, but adding a shell script with the ruby logic just feels odd.
  * I would like a discussion on this one as I could see it being a route. 
  * Injecting this logic with the rake commands makes the setup trivial.
### rake-tab-completion
* Sharable and independent. 
