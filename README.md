# monk-langfuse

This repository contains Monk.io template to deploy langfuse(https://github.com/langfuse/langfuse).


## Prerequisites

- Install Monk
- Register and Login Monk
- Add Cloud Provider


## Clone Repository

```bash
git clone https://github.com/monk-io/monk-langfuse
```

## Make public

```
    langfuse:
      container: langfuse
      port: <- `${port}`
      protocol: tcp
      host-port: <- `${port}`
      # publish: true  <-- uncomment here or setup frontend proxy
```

## Load Template

```bash
cd monk-langfuse
monk load MANIFEST
```


## Deploy

```bash
 ./monk run langchain/stack                
? Select tag to run [local/langchain/stack] on: prod
✔ Starting the run job: local/langchain/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% ghcr.io/langfuse/langfuse:latest sergtest8
✔ [================================================] 100% postgres:latest sergtest8
✔ Checking/pulling images DONE
✔ Starting containers DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/database connections graph updating DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/database connections graph has been updated DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/database services initialization DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/database services have been initialized DONE
✔ Host ports have been added to container 7449b0129bea488c9f6ec8b2a61b5ab3-chain-database-postgres DONE
✔ New container 7449b0129bea488c9f6ec8b2a61b5ab3-chain-database-postgres created DONE
✔ Container 7449b0129bea488c9f6ec8b2a61b5ab3-chain-database-postgres network has been configured DONE
✔ Container 7449b0129bea488c9f6ec8b2a61b5ab3-chain-database-postgres has been started DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/server connections graph updating DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/server connections graph has been updated DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/server services initialization DONE
✔ Runnable templates/local/langchain/stack/runnables/templates/local/langchain/server services have been initialized DONE
✔ Host ports have been added to container ca8bf2d94fc5ae16695f2a847b49df0b-ngchain-server-langfuse DONE
✔ New container ca8bf2d94fc5ae16695f2a847b49df0b-ngchain-server-langfuse created DONE
✔ Container ca8bf2d94fc5ae16695f2a847b49df0b-ngchain-server-langfuse network has been configured DONE
✔ Container ca8bf2d94fc5ae16695f2a847b49df0b-ngchain-server-langfuse has been started DONE
✔ Started local/langchain/stack
🔩 templates/local/langchain/stack
 └─🧊 Peer sergtest8
    ├─🔩 templates/local/langchain/database 
    │  └─📦 7449b0129bea488c9f6ec8b2a61b5ab3-chain-database-postgres running
    │     ├─🧩 postgres:latest                                                
    │     └─💾 /var/lib/monkd/volumes/langchain/postgresql -> /var/lib/postgresql/data
    └─🔩 templates/local/langchain/server   
       └─📦 ca8bf2d94fc5ae16695f2a847b49df0b-ngchain-server-langfuse running
          ├─🧩 ghcr.io/langfuse/langfuse:latest
          └─🔌 open (public) 34.83.241.24:3000 -> 3000

💡 You can inspect and manage your above stack with these commands:
        monk logs (-f) local/langchain/stack - Inspect logs
        monk shell     local/langchain/stack - Connect to the container's shell
        monk do        local/langchain/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!
```


## Check health
```bash
curl http://34.83.241.24:3000/api/public/health
```


## Variables

You could check list of variables here: https://langfuse.com/docs/deployment/self-host#configuring-environment-variables