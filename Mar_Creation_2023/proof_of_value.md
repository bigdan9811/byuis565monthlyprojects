# Proof of Value
*Meterpreter Snort Rule*

The test cases below will include a target and an attacker machine. The target machine will have our Meterpreter Snort rule code stored and running on it, where the attacker machine will run Meterpreter to attack the target machine. In this scenario, it will show what the target machine will see before our Meterpreter Snort rule is implemented and what the target machine will see after it is implemented.

---

This image below shows the setup and configuration of our Metasploit instance that was used for testing.

![metasploit-config](images/image3.png)

This alert shows a successful detection of possible meterpreter activity dependent on the type of information found in the packet contents. This is specific to rule #2 mentioned and explained here [here](Documentation.md).

![metasploit-config](images/image1.png)

Below is a deep dive into the packet contents that shows "meterpreter" discovered. This shows that our Snort rule for this criteria was successful. 

![metasploit-config](images/image2.png)

This alert below shows our Snort rule #4 correctly detecting whenthere was possible malicious code uploaded. Snort rule #4 can be found here [here](Documentation.md).

![metasploit-config](images/image4.png)

Yet another test case, we were able to successfully detect an SQL injection on our system. Implementation of a rule such as this could be blocking this user/IP address once this type of activity was detected.

![metasploit-config](images/image5.png)

---

These test cases provide a proof of value that our Meterpeter Snort rules will notify the user when there is a detection of potential Meterpeter activity, along with other potentially malicious activity. We decided to just alert the user and not terminate the session as to not interupt daily work flow. This can be modified depending on the use case. More documentation can be located [here](Documentation.md).
