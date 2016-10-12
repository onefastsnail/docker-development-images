# Docker development images 

This repo simply contains the Dockerfiles to build the images to use during development. For now the commands reference my public found on Dockerhub.

### Node related commands

Run these commands inside the app folder.

* docker run -it --rm -v $(pwd):/data onefastsnail/node-bower-gulp COMMAND
* docker run -it --rm -v $(pwd):/data onefastsnail/node-bower-gulp bower search bootstrap --allow-root
* docker run -it --rm -v $(pwd):/data onefastsnail/node-bower-gulp npm install
* docker run -it --rm -v $(pwd):/data onefastsnail/node-bower-gulp gulp

### Against a dev container

Run these inside the app folder. This container contains many dev tools such as flightplan, node, wpcli, etc.

* docker run --rm -it -v $SSH_AUTH_SOCK:/tmp/agent.sock -e SSH_AUTH_SOCK=/tmp/agent.sock -v $(pwd):/data onefastsnail/development COMMAND
* docker run --rm -it -v $SSH_AUTH_SOCK:/tmp/agent.sock -e SSH_AUTH_SOCK=/tmp/agent.sock -v $(pwd):/data onefastsnail/development ssh-add -l

You can also just bash directly into this container, from which all the tools are available in there. You may need to pass in some .env files depending upon what your wanting to do.

* docker run --rm -it -v $SSH_AUTH_SOCK:/tmp/agent.sock -e SSH_AUTH_SOCK=/tmp/agent.sock -v $(pwd):/data onefastsnail/development


### Flightplan / Deployment

For now only the main deploy and build tasks are available and should be run in the app/ folder.

* docker run --rm -it -v $SSH_AUTH_SOCK:/tmp/agent.sock -e SSH_AUTH_SOCK=/tmp/agent.sock -v $(pwd):/data onefastsnail/development fly test:staging
* docker run --rm -it -v $SSH_AUTH_SOCK:/tmp/agent.sock -e SSH_AUTH_SOCK=/tmp/agent.sock -v $(pwd):/data onefastsnail/development fly ping:staging
* docker run --rm -it -v $SSH_AUTH_SOCK:/tmp/agent.sock -e SSH_AUTH_SOCK=/tmp/agent.sock -v $(pwd):/data onefastsnail/development fly deploy:production


### WP CLI

Run these commands inside the app/dist folder, ensure you link to the correct .env files and vars.

* docker run --rm -it -v $(pwd):/app --link mysql:mysql onefastsnail/wpcli wp --allow-root user list


## Notes

* To be used on a Linux machine, as the reference to the $SSH_AUTH_SOCK variable doesnt exist on a Mac, and requires some symbolic linking goodness :).

## Credits

Paul Stewart

## License

What license? :)
