The apache image contains a webserver and exposes port 80. To start the container type:
docker run -d --name   bestapp   -p 8081:80 391405332002.dkr.ecr.ca-central-1.amazonaws.com/testing1:4

Testing push to ecr

RUNNING THE APPLICATION USING THE ERC BUILT IMAGE. 

docker run -d --name   bestapp   -p 8080:80 