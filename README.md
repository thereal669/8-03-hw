# Домашнее задание к занятию "`Система мониторинга Zabbix`" - `Хавилов Виталий`


### Задание 1

`Ниже опишу этапы по установке Zabbix сервера, производил установку на системе Debian 12`

1. `apt install sudo`
2. `sudo apt update && sudo apt upgrade -y`
3. `sudo -u postgres createuser --pwprompt zabbix`
4. `sudo -u postgres createdb -O zabbix zabbix`
5. `wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian12_all.deb`
6. `dpkg -i zabbix-release_latest_7.4+debian12_all.deb`
7. `apt update`
8. `apt install zabbix-server-pgsql zabbix-frontend-php php8.2-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent`
9. `zcat /usr/share/zabbix/sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix`
10. `sudo nano /etc/zabbix/zabbix_server.conf (меняем пароль от базы данных)`
11. `sudo systemctl restart zabbix-server zabbix-agent apache2`
12. `sudo systemctl enable zabbix-server zabbix-agent apache2`

![Скрин 1](https://raw.githubusercontent.com/thereal669/8-03-hw/main/pics/complete_setup.jpg)
![Скрин 2](https://raw.githubusercontent.com/thereal669/8-03-hw/main/pics/first_auth.jpg)


---

### Задание 2

`Установка zabbix-agent'а на виртуальные машины Debian 12`

1. `wget https://repo.zabbix.com/zabbix/7.4/release/debian/pool/main/z/zabbix-release/zabbix-release_latest_7.4+debian12_all.deb`
2. `dpkg -i zabbix-release_latest_7.4+debian12_all.deb`
3. `apt update`
4. `apt install zabbix-agent`
5. `sudo nano /etc/zabbix/zabbix_agentd.conf (заменить ip-адреса сервера + написать хостнейм, по возможности можно раскоментировать порты актуальные)`
6. `systemctl restart zabbix-agent`
7. `systemctl enable zabbix-agent`

![Скрин 3](https://raw.githubusercontent.com/thereal669/8-03-hw/main/pics/two_hosts_import.jpg)

![Скрин 4](https://raw.githubusercontent.com/thereal669/8-03-hw/main/pics/logs_zabbix_agent.jpg)

![Скрин 5](https://raw.githubusercontent.com/thereal669/8-03-hw/main/pics/logs_zabbix_agent_2.jpg)

![Скрин 6](https://raw.githubusercontent.com/thereal669/8-03-hw/main/pics/latest_data.jpg)



