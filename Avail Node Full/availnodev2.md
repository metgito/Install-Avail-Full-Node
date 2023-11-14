1:

git checkout v1.7.2

2:

cd avail 

3:

sudo systemctl stop availd.service

 4:

git pull 

5:

git checkout v1.8.0.0 

6:

cargo run \--locked \--release \-- \--chain goldberg -d ./output 

7:

sudo nano /etc/systemd/system/availd.service 

------------------------------------

\[Unit\] Description=Avail
Validator After=network.target StartLimitIntervalSec=0 \[Service\]
User=root ExecStart= /root/avail/target/release/data-avail \--base-path
\`pwd\`/data \--chain goldberg \--name \"HerslayTC\" Restart=always
RestartSec=120 \[Install\] WantedBy=multi-user.target Đổi tên chain =
goldberg

-----------------------------------

8:

sudo systemctl disable availd.service 
sudo systemctl enable availd.service 

9:

systemctl daemon-reload 

10:

sudo systemctl start availd.service

11:

sudo systemctl status availd.service

12:

journalctl -f -u availd 13:

Here
https://telemetry.avail.tools/#list/0x6f09966420b2608d1947ccfb0f2a362450d1fc7fd902c29b67c906eaa965a7ae
