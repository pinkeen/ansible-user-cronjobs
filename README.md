Configure per-user cronjobs with a twist 
========================================

The `cron` ansible module works fine most of the time although using it has one serious flaw: it provides no way
to remove unused or changed cronjobs. Once you change the name or remove a cronjob you will likely have to manually
remove old entry.

This role manages only user cronjobs in `/var/spool/cron/{{ username }}`. Works with CentOS/RHEL 6/7.
Supporting other distributions will probably require change of this path.

Configure
```yml
    cronjobs:
        username:
            - name: cronjobname (optional)
              cmd: /usr/bin/yourcmd
              min: *
              hour: *
              day: *
              month: *
              weekday: *
        username2:
            - name: sth
              min: 0
```