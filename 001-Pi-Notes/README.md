# Pi Notes - Keep track of things on your development SD cards

How many times has this happened to you? You have 6 (or 12 or 25) Pi's on your network, and about 50 (or more) microSD cards with different projects that you are trying to keep somewhat organized?

Aside from the really obvious thing of labeling your extremely tiny SD cards with a code and keeping a decoder whiteboard:

* A1: node experiments
* A2: asterisk experiments
* B6: php project #4

Where do you keep your own internal notes? Notes that don't necessarily go into version control, but things like where you stopped because of that client's call, or an emergency fix that interrupted you? Or better yet - what dang port(s) are the web servers or database servers listening to for this card? (That one always annoys the hell out of me)

Wouldn't it be cool if, instead of trying to make the decoder whiteboard a note-taking hell, why not put these notes in an HTML file and and serve it up on a dedicated port? (I use port 88) But installing a full web server for this is somewhat, well, stupid. But what if you could do it with a simple shell script of less than 10 lines with NO big dedicated web server?

```
#!/bin/sh
PORT="88"
FILE="notes.html"

while [ 1 ];
do
    { printf 'HTTP/1.0 200 OK\r\nContent-Length: %d\r\n\r\n' "$(wc -c < ${FILE})"; cat ${FILE}; } | nc -l ${PORT} >/dev/nul
done
```

I call script this the Single Page Web Server (spws). Mine lives in /root and is started by /etc/rc.local on each boot. You could start it in a number of ways at boot (supervisor or an entry in /etc/init.d comes to mind) but I prefer the very simplest number of changes from the baseline.

Now, your notes are always available (even remotely) if the Pi is running at http://**[ip address]**:88

