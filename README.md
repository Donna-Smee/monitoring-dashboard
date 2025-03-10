# Simple steps/explanation


## Step 1: Clone the GitHub
Clone this github repo (for monitoring)
```
https://github.com/Donna-Smee/monitoring-dashboard
```

## Step 2: Start Docker Desktop
Make sure you have Docker Desktop running

## Step 3: Docker-compose up
After cloning the repo, make sure you're in the folder: monitoring-dashboard
Run this command 
``` 
docker-compose up -d --pull always 
```

(The pull always make sure it always has the newest deployment)

Wait until done (the first time might take a while), but anytime after should be fast.

Note: Grafana sometimes takes a while to start (show up on localhost) but if its 15 min plus, just go to Docker Desktop and restart that container.

## Step 4: Go to the urls

To see the first web app
``` 
http://localhost:3000/ 
```

To see the second web app
``` 
http://localhost:4000/ 
```

To see the Prometheus
``` 
http://localhost:9090/ 
```

To see Grafana
``` 
http://localhost:8080/ 
```

In Prometheus, you can execute some queries. The simple one that just gets all http requests is:
```
http_request_duration_seconds_total
```
You will see all requests. You should see the 200 OK requests for both websites if you visited it.

You can switch to Graphs to get a more visual view.

## Error sending
The Puppeteer is responsible for sending errors. 
It's just the localhost:3000/error, localhost:4000/error for both websites.
It sends random errors and gives random wait times. You should be able to see the number of errors increasing on it's own on prometheus, if not, go to Docker and restart Puppeteer container.

## Grafana
When you close the applications (docker-compose down), it will delete all data previously. (I believe you can find a command to run Grafana so it can you volumes to remember the data).

Connect to Prometheus as a data source, then we can create dashboards, alerts, notifications, etc. 

## Close Docker
```
docker-compose down
```

