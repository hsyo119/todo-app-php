FROM php:8.2-apache

# DocumentRoot を public に変更
RUN sed -i 's!/var/www/html!/var/www/html/public!g' /etc/apache2/sites-available/000-default.conf

# AllowOverride All を追加（.htaccess 有効化）
RUN echo '<Directory /var/www/html/public>\n\
    AllowOverride All\n\
</Directory>' >> /etc/apache2/apache2.conf

# mod_rewrite を有効化
RUN a2enmod rewrite

# ソースコードを配置
COPY . /var/www/html/

# PDO MySQL ドライバを追加（←これがないと "could not find driver" エラーになる）
RUN docker-php-ext-install pdo pdo_mysql