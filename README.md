# Автоматизация развертывания приложения в локальной среде

## Для начала

1. Проект предназначен для автоматизации развертывания приложения в инфраструктуре из трех серверов (Alt Linux, Astra Linux, RedOS) с последующей настройкой маршрутизации и контроля доступа.
2. Плейбук динамически выдает роли для серверов в зависимости от нагрузки системы. Самый загруженный сервер выполняет роль маршрутизатора и выдает доступ в глобальную сеть. Самый наименее нагруженный сервер выполняет роль клиента, он получает доступ к серверу с базой данных и имеет возможность просматривать саму базу данных. На втором сервере установлена ArangoDB, с помощью Docker контейнера. Версия ArangoDB - 3.8.7.

## Быстрый старт
В проекте представлены плейбуки для автоматизации развертывания приложения. 
Команда для клонирования репозитория:

```
git clone https://github.com/Cassidym-Meredyth/Deploying-a-database.git
cd путь_директории/Deploying-a-database/ansible-playbook
```

Структура проекта:
```
/путь_до_директории/Deploying-a-database/ansible-playbook/
├── ansible.cfg
├── group_vars
│   └── all.yml
├── inventory
│   └── hosts.yml
├── playbooks
│   ├── configure_network.yml
│   ├── main.yml
│   └── test_router.yml
└── roles
    ├── client
    │   ├── handlers
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       └── network_interface.network.j2
    ├── db
    │   ├── handlers
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       └── network_interface.network.j2
    └── router
        ├── files
        │   └── network_interface.network.j2
        ├── handlers
        │   └── main.yml
        ├── tasks
        │   └── main.yml
        └── templates
            └── network_interface.network.j2
```

Команда для запуска плейбуков

```
ansible-playbook -i /путь_до_директории/Deploying-a-database/ansible-playbook//inventory/hosts.yml /путь_до_директории/Deploying-a-database/ansible-playbook/playbooks/main.yml --flush-cache
```

Приложение будет доступно по адресу:
```
http://arangodb.local:8529/_api/version
```

## Заключение
Суперская курсовая работа!!!

![я_после_курсовой](docs/img/cat.gif)
