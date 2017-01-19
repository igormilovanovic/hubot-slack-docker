# Dockerized and Slack-integrated Hubot



[![Docker Hub](https://img.shields.io/badge/docker-ready-blue.svg)](https://registry.hub.docker.com/u/tnkng/armhf-hubot-slack/)
[![](https://images.microbadger.com/badges/image/tnkng/armhf-hubot-slack.svg)](https://microbadger.com/images/tnkng/armhf-hubot-slack "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/tnkng/armhf-hubot-slack.svg)](https://microbadger.com/images/tnkng/armhf-hubot-slack "Get your own version badge on microbadger.com")


This is Docker image for running Hubot for Slack on RaspberryPi3 (ARMv7) and compatible platforms. 


> This work is based on already existing work of https://github.com/chihchun/hubot-slack-docker providing initial Dockerfile and https://hub.docker.com/u/forumi0721alpinearmhf providing me with base Alpine Linux image for ARM HF architecture. Thank you folks.

Setup a hubot from https://slack.com/services/new/hubot and assign the API token to the following command

```
docker pull tnkng/armhf-hubot-slack
docker run -e HUBOT_SLACK_TOKEN=xoxb-1234567890-XXXXXXXXXXXXXXXXXXXXXXXX -d tnkng/armhf-hubot-slack --name hubot-slack
```

# Hubot Scripts
* hubot-diagnostics
* hubot-help
* hubot-heroku-keepalive
* hubot-google-images
* hubot-google-translate
* hubot-pugme
* hubot-maps
* hubot-redis-brain
* hubot-rules
* hubot-shipit
* hubot-moretext
* hubot-standup-alarm
* hubot-victory

## Reference
* Bot Users | Slack https://api.slack.com/bot-users
