# Lin-CMS system has weak password vulnerability

**System fingerprint status**：

The system fingerprint status is as follows:

![img](C:/Users/%E8%83%A1%E5%B9%BF%E5%B7%9D/AppData/Local/Temp/ksohtml15524/wps1.jpg) 

 

**vulnerability analysis**：

The tests folder is a file used by developers for testing, and the config.py file exists in the tests folder.

![img](C:/Users/%E8%83%A1%E5%B9%BF%E5%B7%9D/AppData/Local/Temp/ksohtml15524/wps2.jpg) 

This file contains the administrator's default account and password.Due to the failure to delete and clean up in time, a security risk was left behind.

Attackers can directly log in with the default administrator account and password that have not been cleared, gain control of the account, and thus face high risks such as complete system takeover and leakage of sensitive information.

 