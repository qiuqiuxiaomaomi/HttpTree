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


