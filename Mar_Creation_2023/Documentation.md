## March Documentation

For our March Creation our group decided to build off of our Janurary Creation and continue working on developing a Snort firewall rules that detect when there is potential Metasploit/Meterpreter activity being performed on a target. In January, we successfully were able to detect when there was activity over port 4444, a common Metasploit/Meterpreter port, but for the March creation, we added several new Snort rules. With a better understanding of how Snort rules worked, we were able to add a lot of different types of rules. These rules will be further explained below.

Our idea came originally from a presentation given by Nicholas Trout, a Sandia National Lab employee, at a research conference. Nicholas' presentation can be found [**here**](https://www.osti.gov/biblio/1806612). 

Nicholas studied network traffic with tools such as Wireshark to identify and classify Meterpreter traffic. With his research we learned that some default configurations of Meterpreter include being used on port 4444 and having a version-less HTTP response. With this information, we built specific Snort rules to look for this type of activity. More information on the type of criteria we are looking for is included in his research, linked above.

**Snort Rules:** 
```
alert tcp any 4444 -> any any (msg:"Possible meterpreter activity detected on port 4444"; \
sid:12345;)

alert tcp any any -> any any (msg:"Possible meterpreter activity detected in packet contents"; \
content:"meterpreter"; \
nocase; \
sid:123456;)

alert tcp any any -> any any (msg:"Detected possible SQL injection attempt"; \
pcre:"/(user|usr|pass|password|pwd)=%27/"; \
sid:13444324;)

alert tcp any any -> any any (msg:"Detected upload of possible malicious code containing php passthru() function"; \
content:"passthru("; \
sid:123123;)

alert tcp any any -> any any (msg:"Detected upload of possible malicious code containing exec() function"; \
content:"exec("; \
sid:123125;)

alert tcp any any -> any any (msg:"Detected upload of possible malicious code containing system() function"; \
content:"system("; \
sid:1231251;)

alert tcp any any -> any any (msg:"Detected upload of possible malicious code containing eval() function"; \
content:"eval("; \
sid:1231253;)

alert tcp any any -> any any (msg:"Detected request for file containing unsafe code eval() function"; \
flow:to_server; \
content:"eval("; \
sid:1231264;)

alert tcp any any -> any any (msg:"Possible version-less http response"; \
flow:established,to_server; \
content:"HTTP/"; \
#content:"\r\n\r\n"; \
pcre:"/^HTTP\/\s*\r\n/smi"; \
sid:1234567;)
```

Our original rule created in Janurary alerts when tcp traffic is found using port 4444 (the default Meterpreter port), and sends the message "Meterpreter session detected". The above rules have the following funtionality, in order that they appear above. 

1st, detecting port 4444 activity. 

2nd, detecting when "meterpreter" was included in the packet of the traffic.

3rd, detecting potential SQL injection attempts.

4th, detecting when potentially malicious code was uploaded, specifically when it contained a php passthru() function.

5th, 6th, and 7th, detecting similarly as rule 4, but when there are exec(), system(), or evel() functions are included.

8th, detecting when there is a request for a file containing code with an eval() function.

9th, detecting when there is a possible version-less HTTP response.

Test cases will be included in the [**Proof-of-Value.md**](https://github.com/bigdan9811/byuis565monthlyprojects/blob/main/Mar_Creation_2023/proof_of_value.md) file of this repository. 
