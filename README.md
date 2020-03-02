openssl_for_muduo client and server sample
=======

Muduo is a multithreaded C++ network library based on the reactor pattern.  
http://github.com/chenshuo/muduo

But I didn't found there is openssl support.  
This is a client sample use SSL_BIO and muduo.  
This is a good sample for reactor networking library to use openssl.  
You can easily modify it to adapt  other networking library.  
If you want to learn more about openssl in server side, please see reference 1



# How To Use?
1. download and compile muduo library from http://github.com/chenshuo/muduo  
2. modify the Makefile to find muduo library
3. install openssl  
  for centos: yum install openssl-devel  
  for ubuntu: apt install openssl libssl-dev -y  
4. type make to compile this client.cpp  
5. sslclient will be generated in this folder




# Core tech
Usually openssl is implemented only by SSL_read and SSL_write like  
 https://github.com/yedf/openssl-example  
This will use openssl to read and write socket.  
In some case, the data is received by networking library, the user program can just use the data already received by networking lib,  maybe you can try SSL_BIO to implement ssl socket.

1. use SSL_is_init_finished() to judge the handshake is ok.
2. when you want to recv data :  
BIO_write   and  SSL_read  
3. when you want to send data:  
SSL_write   and  BIO_read

# More
+ This code is just example. The best method to use ssl is to implement  SSL-TcpConnection to handle data receive and send. 


# Reference:
1. https://github.com/my-official/IOCP_SSL
2. https://blog.csdn.net/xiaoqing_2014/article/details/79720913




