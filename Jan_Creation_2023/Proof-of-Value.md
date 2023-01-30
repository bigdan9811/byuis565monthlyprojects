# Proof of Value
*Meterpreter Snort Rule*

This test case will include a target and an attacker machine. The target machine will have our Meterpreter Snort rule code stored and running on it, where the attacker machine will run Meterpreter to attack the target machine. In this scenario, it will show what the target machine will see before our Meterpreter Snort rule is implemented and what the target machine will see after it is implemented.

---

The following image will shows the Meterpreter configuration (IP and Port).

![metasploit-config](images/Metasploit-config.png)

This next image displays the target machine information.

![metasploit-config](images/target-machine-info.png)

Next, the exploit is run from the attackers machine.

![metasploit-config](images/running-exploit.png)

Below shows the results on the target machine **before** the Snort rule was implemented on the target machine.

![metasploit-config](images/pre-metasploit-rule.png)

Showing the results on the target machine **after** the Snort rule was implemented on the target machine. Notice the "Meterpeter session detected" message being sent.

![metasploit-config](images/post-metasploit-rule.png)

---

This test case provides a proof of value that our Meterpeter Snort rule will notify the user when there is a detection of potential Meterpeter activity. We decided to just alert the user and not terminate the session as to not interupt daily work flow. This can be modified depending on the use case. More documentation can be located [here](Documentation.md).
