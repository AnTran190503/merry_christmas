Cài đặt Java: Tải JDK 14.0.1 từ trang web chính thức của Oracle hoặc sử dụng các lệnh sau:

bash
Sao chép mã
sudo apt-get update
sudo apt-get install openjdk-14-jdk
Tải xuống và giải nén Apache Spark 3.1.1 với Hadoop 2.7:

bash
Sao chép mã
wget https://downloads.apache.org/spark/spark-3.1.1/spark-3.1.1-bin-hadoop2.7.tgz
tar -xzf spark-3.1.1-bin-hadoop2.7.tgz
mv spark-3.1.1-bin-hadoop2.7 ~/spark-3.1.1-bin-hadoop2.7
Bước 1': Thiết lập môi trường Java
Thêm các biến môi trường JDK vào tệp .bashrc của bạn:

bash
Sao chép mã
echo "export JAVA_HOME=/home/hufi/jdk-14.0.1/" >> ~/.bashrc
echo "export PATH=\$PATH:\$JAVA_HOME/bin" >> ~/.bashrc
source ~/.bashrc
Bước 2: Thiết lập các nút Master và Worker
Thiết lập Nút Master:

Đi đến thư mục Spark và khởi động nút master:

bash
Sao chép mã
cd ~/spark-3.1.1-bin-hadoop2.7/bin/
./spark-class org.apache.spark.deploy.master.Master
Thiết lập Nút Worker:

Khởi động các nút worker bằng cách kết nối chúng với master:

bash
Sao chép mã
cd ~/spark-3.1.1-bin-hadoop2.7/bin/
./spark-class org.apache.spark.deploy.worker.Worker spark://172.17.10.233:7077
Lưu ý: Thay thế 172.17.10.233 bằng địa chỉ IP thực tế của nút master của bạn.

Sửa lỗi Quyền Java (nếu có):
Nếu bạn gặp lỗi quyền Java, hãy chạy lệnh sau:

bash
Sao chép mã
chmod +x /home/hufi/jdk-14.0.1/bin/*
Bước 3: Chạy một chương trình Scala trên master
Mở một terminal khác và chạy Spark Shell để kiểm tra thiết lập với mã Scala:

bash
Sao chép mã
cd ~/spark-3.1.1-bin-hadoop2.7/bin/
./spark-shell --master spark://172.17.10.233:7077
Bước 4: Kiểm tra giao diện web để xác minh
Để kiểm tra xem các nút master và worker có được kết nối hay không, hãy mở trình duyệt của bạn và truy cập:

Giao diện nút Master: http://localhost:8080
Giao diện nút Worker: http://localhost:8081
