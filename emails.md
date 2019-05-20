
# SPF

examples
TXT @ "v=spf1 a include:_spf.google.com ~all"
v=spf1 include:_spf.google.com include:mktomail.com ip4:167.89.11.171 a:o167-89-11-171.outbound-mail.sendgrid.net -all


From: https://www.digitalocean.com/community/tutorials/how-to-use-an-spf-record-to-prevent-spoofing-improve-e-mail-reliability

SPF records may define zero or more mechanisms. Mechanisms can be used to describe the set of hosts which are designated as authorized, outbound mailers for the domain. The following list are common mechanisms included in an SPF record:

all | ip4 | ip6 | a | mx | ptr | exists | include


+	Pass = The address passed the test; accept the message. Example: "v=spf1 +all"
-	(Hard) Fail = The address failed the test; bounce any e-mail that does not comply. Example: "v=spf1 -all"
~	Soft Fail = The address failed the test, but the result is not definitive; accept & tag any non-compliant mail. Example: "v=spf1 ~all"
?	Neutral = The address did not pass or fail the test; do whatever (probably accept the mail). Example: "v=spf1 ?all"


all	Matches all local and remote IPs and goes at the end of the SPF record. Example: "v=spf1 +all"
ip4	Specifies a single IPv4 address or an acceptable IPv4 address range. A mask of /32 is assumed if no prefix-length is included. Example: "v=spf1 ip4:192.168.0.1/16 -all"
ip6	Same concept found in ip4, but, obviously, with IPv6 addresses, instead. If no prefix-length is given, /128 is assumed (singling out an individual host address). Example: "v=spf1 ip6:1080::8:800:200C:417A/96 -all"
a	Specifies all IPs in the DNS A record. Example: "v=spf1 a:domain.com -all"
mx	Specifies all A records for each host's MX record. Example: "v=spf1 mx mx:domain.com -all"
ptr	Specifies all A records for each host's PTR record. Example: "v=spf1 ptr:domain.com -all"
exists	Specifies one or more domains normally singled out as exceptions to the SPF definitions. An A query is performed on the provided domain; if a result is found a match occurs. Example: "v=spf1 exists:domain.com -all"
include	Specifies other domains that are authorized domains. Example: "v=spf1 include:outlook.microsoft.com -all"

v=spf1 include:_spf.google.com include:mktomail.com ip4:167.89.11.171 a:o167-89-11-171.outbound-mail.sendgrid.net ip4:173.203.187.74 -all