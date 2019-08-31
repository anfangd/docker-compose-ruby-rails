# image
FROM ruby:2.5.3

ENV LANG C.UTF-8

RUN apt-get update -qq && \
    apt-get install -y \
      build-essential \
      libpq-dev \
      nodejs \
    && rm -rf /var/lib/apt/lists/*

RUN gem install bundler

# working directory
RUN mkdir /app
ENV APP_ROOT /app
WORKDIR $APP_ROOT

# Add Gemfile
ADD ./src/Gemfile $APP_ROOT/Gemfile
ADD ./src/Gemfile.lock $APP_ROOT/Gemfile.lock

# bundle install
RUN bundle install
ADD ./src/ $APP_ROOT
