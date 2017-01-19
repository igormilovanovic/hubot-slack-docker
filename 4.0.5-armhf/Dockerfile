FROM forumi0721alpinearmhf/alpine-armhf-nodejs

MAINTAINER Igor Milovanovic "https://twitter.com/f13o"
MAINTAINER Rex Tsai "https://about.me/chihchun"

# Software versions
ENV HUBOT_SLACK_VERSION=4.0.5
ENV HUBOT_VERSION=0.4.0
ENV YO_VERSION=1.8.5
ENV COFFEE_SCRIPT=1.10.0

# Usual update / upgrade
RUN apk update
RUN apk add jq

# Install coffee-script, hubot
RUN npm install -g yo@${YO_VERSION} \
        coffee-script@${COFFEE_SCRIPT} \
        generator-hubot@${HUBOT_VERSION}

# Working enviroment
RUN mkdir -p /opt/bot
ENV BOTDIR /opt/bot
RUN install -o nobody -d ${BOTDIR}

WORKDIR ${BOTDIR}

# Install Hubot
USER nobody
ENV HOME ${BOTDIR}
RUN yo hubot --name="Hubot" --defaults

# Install slack adapter
RUN npm install hubot-slack@${HUBOT_SLACK_VERSION} --save

# Install moretext
RUN npm install moretext@1.0.0 --save
ADD scripts/moretext.coffee ${BOTDIR}/scripts/moretext.coffee

# Insall standup-alarm
RUN npm install hubot-standup-alarm@0.1.0 --save \
 && (cat external-scripts.json && echo '["hubot-standup-alarm"]') | jq -s add > external-scripts.json.new \
 && mv external-scripts.json.new external-scripts.json

# Install hubot-victory
RUN npm install hubot-victory@1.5.3 \
 && (cat external-scripts.json && echo '["hubot-victory"]') | jq -s add > external-scripts.json.new \
 && mv external-scripts.json.new external-scripts.json

# Install hubot-ip
RUN npm install hubot-ip@0.0.0 --save \
 && (cat external-scripts.json && echo '["hubot-ip"]') | jq -s add > external-scripts.json.new \
 && mv external-scripts.json.new external-scripts.json

# Install sentimental (required redis-server)
# RUN npm install hubot-sentimental@1.0.8 --save \
#  && (cat external-scripts.json && echo '["hubot-sentimental"]') | jq -s add > external-scripts.json.new \
# && mv external-scripts.json.new external-scripts.json

# Entrypoint
CMD ["bin/hubot --adapter slack"]
