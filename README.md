# HttpTree
Http技术研究

RequestConfig requestConfig = RequestConfig.custom()
                    .setConnectionRequestTimeout(config.connReqTimeout)   
                    //从连接池中获取连接的超时时间
                    //与服务器连接超时时间：httpclient会创建一个异步线程用以创建  socket连接，此处设置该socket的连接超时时间
                    .setConnectTimeout(config.connTimeout)
                    .setSocketTimeout(config.socketTimeout)               //socket读数据超时时间：从服务器获取响应数据的超时时间
                    .build();


<pre>
从连接池获取可用连接超时：  setConnectionRequestTimeout
 
连接目标超时   setConnectTimeout

等待响应超时   setSocketTimeout    
</pre>

<pre>
Http请求方式：
      GET
      POST
      DELETE
      PUT
      OPTIONS
      HEAD
      TRACE
      CONNECT

      GET与POST区别：
                   1）get请求无消息体，只能携带少量数据。
                   2）post请求由消息体，可以携带大量数据。

             携带数据的方式：
                          1）get请求将数据放在URL地址中；
                          2）POST请求将数据放在消息体中；

                          3）GET请求提交的数据最多1024字节。
                          5）POST请求对提交数据的长度没有限制。
</pre>

### Request Header

![](https://i.imgur.com/cW0zrd5.png)

### Response Header

![](https://i.imgur.com/wrQDs6k.png)

<pre>
同步 VS 异步：
      同步与异步是针对应用程序与内核的交互而言的。
      1）同步过程中进程触发IO操作或者轮询的去查看IO操作是否完成。
      2）异步过程中进程触发IO操作以后，直接返回，做自己的事情，IO交给内核来处理，完成后内核
         通知进程IO处理完成。

阻塞 VS 非阻塞：
      阻塞：
          调用返回前，线程挂起；
      非阻塞：
          调用不会阻塞线程，而且立即返回。
</pre>

HTTPS通信的步骤

![](https://i.imgur.com/ASet9Sk.png)

<pre>
HTTPS通信的步骤

     1）客户端请求服务器，发送握手消息
     2）服务器返回客户端自己的加密算法、数字证书和公钥；
     3）客户端验证服务器端发送来的数字证书是否与本地受信任的证书相关信息一致；

     如果验证通过，则浏览器会采用自身的随机数算法产生一个随机数，并用服务器发送来的公钥
     加密；发送给服务器；这里如果有人通过攻击获取了这个消息，那也没用，因为他没有解密此段
     消息所需要私钥；验证通过的网站在浏览器地址栏的右边会有一安全锁的标识；

     5）服务器解密得到此随机数，并用此随机数作为密钥采用对称加密算法加密一段握手消息发送
     给浏览器；

     6）浏览器收到消息后解密成功，则握手结束，后续的信息都通过此随机密钥加密传输。

     以上是服务端认证的情况，如果服务端对访问的客户端也有认证需求，则客户端也需要将自己的
     证书发送给服务器，服务器认证不通过，通讯结束；原理同上；
</pre>


