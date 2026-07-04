# Enable SSH on Fedora Live

## Enable SSH on Fedora

1. Install the SSH server (if it isn’t already installed):

sudo dnf install openssh-server

2. Enable and start the service:

sudo systemctl enable --now sshd

3. Verify it’s running:

sudo systemctl status sshd

You should see something like:

Active: active (running)

4. If Fedora’s firewall is enabled, allow SSH:

sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload

5. Find the machine’s IP address:

ip addr

or the simpler:

hostname -I

You might see something like:

192.168.1.42

6. Set password (if needed)

passwd

## Connect using the IP

From another Linux or macOS machine:

ssh username@192.168.1.42
