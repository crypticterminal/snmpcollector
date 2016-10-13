# snmpcollector

## Run from master
If you want to build a package yourself, or contribute. Here is a guide for how to do that.

### Dependencies

- Go 1.5
- NodeJS >=6.2.1

### Get Code

```
go get github.com/toni-moreno/snmpcollector
```

### Building the backend
Replace X.Y.Z by current version number in package.json file

```
cd $GOPATH/src/github.com/toni-moreno/snmpcollector
go run build.go setup            (only needed once to install godep)
godep restore                    (will pull down all golang lib dependencies in your current GOPATH)
go run build.go build
```

### Building frontend assets

```
npm install
PATH=$(npm bin):$PATH
npm run tsc
cd public/
ln -s ../node_modules/ ./node_modules
cd ..

```

### Recompile backend on source change
To rebuild on source change (requires that you executed godep restore)
```
go get github.com/Unknwon/bra
bra run
```
### Running first time 
To execute without any configuration you need a minimal config.toml file on the conf directory.

```
cp conf/sample.config.toml conf/config.toml
./bin/snmpcollector
```
#### Online config 

Now you wil be able to configure metrics/measuremnets and devices from the builting web server at  http://localhost:8090

### Offline configuration.

You will be able also insert data directly on the sqlite db that snmpcollector has been created at first execution on config/snmpcollector.db examples on example_config.sql

```
cat conf/example_config.sql |sqlite3 conf/snmpcollector.db
```
