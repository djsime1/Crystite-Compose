# Crystite-Compose
A simple docker-compose setup for [Crystite](https://github.com/Nihlus/Crystite)

## Quick-start
Assuming you're familiar with `docker` and `docker-compose`, getting started is quite easy. This repository also works with `podman` and `podman-compose`, if that's your jam.

1. Clone this repository or download the files from Github.
2. Copy `.env.sample` to `.env`, Enter Steam account credentials into the new file (Must have Steam Guard disabled, preferably create a new account just for dedicated servers).
3. Copy `Config/Config.json.sample` to `Config/Config.json` and set it up to your liking (Do not change the Data, Cache, or Logs folder!)
4. Run `docker-compose up -d` to start the server. You can control Crystite through its [HTTP API](https://github.com/Nihlus/Crystite/blob/main/docs/index.md), or by running the `docker-compose exec crystite /usr/lib/crystitectl/crystitectl` command.

Any time you change the server's configuration (Config.json, appsettings.json, .env, etc.), you will need to recreate the container using `docker-compose up -d --force-recreate` for it to take effect.

## Updating the headless
**These instructions will change once Docker support is merged into the upstream Crystite repo**

The container image will need to be updated to match the game version. Try pulling a newer version by running `docker-compose up -d --pull`.
Otherwise, you can build the new image yourself by cloning [this repository](https://github.com/djsime1/Crystite) alongside this folder (i.e, Crystite and Crystite-Compose reside next to each other in the same parent folder), then uncomment the "build" entry in docker-compose.yml and run `docker-compose up -d --build`.

## Troubleshooting/FAQ

### How do I view the live log output?
Run this command: `docker-compose logs -f --tail 100`

### I keep getting errors (after updating) or the container keeps crashing
If you're experiencing errors/crashing after an update, you can try deleting the game and assets volume.
To do this, run `docker-compose down -v && docker compose up -d`. **This will delete any locally stored worlds!**

## Modloader support
This container can automatically set up and configure supported modloaders, follow the instructions below to set one up.

### ResoniteModLoader (RML):
1. Create folders named rml_mods, rml_libs, and rml_config in this folder.
2. Place the mods you want to install in the rml_mods folder. Don't put 0Harmony.dll in rml_libs, it will be automatically downloaded.
3. Set `MODLOADER=ResoniteModLoader` in .env
4. Uncomment lines 19-21 in docker-compose.yml
5. Run `docker-compose up -d --force-recreate` to apply the changes and install the mods.

### MonkeyLoader:
MonkeyLoader is not supported at this time. If your name is Banane9, please reach out and help me because I couldn't get it working ;-;