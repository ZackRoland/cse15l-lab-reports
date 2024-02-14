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
![Image](https://i.postimg.cc/5NqMrWRX/Lab-2-Screenshot-1.png)
1) The method in the code that is called is the handleRequest method which takes in a url and displays the user and message when given the input
2) The relevant argument to the handleRequest method is the url since that is the main input were working with
3) This specific request identifies a unique user so the user and message values get set which subsequently sets the usersMessage variable
from which the messageHistory variable gets updated with to add the usersMessage to it. the end result is returning what is stored in usersMessage
and if the path is just "/" the messageHistory is displayed which displays all the messages that lie within messageHistory. The screenshot is the result
of entering the path of "/" which displays only 1 message since just 1 message has been stored as of yet
```
/add-message?s=How are you&user=yash
```
![Image](https://i.postimg.cc/sgTCV9yy/Lab-2-Screenshot-2.png)
1) The method in the code that is called is the handleRequest method which takes in a url and displays the user and message when given the input
2) The relevant argument to the handleRequest method is the url since that is the main input were working with
3) This specific request identifies a unique user so the user and message values get set which subsequently sets the usersMessage variable
from which the messageHistory variable gets updated with to add the usersMessage to it. the end result is returning what is stored in usersMessage
and if the path is just "/" the messageHistory is displayed which displays all the messages that lie within messageHistory. he screenshot is the result
of entering the path of "/" which displays 2 messages instead of one since "jpolitz" had added a message previously
