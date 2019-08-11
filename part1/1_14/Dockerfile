FROM ruby:2.6.0
COPY . .
EXPOSE 3000

ENV RAILS_LOG_TO_STDOUT=true

# editor for rails credentials:edit
ENV EDITOR="vi --wait"

# install node for javascript runtime
RUN apt-get update
RUN apt install -y --allow-unauthenticated nodejs

RUN bundle install

# fix missing master key
RUN rm config/credentials.yml.enc
RUN rails credentials:edit

RUN rails db:migrate RAILS_ENV=production

# couldn't fix missing yarn
RUN rake assets:precompile

ENTRYPOINT rails s -e production