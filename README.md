# jira
default port: 8080

## How to run with docker-compose
```
    docker-compose up -d
```

- default db(mysql5.7) configure:

```bash
    driver=mysql5.7+
    host=mysql-jira
    port=3306
    db=jira
    user=jira
    passwd=123123
```

## How to run with docker

- start jira

```
    docker run -p 8080:8080 -v jira_home_data:/var/jira --name jira-srv -e TZ='Asia/Shanghai' zouchengli/jira
```

## How to hack jira

```
docker exec jira-srv java -jar /var/agent/atlassian-agent.jar \
    -p jira \
    -m chengli.zou@gmail.com \
    -n chengli.zou@gmail.com \
    -o http://localhost:8080 \
    -s copy-you-server-id
```

## How to hack jira plugin

- .eg I want to use BigGantt plugin
1. Install BigGantt from jira marketplace.
2. Find `App Key` of BigGantt is : `eu.softwareplant.biggantt`
3. Execute :

```
docker exec jira-srv java -jar /var/agent/atlassian-agent.jar \
    -p eu.softwareplant.biggantt \
    -m chengli.zou@gmail.com \
    -n chengli.zou@gmail.com \
    -o http://localhost:8080 \
    -s copy-you-server-id
```

4. Paste your license 
