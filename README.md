 		
			
		


Preparing computers:
	Widows 11 install
1.	Connect Talgo LAN (cable), prepare boot USB disk Windows 11 installer
2.	Boot from usb (F9 on HP computers)
3.	Launch installation windows 11
4.	Language to install – English (United States)
Time and Currency format – Russia (Russia)
Keyboard input – US
5.	Delete all drive partition
Next, install, restart
6.	Region – Kazakhstan
7.	Keyboard US
8.	Add – Russia – Russian
9.	Put computer name (or can do it later)
10.	Set up for work or school
11.	Sign in options - Domain join instead
12.	User name – Talgo (password talgo)
13.	Security question – any, answer - Talgo
14.	Enable all items > Accept
OS preparing
1.	Add Russian language pack
2.	Change region to Kazakhstan (or uzbekistan)
3.	Region format – Russian (Russia)
4.	Date & Time – time zone +5 Astana (Tashkent)
5.	Check correct time, check available display language (should be English as main, additional Russian)
6.	Computer Management > users >
7.	Set Local Administrator password – Loc@pas.20

Control Panel:
8.	User Account settings > User Account control settings – disable > ok    
9.	Firewall settings > Inbound rules > Action > new rule
Custom > next > next > Protocol type – ICMPv4 > Customize > enable Echo Request
Next > next > next > next > Name – ping > finish
10.	Programs and Features > Turn Windows features on > install Net.Framework 3.5
11.	Clock and Region > Region > Format – Russian (Russia)
Administrative > copy setting - check all
Change system local – Russian (Russia)
12.	Ok > restart
13.	Login as Local administrator
14.	Computer Management > users > delete Talgo user
15.	install all updates, check for additional and optional updates, check few times.
16.	Optional Features > View Features > WMIC > add
17.	Rename computer according to the BMC system (ex. LKZ00001)



Software Install
1.	Create computer object in AD with same computer name
2.	Join to domain > restart
3.	Login with domain administrator account
Next Software located: \\talfalsrv01\Software\Computer installation (Almaty)
4.	Install Antivirus \01.Antivirus\Panda\Agentes\Cytomic Endpoint Agent_General.msi
5.	Install BCM \02.BCM\20.8.0.0\BCM_Agent_27-11.exe (run as administrator)
6.	Install Adobe reader \04. Adobe reader\AcroRdrDCx642200320282_MUI.exe
7.	Install Winrar \05. Winrar
8.	Install PDFCreator \08. PDF Creator
9.	Install SAP \09. SAP\Sap_7.70\Sap770ySLC.exe
10.	Reboot computer
11.	Install C:\Program Files (x86)\SAP\FrontEnd\SecureLogin
12.	Install Office \10. Office\Office 365 English > Espanol > Russian (run as administrator)
13.	Install PhishAlarm \11. Boton correo Phising\PhishAlarm.exe
14.	Install VPN Palo Alto \12. VPN\Nueva VPN-ForcePoint\(readme)
15.	Execute LAPS \13. LAPS\LAPS.x64.msi
16.	ProofpointProxy \14. ProofpointProxy\install2.bat (wait till window closed) 
17.	ProofpointDLP \15. ProofpointDLP\instalardlp.bat (wait till window closed)
18.	Execute printdrive.bat (run as administrator)
19.	Check disk encryption with cmd (run as administrator) command “Manage-bde -status”
Should be encrypted 100%
If not – do this:
Cmd command “manage-bde -on c: -recoverypassword”
Wait for end > reboot
Check disk encryption again

20.	Cmd command “gpupdate /force” > reboot
21.	Fill BMC information
22.	Fill information in excel sheet




Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\SAP\General

