FROM drupal:10.2.6-php8.3-apache-bullseye

RUN apt-get update && \
    apt-get install -y git rsync sqlite3 vim && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN composer require 'drupal/paragraphs:^1.17' && \
    composer require 'drush/drush:^12.5.2.0'

RUN git clone https://github.com/nyuhpc/CD-finder.git /opt/drupal/web/modules/cd-finder

RUN drush site:install --yes \
	standard \
	--db-url=sqlite://sites/default/files/.ht.sqlite \
	--site-name=data-finder && \
    drush pm:install finder --yes

COPY .ht.sqlite /opt/drupal/web/sites/default/files/.ht.sqlite

RUN chown -R www-data:www-data web/sites web/modules web/themes

RUN drush cache:rebuild
