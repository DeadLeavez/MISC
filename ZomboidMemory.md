# Zomboid Memory
To increase the memory Project Zomboid is allowed to use, follow the steps below.

### Step 1: Find your installation.

Either navigate to ``\SteamLibrary\steamapps\common\ProjectZomboid`` 

Or 

- Right click the game in steam.
- - Manage
- - - Browse local files

### Step 2: ProjectZomboid64.bat

Locate ``ProjectZomboid64.bat`` in the folder above and open it in a text editor of your preference. 

Find (``ctrl+f``) the following text: ``-Xmx3072m`` and replace it with ``-Xmx8G -Xms6G``

There will be two lines that has the ``-Xmx3072m`` and you want to replace both with the string above.

Save the file

### Step 3: ProjectZomboid64.json

Locate ``ProjectZomboid64.json`` in the folder above and open it in a text editor of your preference. 

Again, we want to find the Xmx line, but it's a bit different in this file. Under ``vmargs`` you will find a line that looks like this ``"-Xmx3072m",``.

You want to replace the line with ``"-Xmx8G",`` and then make a new line and add ``"-Xms6G",``

Afterwards, it should look like this

```json
	"vmArgs": [
		"-Djava.awt.headless=true",
		"-Xmx8G",
		"-Xms6G",
		"-Dzomboid.steam=1",
		"-Dzomboid.znetlog=1",
        ...
```