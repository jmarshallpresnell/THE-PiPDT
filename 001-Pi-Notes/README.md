# Pi Notes

How many times has this happened to you? You have 6 (or 12 or 25) Pi's on your network, and about 50 (or more) &micro;SD cards with different projects that you are trying to keep somewhat organized?

Aside from the really obvious thing of labeling your extremely tiny &micro;SD cards with a code and keeping a decoder whiteboard:

* A1: node experiments
* A2: asterisk experiments
* B6: php project #4

Or maybe using old-fashioned index cards with an SD card holder taped to it with notes? (*This is actually a great way to organize your offline &micro;SD cards!*)

But where do you keep your own internal notes? Notes that don't necessarily go into version control, but things like where you stopped because of that client's call, or an emergency fix that interrupted you? Or better yet - what port(s) are the web or database or MQTT or memcache servers listening to for this card? (That one always annoys the hell out of me, especially if things are on non-standard ports or there's multiple instances of a specific type of server that is is running)

Wouldn't it be cool if, instead of trying to make the decoder whiteboard a note-taking hell, or learning how to write the size of a legal agreement's disclaimers... why not put these notes in an HTML file and and serve it up on a dedicated port? But installing a full web server for this is somewhat, well, STOOPID. But what if you could do it with a simple shell script of less than 10 lines with *no* big dedicated web server?

Voila:

```
#!/bin/sh
PORT="88"
FILE="notes.html"

while [ 1 ];
do
    { printf 'HTTP/1.0 200 OK\r\nContent-Length: %d\r\n\r\n' "$(wc -c < ${FILE})"; cat ${FILE}; } | nc -l ${PORT} >/dev/nul
done
```

I call this script the **Single Page Web Server** (*spws*). Mine lives in `/root` and is started by `/etc/rc.local` on each boot. You could start it in a number of ways at boot (supervisor or an entry in `/etc/init.d` comes to mind) but I prefer the very simplest number of changes from the baseline. 

I've made a modified image of Raspbian Buster (and Stretch and Jessie!) that has this already installed so the effort required is minimal. (In a later PiPDT, we'll talk about making your own &micro;SD images!)

Your image-specific notes are always available (even remotely) if the Pi is running at http://[ip address]:88

*Due to the nature of linux command line processing, the html file is read before the nc command is executed, so it will require TWO refreshes after you modify the notes file before it serves it up. Yeah, annoying a bit, but it's only 8 lines!*