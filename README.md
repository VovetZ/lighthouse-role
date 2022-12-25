Lighthouse-role
=========

Роль устанавливает Lighthouse и Nginx

### Требования

1. Выполнение роли на deb-based дистрибутивах Linux (Debian, Ubuntu)
2. На хосте предварительно установлена утилита unzip

### Переменные

В [defaults](./defaults/main.yml) указана версия Nginx 1.18.0

В [vars](./vars/main.yml) указан порт Lighthouse, по умолчанию 80.

### Зависимости

Нет зависимостей

### Пример использования роли

Для использования на хостах, где уже установлена утилита Unzip:

```yaml
- name: Install Lighthouse
  hosts: lighthouse
  roles:
    - lighthouse-role
```

Для с установки утилиты Unzip в рамках pre_tasks:

```yaml
- name: Install Lighthouse
  hosts: lighthouse
  pre_tasks:
    - name: install unzip
      become: true
      ansible.builtin.apt:
        name: unzip
        state: present
        update_cache: yes
  roles:
    - lighthouse-role
```


License
-------

Free

Author Information
------------------

Владимир Кузеванов
