__Major threats__: Unauthorized access

#### What?
GuardDuty is an Intrusion Detection System (IDS) in AWS, it can generate a finding when an malicious is detected.

![image](https://github.com/user-attachments/assets/c2edf472-0169-4392-ac06-45df42c856dd)
(source: https://medium.com/@tahirbalarabe2/%EF%B8%8Fthreat-detection-with-aws-guardduty-f6f72d9da62a)

#### How
Guardduty monitors the following data sources in AWS:
1. network traffic
2. CloudTrail logs (management events, data events)
3. DNS queries
4. VPC Flow Logs
5. EKS logs
   
#### Integrating
1. EventBridge, CloudWatch, SNS
2. CloudTrail
3. Lambda: modify WebACL, update NACL.

#### Advanced concepts:
1. GuardDuty can manage multiple accounts: administrator account, member accounts.
2. Trusted IP List
3. Threat IP List
4. Suppression Rules
