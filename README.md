#EC2 Auto Start/Stop Scheduler

Automatically starts and stops AWS EC2 instances on weekdays using AWS Lambda and Amazon EventBridge.

-> Architecture
EventBridge (Cron Schedule) → Lambda Function → EC2 Instance

-> How It Works
- Every weekday at **9:00 AM IST** → EC2 instance **starts**
- Every weekday at **9:00 PM IST** → EC2 instance **stops**
- Instances are selected based on tags: `AutoStart: true` and `AutoStop: true`

-> AWS Services Used
- Amazon EC2
- AWS Lambda (Python)
- Amazon EventBridge Scheduler
- AWS IAM

-> EC2 Tags Required
| Tag Key | Tag Value |
|---------|-----------|
| AutoStart | true |
| AutoStop | true |
| Environment | Development |

-> EventBridge Schedules
| Schedule Name | Cron | Action |
|--------------|------|--------|
| EC2-Start-9AM-IST | `0 9 ? * MON-FRI *` | Start EC2 |
| EC2-Stop-9PM-IST | `0 21 ? * MON-FRI *` | Stop EC2 |

-> IAM Permissions
- AmazonEC2FullAccess
- CloudWatchLogsFullAccess

*Region
Asia Pacific - Mumbai (`ap-south-1`)
