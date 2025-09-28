# This repo is to demonstrate an authentication issue with Symfonium (subsonic api) and navidrome

## Info

Evenerything is set up and ready to go.

The following parameters are set:

Proxy:

* username: demo
* password: demo

Navidrome

* username: admin
* password: admin

Following tools are used:

* docker compose
* smartphone with Symfonium app in same wifi network

## Steps to reproduce


1. Start the docker compose setup with `docker compose up`
2. Open the `man in the middle` proxy on http://localhost:8081, the exact url with the password is shown in the terminal
3. Open the Symfonium app on your smartphone
4. Add a new server with the following parameters:
   * Provider: Subsonic
   * Server URL: http://<your computer's local ip> or <name>
   * Username: admin
   * Password: admin
   * Extra authentication > Proxy Authentication
   * Username: demo
   * Password: demo
5. Select the "example"-mp3 in Symfonium
6. Observe the request in the proxy (should throw a 400), see the 400 error in the docker compose log
