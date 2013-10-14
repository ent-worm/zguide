.output chapter1.wd
.bookmark basics

+ Basics

# 基础

++ Fixing the World

## 给这个世界打上补丁

How to explain 0MQ? Some of us start by saying all the wonderful things it does. //It's sockets on steroids. It's like mailboxes with routing. It's fast!//  Others try to share their moment of enlightenment, that zap-pow-kaboom satori paradigm-shift moment when it all became obvious. //Things just become simpler. Complexity goes away. It opens the mind.//  Others try to explain by comparison. //It's smaller, simpler, but still looks familiar.//  Personally, I like to remember why we made 0MQ at all, because that's most likely where you, the reader, still are today.

要怎么介绍0MQ呢？

有些会列举它各种超炫功能。*它是类固醇的通道啦，像自动送信的邮箱啦，而且速度超快！*

其他人会说那些顿悟的感受，就像“重击——会心一击——致命一击！”一样，灵光一现，一切都清晰明了了。*事变简单了！完全不复杂了！思维开阔了！*

还有些人会作比较。*虽然它小而简单，但你仍会觉得无比熟悉。*

就我个人而言，我更愿意分享当初我们为何要写0MQ，因为当初，我们的处境就和读者你一模一样。

Programming is science dressed up as art because most of us don't understand the physics of software and it's rarely, if ever, taught. The physics of software is not algorithms, data structures, languages and abstractions. These are just tools we make, use, throw away. The real physics of software is the physics of people--specifically, our limitations when it comes to complexity, and our desire to work together to solve large problems in pieces. This is the science of programming: make building blocks that people can understand and use //easily//, and people will work together to solve the very largest problems.

编程就像一门伪装成艺术的科学，因为大部分人不明白什么是软件的本质，就算被教导过，也真是少得可怜。软件的本质，不是算法，不是数据结构，不是编程语言或是抽象。这些仅仅是工具，我们制造它，使用它，然后丢弃它。而软件真正的本质在于人，换而言之，在于面对复杂问题时人的瓶颈，而我们是否愿意通过协作将大的问题分而治之。这才是编程科学：造一些易懂*易用*的小模块，而大家可以协作解决大难题。

We live in a connected world, and modern software has to navigate this world. So the building blocks for tomorrow's very largest solutions are connected and massively parallel. It's not enough for code to be "strong and silent" any more. Code has to talk to code. Code has to be chatty, sociable, well-connected. Code has to run like the human brain, trillions of individual neurons firing off messages to each other, a massively parallel network with no central control, no single point of failure, yet able to solve immensely difficult problems. And it's no accident that the future of code looks like the human brain, because the endpoints of every network are, at some level, human brains.

我们生活在一个互联的世界，现代软件也需要能映射这个世界。这就是说，为了解决未来更大的问题，我们的模块必须提供互联和高度并行的能力。沉默而健壮代码已经完全不够了，代码必须健谈、相互关联，代码之间要能交流。代码得和人脑一样，数以万亿的神经元高速的传递信息，高度并行，无须中央控制，没有节点故障，但仍能有效的解决问题。这一切并不意外，因为从某种意义上来讲，现在网络上的每个节点都是一个人脑。

If you've done any work with threads, protocols, or networks, you'll realize this is pretty much impossible. It's a dream. Even connecting a few programs across a few sockets is plain nasty when you start to handle real life situations. Trillions? The cost would be unimaginable. Connecting computers is so difficult that software and services to do this is a multi-billion dollar business.

如果你曾用过线程、协议或者网络，你也许会说这是天方夜谭。解决实际问题中，用套接字连几个程序就足够麻烦了。数以万亿？别开玩笑了。要知道，也只有土豪公司才能担负得起用大量计算机互联来提供软件和服务。

