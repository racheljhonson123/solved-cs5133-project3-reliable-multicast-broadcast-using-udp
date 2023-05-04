Download Link: https://assignmentchef.com/product/solved-cs5133-project3-reliable-multicast-broadcast-using-udp
<br>
The objective of this programming project is to learn UDP reliable client-server interaction using UDP socket interface. After completing the project, you will have a basic understanding of the steps required to add reliability features in UDP applications for developing a networking application.

<ol start="2">

 <li><strong>Project Specification: </strong></li>

</ol>

Multicast only applies to UDP, which is connectionless and provide no reliability. Multicast is unreliable as there is no guarantee that every multicast message destined for the same multicast group address will be received by every host subscribing to this multicast group. In order to fit the reliability needs of multicast applications, many schemes have been proposed. In this project, you are required to implement a Reliable <em>Multicast Server and a Client</em> in C language that implements a simple version of reliable multicasting. Allow up to 5 reliable clients to simultaneously subscribe to the multicast group served by your Reliable Multicast Server. Each of the subscribing clients will be <em>executed on a distinct host in the CS GPEL machines</em>, and the reliable multicast server will keep track of all current subscribed clients. Every time the server multicasts a message, it expects an acknowledgment from every subscribed client. If the server does not receive acknowledgments from all subscribing clients within a timeout period, the server will <em>unicast the message</em> to each subscribed client that <u>fails to acknowledge</u>. The server would not proceed to multicast the next message until it <em>successfully receives an acknowledgment</em> from every subscribed client.

<strong>2.1.</strong> <strong>Multi-cast Server Behavior: </strong>

<ul>

 <li>At startup, the server takes an argument that specifies the <em>port number</em> that it is listening to. You have to use (<em>5000</em>+<em>last 4 digits</em> of your student-id number) to avoid requesting same port by multiple students.</li>

 <li>After successful startup, the multi-cast server program will ask the user to create a group <em>(e.g., OUCS)</em> and maximum number of clients <em>(e.g., 5)</em> can join in the group to receive broadcast messages.</li>

 <li>Next, your multicast server should prompt the user to enter the <em>number of messages</em> to be multicasted among clients. At the same time, your multicast server should listen for <em>joining and leaving requests</em> from the clients, until the user finishes inputting all messages.</li>

 <li>As clients may use the message “<strong>JOIN</strong>” to join the multicast group and “<strong>QUIT</strong>” to leave from the group, server needs to maintain the active client list for message broadcasting purpose. If the client is unable to join the multicast group, send an error message to client (e.g., more than maximum number of clients join the multicast group). If the client closes the connection, the server should remove this client from the active client list and print out the <em>client IP + port information</em>.</li>

 <li>In order to simulate possible message loss, your multicast server and clients should “<strong>accept</strong>” only <em>90%</em> received messages and discard the remaining <em>10%</em>. The clients acknowledge only “<strong>accepted</strong>” messages, not all the received messages.</li>

 <li>Your multicast server will wait for <em>2 seconds</em> for acknowledgments from its clients. After the timeout expires, the server starts <em>unicasting</em> the same message to those clients that fail to acknowledge this message (or whose acknowledgment is discarded by the server).</li>

 <li>When <u>sending out</u> a message, your multicast server should display the <em>content of the message</em>, and whether the message is <em>multicasted or unicasted</em>. <strong><u>For example</u></strong><u>,</u> “<em>Content of the message</em>, <em>Multicasted to …</em> or <em>Content of the message, Unicasted to …</em>”.</li>

 <li>When <u>accepting</u> a message, your multicast client should display the <em>content of the message</em>, along with a tag specifying whether the message is a multicast message or a unicast message (which is a retransmission).</li>

 <li>Server requires to unsubscribe all clients from the group <em>(e.g., OUCS)</em> as soon as it receives the string “<strong>CLEARALL</strong>” from user input.</li>

</ul>




<strong>2.2.</strong> <strong>Client Behavior: </strong>

<ul>

 <li>Your client program needs to take two arguments from user during startup that specifies the <em>IP address and port number</em> of the multi-cast server it wants to access.</li>

 <li>After a successful startup, your sender program will first prompt a welcome message that asks the user to input a group name <em>(e.g., OUCS)</em> it wants to join.</li>

 <li>Next, client requires to send the message “<strong>JOIN</strong>” to join the multicast group to receive messages from the multi-cast server.</li>

 <li>Similarly, client can send the message “<strong>QUIT</strong>” to unsubscribe from the group and receive no further messages from the server.</li>

 <li>When accepting a message, your multicast client should display the <em>content of the message</em>, along with a tag specifying whether the message is a <em>multicast message or a unicast message</em> (which is a retransmission).</li>

 <li>In order to simulate possible message loss, your clients should “<strong>accept</strong>” only <em>90%</em> received messages and discard the remaining <em>10%</em>. The clients acknowledge only “accepted” messages, not all the received messages. Note: multi-cast server also randomly discards 10% of received acknowledgements from clients.</li>

 <li>After client accepts a message, it needs to send an acknowledgement message “<strong>RECEIVED</strong>” to the multicast server.</li>

</ul>




<ol start="3">

 <li><strong>Programming Notes: </strong></li>

</ol>

<strong> </strong>

You have to use <u>UDP sockets</u> for implementing both client and server programs. You are allowed to use <em>multi-threading</em> in this project, if requires. You should program each process to print an informative statement whenever it takes an action (e.g., sends or receives a message, detects termination of input, etc.), so that you can see that your processes are working either correctly or not. One should be able to determine from this output if your processes are working correctly. You should hand in screen shots (or file content, if your process is writing to a file) of these informative messages.

Make sure, your multicast server allow the user to specify the listening port number and multicast group name during startup. Make sure you <u>close</u> every socket that you use in your program. If you abort your program, the socket may still hang around and the next time you try and bind a new socket to the port ID you previously used (but never closed), you may get an error. Also, please be aware that port ID’s, when bound to sockets, are system-wide values and thus other students may be using the port number you are trying to use though it’s not recommended. If you need to kill a process after you have started it, you can use the LINUX <em>kill</em> command. Use the LINUX <em>ps</em> command to find the process id of your server.

Any clarifications and revisions to the project will be posted on the course web page on Canvas. Students are encouraged to start this project early and use the <strong>project discussion group</strong> on Canvas for <em>any general questions</em> so that everyone can benefit from the replies.

<strong>File names:</strong>

File names for this project are as follows:

<strong><u>Client:</u></strong> <em>lastNameReliableUDPClient.c </em>

<strong><u>Multi-cast Server:</u></strong><em> lastNameReliableUDPServer.c </em>

<em> </em>