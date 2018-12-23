# nginx Open Configs

## OS Optimization

```bash
# System Level
echo 'fs.file-max = 65535' | sudo tee -a /etc/sysctl.conf
sysctl -p

# User Level
sudo tee -a /etc/security/limits.conf << EOF
*               hard    nofile          65535
*               soft    nofile          65535
root            hard    nofile          65535
root            soft    nofile          65535
EOF

# Systemd Services
sudo sed -i '/DefaultLimitNOFILE/c DefaultLimitNOFILE=65535' /etc/systemd/*.conf
```

## References

- [Nginx Server Configs](https://github.com/h5bp/server-configs-nginx) - *H5BP*
- [nginxconfig.io](https://nginxconfig.io/) - *nginx configuration generator*
- [nginx, Nginx, NGiИX, or NGINX?!](https://news.netcraft.com/archives/2018/02/20/nginx-nginx-nginx-or-nginx.html) - *Netcraft*
- [Pitfalls and Common Mistakes](https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/) - *NGINX*
- [Increase "Open Files Limit"](https://easyengine.io/tutorials/linux/increase-open-files-limit/) - *EasyEngine*
- [Performance Tuning - Tips & Tricks](https://www.nginx.com/blog/performance-tuning-tips-tricks/) - *Alan Murphy of NGINX, Inc.*
