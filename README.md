# MirrorBot Template

Template for running various aria mirrorbots with one common workflow by doing minimal modifications.

## Supported Aria MirrorBots

You can use any of these scripts

- https://github.com/lzzy12/python-aria-mirror-bot
- https://github.com/magneto261290/magneto-python-aria
- https://github.com/SVR666/LoaderX-Bot
- https://github.com/iamLiquidX/MirrorX
- https://github.com/MaxxRider/Maxx-Mirror-Pro
- https://github.com/ghostmirrorlab/python-aria-mirror-bot


## How To Deploy 
To deploy these scripts, you first need to setup the configs, credentials and token.
All these requirements are explained in each of the script's repository.


1. Required  `config.env`, `credentials.json` and `token.pickle`.
2. upload those files to sharing service 
3. I didn't use service accounts, so these three things are all I needed.


### Secrets 
1. Add your own GitHub Credentials as `GitHubMail` and `GitHubName`.
2. Add your GitHub Personal Access Token as `GH_TOKEN` with most of the admin-read-write permissions (but not with delete permission).
3. Add the last two part of mirrorbot repo address as `BotRepoSlug`. For example: "lzzy12/python-aria-mirror-bot" when you want to use the original repo.
4. Add direct URL for `config.env`, `credentials.json` and `token.pickle` as `ConfigSlug`, `CredsSlug` and `PickleSlug`. Remember, these three values are full URL.
5. Add your DockerHub Credentials as `DOCKER_USERNAME` and `DOCKERHUB_TOKEN` (API Token)
6. Run Ubuntu or Mac workflow 


### Some Information
## Ubuntu 
1. The MirrorBot script directory will be `/home/runner/botSource`
2. The workflow will be triggered only on workflow_dispatch.
3. When the bot starts, it will run for exactly 340 minutes, then automatically trigger another dispatch.
4. The workflow will cleanup the workspace in background, so you will have to wait for ### 6 to 12 minutes on bot start to get full space.#
5. So you will get an infinite loop of run with maximum 2-3 minutes of bot downtime.
## MacOS 
1. The MirrorBot script directory will be /home/runner/botSource
2. The workflow will be triggered only on workflow_dispatch.
3. This workflow will run in macos-10.15 runner hosted in GitHub's own VM, and it is a shared VM platform. So, processes sometimes may freeze as it shares only 3 single-threaded    vCPU Cores which is pretty bad for multi-tasking. That's why I suggest you keep MAX_CONCURRENT_DOWNLOADS down to 2 or 3 in aria.sh inside scripts.
4. The workflow will cleanup the workspace which takes 25-30 minutes, according to server pressure. After that, when the bot starts, it will run for exactly 320 minutes. To save    this huge downtime, a second job is used which will automatically trigger another dispatch after 320 minutes from starting point.
5. So you will get an infinite loop of run with maximum 5-10 minutes of bot downtime.

## Disclaimer

This repository is for personal use only.
Do not abuse GitHub Actions by running multiple instances of these bots in a crowded group which exhausts GitHub's Machine Resources.
If you want GitHub to support us by giving out fairly amount of resources to test out our applications, don't get into their radar, keep low.
