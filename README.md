## 常见配置
~~~
###################################################
# 添加外部请求的域名(如果不支持https, 可以改成http)
external_url 'https://gitlab.example.com'
# 修改gitlab对应的时区 
gitlab_rails['time_zone'] = 'PRC'

# 开启邮件支持 
gitlab_rails['gitlab_email_enabled'] = true
gitlab_rails['gitlab_email_from'] = 'gitlab@example.com'
gitlab_rails['gitlab_email_display_name'] = 'GitLab'

# 配置邮件参数
gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.163.com"
gitlab_rails['smtp_port'] = 25
gitlab_rails['smtp_user_name'] = "gitlab@example.com"
gitlab_rails['smtp_password'] = "xxxxxx"
gitlab_rails['smtp_domain'] = "domian.com"
gitlab_rails['smtp_authentication'] = "login"
gitlab_rails['smtp_enable_starttls_auto'] = true
gitlab_rails['smtp_tls'] = false        
###################################################

#SSL密钥相关配置#
nginx['redirect_http_to_https'] = true
nginx['ssl_certificate'] = "/data/gitlab/ssl/gitlab.example.com.crt"
nginx['ssl_certificate_key'] = "/data/gitlab/ssl/gitlab.example.com.key"
~~~

## 修改仓库地址

~~~
进入容器
docker exec -it gitlab-ce bash
修改配置文件
vim /opt/gitlab/embedded/service/gitlab-rails/config/gitlab.yml

gitlab:
  host: 0.0.0.0
  port: 8080
  https: false

重启gitlab
gitlab-ctl restart
~~~



