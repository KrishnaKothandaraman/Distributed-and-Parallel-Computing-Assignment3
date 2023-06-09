# Distributed-and-Parallel-Computing-Assignment3

**For TA's of Comp3258**
You may view the source code for all the Java files written here and use this readme for instructions on how to run the submission!

**Submission directory structure**
```tree
.
├── authfiles
│   ├── OnlineUser.txt
│   ├── UserInfo.txt
│   └── UserStats.txt
├── JPoker24Game.jar
├── JPoker24GameRoomServer.jar
├── JPoker24GameServer.jar
├── res.jar
└── security.policy
```

> **Note**: After testing the package's .jar, sometimes when running these commands from the command line, you may notice the application taking a long time to set up once you click "Play Game". I'm not sure what the cause is, but if you encounter it, give it a minute or so to boot up! The same happens when you first set up the GameRoomServer.

There are three main components to this project:
1. **JPoker24Game.jar**: This is the .jar file for the client and all the libraries that the client uses.
2. **JPoker24GameServer.jar**: This is the .jar file that handles the authentication for the users through RMI.
3. **JPoker24GameRoomServer.jar**: This is the .jar file that implements the GameRoomServer logic for opening rooms and handling players. The communication through JMS happens here.

## Auth Server
Set up:
1. Run rmiregistry with the command `rmiregistry &`.
   > **Note**: Remember to add the path to the `res.jar` file in your CLASSPATH to make sure the `rmiregistry` command works! `res.jar` contains the classfiles for the serverinterface as well as other important utils!
2. In the submission, you will also notice a `security.policy` file along with an `authfiles/` directory. Edit the `security.policy` files to point to the `authfiles/` directory and the files within.

**Run command**: `java -Djava.security.policy=<path-to-security.policy> -jar JPoker24GameServer.jar <ip-addr>`

## GameRoomServer
Set up:
For Glassfish, set up a connection factory called `jms/GameConnectionFactory` and a destination queue called `jms/GameRoomMessageQueue`. These two queues on localhost are used by the client and GameRoomServer for communication!

**Run command**: `java -Djava.security.policy=<path-to-security.policy> -jar JPoker24GameRoomServer.jar`

## Game Client
**Run command**: `java -jar JPoker24Game.jar <ip-addr>`
Once everything is set up, you should be able to play!
