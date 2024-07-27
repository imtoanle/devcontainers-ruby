# [Choice] Ruby version (use -bullseye variants on local arm64/Apple Silicon): 3, 3.3, 3.2, 3.1, 3-bookworm, 3.3-bookworm, 3.2-bookworm, 3.1-bookworm, 3-bullseye, 3.3-bullseye, 3.2-bullseye, 3.1-bullseye, 3-buster, 3.2-buster 3.1-buster
ARG VARIANT=3.2-bookworm
FROM ruby:${VARIANT}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    # Remove imagemagick due to https://security-tracker.debian.org/tracker/CVE-2019-10131
    && apt-get purge -y imagemagick imagemagick-6-common 

RUN apt-get update && apt-get install -y lsb-release
# Install psql 16
RUN echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list
RUN curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor -o /etc/apt/trusted.gpg.d/postgresql.gpg
RUN apt-get update && apt-get install -y postgresql-client-16 tmux git

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment this line to install additional gems.
# RUN gem install <your-gem-names-here>

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1



