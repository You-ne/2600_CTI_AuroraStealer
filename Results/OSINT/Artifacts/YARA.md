\[[[Sources#^462510|1]]\]
```
rule infostealer_win_aurora {
    meta:
        malware = "Aurora"
        description = "Finds Aurora samples based on characteristic strings"
        source = "SEKOIA.IO"
        reference = "https://blog.sekoia.io/aurora-a-rising-stealer-flying-under-the-radar/"
        classification = "TLP:CLEAR"

    strings:
        $str00 = "I'm a teapot" ascii
        $str01 = "wmic cpu get name" ascii
        $str02 = "wmic path win32_VideoController get" ascii
        $str03 = "SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Time Zones" ascii
        $str04 = "Exodus\\exodus.wallet" ascii
        $str05 = "PaliWallet" ascii
        $str06 = "cookies.sqlite" ascii
        $str07 = "Startup\\Documents\\User Data" ascii
        $str08 = "atomic\\Local Storage\\leveldb" ascii
        $str09 = "com.liberty.jaxx\\IndexedDB" ascii
        $str10 = "Guarda\\Local Storage\\leveldb" ascii
        $str11 = "AppData\\Roaming\\Telegram Desktop\\tdata" ascii
        $str12 = "Ethereum\\keystore" ascii
        $str13 = "Coin98" ascii
        $str14 = ".bat.cmd.com.css.exe.gif.htm.jpg.mjs.pdf.png.svg.xml.zip" ascii
        $str15 = "type..eq.main.Grabber" ascii
        $str16 = "type..eq.main.Loader_A" ascii
        $str17 = "type..eq.net/http.socksUsernamePassword" ascii
        $str18 = "powershell" ascii
        $str19 = "start-process" ascii
        $str20 = "http/httpproxy" ascii

    condition:
        uint16(0)==0x5A4D and 15 of them and filesize > 4MB
}
```