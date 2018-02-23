# Supervisor Addon for Jelastic

Supervisor is a client/server system that allows its users to monitor and control a number of processes on UNIX-like operating systems.

## Install it

At this writing moment, this is a prealpha version of this AddOn. You can install it by using the `Import` feature in Jelastic and paste the github-url for supervisord.yml and then choose your environment and container.

## Configure it

After installing the addon you should have a directory in `/var/www/webroot/` called `supervisord.d`, in this directory you can now add configurations. Here's an example, paste this into `test.ini` and upload it through Jelastic UI:

```
[program:test-worker]
process_name=%(program_name)s_%(process_num)02d
command=sh -c 'while ( true ); do date; sleep 1; done'
autostart=true
autorestart=true
user=nginx
numprocs=8
redirect_stderr=true
```

Afterwards, in the top right corner there's a "hamburger" menu, click it and hit `Reload Supervisor` and it will run the configuration.

## supervisorctl

If you want more control over everything, you can use SSH to login to your container and run the command `supervisorctl` and it should give you the current status.

## Fork it, PR us

If you want to make this better, and you know how to. Don't hesitate to fork this repository and send a PR to us. We'll probably merge it!

## Credits

* [Supervisor](http://supervisord.org/)
