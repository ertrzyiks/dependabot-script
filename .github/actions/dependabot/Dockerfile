FROM dependabot/dependabot-core:0.209.0

USER root

ARG CODE_DIR=/home/dependabot/dependabot-script
ARG BUNDLE_USER_HOME=/home/bundle
RUN mkdir -p /home
RUN chown dependabot:dependabot /home
RUN mkdir -p ${CODE_DIR}
RUN mkdir -p ${BUNDLE_USER_HOME}
RUN chown dependabot:dependabot ${BUNDLE_USER_HOME}

USER dependabot

COPY --chown=dependabot:dependabot Gemfile Gemfile.lock ${CODE_DIR}/

WORKDIR ${CODE_DIR}

RUN bundle config set --local path "vendor" \
  && bundle install --jobs 4 --retry 3

COPY --chown=dependabot:dependabot generic-update-script.rb ${CODE_DIR}

CMD ["bundle", "exec", "ruby", "./generic-update-script.rb"]
