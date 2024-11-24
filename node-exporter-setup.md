# Download node-exporter

```bash
sudo wget https://github.com/prometheus/node_exporter/releases/download/v1.8.2/node_exporter-1.8.2.linux-amd64.tar.gz
```

# Extract node-exporter

```bash
tar -xzf node_exporter-1.8.2.linux-amd64.tar.gz
```

# Remove unused node-exporter archive

```bash
rm -rf node_exporter-1.8.2.linux-amd64.tar.gz
```

# Move node-exporter

```bash
sudo mv node_exporter-1.8.2.linux-amd64 /etc/node_exporter
```

# Create a systemd service file for node-exporter

```bash
sudo nano /etc/systemd/system/node_exporter.service
```

# Add the following content to the file:

```nano
[Unit]
Description=Node Exporter
Wants=network-online.target
After=network-online.target

[Service]
ExecStart=/etc/node_exporter/node_exporter
Restart=always

[Install]
WantedBy=multi-user.target
```

# Reload, start, and enable start on boot systemd daemon node-exporter

```bash
sudo systemctl daemon-reload
sudo systemctl enable node_exporter
sudo systemctl restart node_exporter
```

# Verify that node-exporter is running

```bash
sudo systemctl status node_exporter
```
