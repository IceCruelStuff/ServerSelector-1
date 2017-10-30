# ServerSelector
A PocketMine plugin which shows a List with Servers along with their info and a transfer button.
The ServerSelector, with the default style looks like this:
![Example](https://raw.githubusercontent.com/robske110/ServerSelector/master/img/examplesmall.png)

This plugin depends on SignServerStats, you also have to have it installed!

## Usage:
Anyone with the permission `ServerSelector.openList` can open the server selector using the command `/serverlist` or `/serverselector show` or using the item defined in the config.yml (default Compass). (For information how to change the item, see [Configuration](README.md#Configuration))

## Configuration:

### Adding Servers:

Adding servers is easy and can be done in-game as well as from the console. Simply use the command `serverselector add <hostname> [port]` to add a server.
If the server has the port 19132 you do not need to define the port.
Removing servers works the same, the command is `serverselector rem <hostname> [Portz]` for that. 

### config.yml

- **Open with item(s)**

    You can configure items which will open the ServerSelector.    
    - selector-open-items`: An array containing the Item ID(s) which open the ServerSelector. The default is the Compass (345)
    - `selector-item-open-levels`: An array containg the levels the item(s) will open the ServerSelector. The default is null (~), therefore activated in all levels.

- **Hiding offline Servers**
    
    You can configure if you want to display offline servers with `selector.offline.lineX` (defined in styles.yml) or hide them from the list with `hide-offline`. The default is false.

- **Hiding unknown Servers**
    
    You can configure if you want to display `selector.unknown.error` (defined in styles.yml) if the plugin fails to fetch info for a server with `hide-unknown`. The default is false.

### styles.yml
You can edit the style in styles.yml, which is generated in the same directory config.yml is located in. Simply use %COLOUR% (replace COLOUR with the names defined [here](https://github.com/pmmp/PocketMine-MP/blob/master/src/pocketmine/utils/TextFormat.php#L32-L54)) for colours and see the default styles.yml for the special variables (which are %specialVarName%).

## API:
**This plugin has a powerful API, which can mainly modify the server list, prevent it to open under certain conditions, and open it for certain players.**

**A basic documentation is currently WIP, until it is finished you might find the function/event you need by reading the source code.**

_You should always check if your plugin is compatible with the version of ServerSelector present on the current server with the help of the isCompatible function:_

```php
/** @var robske_110\ServerSelector\ServerSelector $serverSelector */
if(!$serverSelector->isCompatible("0.1.0")){
   	$this->getLogger()->critical("Your version of ServerSelector is not compatible with this plugin.");
	$this->getServer()->getPluginManager()->disablePlugin($this);
	return;
}
```