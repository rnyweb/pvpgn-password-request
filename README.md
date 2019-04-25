# pvpgn-password-request
PvPGN password request script. [PHP]

**What is PvPGN?**

PvPGN (Player vs Player Gaming Network) is a free and open source software project offering emulation of various gaming network servers. It is published under the GPL and based upon bnetd.
It currently supports most features of all Battle.net classic clients (Diablo, Diablo II, Diablo II: Lord of Destruction, StarCraft, StarCraft: Brood War, Warcraft II: Battle.net Edition, Warcraft III: Reign of Chaos, Warcraft III: The Frozen Throne). It also offers basic support for Westwood Online clients (Command & Conquer: Tiberian Sun, Command & Conquer: Red Alert 2, Command & Conquer: Yuri's Revenge).

**What is PvPGN password request?**

PvPGN password request is a script written in PHP with a PHP mailer built-in that allow any PvPGN client to recover the password through a Battle.net private server that is running on PvPGN. Officially, PvPGN has no built-in function to rocover a lost password and this script can be used to have that function working.

**How is working?**

PvPGN does generate and output logs if a user is requesting a new password and if the username matches with the email address stored into the database. This script can be used as a Windows service which is running in the background checking every 5 seconds the logs generated by PvPGN. When somebody is requesting the password for their account this script will trigger and an email will be sent to the user with the password stored into the database.

**Requirments:**

- PvPGN logs must be enabled.
- SMTP Server.
- PHP Windows version.
- NSSM(the Non-Sucking Service Manager).

**Tested on:**

OS: Windows 2012 Server Standard.

PvPGN version: 1.8.5.

PHP version: 7.3.4.

NSSM version: 2.24.

**How to implement?**

**Important!** The path directory of NSSM will NOT work if contains any spaces.

Good Example: C:\d2server\nssm
Bad example: c:\d2 server\nssm

1) Download and extract this repostory to your PvPGN folder.
2) Edit config.php file and set the required information such as your path to PvPGN folder and a SMTP server.
3) Add the script to run as a windows service with NSSM(the Non-Sucking Service Manager).

install
nssm install "PvPGN Mailer" C:\Users\Administrator\Desktop\php\php.exe
nssm set "PvPGN Mailer" Description PvPGN Password Request.
nssm set "PvPGN Mailer" AppDirectory C:\Users\Administrator\Desktop\php
nssm set "PvPGN Mailer" AppParameters C:\Users\Administrator\Desktop\sendmail\mailer.php


To manually verify the data
nssm edit "PvPGN Mailer"

To remove
nssm remove "PvPGN Mailer" confirm

how to add delay?
