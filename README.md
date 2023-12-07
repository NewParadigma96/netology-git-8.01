# Домашнее задание к занятию "Система мониторинга Zabbix" - Новоселов Степан


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

### Задание 1

1. [Скриншот авторизации в админке](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/Admin_dashboard.png)

Установка и настройка Zabbix для Debian 11 (Bullseye)

Установка PostgreSQL

'apt install postgresq'

Установка Zabbix репозитория

'''
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb
apt update
'''

Установка Zabbix server, frontend, agent

'apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent'

Создание пользователя БД

'sudo -u postgres createuser --pwprompt zabbix'

Создание БД

'sudo -u postgres createdb -O zabbix zabbix'

Импортирование схемы и данных на сервер Zabbix

'zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix'

Редактирование файла конфигурации БД сервера Zabbix

'sudo nano /etc/zabbix/zabbix_server.conf'

Настройка PHP для Zabbix веб-интерфейса

'sudo nano /etc/httpd/conf.d/zabbix.conf'

Запуск Zabbix server, Zabbix agent и веб-сервер

'''
sudo systemctl restart zabbix-server apache2 # zabbix-agent 
sudo systemctl enable zabbix-server apache2 # zabbix-agent
'''

### Задание 2

![Скриншот раздела Configuration > Hosts](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/Configuratoin_hosts.png)
![Скриншот лога zabbix agent](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/zabbix_agent_log.png)
![Скриншот раздела Monitoring](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/Latest_data.png)

Установка Zabbix agent

'apt install zabbix-agent'

Настройка файла конфигурации zabbix agent

'sudo nano /etc/zabbix/zabbix_agentd.conf'

Запуск Zabbix agent

'''
sudo systemctl restart zabbix-agent
sudo systemctl enable zabbix-agent
'''

Просмотров лога zabbix agent

'cat /var/zabbix/zabbix_agentd.log'
