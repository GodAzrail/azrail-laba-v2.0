Azrail-Laba VPN Panel
Панель управления сетевой инфраструктурой и VPN-клиентами (AmneziaWG).

Быстрый старт
1. Клонирование репозитория
Bash
git clone https://github.com/GodAzrail/azrail-laba-v2.0.git /opt/Azrail-Laba
cd /opt/Azrail-Laba
2. Настройка окружения
Bash
# Установка необходимых системных пакетов (если не установлены)
sudo apt update && sudo apt install -y python3-venv

# Создание и активация виртуального окружения
python3 -m venv venv
source venv/bin/activate

# Установка зависимостей
pip install --upgrade pip
pip install -r requirements.txt
3. Настройка сети и запуск
Bash
# Включение пересылки трафика
sudo sysctl -w net.ipv4.ip_forward=1

# (Опционально) Настройка NAT для Docker-контейнера (если используется AmneziaWG)
# docker exec -i amnezia-awg2 iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j MASQUERADE

# Запуск панели в фоновом режиме
nohup ./venv/bin/python app.py > panel.log 2>&1 &
Требования
ОС: Ubuntu 22.04+

Python: 3.10+

Права: Для работы на 80-м порту требуются права root.

Дополнительная информация
Логи: Все записи о работе панели сохраняются в файл panel.log.

Данные: Файлы users.json, custom_clients.txt и traffic_history.json создаются автоматически или переносятся с предыдущих инстансов вручную.

Безопасность: Не забывайте настраивать API-KEY для взаимодействия с внешними системами
