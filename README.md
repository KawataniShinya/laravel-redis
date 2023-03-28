# laravel-auth

## composition
- Nginx
- Laravel
- Breeze
- MySQL
- Docker

## install and Usage
1. コンテナ起動
```shell
docker-compose build
docker-compose up -d
```

2. コンテナ確認
```shell
docker ps
docker-compose ps
```

3. 初期設定(アプリケーション環境)
```shell
docker-compose exec app bash
composer install
cp -p /var/www/app/.env.auth /var/www/app/.env
php artisan key:generate
npm install
npm run build
exit
```

4. 初期設定(データベース設定)
```shell
docker-compose exec db bash
mysql -u root -proot -e "CREATE USER 'laravelUser' IDENTIFIED BY 'password00'"
mysql -u root -proot -e "GRANT all ON *.* TO 'laravelUser'"
mysql -u root -proot -e "FLUSH PRIVILEGES"
mysql -u root -proot -e "CREATE DATABASE laravel_db"
exit
```
```shell
docker-compose exec app bash
php artisan migrate:fresh --seed
exit
```

5. ログイン
```
http://localhost:8080/
```
```
Email : test@test.com
Password : password123
```