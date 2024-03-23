<h1>Module 6 Reflection</h1>

<h3>Commit 1: Handle-connection, check response </h3>
In this commit, I successfully created the ```handle_connection``` function, which is responsible for handling the TCP connection. I used port 7878. The function utilizes ```BufReader``` to read the TCP stream. The ```BufReader``` is used here to read the TCP stream line by line.

<h3>Commit 2: Returning HTML </h3>
In this commit, I successfully implemented the returning function to the client. The ```handle_connection``` function has been updated to read the contents of the hello.html file. The ```fs::read_to_string("hello.html")``` function is used to read the contents of the hello.html file.
The content length of the response is set to the length of the contents of the ```hello.html``` file.

![Commit 2 screen capture](/assets/images/commit2.png)

<h3>Commit 3: Validating request and selectively responding </h3>
In this commit, I successfully implemented a feature to selectively respond to the client based on the request. The ```handle_connection``` function has been updated to check the request and respond accordingly.
If the request is for the root path, the server responds with a ```HTTP/1.1 200 OK``` status line based on the ```hello.html``` file.
If the request is not for the root path, the server responds with a ```HTTP/1.1 404 NOT FOUND``` status line based on the ```404.html``` file.


![Commit 3 screen capture](/assets/images/commit3.png)

<h3>Commit 4: Simulation of slow request </h3>
In this commit, I implemented a slow request simulation feature by using ```/sleep``` path.
When the server receives a request for the ```/sleep path``` based on status line ```GET /sleep HTTP/1.1```, it puts the current thread to sleep for 10 seconds before responding.
This is done using the ```thread::sleep(Duration::from_secs(10))``` function. After the sleep duration, the server responds with a HTTP/1.1 200 OK status line and serves the hello.html file.