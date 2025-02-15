
<div align="center">
  <img src="https://raw.githubusercontent.com/Sopamo/via/main/assets/logo.png" width="269">

  Easily start & stop your local dev environments from your cli
</div>
<hr>
<br /><br />

<div align="center">

[![Watch the via demo video](./assets/thumbnail.png)](https://youtu.be/lD-CBiXZfP4)
[Watch the via demo video](https://youtu.be/lD-CBiXZfP4)
</div>
<br />

## Project setup
First, run

```bash
mkdir ~/.via
cp exampleConfig.json ~/.via/projects/my-project.json
```
Then edit my-project.json to configure your first workspace. You can create as many project.json files as you need. 

Download the [latest version](https://github.com/Sopamo/via/releases) of via and move it to `/usr/local/bin/v`.

You can then run `v my-project start` to start your project. Of course you can rename the my-project.json file to match your project's name.

## Project configuration

### Minimal configuration
```json
{
  "services": {
    "app": {
        "path": "/Users/username/project/app",
        "actions": {
            "start": "docker-compose up -d",
            "stop": "docker-compose stop"
        }
    }
  }
}
```
You always have to specify the start and stop actions.

When running the start action, all other projects will be stopped automatically.

### Adding custom actions
```json
{
  "services": {
    "app": {
        ...
        "actions": {
            ...
            "bash": "docker-compose exec app bash"
        }
    }
  }
}
```
You can run individual actions like this: 

```bash
v my-project app bash
```

<br />
<br />
<br />

## Via development setup
First, follow the project setup instructions.
Then, to run the project locally, install [deno](https://deno.land).

To run the code directly, run:
```bash
deno run --allow-read --allow-run --allow-env ./src/via.ts [project] [service] [action]
```

To build the binary, run:
```bash
deno compile --allow-read --allow-run --allow-env ./src/via.ts
```