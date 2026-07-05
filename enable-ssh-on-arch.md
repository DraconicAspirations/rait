On Arch, it’s basically the same idea: install OpenSSH, enable the SSH daemon, and allow it through the firewall if you use one.

Run this on the Arch machine:

```bash
sudo pacman -S openssh
sudo systemctl enable --now sshd
```

Check that it’s running:

```bash
systemctl status sshd
```

From another machine, connect with:

```bash
ssh username@arch-machine-ip
```

To find the Arch machine’s IP:

```bash
ip addr
```

Look for something like `192.168.x.x` under your Ethernet or Wi-Fi interface.

If you use a firewall, for example `ufw`, allow SSH:

```bash
sudo ufw allow ssh
```

Or if using `firewalld`:

```bash
sudo firewall-cmd --add-service=ssh --permanent
sudo firewall-cmd --reload
```

The main SSH config file is here:

```bash
/etc/ssh/sshd_config
```

After editing it, restart SSH:

```bash
sudo systemctl restart sshd
```

One small Arch-specific thing: the service is called `sshd`, not `ssh`. So this is correct:

```bash
sudo systemctl enable --now sshd
```

Not:

```bash
sudo systemctl enable --now ssh
```
