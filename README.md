# Deploying weblink

There are easy ways to run your own instance of weblink server.

1. Deploying to Render

   This option is completely free.

   Deployment configuration is defined in `render.yaml`.

   [Deploy to Render](https://render.com/deploy?repo=https://github.com/soylent/deploy-weblink/tree/main)

1. Deploying to Koyeb

   This option is completely free.

   Enter the URL of this repo if it is not populated.

   [Deploy to Koyeb](https://app.koyeb.com/deploy?name=weblink&repository=soylent%2Fdeploy-weblink&branch=main&instance_type=free&ports=8080%3Bhttp%3B%2F)

1. Deploying to Heroku

   You can get one year of free service if you are a student.

   Deployment configuration is defined in `app.json`.

   [Deploy to Heroku](https://heroku.com/deploy?template=https://github.com/soylent/deploy-weblink/tree/main)

To use your new server, add the `server` param to the weblink URL that you
open on your phone. Example:

```
http://172.20.10.2:8080/?server=wss://<your-weblink>
```

## Troubleshooting

1. Check that your weblink server is up:

   ```
   $ curl -i https://<your-weblink>/healthcheck
   ...
   OK
   ```

1. Manually send a proxy request through your weblink server.

   You will need `wscat2` for this:

   ```
   $ npm install -g wscat2
   ```

   Connect and send the request:

   ```
   $ wscat -b wss://<your-weblink>/ws/rem/relay
   > CONNECT example.org:80 HTTP/1.1

   < HTTP/1.1 200 Connection established

   > GET / HTTP/1.1
   > Host: example.org

   < HTTP/1.1 200 OK
   < ...
   ```

1. Check the logs:

- Local weblink server logs
- Remote weblink server logs
- Browser console
