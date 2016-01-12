# Dreamhost API - PowerShell

The purpose of this code is to allow interfacing with a Dreamhost account via their API.  Once such purpose would be to automatically update DNS records for ***DNS hosted only*** records for remote hosts that have dynamic IP's.

## Supported API Commands
---
### DNS Records
- Listing
```
> DnsRecord-Fetch -apiKey 6SHU5P2HLDAYECUM | Format-Table


Record                               Value                                Type                                Comment                             Editable
------                               -----                                ----                                -------                             --------
groo.com                             208.113.141.116                      A                                                                       No
ssh.album.groo.com                   75.119.200.215                       A                                                                       No
a6.groo.com                          1234:1234:1234:1234:1234:1234:123... AAAA                                test                                Yes
aaaaaa.groo.com                      0000:0000:0000:0000:0000:0000:000... AAAA                                testing!                            Yes
mailboxes.google.groo.com            208.97.187.203                       A                                                                       No
image.groo.com                       d1z8lr53cxmcgi.cloudfront.net.       CNAME                               104::cloudfront                     Yes
etc...
```
- Adding
```
> DnsRecord-Add -apiKey 6SHU5P2HLDAYECUM -record "sub.domain.suffix" -type "A" -value (PublicIP-Fetch)


Are you sure want to add the following record: sub.domain.suffix | A | %CURL_IP%: y

Record successfully added
```
- Removing