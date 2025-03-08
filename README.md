# java-shopping 



apt-get update
apt-get install maven -y
apt-get install openjdk-11-jre -y


mvn clean package -DshipTests=true
# docker build -t shopping:latest -f docker/Dockerfile .
#docker run -d --name java-shoppingcart -p 8070:8070 shopping:latest
