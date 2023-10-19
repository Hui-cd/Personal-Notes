## TCP Connection
系统之间采用TCP通讯协议
在Java中服务器和客户端之间使用Socket进行通讯，其中服务器会创建一个Socket对象，客户端和服务器通过对这个socket对象的写入和读取来进行通信
- 服务器实例化一个serverSocket对象，表示通过服务器上的端口通信
- 服务器调用ServerSocket的accept方法，该方法将一直等待，直到客户端连接上服务器给定的端口
- 服务器正在等待时，客户端实例化一个Socket对象，指定服务器名称和端口号来请求连接
- Socket类的构造函数试图将客户端连接到指定的服务器和端口号。如果连接建立，则客户端创建一个socket对象和服务器进行通讯、
- 服务器上，accept（）方法返回服务器上一个新的socket引用，该socket连接到客户端的socket
### Example
Server
``` java
import java.net.*;

import java.io.*;

public class GreetingServer extends Thread{

   private ServerSocket serverSocket;

   public GreetingServer(int port) throws IOException{

      this.serverSocket = new ServerSocket(port);

      serverSocket.setSoTimeout(10000);

   }

  
   public void run(){

      while(true){

         try {

            Socket server = serverSocket.accept();

            System.out.print("server address"+server.getRemoteSocketAddress());

            DataInputStream input = new DataInputStream(server.getInputStream());

            System.out.println(input.readUTF());

            DataOutputStream output = new DataOutputStream(server.getOutputStream());

            output.writeUTF("connection " + server.getLocalSocketAddress());

         } catch (IOException e) {

            // TODO Auto-generated catch block

            e.printStackTrace();

         }

      }

   }

  

   public static void main(String[] args) {

      int port = Integer.parseInt(args[0]);

      try {

         Thread t = new GreetingServer(port);

         t.run();

      } catch (Exception e) {

         e.printStackTrace();

         // TODO: handle exception

      }

   }

}
```

Client
``` java
import java.net.*;

import java.io.*;

public class GreetingClient{

   public static void main(String[] args) {

      String serverName = args[0];

      int port = Integer.parseInt(args[1]);

      try {

         System.out.println("server " + serverName + "port "+ port);

         Socket client = new Socket(serverName,port);

         OutputStream outToServer = client.getOutputStream();

         DataOutputStream out = new DataOutputStream(outToServer);

         out.writeUTF("Hello from " + client.getLocalSocketAddress());

         InputStream inFromServer = client.getInputStream();

         DataInputStream in = new DataInputStream(inFromServer);

         System.out.println("服务器响应： " + in.readUTF());

         client.close();

      } catch (Exception e) {

         // TODO: handle exception

         e.printStackTrace();

      }

   }

}
```