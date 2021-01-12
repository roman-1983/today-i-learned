# Configure timezone

For nearly all projects i am using a vagrant box to develop locally. Most of them run under Debian or Ubuntu.
In a lot of projects we share the virtual machine - and sometimes it is not configured properly.

I had a problem using an API - and i  figured out that the time was not set correct. So first i fixed the timezone:
This open a interactive prompt which makes it easy to set the timezone. 

```bash
dpkg-reconfigure tzdata
```

To automate this step it is also possible to set the timezone without prompt:

```bash
cp /usr/share/zoneinfo/Europe/Berlin /etc/localtime
```