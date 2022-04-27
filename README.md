# DAP

## What is DAP?

DAP (Dedicated application protocol) is an bianry application protocol designed for common-purpose data exchange without using HTTP protocol, which is originally designed only for hypertext transmission. DAP is working over TCP/IP and use simple request-response model for communication.

## Why should you need to use DAP?

- **It's compact.** Because of DAP is a binary protocol it doesn't use any redundant data, that can be human-readable, but useless for machines
- **It's stupid simple.** You only need to specify authentication token (optional), procedure ID and you payload, and in response you will get result code and payload from server
- **It's extensible.** in payload you can provide some additional information, such as headers, payload encoding, and other useful information, and then add support of this protocol extension to your library.

## Protocol description

### Request

First two bytes are used to specify length of authentication token. Then goes the token itself. After token there is one byte that used from procedure id (you can mind that this is something like URI). All other bytes must be considered to be payload.

### Response

First byte is a result code. Currently we suppose, that any non-zero code means error, and zero means success. All other bytes must be considered to be payload.
