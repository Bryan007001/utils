unzip docker-rpm.zip
cd docker-rpm
createrepo .

#如果没有安装createrepo，执行下面这句
#sudo yum localinstall -y --nogpgcheck docker-rpm/createrepo*.rpm

#将如下baseurl改为实际的目录
cat > /etc/yum.repos.d/local.repo <<EOF
[local]
name=Local Repository
baseurl=file:///root/app/utils/docker/docker-rpm
enabled=1
gpgcheck=0
EOF

cd ..
cp -p docker-compose /usr/bin/
chmod 755 /usr/bin/docker-compose
