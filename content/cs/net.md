---
title: "Application layer"
date: 2023-07-01T09:31:32+08:00
---

## 1. Application layer

### 1.1 HTTP

The format of the http request message

The first line is the request line
```shell
<HTTP method> url <HTTP version>
```

The following lines are header lines, like

```shell
Host: www.baidu.com
```

The format of the http response message

The first line is the status line

```shell
HTTP/1.1 200 OK
```

The following lines are header lines, in these lines, user will be informed
the Connection is closed and the server...etc

## 2. Transport layer

Demultiplexing takes data from different socket from the source server.

Multiplexing takes data with header lines to generate the message.

### 2.1 UDP
UDP add a little things to the ip, like the source port and the destination port.

The message of udp looks like this.

```shell
|source port | destination port|
|len         | checksum        |
the real data
```

You can examine the message of udp by checksum but you can not recover it.

### 2.2 TCP

The get back N

In the GBN protocol, it allows the senders to send multiple packets.

```shell
|the packets have been ack|base| the packets have been send but not ack |nextseqnum| wait to send |
```

When the windows is full, it will not send any packets. What's more, the GBN use the 
cumulative acknowledge to store the ack.

When the timeout, the gbn will send all the packets it send but not ack.

Select Retransmission

The SR will only send packets that are timeout.

The form of the tcp message.

```shell
|source port|dest port|
|       The seq       |
|     The ACK num     |
```

## 3. NetWork Layer

### 3.1 Forward and routing

According to the head of the packet, it can be forward to other device.


### 3.2 IPV4

IPV4 is called the data packet.

The keyword in the ipv4 are as followings.

- version:the version of the ipv4
- length:the length of the packet
- services type:
- ttl: time to live
- protocol: when the packet arrived at the destination it will work.
- checksum: check the error
- source address
- target address
- data

As the ipv4 decode. 

It is called the dotled・decimal notation, the net address netmask means the length of the left part of the ip.

### 3.3 Change of net address.

Using the nat to translate the address.

### 3.4 The ipv6

```shell
|   version |   type of stream   |   tag of stream     |
|   payload length | the next header | the jump limit  |

```