alert tcp any 4444 -> any any (msg:"Meterpreter session detected"; sid:1000001;)
