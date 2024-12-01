# Install and configure gitlab on server with debian package

## Installation(https://about.gitlab.com/install/#debian)

Configuration server hostname and ip address:

```bash
sudo vim /etc/hosts
38.0.101.76 gitlab.anisa.local
hostnamectl set-hostname gitlab.anisa.local
```

Install and configure the necessary dependencies

```bash
sudo apt-get update
sudo apt-get install -y curl openssh-server ca-certificates perl
```

**Optional**: Install and configure SMTP

```bash
sudo apt-get install -y postfix
```

### Download and extract the GitLab package manually

Check the `https://packages.gitlab.com/gitlab/gitlab-ce` for the latest version.

Download debian packages based on your OS version.

For debian 12 (bookworm):

```bash
wget --content-disposition https://packages.gitlab.com/gitlab/gitlab-ce/packages/debian/bookworm/gitlab-ce_17.4.5-ce.0_amd64.deb/download.deb
```

After the download is complete, install the package:

```bash
sudo dpkg -i gitlab-ce_17.4.5-ce.0_amd64.deb
```
Edit gitlab config file and set external url:

```bash
sudo vim /etc/gitlab/gitlab.rb

external_url 'https://gitlab.anisa.local'

gitlab-ctl reconfigure
```

Find root password:

```bash
sudo cat /etc/gitlab/initial_root_password
```

Open gitlab on browser: https://gitlab.anisa.local and login with root password and username root.
Don't forget to change root password after login because it's valid for 24 hours.