So we live in a world where the wiring is years ahead of our ability to use it. We had a software crisis in the 1980s, when leading software engineers like Fred Brooks believed [http://en.wikipedia.org/wiki/No_Silver_Bullet there was no "Silver Bullet"] to "promise even one order of magnitude of improvement in productivity, reliability, or simplicity".

所以，现实世界是我们根本没法驾驭当前的网络。80年代曾经有过一次软件危机，像Fred Brooks这样的软件开发先驱们相信[没有银弹](http://en.wikipedia.org/wiki/No_Silver_Bullet)能“让软件开发的生产率、可靠性或者简单性中任何一项瞬间提高一个档次”。

Brooks missed free and open source software, which solved that crisis, enabling us to share knowledge efficiently. Today we face another software crisis, but it's one we don't talk about much. Only the largest, richest firms can afford to create connected applications. There is a cloud, but it's proprietary. Our data and our knowledge is disappearing from our personal computers into clouds that we cannot access and with which we cannot compete. Who owns our social networks? It is like the mainframe-PC revolution in reverse.

Brooks没有预见到，自由和开源软件运动解决这次危机，让我们能更有效的分享知识。如今，我们又面临另一次软件危机，但是我们都没有过多的谈及它。只有最大、最富有的公司才能创造出互联的应用。当然了，谁都知道有云，但是并不是全人类的云。我们的数据和知识从个人电脑中消失，转移到了我们无法接触的云上了，这让我们根本无法与之竞争。想想现在谁掌控着我们的社交网络？这简直就是大型机对个人电脑的逆袭。

We can leave the political philosophy [http://swsi.info for another book]. The point is that while the Internet offers the potential of massively connected code, the reality is that this is out of reach for most of us, and so large interesting problems (in health, education, economics, transport, and so on) remain unsolved because there is no way to connect the code, and thus no way to connect the brains that could work together to solve these problems.

我们暂且不管其中的的政治哲学，那些都可以[另外出书](http://swsi.info)了。问题在于互联网提供了让代码互联的潜力，现实却是我们大部分人根本无从用起。而那些有趣的大规模问题（健康、教育、金融、交通等）却因为我们无法使用那些代码而迟而未决，因为我们根本没有办法连接到那些大脑，协同工作又从何谈起呢。

There have been many attempts to solve the challenge of connected code. There are thousands of IETF specifications, each solving part of the puzzle. For application developers, HTTP is perhaps the one solution to have been simple enough to work, but it arguably makes the problem worse by encouraging developers and architects to think in terms of big servers and thin, stupid clients.

曾经有过很多对代码进行互联的尝试。有着成百上千的IETF(互联网工程任务组)草案，每一个都尝试解决某部分难题。对于应用开发者，HTTP可能是一个还算简单的方案，但我们也可以说它让情况更加恶化，因为该协议鼓励着开发者和架构师构建重量级的服务器、轻量却笨拙的客户端。

So today people are still connecting applications using raw UDP and TCP, proprietary protocols, HTTP, and Websockets. It remains painful, slow, hard to scale, and essentially centralized. Distributed P2P architectures are mostly for play, not work. How many applications use Skype or Bittorrent to exchange data?

时至今日，人们还在使用最原始的UDP、TCP、私有协议、HTTP、WebSockets来连接应用程序，这些工作痛苦、缓慢、扩展性差，而且基本上都是试图中心化。而分布式P2P协议却大多只是在娱乐领域使用，而非工作领域。有谁会用Skype或者Bittorrent来交换数据么？

Which brings us back to the science of programming. To fix the world, we needed to do two things. One, to solve the general problem of "how to connect any code to any code, anywhere". Two, to wrap that up in the simplest possible building blocks that people could understand and use //easily//.

这一现实再次将我们拉回到编程科学上来。为了修正这个世界，我们需要做两件事。其一，解决能在任何地点、让任意代码互联的问题。其二，将这一方法打包成易懂*易用*的、最最简单的程序模块提供给人们。

It sounds ridiculously simple. And maybe it is. That's kind of the whole point.

这些听起来太简单了！不过，也许真是这样。其实也就是这样的。

++ Starting Assumptions

## 预先假定

We assume you are using at least version 3.2 of 0MQ. We assume you are using a Linux box or something similar. We assume you can read C code, more or less, as that's the default language for the examples. We assume that when we write constants like PUSH or SUBSCRIBE, you can imagine they are really called {{ZMQ_PUSH}} or {{ZMQ_SUBSCRIBE}} if the programming language needs it.

我们假定你使用了至少为3.2版本的0MQ。假定你使用的是Linux或其他类似系统。假定你多少懂一点C代码，因为示例程序默认情况下都是C代码。我们还假定当我们提及PUSH或SUBSCRIBE等常量时，你得知道程序真正需要的其实是{{ZMQ_PUSH}}或{{ZMQ_SUBSCRIBE}}。

++ Getting the Examples

## 获取示例

The examples live in a public [https://github.com/imatix/zguide GitHub repository]. The simplest way to get all the examples is to clone this repository:

[[code]]
git clone --depth=1 git://github.com/imatix/zguide.git
[[/code]]

示例程序都在公开的[Github项目](https://github.com/imatix/zguide)中。欲获取全部示例，最简单的方法：

```
git clone --depth=1 git://github.com/imatix/zguide.git
```

Next, browse the examples subdirectory. You'll find examples by language. If there are examples missing in a language you use, you're encouraged to [http://zguide.zeromq.org/main:translate submit a translation]. This is how this text became so useful, thanks to the work of many people. All examples are licensed under MIT/X11.

其次，打开examples子目录。你可以按语言找到相应的示例。如果缺了你使用的编程语言，我们欢迎你[提交一份“翻译”](http://zguide.zeromq.org/main:translate)。得益于众人的帮助，这份文档才如此好用。所有的示例代码都遵循MIT/X11许可。

++ Ask and Ye Shall Receive

## 请求、接收

So let's start with some code. We start of course with a Hello World example. We'll make a client and a server. The client sends "Hello" to the server, which replies with "World"[figure]. Here's the server in C, which opens a 0MQ socket on port 5555, reads requests on it, and replies with "World" to each request:

那么，让我们从一些简单的代码开始。我们当然先来一个“Hello World”。我们将写一个client和server。client将发送“Hello”给server，然后server将返回“World”。这里是C代码实现的server，它在5555端口打开了一个0MQ套接字，从该端口接收请求，收到请求后应答“World”：

[[code type="example" title="Hello World server" name="hwserver" language="C"]]
[[/code]]

[[code type="textdiagram" title="Request-Reply"]]
  #------------#
  |   Client   |
  +------------+
  |    REQ     |
  '---+--------'
      |    ^
      |    |
Hello |    | World
      |    |
      v    |
  .--------+---.
  |    REP     |
  +------------+
  |   Server   |
  #------------#
[[/code]]

The REQ-REP socket pair is in lockstep. The client issues {{zmq_send[3]}} and then {{zmq_recv[3]}}, in a loop (or once if that's all it needs). Doing any other sequence (e.g., sending two messages in a row) will result in a return code of -1 from the {{send}} or {{recv}} call. Similarly, the service issues {{zmq_recv[3]}} and then {{zmq_send[3]}} in that order, as often as it needs to.

REQ-REP套接字对是完全同步的。client使用{{zmq_send[3]}}发送详细，然后循环{{zmq_recv[3]}}接受消息（或者只按照需求等待一次）。乱序（如连续发送两次消息）调用{{send}}或者{{recv}}都将导致返回-1。同理，服务也必须按照顺序，先{{zmq_recv[3]}}然后{{zmq_send[3]}}，按需循环。

0MQ uses C as its reference language and this is the main language we'll use for examples. If you're reading this online, the link below the example takes you to translations into other programming languages. Let's compare the same server in C++:

0MQ使用C作为参考手册的语言，同时C也是我们用来作为示例的语言。如果你是在在线浏览手册，那么例子下面的链接提供了其他语言的“翻译”。让我们看一下C++版本的server：

[[code type="example" title="Hello World server" name="hwserver" language="C++"]]
[[/code]]

You can see that the 0MQ API is similar in C and C++. In a language like PHP or Java, we can hide even more and the code becomes even easier to read:

你会发现，C和C++版本的0MQ API非常的相似。而对于PHP或Java等语言，我们甚至可以隐藏起更多的细节，代码更为简洁：

[[code type="example" title="Hello World server" name="hwserver" language="PHP"]]
[[/code]]

[[code type="example" title="Hello World server" name="hwserver" language="Java"]]
[[/code]]

Here's the client code:

以下是client的代码：

[[code type="example" title="Hello World client" name="hwclient"]]
[[/code]]

Now this looks too simple to be realistic, but 0MQ sockets have, as we already learned, superpowers. You could throw thousands of clients at this server, all at once, and it would continue to work happily and quickly. For fun, try starting the client and //then// starting the server, see how it all still works, then think for a second what this means.

看起来还不够实用？但是我们已经说过了，0MQ套接字有着超能力。你可以一次性抛出成千上百个client给这个server，而它仍然工作的欢快无比。好玩的是，你也可以先启动client，*然后*才启动server，看看它是否还工作，想想看，这意味着什么？

Let us explain briefly what these two programs are actually doing. They create a 0MQ context to work with, and a socket. Don't worry what the words mean. You'll pick it up. The server binds its REP (reply) socket to port 5555. The server waits for a request in a loop, and responds each time with a reply. The client sends a request and reads the reply back from the server.

让我们简单的解释一下这两段程序到底做了什么。他们打开了一份0MQ上下文以及一个套接字。先别急着弄懂这些词，你会明白的。server绑定了一个5555号端口的REP（应答）套接字，然后在循环中等待请求，每次回复一个应答。而client就是给server发送请求并读取应答。

If you kill the server (Ctrl-C) and restart it, the client won't recover properly. Recovering from crashing processes isn't quite that easy. Making a reliable request-reply flow is complex enough that we won't cover it until [#reliable-request-reply].

如果你杀死了server进程（Ctrl-C）并重启，client不能正确的恢复。想恢复挂掉的进程可没那么容易。我们将在[#可靠请求-应答]解决如何可靠的请求-应答这一难题。

There is a lot happening behind the scenes but what matters to us programmers is how short and sweet the code is, and how often it doesn't crash, even under a heavy load. This is the request-reply pattern, probably the simplest way to use 0MQ. It maps to RPC and the classic client/server model.

这东西背后有不少机制，但是对我们重要的是，这些代码短小精悍，高负荷下也不会轻易出错。这就是请求-应答模式，0MQ最简单的使用方法。它映射了RPC协议以及经典的client/server模型。

++ A Minor Note on Strings

0MQ doesn't know anything about the data you send except its size in bytes. That means you are responsible for formatting it safely so that applications can read it back. Doing this for objects and complex data types is a job for specialized libraries like Protocol Buffers. But even for strings, you need to take care.

In C and some other languages, strings are terminated with a null byte. We could send a string like "HELLO" with that extra null byte:

[[code language="C"]]
zmq_send (requester, "Hello", 6, 0);
[[/code]]

However, if you send a string from another language, it probably will not include that null byte. For example, when we send that same string in Python, we do this:

[[code language="Python"]]
socket.send ("Hello")
[[/code]]

Then what goes onto the wire is a length (one byte for shorter strings) and the string contents as individual characters[figure].

[[code type="textdiagram" title="A 0MQ string"]]
#-----#  #-----+-----+-----+-----+-----#
|  5  |  |  H  |  e  |  l  |  l  |  o  |
#-----#  #-----+-----+-----+-----+-----#
[[/code]]

And if you read this from a C program, you will get something that looks like a string, and might by accident act like a string (if by luck the five bytes find themselves followed by an innocently lurking null), but isn't a proper string. When your client and server don't agree on the string format, you will get weird results.

When you receive string data from 0MQ in C, you simply cannot trust that it's safely terminated. Every single time you read a string, you should allocate a new buffer with space for an extra byte, copy the string, and terminate it properly with a null.

So let's establish the rule that **0MQ strings are length-specified and are sent on the wire //without// a trailing null**. In the simplest case (and we'll do this in our examples), a 0MQ string maps neatly to a 0MQ message frame, which looks like the above figure--a length and some bytes.

Here is what we need to do, in C, to receive a 0MQ string and deliver it to the application as a valid C string:

[[code language="C"]]
//  Receive 0MQ string from socket and convert into C string
//  Chops string at 255 chars, if it's longer
static char *
s_recv (void *socket) {
    char buffer [256];
    int size = zmq_recv (socket, buffer, 255, 0);
    if (size == -1)
        return NULL;
    if (size > 255)
        size = 255;
    buffer [size] = 0;
    return strdup (buffer);
}
[[/code]]

This makes a handy helper function and in the spirit of making things we can reuse profitably, let's write a similar {{s_send}} function that sends strings in the correct 0MQ format, and package this into a header file we can reuse.

The result is {{zhelpers.h}}, which lets us write sweeter and shorter 0MQ applications in C. It is a fairly long source, and only fun for C developers, so [https://github.com/imatix/zguide/blob/master/examples/C/zhelpers.h read it at leisure].

++ Version Reporting

0MQ does come in several versions and quite often, if you hit a problem, it'll be something that's been fixed in a later version. So it's a useful trick to know //exactly// what version of 0MQ you're actually linking with.

Here is a tiny program that does that:

[[code type="example" title="0MQ version reporting" name="version"]]
[[/code]]

++ Getting the Message Out

The second classic pattern is one-way data distribution, in which a server pushes updates to a set of clients. Let's see an example that pushes out weather updates consisting of a zip code, temperature, and relative humidity. We'll generate random values, just like the real weather stations do.

Here's the server. We'll use port 5556 for this application:

[[code type="example" title="Weather update server" name="wuserver"]]
[[/code]]

There's no start and no end to this stream of updates, it's like a never ending broadcast[figure].

Here is the client application, which listens to the stream of updates and grabs anything to do with a specified zip code, by default New York City because that's a great place to start any adventure:

[[code type="example" title="Weather update client" name="wuclient"]]
[[/code]]

[[code type="textdiagram" title="Publish-Subscribe"]]
               #-------------#
               |  Publisher  |
               +-------------+
               |     PUB     |
               '-------------'
                    bind
                      |
                      |
                   updates
                      |
      .---------------+---------------.
      |               |               |
   updates         updates         updates
      |               |               |
      |               |               |
      v               v               v
   connect         connect         connect
.------------.  .------------.  .------------.
|    SUB     |  |    SUB     |  |    SUB     |
+------------+  +------------+  +------------+
| Subscriber |  | Subscriber |  | Subscriber |
#------------#  #------------#  #------------#
[[/code]]

Note that when you use a SUB socket you **must** set a subscription using {{zmq_setsockopt[3]}} and SUBSCRIBE, as in this code. If you don't set any subscription, you won't get any messages. It's a common mistake for beginners. The subscriber can set many subscriptions, which are added together. That is, if an update matches ANY subscription, the subscriber receives it. The subscriber can also cancel specific subscriptions. A subscription is often, but not necessarily a printable string. See {{zmq_setsockopt[3]}} for how this works.

The PUB-SUB socket pair is asynchronous. The client does {{zmq_recv[3]}}, in a loop (or once if that's all it needs). Trying to send a message to a SUB socket will cause an error. Similarly, the service does {{zmq_send[3]}} as often as it needs to, but must not do {{zmq_recv[3]}} on a PUB socket.

In theory with 0MQ sockets, it does not matter which end connects and which end binds. However, in practice there are undocumented differences that I'll come to later. For now, bind the PUB and connect the SUB, unless your network design makes that impossible.

There is one more important thing to know about PUB-SUB sockets: you do not know precisely when a subscriber starts to get messages. Even if you start a subscriber, wait a while, and then start the publisher, **the subscriber will always miss the first messages that the publisher sends**. This is because as the subscriber connects to the publisher (something that takes a small but non-zero time), the publisher may already be sending messages out.

This "slow joiner" symptom hits enough people often enough that we're going to explain it in detail. Remember that 0MQ does asynchronous I/O, i.e., in the background. Say you have two nodes doing this, in this order:

* Subscriber connects to an endpoint and receives and counts messages.
* Publisher binds to an endpoint and immediately sends 1,000 messages.

Then the subscriber will most likely not receive anything. You'll blink, check that you set a correct filter and try again, and the subscriber will still not receive anything.

Making a TCP connection involves to and from handshaking that takes several milliseconds depending on your network and the number of hops between peers. In that time, 0MQ can send many messages. For sake of argument assume it takes 5 msecs to establish a connection, and that same link can handle 1M messages per second. During the 5 msecs that the subscriber is connecting to the publisher, it takes the publisher only 1 msec to send out those 1K messages.

In [#sockets-and-patterns] we'll explain how to synchronize a publisher and subscribers so that you don't start to publish data until the subscribers really are connected and ready. There is a simple and stupid way to delay the publisher, which is to sleep. Don't do this in a real application, though, because it is extremely fragile as well as inelegant and slow. Use sleeps to prove to yourself what's happening, and then wait for [#sockets-and-patterns] to see how to do this right.

The alternative to synchronization is to simply assume that the published data stream is infinite and has no start and no end. One also assumes that the subscriber doesn't care what transpired before it started up. This is how we built our weather client example.

So the client subscribes to its chosen zip code and collects a thousand updates for that zip code. That means about ten million updates from the server, if zip codes are randomly distributed. You can start the client, and then the server, and the client will keep working. You can stop and restart the server as often as you like, and the client will keep working. When the client has collected its thousand updates, it calculates the average, prints it, and exits.

Some points about the publish-subscribe (pub-sub) pattern:

* A subscriber can connect to more than one publisher, using one connect call each time. Data will then arrive and be interleaved ("fair-queued") so that no single publisher drowns out the others.

* If a publisher has no connected subscribers, then it will simply drop all messages.

* If you're using TCP and a subscriber is slow, messages will queue up on the publisher. We'll look at how to protect publishers against this using the "high-water mark" later.

* From 0MQ v3.x, filtering happens at the publisher side when using a connected protocol ({{tcp://}} or {{ipc://}}). Using the {{epgm://}} protocol, filtering happens at the subscriber side. In 0MQ v2.x, all filtering happened at the subscriber side.

This is how long it takes to receive and filter 10M messages on my laptop, which is an 2011-era Intel i5, decent but nothing special:

[[code]]
$ time wuclient
Collecting updates from weather server...
Average temperature for zipcode '10001 ' was 28F

real    0m4.470s
user    0m0.000s
sys     0m0.008s
[[/code]]

++ Divide and Conquer

[[code type="textdiagram" title="Parallel Pipeline"]]
            #-------------#
            |  Ventilator |
            +-------------+
            |    PUSH     |
            '------+------'
                   |
                 tasks
                   |
      .------------+-------------.
      |            |             |
      v            v             v
.----------.  .----------.  .----------.
|   PULL   |  |   PULL   |  |   PULL   |
+----------+  +----------+  +----------+
|  Worker  |  |  Worker  |  |  Worker  |
+----------+  +----------+  +----------+
|   PUSH   |  |   PUSH   |  |   PUSH   |
'----+-----'  '----+-----'  '----+-----'
      |            |             |
      '------------+-------------'
                   |
                results
                   |
                   v
            .-------------.
            |    PULL     |
            +-------------+
            |    Sink     |
            #-------------#
[[/code]]

As a final example (you are surely getting tired of juicy code and want to delve back into philological discussions about comparative abstractive norms), let's do a little supercomputing. Then coffee. Our supercomputing application is a fairly typical parallel processing model[figure]. We have:

* A ventilator that produces tasks that can be done in parallel
* A set of workers that process tasks
* A sink that collects results back from the worker processes

In reality, workers run on superfast boxes, perhaps using GPUs (graphic processing units) to do the hard math. Here is the ventilator. It generates 100 tasks, each one is a message telling the worker to sleep for some number of milliseconds:

[[code type="example" title="Parallel task ventilator" name="taskvent"]]
[[/code]]

Here is the worker application. It receives a message, sleeps for that number of seconds, and then signals that it's finished:

[[code type="example" title="Parallel task worker" name="taskwork"]]
[[/code]]

Here is the sink application. It collects the 100 tasks, then calculates how long the overall processing took, so we can confirm that the workers really were running in parallel if there are more than one of them:

[[code type="example" title="Parallel task sink" name="tasksink"]]
[[/code]]

The average cost of a batch is 5 seconds. When we start 1, 2, or 4 workers we get results like this from the sink:

* 1 worker: total elapsed time: 5034 msecs.
* 2 workers: total elapsed time: 2421 msecs.
* 4 workers: total elapsed time: 1018 msecs.

Let's look at some aspects of this code in more detail:

* The workers connect upstream to the ventilator, and downstream to the sink. This means you can add workers arbitrarily. If the workers bound to their endpoints, you would need (a) more endpoints and (b) to modify the ventilator and/or the sink each time you added a worker. We say that the ventilator and sink are //stable// parts of our architecture and the workers are //dynamic// parts of it.

* We have to synchronize the start of the batch with all workers being up and running. This is a fairly common gotcha in 0MQ and there is no easy solution. The {{zmq_connect}} method takes a certain time. So when a set of workers connect to the ventilator, the first one to successfully connect will get a whole load of messages in that short time while the others are also connecting. If you don't synchronize the start of the batch somehow, the system won't run in parallel at all. Try removing the wait in the ventilator, and see what happens.

* The ventilator's PUSH socket distributes tasks to workers (assuming they are all connected //before// the batch starts going out) evenly. This is called //load balancing// and it's something we'll look at again in more detail.

* The sink's PULL socket collects results from workers evenly. This is called //fair-queuing//[figure].

[[code type="textdiagram" title="Fair Queuing"]]
#---------#   #---------#   #---------#
|  PUSH   |   |  PUSH   |   |  PUSH   |
'----+----'   '----+----'   '----+----'
     |             |             |
 R1, R2, R3       R4           R5, R6
     |             |             |
     '-------------+-------------'
                   |
             fair-queuing
         R1, R4, R5, R2, R6, R3
                   |
                   v
            .-------------.
            |     PULL    |
            #-------------#
[[/code]]

The pipeline pattern also exhibits the "slow joiner" syndrome, leading to accusations that PUSH sockets don't load balance properly. If you are using PUSH and PULL, and one of your workers gets way more messages than the others, it's because that PULL socket has joined faster than the others, and grabs a lot of messages before the others manage to connect. If you want proper load balancing, you probably want to look at the The load balancing pattern in [#advanced-request-reply].

++ Programming with 0MQ

Having seen some examples, you must be eager to start using 0MQ in some apps. Before you start that, take a deep breath, chillax, and reflect on some basic advice that will save you much stress and confusion.

* Learn 0MQ step-by-step. It's just one simple API, but it hides a world of possibilities. Take the possibilities slowly and master each one.

* Write nice code. Ugly code hides problems and makes it hard for others to help you. You might get used to meaningless variable names, but people reading your code won't. Use names that are real words, that say something other than "I'm too careless to tell you what this variable is really for". Use consistent indentation and clean layout. Write nice code and your world will be more comfortable.

* Test what you make as you make it. When your program doesn't work, you should know what five lines are to blame. This is especially true when you do 0MQ magic, which just //won't// work the first few times you try it.

* When you find that things don't work as expected, break your code into pieces, test each one, see which one is not working. 0MQ lets you make essentially modular code; use that to your advantage.

* Make abstractions (classes, methods, whatever) as you need them. If you copy/paste a lot of code, you're going to copy/paste errors, too.

+++ Getting the Context Right

0MQ applications always start by creating a //context//, and then using that for creating sockets. In C, it's the {{zmq_ctx_new[3]}} call. You should create and use exactly one context in your process. Technically, the context is the container for all sockets in a single process, and acts as the transport for {{inproc}} sockets, which are the fastest way to connect threads in one process. If at runtime a process has two contexts, these are like separate 0MQ instances. If that's explicitly what you want, OK, but otherwise remember:

**Do one {{zmq_ctx_new[3]}} at the start of your main line code, and one {{zmq_ctx_destroy[3]}} at the end.**

If you're using the {{fork()}} system call, each process needs its own context. If you do {{zmq_ctx_new[3]}} in the main process before calling {{fork()}}, the child processes get their own contexts. In general, you want to do the interesting stuff in the child processes and just manage these from the parent process.

+++ Making a Clean Exit

Classy programmers share the same motto as classy hit men: always clean-up when you finish the job. When you use 0MQ in a language like Python, stuff gets automatically freed for you. But when using C, you have to carefully free objects when you're finished with them or else you get memory leaks, unstable applications, and generally bad karma.

Memory leaks are one thing, but 0MQ is quite finicky about how you exit an application. The reasons are technical and painful, but the upshot is that if you leave any sockets open, the {{zmq_ctx_destroy[3]}} function will hang forever. And even if you close all sockets, {{zmq_ctx_destroy[3]}} will by default wait forever if there are pending connects or sends unless you set the LINGER to zero on those sockets before closing them.

The 0MQ objects we need to worry about are messages, sockets, and contexts. Luckily it's quite simple, at least in simple programs:

* Use {{zmq_send[3]}} and {{zmq_recv[3]}} when you can, it avoids the need to work with zmq_msg_t objects.

* If you do use {{zmq_msg_recv[3]}}, always release the received message as soon as you're done with it, by calling {{zmq_msg_close[3]}}.

* If you are opening and closing a lot of sockets, that's probably a sign that you need to redesign your application. In some cases socket handles won't be freed until you destroy the context.

* When you exit the program, close your sockets and then call {{zmq_ctx_destroy[3]}}. This destroys the context.

This is at least the case for C development. In a language with automatic object destruction, sockets and contexts will be destroyed as you leave the scope. If you use exceptions you'll have to do the clean-up in something like a "final" block, the same as for any resource.

If you're doing multithreaded work, it gets rather more complex than this. We'll get to multithreading in the next chapter, but because some of you will, despite warnings, try to run before you can safely walk, below is the quick and dirty guide to making a clean exit in a //multithreaded// 0MQ application.

First, do not try to use the same socket from multiple threads. Please don't explain why you think this would be excellent fun, just please don't do it. Next, you need to shut down each socket that has ongoing requests. The proper way is to set a low LINGER value (1 second), and then close the socket. If your language binding doesn't do this for you automatically when you destroy a context, I'd suggest sending a patch.

Finally, destroy the context. This will cause any blocking receives or polls or sends in attached threads (i.e., which share the same context) to return with an error. Catch that error, and then set linger on, and close sockets in //that// thread, and exit. Do not destroy the same context twice. The {{zmq_ctx_destroy}} in the main thread will block until all sockets it knows about are safely closed.

Voila! It's complex and painful enough that any language binding author worth his or her salt will do this automatically and make the socket closing dance unnecessary.

++ Why We Needed 0MQ

Now that you've seen 0MQ in action, let's go back to the "why".

Many applications these days consist of components that stretch across some kind of network, either a LAN or the Internet. So many application developers end up doing some kind of messaging. Some developers use message queuing products, but most of the time they do it themselves, using TCP or UDP. These protocols are not hard to use, but there is a great difference between sending a few bytes from A to B, and doing messaging in any kind of reliable way.

Let's look at the typical problems we face when we start to connect pieces using raw TCP. Any reusable messaging layer would need to solve all or most of these:

* How do we handle I/O? Does our application block, or do we handle I/O in the background? This is a key design decision. Blocking I/O creates architectures that do not scale well. But background I/O can be very hard to do right.

* How do we handle dynamic components, i.e., pieces that go away temporarily? Do we formally split components into "clients" and "servers" and mandate that servers cannot disappear? What then if we want to connect servers to servers? Do we try to reconnect every few seconds?

* How do we represent a message on the wire? How do we frame data so it's easy to write and read, safe from buffer overflows, efficient for small messages, yet adequate for the very largest videos of dancing cats wearing party hats?

* How do we handle messages that we can't deliver immediately? Particularly, if we're waiting for a component to come back online? Do we discard messages, put them into a database, or into a memory queue?

* Where do we store message queues? What happens if the component reading from a queue is very slow and causes our queues to build up? What's our strategy then?

* How do we handle lost messages? Do we wait for fresh data, request a resend, or do we build some kind of reliability layer that ensures messages cannot be lost? What if that layer itself crashes?

* What if we need to use a different network transport. Say, multicast instead of TCP unicast? Or IPv6? Do we need to rewrite the applications, or is the transport abstracted in some layer?

* How do we route messages? Can we send the same message to multiple peers? Can we send replies back to an original requester?

* How do we write an API for another language? Do we re-implement a wire-level protocol or do we repackage a library? If the former, how can we guarantee efficient and stable stacks? If the latter, how can we guarantee interoperability?

* How do we represent data so that it can be read between different architectures? Do we enforce a particular encoding for data types? How far is this the job of the messaging system rather than a higher layer?

* How do we handle network errors? Do we wait and retry, ignore them silently, or abort?

Take a typical open source project like [http://hadoop.apache.org/zookeeper/ Hadoop Zookeeper] and read the C API code in {{[http://github.com/apache/zookeeper/blob/trunk/src/c/src/zookeeper.c src/c/src/zookeeper.c]}}. When I read this code, in January 2013, it was 4,200 lines of mystery and in there is an undocumented, client/server network communication protocol. I see it's efficient because it uses {{poll}} instead of {{select}}. But really, Zookeeper should be using a generic messaging layer and an explicitly documented wire level protocol. It is incredibly wasteful for teams to be building this particular wheel over and over.

But how to make a reusable messaging layer? Why, when so many projects need this technology, are people still doing it the hard way by driving TCP sockets in their code, and solving the problems in that long list over and over[figure]?

It turns out that building reusable messaging systems is really difficult, which is why few FOSS projects ever tried, and why commercial messaging products are complex, expensive, inflexible, and brittle. In 2006, iMatix designed [http://www.amqp.org AMQP] which started to give FOSS developers perhaps the first reusable recipe for a messaging system. AMQP works better than many other designs, [http://www.imatix.com/articles:whats-wrong-with-amqp but remains relatively complex, expensive, and brittle]. It takes weeks to learn to use, and months to create stable architectures that don't crash when things get hairy.

[[code type="textdiagram" title="Messaging as it Starts"]]
.------------.
|            |
|  Piece A   |
|            |
'------------'
      ^
      |
     TCP
      |
      v
.------------.
|            |
|  Piece B   |
|            |
'------------'
[[/code]]

Most messaging projects, like AMQP, that try to solve this long list of problems in a reusable way do so by inventing a new concept, the "broker", that does addressing, routing, and queuing. This results in a client/server protocol or a set of APIs on top of some undocumented protocol that allows applications to speak to this broker. Brokers are an excellent thing in reducing the complexity of large networks. But adding broker-based messaging to a product like Zookeeper would make it worse, not better. It would mean adding an additional big box, and a new single point of failure. A broker rapidly becomes a bottleneck and a new risk to manage. If the software supports it, we can add a second, third, and fourth broker and make some failover scheme. People do this. It creates more moving pieces, more complexity, and more things to break.

And a broker-centric setup needs its own operations team. You literally need to watch the brokers day and night, and beat them with a stick when they start misbehaving. You need boxes, and you need backup boxes, and you need people to manage those boxes. It is only worth doing for large applications with many moving pieces, built by several teams of people over several years.

[[code type="textdiagram" title="Messaging as it Becomes"]]
        .---.             .---.
.---.   |   |   .---.  ^  |   |
|   +-->|   |<--|   |  |  |   |
|   |   '---'   |   |  |  '-+-'
'-+-'           '-+-'  |    |
  |               ^    |    |
  |       .-------+----+----'
  |       |       |    |
  '-------+-------+----+--.
          |       |    |  |
  .-------+-------+----+--+-----.
  |       v       |       v     |
.-+-.   .---.     |     .---.   |
|   |   |   |   .-+-.   |   |-->|
|   +-->|   +-->|   +-->|   |   |
'---'   '---'   |   |   '---'   |
          ^     '-+-'     ^     |
          |       |       |     |
  .-------+-------+-------'     |
  |       |       |             |
  v     .-+-.     v     .---.   |
.---.   |   |   .---.   |   |   |
|   |<--|   |<--|   |<--|   |<--'
|   |   '---'   |   |   '---'
'---'           '---'
[[/code]]

So small to medium application developers are trapped. Either they avoid network programming and make monolithic applications that do not scale. Or they jump into network programming and make brittle, complex applications that are hard to maintain. Or they bet on a messaging product, and end up with scalable applications that depend on expensive, easily broken technology. There has been no really good choice, which is maybe why messaging is largely stuck in the last century and stirs strong emotions: negative ones for users, gleeful joy for those selling support and licenses[figure].

What we need is something that does the job of messaging, but does it in such a simple and cheap way that it can work in any application, with close to zero cost. It should be a library which which you just link, without any other dependencies. No additional moving pieces, so no additional risk. It should run on any OS and work with any programming language.

And this is 0MQ: an efficient, embeddable library that solves most of the problems an application needs to become nicely elastic across a network, without much cost.

Specifically:

* It handles I/O asynchronously, in background threads. These communicate with application threads using lock-free data structures, so concurrent 0MQ applications need no locks, semaphores, or other wait states.

* Components can come and go dynamically and 0MQ will automatically reconnect. This means you can start components in any order. You can create "service-oriented architectures" (SOAs) where services can join and leave the network at any time.

* It queues messages automatically when needed. It does this intelligently, pushing messages as close as possible to the receiver before queuing them.

* It has ways of dealing with over-full queues (called "high water mark"). When a queue is full, 0MQ automatically blocks senders, or throws away messages, depending on the kind of messaging you are doing (the so-called "pattern").

* It lets your applications talk to each other over arbitrary transports: TCP, multicast, in-process, inter-process. You don't need to change your code to use a different transport.

* It handles slow/blocked readers safely, using different strategies that depend on the messaging pattern.

* It lets you route messages using a variety of patterns such as request-reply and pub-sub. These patterns are how you create the topology, the structure of your network.

* It lets you create proxies to queue, forward, or capture messages with a single call. Proxies can reduce the interconnection complexity of a network.

* It delivers whole messages exactly as they were sent, using a simple framing on the wire. If you write a 10k message, you will receive a 10k message.

* It does not impose any format on messages. They are blobs of zero to gigabytes large. When you want to represent data you choose some other product on top, such as msgpack, Google's protocol buffers, and others.

* It handles network errors intelligently, by retrying automatically in cases where it makes sense.

* It reduces your carbon footprint. Doing more with less CPU means your boxes use less power, and you can keep your old boxes in use for longer. Al Gore would love 0MQ.

Actually 0MQ does rather more than this. It has a subversive effect on how you develop network-capable applications. Superficially, it's a socket-inspired API on which you do {{zmq_recv[3]}} and {{zmq_send[3]}}. But message processing rapidly becomes the central loop, and your application soon breaks down into a set of message processing tasks. It is elegant and natural. And it scales: each of these tasks maps to a node, and the nodes talk to each other across arbitrary transports. Two nodes in one process (node is a thread), two nodes on one box (node is a process), or two boxes on one network (node is a box)--it's all the same, with no application code changes.

++ Socket Scalability

Let's see 0MQ's scalability in action. Here is a shell script that starts the weather server and then a bunch of clients in parallel:

[[code]]
wuserver &
wuclient 12345 &
wuclient 23456 &
wuclient 34567 &
wuclient 45678 &
wuclient 56789 &
[[/code]]

As the clients run, we take a look at the active processes using the {{top}} command', and we see something like (on a 4-core box):

[[code]]
PID  USER  PR  NI  VIRT  RES  SHR S %CPU %MEM   TIME+  COMMAND
7136  ph   20   0 1040m 959m 1156 R  157 12.0 16:25.47 wuserver
7966  ph   20   0 98608 1804 1372 S   33  0.0  0:03.94 wuclient
7963  ph   20   0 33116 1748 1372 S   14  0.0  0:00.76 wuclient
7965  ph   20   0 33116 1784 1372 S    6  0.0  0:00.47 wuclient
7964  ph   20   0 33116 1788 1372 S    5  0.0  0:00.25 wuclient
7967  ph   20   0 33072 1740 1372 S    5  0.0  0:00.35 wuclient
[[/code]]

Let's think for a second about what is happening here. The weather server has a single socket, and yet here we have it sending data to five clients in parallel. We could have thousands of concurrent clients. The server application doesn't see them, doesn't talk to them directly. So the 0MQ socket is acting like a little server, silently accepting client requests and shoving data out to them as fast as the network can handle it. And it's a multithreaded server, squeezing more juice out of your CPU.

++ Upgrading from 0MQ v2.2 to 0MQ v3.2

+++ Compatible Changes

These changes don't impact existing application code directly:

* Pub-sub filtering is now done at the publisher side instead of subscriber side. This improves performance significantly in many pub-sub use cases. You can mix v3.2 and v2.1/v2.2 publishers and subscribers safely.

* 0MQ v3.2 has many new API methods ({{zmq_disconnect[3]}}, {{zmq_unbind[3]}}, {{zmq_monitor[3]}}, {{zmq_ctx_set[3]}}, etc.)

+++ Incompatible Changes

These are the main areas of impact on applications and language bindings:

* Changed send/recv methods: {{zmq_send[3]}} and {{zmq_recv[3]}} have a different, simpler interface, and the old functionality is now provided by {{zmq_msg_send[3]}} and {{zmq_msg_recv[3]}}. Symptom: compile errors. Solution: fix up your code.

* These two methods return positive values on success, and -1 on error. In v2.x they always returned zero on success. Symptom: apparent errors when things actually work fine. Solution: test strictly for return code = -1, not non-zero.

* {{zmq_poll[3]}} now waits for milliseconds, not microseconds. Symptom: application stops responding (in fact responds 1000 times slower). Solution: use the {{ZMQ_POLL_MSEC}} macro defined below, in all {{zmq_poll}} calls.

* {{ZMQ_NOBLOCK}} is now called {{ZMQ_DONTWAIT}}. Symptom: compile failures on the {{ZMQ_NOBLOCK}} macro.

* The {{ZMQ_HWM}} socket option is now broken into {{ZMQ_SNDHWM}} and {{ZMQ_RCVHWM}}.  Symptom: compile failures on the {{ZMQ_HWM}} macro.

* Most but not all {{zmq_getsockopt[3]}} options are now integer values. Symptom: runtime error returns on {{zmq_setsockopt}} and {{zmq_getsockopt}}.

* The {{ZMQ_SWAP}} option has been removed. Symptom: compile failures on {{ZMQ_SWAP}}. Solution: redesign any code that uses this functionality.

+++ Suggested Shim Macros

For applications that want to run on both v2.x and v3.2, such as language bindings, our advice is to emulate c3.2 as far as possible. Here are C macro definitions that help your C/C++ code to work across both versions (taken from [http://czmq.zeromq.org CZMQ]):

[[code type="fragment" name="upgrade-shim"]]
#ifndef ZMQ_DONTWAIT
#   define ZMQ_DONTWAIT     ZMQ_NOBLOCK
#endif
#if ZMQ_VERSION_MAJOR == 2
#   define zmq_msg_send(msg,sock,opt) zmq_send (sock, msg, opt)
#   define zmq_msg_recv(msg,sock,opt) zmq_recv (sock, msg, opt)
#   define zmq_ctx_destroy(context) zmq_term(context)
#   define ZMQ_POLL_MSEC    1000        //  zmq_poll is usec
#   define ZMQ_SNDHWM ZMQ_HWM
#   define ZMQ_RCVHWM ZMQ_HWM
#elif ZMQ_VERSION_MAJOR == 3
#   define ZMQ_POLL_MSEC    1           //  zmq_poll is msec
#endif
[[/code]]

++ Warning: Unstable Paradigms!

Traditional network programming is built on the general assumption that one socket talks to one connection, one peer. There are multicast protocols, but these are exotic. When we assume "one socket = one connection", we scale our architectures in certain ways. We create threads of logic where each thread work with one socket, one peer. We place intelligence and state in these threads.

In the 0MQ universe, sockets are doorways to fast little background communications engines that manage a whole set of connections automagically for you. You can't see, work with, open, close, or attach state to these connections. Whether you use blocking send or receive, or poll, all you can talk to is the socket, not the connections it manages for you. The connections are private and invisible, and this is the key to 0MQ's scalability.

This is because your code, talking to a socket, can then handle any number of connections across whatever network protocols are around, without change. A messaging pattern sitting in 0MQ scales more cheaply than a messaging pattern sitting in your application code.

So the general assumption no longer applies. As you read the code examples, your brain will try to map them to what you know. You will read "socket" and think "ah, that represents a connection to another node". That is wrong. You will read "thread" and your brain will again think, "ah, a thread represents a connection to another node", and again your brain will be wrong.

If you're reading this Guide for the first time, realize that until you actually write 0MQ code for a day or two (and maybe three or four days), you may feel confused, especially by how simple 0MQ makes things for you, and you may try to impose that general assumption on 0MQ, and it won't work. And then you will experience your moment of enlightenment and trust, that //zap-pow-kaboom// satori paradigm-shift moment when it all becomes clear.
