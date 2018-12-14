# ee4-tools

A mostly working collection of scripts for managing an [EasyEngine](https://easyengine.io) WordPress hosting server. This is not an official project from EasyEngine and may be renamed in the future. 

The backup script creates a full compressed copy of each site to upload to S3. The 'htdocs' folder and MariaDB/MySQL database are uploaded in separate well organized folders and files. This is opposite of other projects that attempt to create incremental backups. Glacier storage is inexpensive. Full site copies along with S3 lifecycle rules offer the storage and retention this project looks to fulfill. Place the ee4-backup-sites v4 script (or backup_sites_s3 & backup_mysql_s3 v3 scripts) in /etc/cron.daily/ for automated backups after your testing.

### EasyEngine v4 Tools

- Server setup script (Ubuntu 18.04)
- Restore from v3 backup (v4 Coming)
- Backup (Compress, Encrypt, and copy to S3)

### EasyEngine v3 Tools

- Backup all EasyEngine sites to S3
- Backup all MySQL databases to S3 (EasyEngine not required)
- Restore a single WordPress site from S3
- Create a full server restore list with EasyEngine parapmeters (ex. --wp)
- CloudFlare UFW IP address whitelist script
- Create an uncolorized EasyEngine site list
- Fix the ownership (chown) of files based on the parent folder 
- LetsEncrypt Delete, Renew and Status scripts
- Check the WordPress version on all sites
- Update the WordPress version on all sites suitable for cron
- [WordOps](https://wordops.org/) the v3 EasyEngine fork project may be supported in the future

## Getting Started

Please use caution, some bucket names/folders are still hard coded. 

No support available. Use at your own risk.

The ee4-restore-site script only restores from v3 backups. This is currently being used for v3 to v4 migration. A v4 restore script will be added soon.

### Prerequisites

Tested with Ubuntu 18.04 on Amazon LightSail & Amazon S3 for backup storage.

Use AWS S3 cli. S3cmd is no longer supported. References to s3cmd will be removed in future updates.

### Installing

Edit the .backup_sites_mysql_s3.conf & .ee4-backup-settings.conf files first. Then edit and review each script before using. Some scripts still have hard coded folders at this time. 

Then run ee4-server-setup on your fresh Ubuntu 18.04 VPS.

Setup a GPG key. 

Edit and test the ee4-backup-sites script. Then place in your /etc/cron.daily/ folder. 

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
