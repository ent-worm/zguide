.-  Instructions for mkwikidot
.set GIT=https://github.com/imatix/zguide
.set BRANCH=master
.output preface.wd

**By Pieter Hintjens, CEO of iMatix**

Please use the [$(GIT)/issues issue tracker] for all comments and errata. This version covers the latest stable release of 0MQ (3.2). If you are using older versions of 0MQ then some of the examples and explanations won't be accurate.

请使用[issue tracker](https://github.com/imatix/zguide/issues)来提交评论和勘误表。这一版覆盖了0MQ的最新稳定版本（3.2版本）。如果你还在使用旧版本的0MQ，那么本书中部分解释和示例可能是不准确的。

The Guide is originally [/page:all in C], but also in [/php:all PHP], [/py:all Python], [/lua:all Lua], and [/hx:all Haxe]. We've also translated most of the examples into C++, C#, CL, Delphi, Erlang, F#, Felix, Haskell, Java, Objective-C, Ruby, Ada, Basic, Clojure, Go, Haxe, Node.js, ooc, Perl, and Scala.

这本手册支持C语言，但同样也支持PHP，Python，Lua以及Haxe。我们同样将大部分示例都翻译成了C++，C#，CL，Delphi，Erlang，F#，Felix，Haskell，Java， Objective-C，Ruby，Ada，Basic，Clojure，Go，Haxe，Node.js，ooc，Perl以及Scala。

+ Preface
 
# 前言

++ 0MQ in a Hundred Words

## 0MQ百字箴言

0MQ (also known as ZeroMQ, 0\MQ, or zmq) looks like an embeddable networking library but acts like a concurrency framework. It gives you sockets that carry atomic messages across various transports like in-process, inter-process, TCP, and multicast. You can connect sockets N-to-N with patterns like fan-out, pub-sub, task distribution, and request-reply. It's fast enough to be the fabric for clustered products. Its asynchronous I/O model gives you scalable multicore applications, built as asynchronous message-processing tasks. It has a score of language APIs and runs on most operating systems. 0MQ is from [http://www.imatix.com iMatix] and is LGPLv3 open source.

0MQ（也被称作ZeroMQ，0\MQ或是zmq）看起来就像一个可嵌入的网络库，但它其实更像一个并发框架。它的套接字通过进程内部、进程间、TCP以及多播等传输层来传递原子信息。用扇入-扇出、发布-订阅、任务分发以及请求-应答等模式，套接字可以做到N到N的连接。它的速度足以支撑大型的集群服务。而用它的异步I/O模型构建出异步消息处理任务，给你的多核应用程序带来更多的扩展性。它有很多语言的API而且可以运行在绝大多数操作系统上。0MQ遵循LGPLv3开源许可。

++ How It Began

## 起源

We took a normal TCP socket, injected it with a mix of radioactive isotopes stolen from a secret Soviet atomic research project, bombarded it with 1950-era cosmic rays, and put it into the hands of a drug-addled comic book author with a badly-disguised fetish for bulging muscles clad in spandex[figure]. Yes, 0MQ sockets are the world-saving superheroes of the networking world.

我们将普通的TCP套接字，注入到从苏联机密原子研究项目中偷来的放射性同位素混剂，佐以50年代的宇宙射线轰击，将其交给一个乔装失败、塞着棉花肌肉还嗑多了药的漫画家。没错，0MQ套接字就是拯救网络世界的超级英雄！

[[code type="textdiagram" title="A terrible accident..."]]
.------------.        .--------------.
|            |        |              |
| TCP socket +------->|              | ZAP!
|            | BOOM!  |  0MQ socket  |
'------------'        |              |  POW!!
  ^    ^    ^         |              |
  |    |    |         '--------------'
  |    |    |
  |    |    |
  |    |    '--------- Spandex
  |    |
  |    '-------------- Cosmic rays

 Illegal radioisotopes from
 secret Soviet atomic city
[[/code]]

++ The Zen of Zero

## 0之禅

The Ø in 0MQ is all about tradeoffs. On the one hand this strange name lowers 0MQ's visibility on Google and Twitter. On the other hand it annoys the heck out of some Danish folk who write us things like "ØMG røtfl", and "Ø is not a funny looking zero!" and "//Rødgrød med Fløde!//", which is apparently an insult that means "may your neighbours be the direct descendants of Grendel!"  Seems like a fair trade.

0MQ中的Ø其实指是开销。一方面这个怪异的名字不太会吸引Google或Twitter的注意力。另一方面惹到了写“ØMG røtfl”（译者注：Oh my God和Rolling on the floor laugh）、“Ø可不是看起来搞笑的0！”或“*Rødgrød med Fløde!*”（译者注：丹麦的一种甜食）的丹麦人，因为这好像跟“你家邻居会不会都是戈兰德尔的后代”一样有点侮辱人。

Originally the zero in 0MQ was meant as "zero broker" and (as close to) "zero latency" (as possible). Since then, it has come to encompass different goals: zero administration, zero cost, zero waste. More generally, "zero" refers to the culture of minimalism that permeates the project. We add power by removing complexity rather than by exposing new functionality.

0MQ的0其实是表示无需中间件以及（几乎）零延迟。既然如此，这就包括几个不同的目标：无需管理、零消耗以及零浪费。更简单的说，“0”意指该项目中最深入人心的最小化文化。我们是靠去除复杂性而非增强功能，借以提高其能力。

++ Audience

This book is written for professional programmers who want to learn how to make the massively distributed software that will dominate the future of computing. We assume you can read C code, because most of the examples here are in C even though 0MQ is used in many languages. We assume you care about scale, because 0MQ solves that problem above all others. We assume you need the best possible results with the least possible cost, because otherwise you won't appreciate the trade-offs that 0MQ makes. Other than that basic background, we try to present all the concepts in networking and distributed computing you will need to use 0MQ.

## 目标读者

这本书是写给那些希望学习完成大规模分布式软件（主宰未来计算世界）的高级程序员。我们假设你读得懂C代码，因为虽然各种语言都能用0MQ，但是本书中的示例都是C语言的。我们同样假设你关心扩展性，因为0MQ比其他项目更早的解决了这个问题。我们还假设你希望用最小的代价获得尽可能好的结果，否则你可能不太会欣赏0MQ所做的折衷。除了基本背景外，我们还试图将使用0MQ会碰到的网络和分布式计算的概念展现给你。

++ Acknowledgements

## 致谢

Thanks to Andy Oram for making [http://shop.oreilly.com/product/0636920026136.do the O'Reilly book] happen, and editing this text.

感谢Andy Oram编辑、出版了[这本O'Reilly的书](http://shop.oreilly.com/product/0636920026136.do)。

Thanks to Bill Desmarais, Brian Dorsey, Daniel Lin, Eric Desgranges, Gonzalo Diethelm, Guido Goldstein, Hunter Ford, Kamil Shakirov, Martin Sustrik, Mike Castleman, Naveen Chawla, Nicola Peduzzi, Oliver Smith, Olivier Chamoux, Peter Alexander, Pierre Rouleau, Randy Dryburgh, John Unwin, Alex Thomas, Mihail Minkov, Jeremy Avnet, Michael Compton, Kamil Kisiel, Mark Kharitonov, Guillaume Aubert, Ian Barber, Mike Sheridan, Faruk Akgul, Oleg Sidorov, Lev Givon, Allister MacLeod, Alexander D'Archangel, Andreas Hoelzlwimmer, Han Holl, Robert G. Jakabosky, Felipe Cruz, Marcus McCurdy, Mikhail Kulemin, Dr. Gergő Érdi, Pavel Zhukov, Alexander Else, Giovanni Ruggiero, Rick "Technoweenie", Daniel Lundin, Dave Hoover, Simon Jefford, Benjamin Peterson, Justin Case, Devon Weller, Richard Smith, Alexander Morland, Wadim Grasza, Michael Jakl, Uwe Dauernheim, Sebastian Nowicki, Simone Deponti, Aaron Raddon, Dan Colish, Markus Schirp, Benoit Larroque, Jonathan Palardy, Isaiah Peng, Arkadiusz Orzechowski, Umut Aydin, Matthew Horsfall, Jeremy W. Sherman, Eric Pugh, Tyler Sellon, John E. Vincent, Pavel Mitin, Min RK, Igor Wiedler, Olof Åkesson, Patrick Lucas, Heow Goodman, Senthil Palanisami, John Gallagher, Tomas Roos, Stephen McQuay, Erik Allik, Arnaud Cogoluègnes, Rob Gagnon, Dan Williams, Edward Smith, James Tucker, Kristian Kristensen, Vadim Shalts, Martin Trojer, Tom van Leeuwen, Hiten Pandya, Harm Aarts, Marc Harter, Iskren Ivov Chernev, Jay Han, Sonia Hamilton, Nathan Stocks, Naveen Palli, and Zed Shaw for their contributions to this work.

感谢Bill Desmarais, Brian Dorsey, Daniel Lin, Eric Desgranges, Gonzalo Diethelm, Guido Goldstein, Hunter Ford, Kamil Shakirov, Martin Sustrik, Mike Castleman, Naveen Chawla, Nicola Peduzzi, Oliver Smith, Olivier Chamoux, Peter Alexander, Pierre Rouleau, Randy Dryburgh, John Unwin, Alex Thomas, Mihail Minkov, Jeremy Avnet, Michael Compton, Kamil Kisiel, Mark Kharitonov, Guillaume Aubert, Ian Barber, Mike Sheridan, Faruk Akgul, Oleg Sidorov, Lev Givon, Allister MacLeod, Alexander D'Archangel, Andreas Hoelzlwimmer, Han Holl, Robert G. Jakabosky, Felipe Cruz, Marcus McCurdy, Mikhail Kulemin, Dr. Gergő Érdi, Pavel Zhukov, Alexander Else, Giovanni Ruggiero, Rick "Technoweenie", Daniel Lundin, Dave Hoover, Simon Jefford, Benjamin Peterson, Justin Case, Devon Weller, Richard Smith, Alexander Morland, Wadim Grasza, Michael Jakl, Uwe Dauernheim, Sebastian Nowicki, Simone Deponti, Aaron Raddon, Dan Colish, Markus Schirp, Benoit Larroque, Jonathan Palardy, Isaiah Peng, Arkadiusz Orzechowski, Umut Aydin, Matthew Horsfall, Jeremy W. Sherman, Eric Pugh, Tyler Sellon, John E. Vincent, Pavel Mitin, Min RK, Igor Wiedler, Olof Åkesson, Patrick Lucas, Heow Goodman, Senthil Palanisami, John Gallagher, Tomas Roos, Stephen McQuay, Erik Allik, Arnaud Cogoluègnes, Rob Gagnon, Dan Williams, Edward Smith, James Tucker, Kristian Kristensen, Vadim Shalts, Martin Trojer, Tom van Leeuwen, Hiten Pandya, Harm Aarts, Marc Harter, Iskren Ivov Chernev, Jay Han, Sonia Hamilton, Nathan Stocks, Naveen Palli, 以及Zed Shaw为本书作出的贡献。
