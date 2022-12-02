FROM dependabot/dependabot-core:0.209.0

ARG CODE_DIR=/home/dependabot/dependabot-script
ARG BUNDLE_USER_HOME=/home/bundle
RUN mkdir -p ${CODE_DIR}
RUN mkdir -p ${BUNDLE_USER_HOME}
COPY Gemfile Gemfile.lock ${CODE_DIR}/
WORKDIR ${CODE_DIR}

RUN bundle config set --local path "vendor" \
  && bundle install --jobs 4 --retry 3

COPY generic-update-script.rb ${CODE_DIR}

CMD ["bundle", "exec", "ruby", "./generic-update-script.rb"]
