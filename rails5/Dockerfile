FROM 4armed/ruby:2.3.4
MAINTAINER Marc Wickenden <marc@4armed.com>

RUN apt-get update && apt-get install -y build-essential zip libsqlite3-dev && rm -rf /var/lib/apt/lists/*

RUN echo 'gem: --no-rdoc --no-ri' >> $HOME/.gemrc && \
    gem install bundler

ENV RAILS_ENV production
ENV RACK_ENV production

RUN git clone https://github.com/4ARMED/inject-some-sql.git /app

WORKDIR /app/rails5
RUN bundle install && rake db:setup db:seed

EXPOSE 3000

CMD rails s
