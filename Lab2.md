
## Part 1
![Image](https://cdn.discordapp.com/attachments/974137838180380672/1200952008585269389/Screenshot_2024-01-27_at_3.40.47_PM.png?ex=65c80cb7&is=65b597b7&hm=b6be69db6dc74d61f6bfc9f5e3377d1d845a493334e3678041d882662c9653e8&)

Inorder to achieve this output shown above, I compiled and ran `ChatServer` with port `5555`. I then used the path `/add-message` along with the query ` ?s=How are you?&user= Viraj`.
In the code, the method `handleRequest` takes the URL and checks to see that it contains the path `/add-message`, which it does. this means it is expecting a query with two arguments: `s`, and `user`, which in this case were `"How are you?"` and `"Viraj"` respectively. it then uses a String array paramaters to split the query into `"s=How are you"` and `"user = Viraj"`. Another String array called messages splits paramaters at `index 0`, which is `"s=How are you?"` using `"="` as the argument so that messages now contains `"s"` and `"How are you"`. The String array called users does this same concept with `"user = Viraj"`, found in `paramater[1]`, to store `"user"` and `"Viraj"` seperately. Finally, String `message`, `user`, and `output`, capture the desired message, by getting the user and its message from the seperated strings in the previous array to form: `Viraj: How are you?`
</p>


![Image](https://cdn.discordapp.com/attachments/974137838180380672/1200952008920805416/Screenshot_2024-01-27_at_3.41.27_PM.png?ex=65c80cb7&is=65b597b7&hm=433243f60c5312688585f57280b7af9ee5665a9d7b055f9b7972fb4e47ab6bc0&)


Just like the previous `add-message` call, the exact same process was used with user `"Karthik"` and message `"I'm doing well"`. Ultimatley, this output was stored in the same variable called output (shown below) that also contained `"Viraj: How are you"`. This was doing using `+=` to add to the previous message and `"\n"` to create a new line for the subsequent message.

Below is the code for the `ChatServer` as required in the lab report:
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
```

## Part 2

### Here is the absolute path to the private key:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1201951365598019686/Screenshot_2024-01-30_at_10.03.27_AM.png?ex=65cbaf70&is=65b93a70&hm=9208994a8806c80516666fbc0c170fe423bd96f24a60b082eb31a6ab4bf0e58c&)

### Here is the absolute path to the public on the ieng6 server:

![Image](https://cdn.discordapp.com/attachments/974137838180380672/1201951365900013608/Screenshot_2024-01-30_at_10.04.31_AM.png?ex=65cbaf70&is=65b93a70&hm=6063ac79424996609d697e0d8503b53639a16c233ceb58031d800e73c2cdb007&)

### Finally, here is a terminal interaction of logging into ieng6 server without entering a password:


![Image](https://cdn.discordapp.com/attachments/974137838180380672/1201951365207961640/Screenshot_2024-01-30_at_10.03.08_AM.png?ex=65cbaf70&is=65b93a70&hm=c12e8d21e73e19341a88faadd988697d4c2d4177bcddda74d87971b81b68b08f&)


## Part 3

In lab, learning how to use querys and a local host website was interesting. I got to learn about ports and servers which was something that I have not used before. I also got to learn more about unix commands and they turn out to make coding in other classes easier because I stay organized better.
