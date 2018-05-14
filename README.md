# command-NodeJs


https://stackoverflow.com/questions/8553957/how-to-release-localhost-from-error-listen-eaddrinuse/22875192#22875192


You are getting the error EADDRINUSE because the port, which your application wants to use, is occupied by another process. To release this port, you need to terminate the occupying process.

Since you are on Windows, you can terminate the process using the command prompt (cmd). With the cmd you can discover the process ID (PID) of the blocking application. You will need the PID in order to terminate / kill the process.

Here is a step-by-step guide...

Find all processes which are running on a specified port (in this example, Port is "3000"):

netstat -ano | find ":3000 "

The netstat command will list up all processes running on the specified port. In the last column of the netstat results you can see the PIDs (in this example, PID is "8308"). You can find out more about a specific PID by running the following command:

tasklist /fi "pid eq 8308"

If you want to terminate a process, you can do that with the following command by using its PID (in this example, PID is "8308"):

taskkill /pid 8308 /f
