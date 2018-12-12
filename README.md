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


