This project has been requested to be cloned and worked on for the purpose of Udacity's Cloud DevOps course's 3rd project.

If you would like to run this project yourself, here's what you need:
-A circleci account
-An AWS account
-A postgres DB (make sure you fill in the initial DB name in the additional configuration)
-An IAM user for EC2ReadOnlyAccess (for prometheus which's the last step)
-Fill in the environment variables accordingly in the circleci project settings:
AWS\*ACCESS_KEY_ID=(from IAM user with programmatic access)
AWS_SECRET_ACCESS_KEY= (from IAM user with programmatic access)
AWS_DEFAULT_REGION=(your default region in aws)
TYPEORM_CONNECTION=postgres
TYPEORM_MIGRATIONS_DIR=./src/migrations
TYPEORM_ENTITIES=./src/modules/domain/\*\*/\_.entity.ts
TYPEORM_MIGRATIONS=./src/migrations/\*.ts
TYPEORM_HOST={your postgres database endpoint in RDS}
TYPEORM_PORT=5432 (or the port from RDS if it’s different)
TYPEORM_USERNAME={your postgres database username in RDS}
TYPEORM_PASSWORD={your postgres database password in RDS}
TYPEORM_DATABASE={your postgres database name in RDS}

Be very sure to check your inbound ports in the security group's settings because this is where most mistakes happen:
9090, 9093, 9100, 5432 (or your own DB port), 3030, 22

Run the build and you got yourself a fully functional CI/CD pipeline.

To make your own prometheus server and receive alerts follow these articles:
https://codewizardly.com/prometheus-on-aws-ec2-part1/
https://codewizardly.com/prometheus-on-aws-ec2-part3/
https://codewizardly.com/prometheus-on-aws-ec2-part2/
https://codewizardly.com/prometheus-on-aws-ec2-part4/
(I recommend to not use g-mail, I'll add links for Slack instead)
https://grafana.com/blog/2020/02/25/step-by-step-guide-to-setting-up-prometheus-alertmanager-with-slack-pagerduty-and-gmail/
