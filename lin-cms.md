# Lin-CMS system has weak password vulnerability

**System fingerprint status**：

The system fingerprint status is as follows:

![image-20251223171426540](https://gitee.com/star3119391396/cloudimage/raw/master/img/image-20251223171426540.png) 

 

**vulnerability analysis**：

The tests folder is a file used by developers for testing, and the config.py file exists in the tests folder.

![image-20251223171437103](https://gitee.com/star3119391396/cloudimage/raw/master/img/image-20251223171437103.png) 

This file contains the administrator's default account and password.Due to the failure to delete and clean up in time, a security risk was left behind.

Attackers can directly log in with the default administrator account and password that have not been cleared, gain control of the account, and thus face high risks such as complete system takeover and leakage of sensitive information.

 