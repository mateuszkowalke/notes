# IDT

### Overall Architecture

This system's purpose is to enable managing of a digital signage system using LAN. It consists of a local server and several players (android STBs or androidTVs). The system uses also DVBT gateway's multicast output to play TV embedded in templates.

#### Backend

The entrypoint for backend server is in _IDT/nodejs/IDT/server.js. It starts an express server.

First, there are some logging functions defined. Static serving is set for assets regarding tizen and webos players.

Next interesting setup function is [validateNICs](validateNICs) which checks for network interfaces present on the host. There are different procedures for hosts of type 'gateway' and regular server.

After that the server starts listening on port 80 on the ip address of the 1st NIC. If there are two NICs then the server listens on the 2nd one too.

Next, if there are no passwords set in the system.json, hashes are generated for default values of passwords. There are also some other defaults being set in system.json, if not specified.

Then other json configs are being checked and set to defaults as necessary. It sets channels, sources, playlists, videos etc.

***In testSystemLicense the secret used is hardcoded.***
***Also looks like the commented code below the place where testSystemLicense is first referenced has been actually refactored there and no longer needed.***

If the system license is valid, the endpoint license is being generated (system.epl). Otherwise, if the system license is invalid, the endpoint license is being checked.

Next, the routes for proxying widget requests are registered.

Then there are endpoints related to channels - returning lists for endpoints, changing channels etc. Changing channels, showing and hiding alerts, sending and hiding messages and sending STB commands are done using aminoEASSupport class.

Then there's an endpoint for saving predefined messages on the server.

System endpoints follow:

- reading config json files,
- uploading channel logos,
- 

#### AminoEAS

sendEAS sends Emergency Alert System message. It uses stbremoteconf.exe binary for sending commands. For details about stbremoteconf function please consult relevant amino documention.

## Questions

- Is amino box supported?
- Is stbremoteconf configured during installation (it signs the messages sent - some key?)?
- Are we using the widget backends of IDT or the ones developed for NTB?
- What is IDX scheduler (a widget?)?
- Why are the endpoints for retrieving channel lists 'mobile'?
- What is the function of 'pin' path parameter?
- /api/system/channellogos an /api/system endpoints are exactly the same. Is it for some backwards compatibility reasons?

## Things to improve

- Move the widgets' backends to separate services of the IDT server instead of separate processes.
- Refactor testSystemLicense.
