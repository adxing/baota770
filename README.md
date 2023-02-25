# baota770
```
Centos安装脚本：
yum install -y wget && wget -O baota770.sh https://ghproxy.com/https://raw.githubusercontent.com/adxing/baota770/main/baota770.sh && sh baota770.sh

Ubuntu/Deepin安装脚本：
wget -O baota770.sh https://ghproxy.com/https://raw.githubusercontent.com/adxing/baota770/main/baota770.sh && bash baota770.sh


升级(降级)到7.7版本命令：
wget https://ghproxy.com/https://github.com/adxing/baota770/raw/main/LinuxPanel-7.7.0.zip
unzip LinuxPanel-7.7.0.zip
cd panel
bash update.sh
cd .. && rm -f LinuxPanel-7.7.0.zip && rm -rf panel

优化命令
echo "{\"uid\":1000,\"username\":\"admin\",\"serverid\":1}" > /www/server/panel/data/userInfo.json
sed -i "/htaccess = self.sitePath+'\/.htaccess'/, /public.ExecShell('chown -R www:www ' + htaccess)/d" /www/server/panel/class/panelSite.py
sed -i "/index = self.sitePath+'\/index.html'/, /public.ExecShell('chown -R www:www ' + index)/d" /www/server/panel/class/panelSite.py
sed -i "/doc404 = self.sitePath+'\/404.html'/, /public.ExecShell('chown -R www:www ' + doc404)/d" /www/server/panel/class/panelSite.py
sed -i "s/return render_template('autherr.html')/return abort(404)/" /www/server/panel/BTPanel/__init__.py
sed -i "/p = threading.Thread(target=check_files_panel)/, /p.start()/d" /www/server/panel/task.py
sed -i "/p = threading.Thread(target=check_panel_msg)/, /p.start()/d" /www/server/panel/task.py
echo "True" > /www/server/panel/data/not_recommend.pl
echo "True" > /www/server/panel/data/not_workorder.pl
sed -i "s/root \/www\/server\/nginx\/html/return 400/" /www/server/panel/vhost/nginx/0.default.conf
