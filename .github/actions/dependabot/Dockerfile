FROM dependabot/dependabot-core:0.209.0

ARG CODE_DIR=/home/dependabot/dependabot-script
RUN mkdir -p ${CODE_DIR}
COPY Gemfile Gemfile.lock ${CODE_DIR}/
WORKDIR ${CODE_DIR}

RUN bundle config set --local path "vendor" \
  && bundle install --jobs 4 --retry 3

COPY generic-update-script.rb ${CODE_DIR}

CMD ["bundle", "exec", "ruby", "./generic-update-script.rb"]
