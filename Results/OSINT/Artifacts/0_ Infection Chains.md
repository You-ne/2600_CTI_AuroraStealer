
Depends on the actor. They have used, notably :
- phishing pages impersonating download pages of legitimate software, including cryptocurrency wallets or remote access tools
- the 911 method making use of YouTube videos and SEO-poised fake cracked software download websites.
\[[[Sources#^462510|1]]\]


---

# Chain 1

\[[[Sources#^462510|1]]\]
Aurora stealer is distributed using a phishing site impersonating Exodus Wallet (cryptocurrency wallet) hosted on hxxps://mividajugosa[.]com/.

Clicking on the “Download” button at the top right initiates the download of a ZIP “_ExodusWeb3.zip_” (SHA256: _2e9dbda19d9c75a82dabac8ffba5ea76689ada81639867c41c395a29aeaba788_) that contains the executable “_ExodusWeb3.exe_” (SHA256: _9db1744112aea85c625cd046fc737bf28bef254bebfbf7123df6844f62167759_) detected as Aurora stealer. 

It communicates to its C2 server on _79.137.195.171:8081_.

# Chain 2

\[[[Sources#^462510|1]]\]
This infection consists in the following steps:

1. A YouTube video on a stolen account describing how to install a cracked software for free and providing a link;

2. From the link provided in the YouTube video, the victim can access a “free software catalogue” website (_e.g. winsofts[.]cloud_);

3. The payload is hosted on a legitimate file sharing platform and embeds Aurora Stealer. The user downloads it, decompresses the archive and executes the file “_setup.exe_”.  
4. Aurora sample communicates to its C2 on _45.15.156[.]97:8081_ and downloads a second-stage payload _(oH7P8GCPXQ.exe)_.

Related URLs:

-   YouTube videos: https://www.youtube.com/watch?v=oy7NPaccBnk
-   Malicious free software catalogue website: https://winsofts.cloud/
-   Next-stage payload: https://cdn.discordapp.com/attachments/1037000444813254768/1042401882041237524/Adobe_Acrobat.zip

File hashes:

-   Downloaded archive (_Adobe_Acrobat.zip_)  
    SHA256: _88e02def17fda0021d4dba5ea812772c542b0fa6ca8930bcf06c42375c00bd29_
-   Aurora sample (_setup.exe_)  
    SHA256: _47332ce5b904b959aa814ddfde8662931fdfb5233422dc45053ad04cffc44fb4_
-   Next-stage payload (_oH7P8GCPXQ.exe_)  
    SHA256: _8e24e96e1e87cf00e27c3a3745414636fbf6e148077c0f6815a2b87bacf85c8d_