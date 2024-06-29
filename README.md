- k3d cluster create --config config.yml
- kubectl cluster-info
- kubectl get nodes
- docker image build -t app:v1 .
- docker tag app:v1 localhost:5000/app:v1
- docker image push localhost:5000/app:v1
- kubectl create -f app-pod.yml
- kubectl get pods


### demo web for testkube 
https://testkube.dev-19.finxact.io/tests

### installing testkube
- install testkube using script
    - `curl -sSLf https://get.testkube.io | sh`

- deploy testkube open-source, standalone agent
    - `testkube init`

### clean up tasks after testing
- Uninstall Testkube CLI
    - `testkube uninstall`
- remove helm repo
    - `helm uninstall testkube`
    - `helm repo remove kubeshop`
    - `testkube purge`  
- remove Testkube namespace
    `kubectl delete namespace testkube`

- postman executer
    - `kubectl testkube create test --file postman_collection.json --type postman/collection --name postman-test`
    - `kubectl testkube run test postman-test`
    - `kubectl testkube create test --file postman_collection.json --type postman/collection --name postman-scheduled-test --schedule="*/5 * * * *"`

### for devops/jenkins integration
rest api can be used https://docs.testkube.io/openapi/ for github integration
    - `port forward 8088`
    - get test execution details: `http://localhost:0000/v1/tests/`
