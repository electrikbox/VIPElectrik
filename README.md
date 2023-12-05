<div align="center"><img src="https://i.imgur.com/wZQUa0l.png" alt="Markdown Monster icon" width=300/></div>
<br>

<h1 align="center">VIPElectrik Rust plugin</h1>

> [!WARNING]
> To use this plugin on your Rust server, you need to have oxide installed, if not, you can follow the steps to do it:
https://www.corrosionhour.com/install-umod-rust-server/

## # Features
* Put player in oxide group.
* Timer UI for each vip player.
* Notify in console when player become vip or get remove form vip.

<img src="https://i.imgur.com/RDR9R5c.png" alt="Markdown Monster icon" />

## # Commands
> [!NOTE]
> This plugin provides both chat and console commands using the same syntax. When using a command in chat, prefix it with a forward slash: `/`.

### Console Commands
(All console commands can be use only by admins) 
* `vipadd <player name or id> <number of days>` - add a player to vip <br>
* `vipremove <player name>` - remove a player from vip <br>
* `vipremove all` - remove all players from vip <br>

### Chat Commands
* `/vipadd <player name or id> <number of days>` - add a player to vip (admin command)<br>
* `/vipremove <player name>` - remove a player from vip (admin command)<br>
* `/vipremove all` - remove all players from vip (admin command)<br>
* `/vipui` - show/hide UI (player command) <br>

## # Configuration
> [!NOTE]
> The settings and options can be configured in the VIPElectrik file under the config directory.The use of an editor and validator is recommended to avoid formatting issues and syntax errors.
* **Timer Refresh :** Set the refresh for UI timer
* **vip oxide group name :** oxide name where player will be added
* **Timer UI options :** UI position
<br>
Default config:

```json
{
  "Timer Refresh (seconds)": 5,
  "vip oxide group name": "vip",
  "Timer UI options": {
    "Text color": "#FFA200",
    "Position left": 4.0,
    "Position right": 94.5,
    "Position bottom": 23.5,
    "Position top": 41.5
  }
}
```

## # Datafile
* **Date :** date when vip will end
* **Name :** vip player name
* **Time :** initial vip length in 'day-hour-min-sec'
* **UI Show :** UI appear on player screen
* **Admin :** who did the command and when
<br>
Exemple data file:

```json
{
  "Players": {
    "76561199011907842": {
      "Date": "2024-05-12T00:00:36.3169241+02:00",
      "Name": "[clan] Bill",
      "Time": "30.00:00:00",
      "UI Show": true,
      "Admin": "Server Console : 06/17/2023 00:00:36"
    },
    "76561198070811659": {
      "Date": "2024-04-05T23:17:59.2842593+02:00",
      "Name": "fren",
      "Time": "364.00:00:00",
      "UI Show": true,
      "Admin": "Electrik : 04/07/2023 23:17:59"
    }
}
```

## # External API Calls

```CS
private bool IsVIP(BasePlayer player) //true if player is VIP, else false.
```
```CS
private bool IsVipTimerShow(BasePlayer player) //true if player has is timer ON, else false.
```
```CS
TimeSpan VIPTimeLeft(BasePlayer player) //get actual vip time left from player
```
Exemple:
```CS
 var player = user.Object as BasePlayer;

    bool isVIP = VIPElectrik.Call<bool>("IsVIP", player);
    Puts($"{player.displayName} vip : {isVIP}");
```
