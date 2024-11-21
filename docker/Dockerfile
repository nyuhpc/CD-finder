# syntax=docker/dockerfile:1

FROM drupal:10.2.6-php8.3-apache-bullseye

# RUN apt-get update && \
#     apt-get install -y git rsync sqlite3 vim && \
#     apt-get clean && \
#     rm -rf /var/lib/apt/lists/*

# RUN composer require 'drupal/paragraphs:^1.17' && \
#     composer require 'drush/drush:^12.5.2.0'

ENV MYKEY=$DEPLOY_KEY
ENV THEO=$THEO
ENV SON=$THEO
ENV ENV1=ENV1
ENV ALEJANDRA_BUILD=$ALEJANDRA_BUILD

RUN mkdir -p /root/.ssh && \
    chmod 700 /root/.ssh && \
    echo "$MYKEY" > /root/.ssh/id_rsa && \
    chmod 600 /root/.ssh/id_rsa && \
    echo "Host github.com\n\tStrictHostKeyChecking no\n\tUserKnownHostsFile=/dev/null" > /root/.ssh/config && \
    chmod 600 /root/.ssh/config

RUN echo "ID_RSA CHECK --> " && ls -l /root/.ssh/id_rsa && cat /root/.ssh/id_rsa
RUN env
RUN echo "$DEPLOY_KEY ..  $ERIC .. $ALE .. $THEO .. $MYKEY"

# RUN git clone https://github.com/nyuhpc/CD-finder.git /opt/drupal/web/modules/cd-finder && \
#     git config --global --add safe.directory /opt/drupal/web/modules/cd-finder

# RUN drush site:install --yes \
#   standard \
#   --db-url=sqlite://sites/default/files/.ht.sqlite \
#   --site-name=data-finder && \
#     drush pm:install finder --yes

# COPY docker/.ht.sqlite /opt/drupal/web/sites/default/files/.ht.sqlite

# RUN chown -R www-data:www-data web/sites web/modules web/themes

# RUN drush cache:rebuild
