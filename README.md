# backend setup

composer install

php artisan migrate
php artisan passport:keys
php artisan passport:client --personal
php artisan db:seed
php artisan serve to start project
# frontend setup 
npm install // i am runing npm 10.2.3
npm run dev  // to start project


sudo chown -R www-data:www-data /var/www/artist/backend
sudo chmod -R 775 /var/www/artist/backend/storage
sudo chmod -R 775 /var/www/artist/backend/bootstrap/cache

Personal access client created successfully.
Client ID: 1
Client secret: GqObOnI9Ise4F5SgZ9LrGEI8VN0NRk0041eHr5vr
