# nginx Open Configs

## OS Optimization

```bash
# System
echo 'fs.file-max = 65535' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# User
sudo tee -a /etc/security/limits.conf << EOF
*               hard    nofile          65535
*               soft    nofile          65535
root            hard    nofile          65535
root            soft    nofile          65535
EOF

# Systemd
sudo sed -i '/DefaultLimitNOFILE/c DefaultLimitNOFILE=65535' /etc/systemd/*.conf
sudo systemctl daemon-reexec
```

## References

- [nginx Server Configs](https://github.com/h5bp/server-configs-nginx) - *H5BP*
- [nginxconfig.io](https://nginxconfig.io/) - *nginx Configuration Generator*
- [nginx, Nginx, NGiИX, or NGINX?!](https://news.netcraft.com/archives/2018/02/20/nginx-nginx-nginx-or-nginx.html) - *Netcraft*
- [Pitfalls and Common Mistakes](https://www.nginx.com/resources/wiki/start/topics/tutorials/config_pitfalls/) - *NGINX*
- [Increase "Open Files Limit"](https://easyengine.io/tutorials/linux/increase-open-files-limit/) - *EasyEngine*
- [Performance Tuning](https://www.nginx.com/blog/performance-tuning-tips-tricks/) - *Alan Murphy of NGINX*
- [Some Simple Things for TUNING Your UBUNTU Server](https://medium.com/@yenthanh/some-simple-things-for-tuning-your-ubuntu-server-3db99383eadb)
