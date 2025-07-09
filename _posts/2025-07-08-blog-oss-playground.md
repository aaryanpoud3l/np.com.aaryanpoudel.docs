---
title: "OSS Application Playground"
date: 2025-07-08T23:10:+00:00
categories: ['Blogs']
tags: ["blog"] 
---

#### Twenty
- OSS [Github](https://github.com/twentyhq/twenty), [Site](https://app.twenty.com) , [Self-hostable](https://twenty.com/developers/section/self-hosting)
- Alternative to Salesforce (need to check usecases of salesforce and compare ) #todo
- Installs fine but usability to be accessed as all it seems to have is details, companies. Workflow feature to be accessed #todo

**Installation**
``` sh
bash <(curl -sL https://raw.githubusercontent.com/twentyhq/twenty/main/packages/twenty-docker/scripts/install.sh)
```

App URL: [localhost:3000](https://localhost:3000)

#### Plane.so
- OSS [Github](https://github.com/makeplane/plane), [Live app](https://app.plane.so/) , [Self-hostable](https://developers.plane.so/self-hosting/overview)
- Alternative to Jira, Trello
- Recommended 
- Good free option live as well but hass certain locked paid modules so need to verify those and their limitations #todo 
  
**Installation**
```sh
mkdir plane-selfhost
cd plane-selfhost

curl -fsSL -o setup.sh https://github.com/makeplane/plane/releases/latest/download/setup.sh

chmod +x setup.sh
./setup.sh

# Here, use 1 => Install, 2 => Run Project,  3 => Stop Project Service
```

App URL: [localhost:8080](http://localhost:8080)
