## 【Description】

This is a community guide for restarting a Judecoin Service Node.

This guide applies to situations where a node needs to be restarted, rerun after an upgrade, restored after a server reboot, or checked again for running status.

This guide is shared in the Discussion section as a community operation reference. It is not an official document yet, but I hope it can help community users restart their nodes more clearly and safely.

## 【Important Notice】

The CLI version used in this example is v3.1.2. This is only for the current version reference.

If Judecoin releases a newer CLI version in the future, please always follow the latest version provided by the official website or official GitHub, and update the download link, extracted folder name, and version number accordingly.

For example:

Current example download file:

judecoin-linux-x64-v3.1.2.tar.bz2

Current example extracted folder:

judecoin-x86_64-linux-gnu-v3.1.2

If the official version is updated to v3.1.3 or higher, please replace the version number with the latest one accordingly.

## 【Judecoin Service Node Restart Process】

### 1. Enter the Server

Log in to your server terminal first, then go to the home directory:

cd ~

### 2. Update the Server Environment

Run:

sudo apt update

Install the required tools:

sudo apt install wget tar bzip2 curl -y

### 3. Download Judecoin CLI

Run:

wget https://www.judecoin.io/storage/files/cli/judecoin-linux-x64-v3.1.2.tar.bz2

Note:

If a newer CLI version has been released officially, replace v3.1.2 in the link above with the latest version number.

### 4. Extract the CLI File

Run:

tar -jxvf judecoin-linux-x64-v3.1.2.tar.bz2

Note:

If you downloaded a newer version file, replace the file name accordingly.

### 5. Enter the Judecoin CLI Directory

Run:

cd judecoin-x86_64-linux-gnu-v3.1.2

Note:

If the official version has been updated, enter the corresponding new version directory.

### 6. Check the Version

Run:

./judecoind --version

If it shows v3.1.2, the current CLI version is correct.

If the official version has been updated, please use the latest displayed version as the reference.

### 7. Stop the Old judecoind Process

Run:

pkill judecoind

Wait for 5 seconds:

sleep 5

Check whether there is still any judecoind process running:

ps aux | grep judecoind

If you only see the grep judecoind line, it usually means the old process has stopped.

### 8. Restart the Service Node

Run:

./judecoind --service-node --service-node-public-ip $(curl -s ifconfig.me) --no-zmq --detach

This command automatically gets the server public IP and restarts the Service Node in the background.

### 9. Check Node Status

Run:

./judecoind status

If you can see the block height, synchronization status, and network connection information, the node has been restarted.

If the node is still syncing, please wait until synchronization is completed.

## 【Common Notes】

1. If the server has already downloaded and extracted the current CLI version, it is not always necessary to download it again. You can directly enter the existing Judecoin CLI directory and restart the node.

2. If ./judecoind status does not show status immediately, the node may have just started and may not be fully initialized yet. Wait 1-2 minutes and check again.

3. If the node still does not show status after a long time, you can run the startup command again:

./judecoind --service-node --service-node-public-ip $(curl -s ifconfig.me) --no-zmq --detach

Then check again:

./judecoind status

4. Restarting the node will not change your wallet staking transaction and will not automatically unlock your stake, but make sure the Service Node private key has been backed up.

5. Do not delete the .bitjudecoin directory, do not delete the key_ed25519 file, and do not disclose your server private key, wallet private key, seed phrase, or AWS .pem file.

6. If the official team releases a new CLI version, please check the official upgrade instructions first before updating the version and restarting the node.

## 【Security Reminders】

Please pay attention to the following:

- Do not disclose server IP addresses, login information, or backend screenshots;
- Do not disclose the Service Node private key;
- Do not disclose wallet seed phrases or private keys;
- Do not disclose AWS .pem files;
- Do not click unknown emails or unknown links;
- When downloading the CLI, prioritize links provided by the official website or official GitHub;
- It is recommended to store the Service Node private key, AWS .pem file, and node records in a hardware encrypted USB drive;
- It is recommended to keep at least two offline backups in separate safe locations.

## 【Conclusion】

This guide is a community operation reference intended to help users quickly restart a Judecoin Service Node.

It is not an official document yet, but I hope it can help community users and provide practical feedback for future documentation.
