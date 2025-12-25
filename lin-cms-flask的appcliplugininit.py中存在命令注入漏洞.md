# Command injection vulnerability exists in appcliplugininit.py in lin-cms-flask

**Vulnerability description:**

Shell=True is used to execute the system command in the__execute_cmd method of app/cli/plugin/init.py, and the command parameters include the plug-in name entered by the user. Attackers can execute arbitrary system commands by constructing malicious plug-in names.

Impact: An attacker can execute arbitrary system commands by constructing malicious plug-in names, potentially causing the server to be completely controlled. This is a serious remote code execution vulnerability.

**Bug code:**

```python
code = subprocess.check_call(cmd, shell=True, stdout=subprocess.PIPE)
```

![image-20251225112942729](https://gitee.com/star3119391396/cloudimage/raw/master/img/image-20251225112942729.png)

**Repair suggestions**

1. Avoid using shell=True and use a parameter list to pass the command;
2. Strictly verify and filter user input and prohibit special characters
3. Use secure APIs instead of direct system command execution;
4. Implement appropriate input verification and sandboxing mechanisms.

**recurring steps**

1. Create a malicious plug-in name that contains the command injection payload
2. Observe whether the constructed command contains dangerous characters
3. Confirm that the use of shell=True increases the risk of command injection

**Concept POC**

```
import subprocess
def mock_execute_cmd(cmd):
    print(f"[MOCK] Executing command: {cmd}")
    if ';' in cmd or '|' in cmd or '&' in cmd or '`' in cmd or '$(' in cmd:
        print("[VULNERABILITY CONFIRMED] Command injection possible!")
        return True
    return False

def simulate_vulnerable_function(plugin_name):
    file_path = "/app/plugin/" + plugin_name + "/requirements.txt"
    cmd = "pip install -r " + file_path
    print(f"Command: {cmd}")
    return mock_execute_cmd(cmd)

simulate_vulnerable_function("malicious_plugin; echo PWNED")
```
