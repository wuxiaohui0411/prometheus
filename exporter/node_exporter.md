# node exporter安装步骤

## 通过wget
wget https://github.com/prometheus/node_exporter/releases/download/v1.4.0/node_exporter-1.4.0.linux-amd64.tar.gz

tar zxvf node_exporter-1.4.0.linux-amd64.tar.gz -C /usr/local/

cd /usr/local

mv node_exporter-1.4.0.linux-amd64 node_exporter-1.4.0

ln -s node_exporter-1.4.0 node_exporter

```bash
cat << EOF >/usr/lib/systemd/system/node_exporter.service 
[Unit] 
Description=https://prometheus.io

[Service]
Restart=on-failure
ExecStart=/usr/local/node_exporter/node_exporter

[Install]
WantedBy=multi-user.target
EOF
```

```bash
systemctl daemon-reload
systemctl start node_exporter
systemctl enable node_exporter
ss -anlp | grep 9100
```