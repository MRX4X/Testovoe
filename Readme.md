## Тестовое задание: сервер статики (Docker + Ansible)

### 1) Подготовка рабочей среды

```bash
docker-compose -f ./Docker-venv/docker-compose.yaml up --build -d
```

### 2) Запуск плейбука с ролями


```bash
ansible-playbook -i ./Ansible/inventory.ini ./Ansible/test_install.yml
```