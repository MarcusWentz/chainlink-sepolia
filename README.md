# chainlink-taiko

Chainlink oracle on Taiko Alpha 3 blockchain which supports API uint256 GET requests.

## Starting the Chainlink node on Taiko with WSS RPC URL:

1. Clone this repository.
```shell
git clone git@github.com:taikoxyz/chainlink-taiko.git
```
2. Start PostgreSQL server instance with Docker

Enter directory
```shell
cd chainlink-taiko 
```
Create docker instance with password
```shell
sudo docker run --name cl-postgres -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
```
3. Test Chainlink Node v2.2.0 with TOML files

Start Chainlink Node after PostgreSQL server is running (modify config.toml if you wish to modify network parameters)
```shell
sudo docker run --platform linux/x86_64/v8 --name chainlink -v $HOME/chainlink-taiko:/chainlink -it -p 6688:6688 --add-host=host.docker.internal:host-gateway smartcontract/chainlink:2.2.0 node -config /chainlink/config.toml -secrets /chainlink/secrets.toml start
```
:warning: Make sure you also install PostgreSQL: :warning:

```shell
sudo apt-get -y install postgresql
```
:warning: Note: if a port is being used, end the process in the port with: :warning:

```shell
sudo lsof -i tcp:5432
```
[SHOWS PROCESS ID IN TCP PORT 5432, EXAMPLE: 25537]:
```shell
sudo kill 25537
```
:warning: Note: if there is an issue with your Chainlink node, try deleting the docker Chainlink node's image and containers. ⚠️

4. Interact with Chainlink node GUI in web browser URL:

http://localhost:6688/

## Reference

Running a Chainlink Node - Configure your node

https://docs.chain.link/chainlink-nodes/v1/running-a-chainlink-node
