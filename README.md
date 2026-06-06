# Azrail-Laba VPN Panel
Легкая веб-панель для управления AmneziaWG в Docker.
## Быстрый старт
```bash
git clone [https://github.com/GodAzrail/Azrail-Laba.git](https://github.com/GodAzrail/Azrail-Laba.git) /opt/Azrail-Laba
cd /opt/Azrail-Laba
python3 -m venv venv
venv/bin/pip install -r requirements.txt
sysctl -w net.ipv4.ip_forward=1
docker exec -i amnezia-awg2 iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j MASQUERADE
nohup /opt/Azrail-Laba/venv/bin/python /opt/Azrail-Laba/app.py > /opt/Azrail-Laba/panel.log 2>&1 &
