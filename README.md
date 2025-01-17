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
