# **LAB 2**
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String message = "";
    String user = "";
    String usersMessage = "";
    String messageHistory = "";
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return messageHistory;
        }  else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("&");
                String[] messageParam = parameters[0].split("=");
                String[] userParam = parameters[1].split("=");
                if (messageParam[0].equals("s")) {
                    message = messageParam[1];
                    user = userParam[1];
                    usersMessage = user +": "+message +"\n";
                    messageHistory += usersMessage +"\n";
                    return usersMessage;
                }
               
                
            }
            return "404 Not Found!";
        }
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
```
/add-message?s=Hello&user=jpolitz
```
![Image]()
```
/add-message?s=How are you&user=yash
```
![Image]()
