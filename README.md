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



Azrail-Laba v2.0
Панель управления сетевой инфраструктурой и VPN-клиентами.

Требования
Ubuntu 22.04+ (рекомендуется)

Python 3.10+

Установленный пакет python3-venv

Быстрая установка
Клонирование репозитория:

Bash
git clone https://github.com/GodAzrail/azrail-laba-v2.0.git /opt/Azrail-Laba
cd /opt/Azrail-Laba
Настройка виртуального окружения:

Bash
python3 -m venv venv
source venv/bin/activate
Установка зависимостей:

Bash
pip install --upgrade pip
pip install -r requirements.txt
Подготовка сети (требуется для работы VPN-панели):

Bash
sysctl -w net.ipv4.ip_forward=1
Запуск:

Bash
# Запуск в фоновом режиме
nohup ./venv/bin/python app.py > panel.log 2>&1 &
Дополнительная информация
Логи: Все записи о работе панели сохраняются в panel.log.

Данные: Файлы users.json и traffic_history.json создаются автоматически или переносятся вручную после первого запуска.

Порт: Приложение по умолчанию использует 80-й порт (требуются права root).
