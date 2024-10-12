# Changes I have made to the standard configuration of LibreChat

## .env UID/GID

In your .env file, the UID and GID variables are commented out:

* UID=1000
* GID=1000

To resolve these warnings, you can uncomment these lines and set the appropriate user ID and group ID.

Run the fulling command to get the variables

* id -u  # For UID
* id -g  # For GID