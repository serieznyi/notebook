Запускаем ssh агент при входе
=============================

Иногда нужно зайти на сервер и что бы deploy ключи уже были добавлены в агента

Добавляем в файл `~/.bashrc` следующее

::

    if [ -z "$SSH_AUTH_SOCK" ] ; then
      eval `ssh-agent -s`
      ssh-add
    fi
    
    ssh-add ~/.ssh/*_deploy_rsa

Еще есть вариант с явным прописыванием ключей на каждый хост в `~/.ssh/config`.

Лучше так же позаботится и о нескольких ключах на одной машине.

:ref:`multiple_deploy_keys_in_ssh`