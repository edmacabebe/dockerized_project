Centos7 operating system and MarkLogic 8.0-5.5

# Please download the MarkLogic in their official site
# https://developer.marklogic.com/products
# Then rename it to MarkLogic.rpm

docker run --name marklogic -d -p 8000:8000 -p 8001:8001 -p 8002:8002 marklogic:8