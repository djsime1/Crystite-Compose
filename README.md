# Crystite-Compose
A simple docker-compose setup for [Crystite](https://github.com/Nihlus/Crystite)

Assuming you're familiar with `docker` and `docker-compose`, getting started is quite easy.
1. Clone this repository (Optionally, clone [this one](https://github.com/djsime1/Crystite) alongside it to build the Dockerfile yourself).
2. Copy `.env.sample` to `.env`, Enter Steam account credentials into the new file (Must have Steam Guard disabled, preferably create a new account dedicated for automation).
3. Copy `Config/Config.json.sample` to `Config/Config.json` and set it up to your liking (Do not change the Data, Cache, or Logs folder!)
4. Run `docker-compose up -d` to start the server. You can control Crystite through its [HTTP API](https://github.com/Nihlus/Crystite/blob/main/docs/index.md), or by running the `docker-compose exec crystite /usr/lib/crystitectl/crystitectl` command.