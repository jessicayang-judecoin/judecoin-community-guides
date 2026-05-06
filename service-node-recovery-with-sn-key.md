## 【Description】

This is a community operation guide for restoring a Judecoin Service Node using the original SN private key.

This guide applies to situations where the original server is lost, reinstalled, damaged, migrated, or no longer available, but the original Service Node private key is still available.

This guide is shared in the Discussion section as a community operation reference. It is not an official document yet, but I hope it can help users restore their nodes more clearly and safely.

## 【Important Notice】

The CLI version used in this example is v3.1.2. This is only for the current version reference.

If Judecoin releases a newer CLI version in the future, please always follow the latest version provided by the official website or official GitHub, and update the download link, extracted folder name, and version number accordingly.

Restoring a Service Node requires the original SN private key.

Do not disclose the SN private key. Do not send it to anyone. Do not post it in any group chat. Do not take screenshots or screen recordings when entering the private key.

## 【Recovery Principle】

A Judecoin Service Node has its own node identity private key.

If the original server is lost or needs to be migrated, the original Service Node identity can be restored on a new server by restoring the original SN private key.

The core idea is:

Restore the original SN private key into a key file, place it at:

/home/ubuntu/.bitjudecoin/key_ed25519

Then restart the Service Node with the restored key.

## 【Judecoin Service Node Recovery Process】

### 1. Install Required Tools

Log in to the server terminal and run:

sudo apt update

sudo apt install wget tar bzip2 curl -y

### 2. Download Judecoin CLI

Run:

wget https://www.judecoin.io/storage/files/cli/judecoin-linux-x64-v3.1.2.tar.bz2

Note:

If a newer CLI version has been officially released, replace v3.1.2 in the link above with the latest version number.

### 3. Extract the CLI File

Run:

tar -jxvf judecoin-linux-x64-v3.1.2.tar.bz2

### 4. Enter the Judecoin CLI Directory

Run:

cd judecoin-x86_64-linux-gnu-v3.1.2

### 5. Check the CLI Version

Run:

./judecoind --version

If it shows v3.1.2, the current CLI version is correct.

If the official version has been updated, please use the latest displayed version as the reference.

### 6. Stop the Old judecoind Process

Run:

pkill judecoind

### 7. Remove Any Temporary sn_key File

Run:

rm -f sn_key

This step avoids conflicts with any old temporary sn_key file in the current directory.

### 8. Restore the SN Private Key

Run:

./judecoin-sn-keys restore sn_key

The system will prompt you to enter the original Service Node private key.

Enter the original SN private key as prompted.

Important:

Make sure your environment is safe when entering the private key. Do not take screenshots, do not record the screen, and do not allow anyone else to see it.

### 9. Create the Judecoin Data Directory

Run:

sudo mkdir -p /home/ubuntu/.bitjudecoin

### 10. Copy the Restored sn_key to the Service Node Key Location

Run:

sudo cp sn_key /home/ubuntu/.bitjudecoin/key_ed25519

### 11. Set Directory and File Permissions

Run:

sudo chown -R ubuntu:ubuntu /home/ubuntu/.bitjudecoin

chmod 700 /home/ubuntu/.bitjudecoin

chmod 600 /home/ubuntu/.bitjudecoin/key_ed25519

### 12. Restart the Service Node

Run:

./judecoind --service-node --service-node-public-ip $(curl -s ifconfig.me) --no-zmq --detach

### 13. Wait for Node Initialization

Run:

sleep 30

### 14. Check Node Status

Run:

./judecoind status

If you can see block height, synchronization status, and network connection information, the node has started successfully.

If the node is still syncing, wait until synchronization is completed.

## 【Full Command Reference】

The following is the full command sequence for reference:

sudo apt update

sudo apt install wget tar bzip2 curl -y

wget https://www.judecoin.io/storage/files/cli/judecoin-linux-x64-v3.1.2.tar.bz2

tar -jxvf judecoin-linux-x64-v3.1.2.tar.bz2

cd judecoin-x86_64-linux-gnu-v3.1.2

./judecoind --version

pkill judecoind

rm -f sn_key

./judecoin-sn-keys restore sn_key

sudo mkdir -p /home/ubuntu/.bitjudecoin

sudo cp sn_key /home/ubuntu/.bitjudecoin/key_ed25519

sudo chown -R ubuntu:ubuntu /home/ubuntu/.bitjudecoin

chmod 700 /home/ubuntu/.bitjudecoin

chmod 600 /home/ubuntu/.bitjudecoin/key_ed25519

./judecoind --service-node --service-node-public-ip $(curl -s ifconfig.me) --no-zmq --detach

sleep 30

./judecoind status

## 【Common Notes】

1. Restoring a node is not the same as registering a new node.

The purpose of this process is to allow a new server to continue using the original Service Node identity.

2. The original SN private key must be used.

If a new SN private key is used, the blockchain will treat it as a different node identity and it may not match the original Service Node.

3. Do not delete the key_ed25519 file.

The key_ed25519 file is the node identity file and is very important.

4. Do not disclose the SN private key.

Anyone who obtains the SN private key may affect the security of the node identity.

5. If the node has already been fully deregistered on-chain and entered the release period, restoring the server may not reactivate the original node.

In that case, the locked stake may need to wait for the release period to end, depending on the on-chain state.

6. If ./judecoind status does not show status immediately, the node may have just started and may not be fully initialized yet. Wait 1-2 minutes and check again.

## 【Security Reminders】

Please pay attention to the following:

- Do not disclose the Service Node private key;
- Do not disclose wallet seed phrases;
- Do not disclose wallet private keys;
- Do not disclose AWS .pem files;
- Do not expose server IP addresses, login information, or backend screenshots;
- Do not send the SN private key through chat apps, emails, or public groups;
- Use a hardware encrypted USB drive to store SN private keys and AWS .pem files;
- Keep at least two offline backups in separate safe locations.

## 【Conclusion】

This guide is a community operation reference intended to help users restore a Judecoin Service Node when they still have the original SN private key.

It is not an official document yet, but I hope it can help community users and provide practical feedback for future documentation.
