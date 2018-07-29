There are two GitHub sets of directions for configuring HTTPS with custom domains. If your domain registrar supports ALIAS or ANAME records (godaddy.com does not) there is one set of instructions to edit them at 

The option you use depends on how your domain registrar (godaddy.com, one.com, etc.) manages their domains. The original way is using 'A Records' and many 

1. At a terminal type `dig +noall +answer hikinthru.com` using your domain. Note the current A record addresses.
2. Go to [this](https://www.godaddy.com/help/change-an-a-record-19239) page at GoDaddy.
3. Login
4. At step 1 click the domain
5. At the 'DNS Management' page, 'Add' four A records for the addresses:
    185.199.108.153
    185.199.109.153
    185.199.110.153
    185.199.111.153
   Type: A
   Host: @
   Points to: IP address above
   TTL: 1 Hour
6. Remove the old A records:
    192.30.252.153
    192.30.252.154