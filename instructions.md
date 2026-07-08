# Instructions to Myself for Setting this up
Really, this is just where I'm documenting everything I do. Plus it will help me practice markdown

## Netbox Automation
The how to get Netbox to kick off this automation
### Basic Outline
1. Spin up a Netbox instance
2. Create Netbox event rule
3. Have it post to docker container

## Custom Python Script
The how to receive and process the stuff from Netbox
### Basic Outline
1. Create docker container ```docker run -it --name automations debian:latest ```
2. Build the proper python script and webhook ingest point
3. Eventually package it as a custom docker container for replication
4. Publish!

## Termix Integration
The how to add the python script output to Termix (and potentially other SSH services)
1. Spin up a Termix instance
2. Find the API endpoint for posting new Termix targets
3. Point your python script to it

## Future Enterprise Level Considerations
This project is just for personal use. If ever needed in an enterprise environment, the following would be useful:
1. Retry Queue - if Termix or other SSH service is unreachable, fail gracefully and potentially log for retry once Termix is reachable again
2. Netbox to Monitoring - when Netbox updates Termix, the python script could easily kick off some sort of automation to update Prometheus, Checkmk, or other monitoring service. Add host to monitoring via automation
3. Slack or MS Teams notification - errors or successes could send a message into Slack (super easy) or Teams (possible, but Teams is annoying. Would need to use custom Teams App integration). Could just do a "if SLACK_WEBHOOK exists in .env, then send errors into there. Use a .env.template file.
4. Robust Error Handling - for enterprise grade systems, JSON logging of errors is great because then its easily ingested by other systems. Create a method of defining where logs are stored and how. This may not be that enterprise... I may just build that as part of this.
5. Termix has HashiCorp Vault SSH Auth support, Tailscale/Wireguard support, and other stuff. Maybe use some of this here? Automate creation and credential deployment?
6. Some other super cool stuff?? To be continued...