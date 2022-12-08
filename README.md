# linux-admin-task

Clone the repo
------------------

```
# git clone https://github.com/piyushgour/linux-admin-task.git
```

Change the working directory 
------------------

```
# cd linux-admin-task
# ls 
```

Output looks like -
```
README.md  app.ini  config_files  inventory.txt  setup.yaml  uwsgi.service  wsgi.py

```

Working with ansible  
--------------------

first we need to update our Host inventory list. So we need to update **inventory.txt** file.
```
# vim inventory.txt 
```
you can use your fav. editor to update inventory file. :-) 

Output looks like -
```
[appserver]
localhost 
```
Update **localhost** value according to you target server's.

Execute Playbook
------------------
```
# ansible-playbook setup.yaml -i inventory.txt 

```

Output looks like :
```

PLAY [appserver] ************************************************************************************

TASK [Gathering Facts] ******************************************************************************
ok: [localhost]

TASK [install required package] *********************************************************************
ok: [localhost]

TASK [Copy data to a file] **************************************************************************
ok: [localhost]

TASK [Create Application INI File] *******************************************************************
changed: [localhost]

TASK [Copy data to a file] **************************************************************************
ok: [localhost]

TASK [Create uWSGI service File] ********************************************************************
changed: [localhost]

TASK [Update uWSGI service file] ********************************************************************
ok: [localhost]

TASK [Enable uwsgi sites] ***************************************************************************
ok: [localhost]

TASK [available uwsgi sites] ************************************************************************
ok: [localhost]

TASK [create uWSGI log directory] *******************************************************************
changed: [localhost]

TASK [uWSGI service start command] ******************************************************************
changed: [localhost]

PLAY RECAP ******************************************************************************************
localhost                  : ok=11   changed=4    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

```


Important Points To summarize:
------------------------------


* ``nginx.conf`` file contains **nginx webserver** configuration under `config_files` folder.
* ``uwsgi.conf`` file contains uwsgi application web configuration under `config_files` folder.
* ``aap.ini`` file contains **uwsgi** configuration.
* ``uwsgi.service`` file contains **os service** related entries.
* ``wsgi.py`` file contains main method that call application execution.