Code adopted from https://github.com/xlab-si/xopera-examples

### Installation and deployment

1. Run `./01install.sh` to install xOpera and Ansible
2. Run `bash 02deploy.sh` to deploy hello app to localhost
3. Open http://locahost to see "hello web"

NOTE: Apache2 installed on deploy, will not be uninstalled
on undeploy and original page is not restored in that case.

### Testing with Docker

Clone this repo.
```
git clone https://github.com/abitrolly/tosca-deploy
cd tosca-deploy
```

The command below runs docker image with Ubuntu 21.04, mounts
current dir there as `/root/tosca` and maps
http://locahost:9999 to port 80 web inside.

```
docker run -v "$(pwd):/root/tosca":Z -w "/root/tosca" -it -p 9999:80 ubuntu:21.04
```

Check that http://locahost:9999 shows standard Apache 2 page.
Once inside the container run commands for deployment.
```
./01install.sh
bash 02deploy.sh
```

Check that http://locahost:9999 now shows "hello web".
