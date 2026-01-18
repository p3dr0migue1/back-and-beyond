+++
date = '2024-11-04T22:51:58Z'
draft = false
tags = []
title = 'Port Already in Use'
+++

If when restarting your django server locally you get the message:
```bash
`Error: That port is already in use.`
```
All you have to do is kill all the processes associated with the port in question.

To do that simply type on your terminal:

```bash
sudo fuser -k 8000/tcp  # this command will kill all processes associated with port 8000
```

You can also use the command line network utility tool `netstat` to kill the process associated with the port Django is running on.

```bash
netstat -ntlp
```

It should display something like this:
```bash
(Not all processes could be identified, non-owned process info
will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8000          0.0.0.0:*               LISTEN      6599/python
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:4381          0.0.0.0:*               LISTEN      31806/spotify
tcp        0      0 127.0.0.1:8000          0.0.0.0:*               LISTEN      30491/ssh
tcp        0      0 0.0.0.0:5355            0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:9485          0.0.0.0:*               LISTEN      30493/ssh
```

So now you can just close the port in which Django is running by killing the process associated with it.
```bash
kill -9 <PID> # in this case: kill -9 6599
```
