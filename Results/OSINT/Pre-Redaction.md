\[[[|]]\]

# History

## Public Knowledge & Investigations

In __April 2022__ started advertised as a __Botnet__, following a __Maas__ (_Malware-as-a-service_) on Russian-speaking undeground forums. The advertising was coming from a threat actor named __*Cheshire*__ \[[[Sources#^462510|1]]\]

At the beginning of __June 2022__, the presumed developer stopped publishing about __Aurora__ botnet, either on __Dark Web__ or its __Telegram__ channels. \[[[Sources#^462510|1]]\]

Discovered in __July 2022__ by SEKOIA.IO; they identified around __fifty__ samples, mainly from "*Cheshire*" and "*Zelizzard*" and less than a dozen C2 servers from __*Aurora*__ botnets.
At the end of the month, the servers were no longer active and no more samples were published in public repositories.
SEKOIA suposed that __Aurora__ development was no longer active.
Another publication on __BHF forum__ in the end of the month suggested that __*Cheshire*__ shifted to developping malware in demand.
\[[[Sources#^462510|1]]\]

In late __August 2022__, Aurora was advertised as a __stealer__ instead of a botnet on Telegram and underground forums. \[[[Sources#^462510|1]]\]

In __October and November 2022__, several hundreds of *collected samples* and dozens of *active C2 servers* and *multiple chains of infection leading to the execution of Aurora stealer* were again observed by SEKOIA, indicating a raise in popularity of __Aurora__.
## Campaigns

# About the actor

## Victimology & Motivations

### Victimes

### Motivations

## Business Model 

According to [[Advertisment_August_2022.png|this advertisment]], the cost is :             
- $250 a month
- $1500 lifetime license
\[[[Sources#^462510|1]]\]



## Proeficient skills

## Communications

### Comm Channels

BHF Forum 
WWH forum
Telegram \[[[Sources#^462510|1]]\]
check XSS forum
Also check Lolz Guru

### Comm Pseudos

"Cheshire" \[[[Sources#^462510|1]]\]
"KO7MO" \[[[Sources#^462510|1]]\]



### Comm Frequency

### GLOBAL COMM ANALISYS

## Linked actors

### Customers


According to SEKOIA, and as of __November 2022__, the following __traffers__ teams were distributing the Aurora botnet.
\[[[Sources#^462510|1]]\]
![[Linked_Traffers_SEKOIA.png|500x500]]


<br>
<br>


# About the code

Written in __Golang__, **Aurora mainly uses the [lxn/win](http://github.com/lxn/win) library to interact with the Windows API, this library relies on Windows Management Instrumentation Command (WMIC).**
\[[[Sources#^462510|1]]\]
## Features
### According to August 2022 Advertisment

\[[[Sources#^462510|1]]\]
![[Advertisment_August_2022.png|500x500]]
Advertisment on XSS forum
Aurora’s promoter claims the stealer has a file grabber and a loader capabilities. During SEKOIA's investigation, only the loader capabilities were observed 

---

### Fingerprinting 

To fingerprint the host, Aurora executes three commands on the infected host:

-   `wmic os get Caption`
-   `wmic path win32_VideoController get name`
-   `wmic cpu get name`

Aurora also takes one screenshot of the infected host.
\[[[Sources#^462510|1]]\]

### Data Extraction

#### Application Data

Aurora targets multiple web browsers, as well as browser extensions including those managing cryptocurrency wallets and applications such as Telegram. The malware uses the function walk of the built-in module [path](https://pkg.go.dev/path/filepath#Walk) to loop over files and directories until it matches a filename or directory name of one of the targeted applications or extensions. \[[[Sources#^462510|1]]\]

**Cryptocurrency browser extensions:**

**Extension id****Cryptocurrency wallet browser extensions**aeachknmefphepccionboohckonoeemgCoin98aiifbnbfobpmeekipheeijimdpnlpgppTerra StationamkmjjmmflddogmhpjloimipbofnfjihWombataodkkagnadcbobfpggfnjeongemjbjcaBOLT XbfnaelmomeimhlpmgjnjophhpkkoljpaPhantomblnieiiffboillknjnepogjhkgnoapacEqualcgeeodpfagjceefieflmdfphplkenlfkEVERcjelfplplebdjjenllpjcblmjkfcffneJaxx LibertydngmlblcodfobpdpecaadgfbcggfjfnmMaiar DeFiffnbelfdoeiohenkjibnmadjiehjhajbYoroifhbohimaelbohpjbbldcngcnapndodjpBinancefhilaheimglignddkjgofkcbgekhenbhOxygenfihkakfobkmkjojpchpfgcmhfjnmnfpiBitAppfnjhmkhhmkbjkkabndcnnogagogbneecRoninfnnegphlobjdpkhecapkijjdkgcjhkibHarmonyhmeobnfnfcmdkdcmlblgagmfpfboieafXDEFIhnfanknocfeofbddgcijnmhnfnkdnaadCoinbasehpglfhgfnhbgpjdenjgmdgoeiappaflnGuardibnejdfjmmkpcnlpebklmnkoeoihofecTronLinkjbdaocneiiinmjbjlgalhcelgbejmnidNiftykncchdigobghenbbaddojjnnaogfppfjiWalletkpfopkelmapcoipemfendmdcghnegimnLiqualitylpfcbjknijpeeillifnkikgncikgfhdoNamimgffkfbidihjpoaomajlbgchddlicgpnPalinanjmdknhkinifnkgdcggcfnhdaammmjGuildnkbihfbeogaeaoehlefnkodbefgpgknnMetaMasknkddgncdjgjfcddamfgcmfnlhccnimigSaturnnlbmnnijcnlegkjjpcfjclmcfggfefdmMEW CXodbfpeeihdkbihmopkbjmoonfanlbfclBravepdadjkfkgcafgbceimcpbkalnfnepbnkKardiaChain

#### Files Data
\[[[Sources#^462510|1]]\]
If a file name matches the stealer logic, the file is encoded in base64 and sent to the C2
![[File_Grabber.png|500x500]]

**Cryptocurrency desktop wallets:**

\Armory Armory

\bytecoin Bytecoin

\Electrum\wallets Electrum

\Ethereum\keystore Ethereum

\Exodus\exodus.wallet Exodus

\Guarda\Local Storage\leveldb Guarda

\com.liberty.jaxx\IndexedDB Jaxx Liberty

\Zcash Zcash

**Other application:**


\AppData\Roaming\Telegram Desktop\tdata Telegram


### C2
\[[[Sources#^462510|1]]\]

The malware communicates using TCP connection on __ports 8081 and 9865__ – 8081 being the most widespread open port. 

All messages abide by the same structure, each keys are described below: 

-   Browser: name of the browser where data was collected (ex: Mozilla, Chromium, _etc_.);
-   Cache: content of the stolen file encoded in base64;
-   FileName: name of the stolen file (_e.g._ cookies.sqlite, Login Data);
-   GRB: likely the grabber configuration. Of note, SEKOIA.IO only observed the value “null”;
-   Info: host fingerprint information, including:
    -   Name: a random name defined by threat actor;
    -   BuildID: name of the build, the value often matches a threat actor’s Telegram account;
    -   OS: Windows version;
    -   HWID: hardware ID;
    -   GPU: graphical card information;
    -   CPU: CPU name and vendor;
    -   RAM: amount of memory;
    -   Location: execution path of Aurora sample;
    -   Screen: size of the screen of the infected host;
    -   IP: expecting the IP address of the infected host but the value is always an empty string.
-   MasterKey: encryption key used to read the data of the stolen file, for instance some browsers store the saved password encrypted;
-   Path: always empty string;
-   Type: type of the exfiltrated data (Browser-Mozilla, Screenshot, _etc._).
First the screenshot is exfiltrated, then any additionnal data. 
---
### Loader
\[[[Sources#^462510|1]]\]
Aurora loader is straightforward, it downloads a remote payload using _net_http_Get_ from the built-in library [net/http](https://pkg.go.dev/net/http), then the file is written on the disk in the temporary directory with a random name. 

The stealer executes the next stage using the following PowerShell command:
`powershell.exe start-process “C:\Users\Admin\AppData\Local\Temp\oH7P8GCPXQ.exe”`

![[Loader.png|500x500]]

---

## Samples Code

\[[[Sources#^462510|1]]\]
Aurora sample BuildID:
@im_HiLLi, @dddaw22123, @t0mi0k4, Zack, DEV, @feozz, @huy, @dgdima, @mutedall, @huy, @HelixHuntter, 5397150605_99, @tipok734, @Ggtwp, 11, @t0mi0k4, shellar, @dzynO1k, shellarlogs, @sou_bss, DEV, zack, INSTALLS, yjrc, shellar, egorix, DEV, 123
