## Designing Distributed Systems 
  by Brendan Burns

#### Chapter 3 - Sidecar pattern
  - sharing pid namespace
    - ```docker run -d <my-app-image>```
    - ```docker run --pid=container:<APP_CONTAINER_ID>  -p 8080:8080    brendanburns/topz:db0fa58 /server```
