![Image](https://cdn.discordapp.com/attachments/974137838180380672/1200952008585269389/Screenshot_2024-01-27_at_3.40.47_PM.png?ex=65c80cb7&is=65b597b7&hm=b6be69db6dc74d61f6bfc9f5e3377d1d845a493334e3678041d882662c9653e8&)

Inorder to achieve this output shown above, I compiled and ran ChatServer with port #5555. I then used the path /add-message along with the query ?s=How are you?&user= Viraj.
In the code, the method handleRequest takes the URL and checks to see that it contains the path /add-message, which it does. this means it is expecting a query with two arguments: s, and user, which in this case were "How are you?" and "Viraj" respectively. it then uses a String array paramaters to split the query into "s=How are you" and "user = Viraj". Another String array called messages splits paramaters at index 0, which is "s=How are you?" using "=" as the argument so that messages now contains "s" and "How are you". The String array called users does this same concept with "user = Viraj", found in paramater[1], to store "user" and "Viraj" seperately. Finally, String message, user, and output, capture the desired message, by getting the user and its message from the seperated strings in the previous array to form: Viraj: How are you?
![Image](https://cdn.discordapp.com/attachments/974137838180380672/1200952008920805416/Screenshot_2024-01-27_at_3.41.27_PM.png?ex=65c80cb7&is=65b597b7&hm=433243f60c5312688585f57280b7af9ee5665a9d7b055f9b7972fb4e47ab6bc0&)

Just like the previous add-message call, the exact same process was used with user Karthik and message "I'm doing well". Ultimatley, this output was stored in the same variable called output (shown below) that also contained "Viraj: How are you". This was doing using ** += **

Below is the code for the ChatServer as required in the lab report:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String user;
    String message;
    String output;
    public String handleRequest(URI url) {   
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("&");
                String[] messages = parameters[0].split("=");
                String[] users = parameters[1].split("=");
                if (parameters[0].contains("s=")) {
                    message = messages[1];
                    user = users[1];
                    output += user + ": " + message +"\n" ;
                }
                return output;

            }
            return "404 Not Found!";
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
