Aurora Labs

Run the following commend from the root location of the auroraLabs repo:
docker-compose -f docker-compose.yaml up -d

The python app will not be running until you make your firs commit.
Modify the Dockerfile ENV RESPONCE to whatever you want
ENV RESPONCE="Devops is great!"

Push the changes to git and it will trigger the jenkins job.

Check that the app is working by:
http://3.75.250.178:5000/messages

Jenkins is accessible via the following URL:
http://3.75.250.178:8080/
user: aurora
pass: adm1cmv1






