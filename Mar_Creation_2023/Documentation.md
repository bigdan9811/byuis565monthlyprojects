## March Documentation

For our March Creation our group decided to build off of our Janurary Creation and continue working on developing a Snort firewall rule that detects when there is potential Metasploit/Meterpreter activity being performed on a target. In January, we successfully were able to detect when there was activity over port 4444, a common Metasploit/Meterpreter port, but for the March creation, we added the ability to detect if the activity contained a versionless-HTTP response.

Our idea came originally from a presentation given by Nicholas Trout, a Sandia National Lab employee, at a research conference. Nicholas' presentation can be found [**here**](https://www.osti.gov/biblio/1806612). 

Nicholas studied network traffic with tools such as Wireshark to identify and classify Meterpreter traffic. With his research we learned that some default configurations of Meterpreter include being used on port 4444 and having a version-less HTTP response. With this information, we built a specific Snort rule to look for this type of activity.

**Snort Rule:** `alert tcp any 4444 -> any any (msg:"Meterpreter session detected"; sid:1000001;)`

This rule alerts when tcp traffic is found using port 4444 (the default Meterpreter port), and sends the message "Meterpreter session detected". In Janurary we decided to just alert the user and not terminate the session as to not interupt daily work flow. For the March Creation, we implemented blocking the suspicious activity rather than only alerting that the activity was taking place.

A test case will be included in the [**Proof-of-Value.md**](https://github.com/bigdan9811/byuis565monthlyprojects/blob/main/Mar_Creation_2023/proof_of_value.md) file of this repository. 
