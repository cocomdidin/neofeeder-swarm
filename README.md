# NeoFeeder Swarm Mode

Implementation of PDDikti's Neofeeder in docker swarm mode.

#### Why?
Because the neofeeder is using docker-compose, which the implementation is not that different with the old feeder.
It still needs single machine per feeder running. What if you need multiple feeder (for multiple universities)?

This implementation bypass that issue, thus gives us better control over our infrastructure in terms of cost and maintenance, as we only need to maintain one docker host.

### Installation
1. Clone this repository.
2. Enter cloned repository.
3. Copy original neofeeder to `source` directory.
4. Run:
    ```bash
   $ chmod +x refresh && ./refresh
    ```
   This will copy necessary files to current directory
5. Make sure the implementation of DockerfileSwarm is in sync with original Dockerfile.
6. Build the image:
    ```bash
   $ docker build -t myrepository/feeder:latest -f DockerfileSwarm
    ```
7. Edit configuration of `swarm.yml` as you need.
8. Deploy the stack:
    ```bash
   $ env APP_PATH_HOST="/path/to/this-repository" docker stack deploy -c swarm.yml neofeeder-university1
    ```
