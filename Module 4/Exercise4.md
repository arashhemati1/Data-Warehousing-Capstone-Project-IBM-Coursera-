## Exercise 4: Schedule a Cron Job to Automate These Tasks

### Task 1: Start the Crontab
- Open the terminal and start the crontab editor by running:
  ```bash
  crontab -e

### Task 2: Schedule the Cron Job
- In the crontab editor, add the following line to schedule the ETL.sh script to run every 24 hours:
  ```bash
  0 0 * * * /bin/sh ETL.sh >> logfile.log 2>&1

### Task 3: Start the Cron Service
- To ensure the cron service is running, start it using:
  ```bash
  sudo service cron start
