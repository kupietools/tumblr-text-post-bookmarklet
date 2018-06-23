# tumblr-text-post-bookmarklet
A working bookmarklet to share web pages to Tumblr text posts. 

I do a lot of posting to Tumblr to archive notes on interesting things I’ve read online. Tumblr’s default bookmarklet and browser extensions have two serious drawbacks:

1.) They either create photo or link posts, nothing else
2.) They frequently don’t work at all: the share window opens, and then the “spinner” graphic sits and pulses endlessly on an otherwise blank page, and the post creation window is never drawn

I don’t like link posts because the original page can move or disappear. I often want to create a text post. Unfortunately these two annoyances make that, well, annoying.

I finally got fed up tonight. Here is a bookmarklet that will open a window to create a Tumblr text post with the title and a “via” link to whatever page you click it on:

    javascript:var%20d=document,w=window,e=w.getSelection,k=d.getSelection,x=d.selection,s=(e?e():(k)?k():(x?x.createRange().text:0)),f='https://www.tumblr.com/widgets/share/tool',l=d.location,e=encodeURIComponent,p='?url='+e(l.href)%20+'&posttype=text'+'&title='+e(d.title)%20+'&selection='+((s!=0)?e(s):'-'),u=f+p;try%7Bif(!/%5E(.*%5C.)?tumblr%5B%5E.%5D*$/.test(l.host))throw(0);tstbklt();%7Dcatch(z)%7Ba%20=function()%7Bif(!w.open(u,'t','toolbar=0,resizable=0,status=1,width=450,height=430'))l.href=u;%7D;if(/Firefox/.test(navigator.userAgent))setTimeout(a,0);else%20a();%7Dvoid(0)

If you don’t know how to create a bookmarklet, dragging ~~[this link](javascript:(var%20d=document,w=window,e=w.getSelection,k=d.getSelection,x=d.selection,s=(e?e():(k)?k():(x?x.createRange().text:0)),f='https://www.tumblr.com/widgets/share/tool',l=d.location,e=encodeURIComponent,p='?url='+e(l.href)%20+'&posttype=text'+'&title='+e(d.title)%20+'&selection='+((s!=0)?e(s):'-'),u=f+p;try%7Bif(!/%5E(.*%5C.)?tumblr%5B%5E.%5D*$/.test(l.host))throw(0);tstbklt();%7Dcatch(z)%7Ba%20=function()%7Bif(!w.open(u,'t','toolbar=0,resizable=0,status=1,width=450,height=430'))l.href=u;%7D;if(/Firefox/.test(navigator.userAgent))setTimeout(a,0);else%20a();%7Dvoid(0))) to your Bookmarks bar should do it for you: Tumblr Text Post~~ (Nevermind, Github won't allow Bookmarklets to work in README files because apparently all Github users are childish and must be protected from themselves. You can grab the draggable bookmarklet from my blog post at [https://www.kupietz.com/2018/06/23/bookmarklet-post-tumblr-text-post-actually-works/].)

If you have text selected on the page, it will include that text as the body of the post. (Be careful, if your text is longer than the maximum allowable length of an URL, the share won’t work.)
