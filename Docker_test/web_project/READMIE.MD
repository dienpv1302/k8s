docker pull nameimage:tag   #Tai ve 1 docker file
docker pull nameimage #Hoặc tải về bản cuối

docker images
docker images -a

docker build -t web_napas_docker .  #Name and optionally a tag in the name:tag format


docker build -t <tên container> #Build một image từ container
    
#Tạo và chạy container, container tự xóa khi kết thúc thì thêm vào tham số --rm
docker run -p 8090:8090 -it --rm web_napas_docker
#Bạn chú ý có tham số -it để khi container chạy, bạn có terminate làm việc ngay với Ubuntu. Tham số này có nghĩa là:
    -t nó có nghĩa là console, cho phép kết nối với terminal để tương tác
    -i có nghĩa duy trì mở stdin để nhập lệnh.

docker run -p 8090:8090 -it -d web_napas_docker #-d Chay ngam

docker save -o web_napas_docker.tar web_napas_docker
docker image rm --force web_napas_docker

docker ps # xem nhung container nao dang chay
docker container ls --all
docker container start -i containerid
docker container start 1ba6b9f73a0c
docker container attach 1ba6b9f73a0c #Nếu có một container với ID là containerid đang chạy, để quay quay trở lại terminal của nó dùng lệnh
#Chạy một lệnh trên container đang chạy
docker exec -it containerid command
#thoát termial vẫn giữ container đang chạy
CTRL +P, CTRL + Q

docker container rm containerid
docker rm $(docker ps --filter status=exited -q) #Remove all container stop
docker image rm $(docker images –a –q) #Delete all image hiện có
docker run –name <tên container> <tên image> #Run container từ image và thay đổi tên container
docker stop $(docker ps –a –q) #Stop all container
docker logs <tên container> #Show log a container
