# Домашнее задание к занятию "GitLab" - Новоселов Степан


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

![Скриншот 1 к заданию 1](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/Castomization%20R1.png)

![Скриншот 2 к заданию 1](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/Castomization%20R2.png)

![Файл PKT](https://github.com/NewParadigma96/netology-git-8.02/blob/main/files/hsrp_advanced%20novoselov.pkt)
### Задание 2

Bash-скрипт
```
FILE=`test -f /var/www/html/index.nginx-debian.html && echo $?`
PORT=`bash -c "</dev/tcp/localhost/80" && echo $?`

if [ $PORT -eq 0 ] && [ $FILE -eq 0 ]; then
	exit 0
else
	exit 1
fi
```

Keepalived.conf
```
global_defs {
	script_user root
	enable_script_security
}

vrrp_script check_g {
	script "/usr/bin/bash.sh
	interval 3
	user root
}

vrrp_instance VI_1 {
	state MASTER
	interface enp0s8
	virtual_router_id 51
	priority 255
	advert_int 1

	virtual_ipaddress {
		192.168.1.15/24
	}

	track_script {
		check_g
	}
}
```

![Скриншот 1 к заданию 2](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/port%20refused.png)
![Скриншот 2 к заданию 2](https://github.com/NewParadigma96/netology-git-8.02/blob/main/img/the%20file%20is%20missing.png)
