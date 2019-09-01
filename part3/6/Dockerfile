FROM ruby:2.6.0-alpine as build-stage
COPY rails-example-project .

ENV RAILS_LOG_TO_STDOUT=true

# editor for rails credentials:edit
ENV EDITOR="vi --wait"

# install node for javascript runtime and the rest because using alpine
RUN apk add --update --no-cache nodejs build-base sqlite-dev tzdata \
    # fixed bundle warning after using alpine
    && bundle lock --add-platform x86-mingw32 x86-mswin32 x64-mingw32 java \
    && bundle install --path=vendor/bundle \
    # fix missing master key
    && rm config/credentials.yml.enc \
    && rails credentials:edit \
    && rails db:migrate RAILS_ENV=production \
    # couldn't fix missing yarn
    && rake assets:precompile \
    # remove files
    && rm -rf node_modules tmp/cache app/assets vendor/assets spec \
    && rm -rf vendor/bundle/ruby/2.6.0/cache/*.gem \
    && find vendor/bundle/ruby/2.6.0/gems/ -name "*.c" -delete \
    && find vendor/bundle/ruby/2.6.0/gems/ -name "*.o" -delete

######################

FROM ruby:2.6.0-alpine
EXPOSE 3000

RUN adduser -D app
USER app

COPY --from=build-stage . .
ENTRYPOINT rails s -e production