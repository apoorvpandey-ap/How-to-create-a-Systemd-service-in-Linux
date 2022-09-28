## video link https://youtu.be/2pxFAQlMCoU
### Create systemd service
You can find running linux service under path **/etc/systemd/system**
`cd /etc/systemd/system`
Create a file named **[servicename.service]** and add the following

```
[Unit]
Description=reposilite service for maven artifact
After=network-online.target

[Service]
User=root
Group=root

WorkingDirectory=/opt/reposilite
ExecStart=/usr/bin/java  -Xmx32M -Dreposilite.port=8082 -jar /opt/reposilite/reposilite-3.0.3-all.jar
Restart=always

[Install]
WantedBy=multi-user.target

```
### After you finish reload the service files to include the new service.
`sudo systemctl daemon-reload`

### Start your new service
`sudo systemctl start [your_new_service].service`

### Check the status of your new service e.g (my new service called unixcop.service)
`sudo systemctl reposilite.service`

### Enable your service on every reboot
`sudo systemctl enable reposilite.service`

### To disable your service on every reboot
`sudo systemctl disable reposilite.service`

###
