$ git clone http://git.consorcionova.com:7990/scm/war/dmd_raloy.git dmd  
$ composer install/update
$ php artisan key:generate
$ php artisan migrate --seed
$ php artisan storage:link
$ php artisan optimize:clear
$ sudo chmod -R 775 vendor
$ sudo chmod -R 775 public
$ sudo chmod -R 775 storage
$ sudo chown -R www-data:www-data dmd
