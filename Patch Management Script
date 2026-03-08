#!/bin/bash

SERVER_LIST="servers.txt"
LOG_FILE="patch_log.txt"

echo "Starting Patch Management Process$(date)">> $LOG_FILE
echo "---------------------------------"

for SERVER in $(cat $SERVER_LIST)
do
    echo "Connecting to $SERVER" >>$LOG_FILE

    ssh -t root@$SERVER "sudo yum update -y" >>$LOG_FILE

    echo "Checking updates on $SERVER" >>$LOG_FILE

    sudo yum check-update

    echo "Installing patches" >>$LOG_FILE

    sudo yum update -y

    echo "Removing unused packages" >>$LOG_FILE
