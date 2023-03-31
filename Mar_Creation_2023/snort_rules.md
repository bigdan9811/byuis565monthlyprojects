alert tcp any 4444 -> any any (msg:"Possible meterpreter activity detected on port 4444"; \
sid:12345;)

alert tcp any any -> any any (msg:"Possible meterpreter activity detected in packet contents"; \
```
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
