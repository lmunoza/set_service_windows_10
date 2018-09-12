# set_service_windows_10

The Set-Service cmdlet changes the properties of a service.

opcions 

Sets:	Boot, System, Automatic, Manual, Disabled

per tal de parar les actualitzacions automàtiques

tecla windows - powershell - administrador

Set-Service -Name BITS -StartupType Disabled
Get-Service BITS | Select-Object Name, StartType, Status

Set-Service -Name wuauserv -StartupType Disabled
Get-Service wuauserv | Select-Object Name, StartType, Status

#per renombrar la computadora
RENAME-COMPUTER -computername (hostname) -newname CONTOSO-FS; RESTART-COMPUTER -force

#per reiniciar la computadora
restart-computer


#obtener privilegios administrador

start-process powershell –verb runAs              - en finestra powershell

a partir d'un d'una finestra cmd.exe

powershell -nologo "start-process powershell -verb runas"

##més d'uns altres links

Para pararlos debes escribir desde PowerShell o Símbolo de sistema ambos como Administrador, uno a la vez y das enter

net stop bits

net stop wuauserv
net stop appidsvc
net stop cryptsvc


Update service restarts automatically

It’s observed that just stopping the service does not work in some cases and it restarts automatically. In such cases one can disable the service completely by running below command.

C:\>sc config wuauserv start= disabled
[SC] ChangeServiceConfig SUCCESS
Imagen

para activarlos, algo parecido, estos son los comandos

net start bits
net start wuauserv
net start appidsvc
net start cryptsvc
Get-Service | Sort-Object Status -descending

There are two ways you can do this:

    Get-service
    Get-WMIObject -Class Win32_Service

    Get-Service | Select-Object Name, DisplayName, Status, StartType

    Get-WmiObject -Class Win32_Service | Select-Object DisplayName, Name, StartMode, State

https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-service?view=powershell-6
