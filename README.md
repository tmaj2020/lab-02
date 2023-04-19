# Lab 2
[Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repo and clone it to your machine to get started!

## Team Members
- Ty Benjamin Majam

## Lab Question Answers

Answer for Question 1: 
	The reliability of UDP changed as only 6 of the numbers that I entered from 1-10 were registered by the server,
	Even though the client had registered that all 10 numbers were sent. This is likely due to the introduction of
	the 50% packet loss that was introduced to the environment, simulating what it would be like if there was a 50%
	chance that somewhere along the way, a router had a full buffer or some other influence caused the packets to be
	dropped
	
Answer for Question 2: 
	When I added the packet loss to the tcp environment, the server appeared to still receive all of the numbers from
	the client. This is likely due to the fact that the protocol in TCP includes transmission reliability. This should
	ensure that all packets from the sender reach their destination at some point in time.

Answer for Question 3: 
	The time it took for the TCP server to receive packets from the sender took much longer when the packet loss was
	introduced. This is likely due to how TCP requires for acknowledgement of the receipt of these packets and has to
	resend the packet that was 'lost' if this acknowledgement is not received by the sender.
-----------------------------------------------------------------------------------------------------------------------------
Answer for Question 1 (server code): 
	The parameters argc and argv are the two parameters that can be accepted into the main function from the command line.
	These parameters typically take on the value of any input that immediately follows the ./program command separated by
	a space.
	
Answer for Question 2 (server code): 
	A UNIX file descriptor is a handle that refers to a specific input/output resource, which in this case is the socket
	the server is using.
	
Answer for Question 3 (server code): 
	A struct is a way for severael variables of potentially different data types to be stored in a common location. These
	variables are then referred to as members of that struct. The sockaddr_in struct appears to include three members:
	sin_family
    sin_addr
    sin_port
	
Answer for Question 4 (server code): 
	The socket() function takes the domain, type, and protocol to use when using a socket to communicate. The domain
	refers to the communication domain (AF_INET refers to IPv4); Type refers to the communication protocol to use such
	as TCP or UDP (SOCK_STREAM refers to TCP); and protocol is left at 0 here since that refers to the default protocol
	for the domain and type selected. The function returns a non-negative integer my system can use to refer to the socket
	connection in future socket-related functions.

Answer for Question 5 (server code): 
	The bind() function takes in three arguments: sockfd (the file descriptor of the socket being bound), addr (the pointer
	to the sockaddr structure that contains the address that the socket should be bound to), and addrlen (the length in
	the bytes of the struct being referred to). The listen() function takes in two parameters: sockfd (the file descriptor
	of the socket being listened to) and backlog (the maximum number of connections that can be made before the server
	starts to refuse connections).

Answer for Question 6 (server code): 
	While(1) should be used since we want to continuously take in messages from the client. Based on the code below, we
	would encounter issues with this code in that the server would be waiting to a response from one client. This is a
	problem if we have multiple clients since that means that the server would be listening to only one of the many 
	clients it has and it likely wouldn't be able to move on to the other clients without first receiving a message from
	the first client it connected to.
	
Answer for Question 7 (server code): 
	The fork() command allows for a server to 'fork' its connection so that it can listen to multiple clients at the same
	time by creating child processes for each one. We could incorporate it by putting another while loop around the accept() 
	function statement and the main while loop we already have. We could then check if our server is forking its connection
	by encompassing the main while loop we already have with an if statement.
	
Answer for Question 8 (server code): 
	A system call is a kind of command that the program is unable to perform on its own, so it has to call on the OS to
	perform specific tasks so the command can properly be carried out.
