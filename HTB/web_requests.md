# Web Requests

# HTTP

HyperText Transfer Protocol (HTTP) is an application-level protcol used to access the World Wide Web Resources.

Default Port **80**

## URL

Resources are access through `URL`

| Component | Example         | Description                                                                                                                                                                   |
| --------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Scheme    | Http            | This is used to identify the protocol being accessed by the client, and ends with a colon and a double slash (`://`)                                                          |
| User Info | admin:password@ | This is an optional component that contains the credentials (separated by a colon `:`) used to authenticate to the host, and is separated from the host with an at sign (`@`) |
| Host      | google.com      | The host signifies the resource location. This can be a hostname or an IP address                                                                                             |
| Port      | 80              | The Port is separated from the Host by a colon (`:`). If no port is specified, http schemes default to port `80` and https default to port `443`                              |
| Path      | /dashboard.php  | This points to the resource being accessed, which can be a file or a folder. If there is no path specified, the server returns the default index (e.g. index.html).           |
| Query     | ?login=true     | The query string starts with a question mark (?), and consists of a parameter (e.g. login) and a value (e.g. true). Multiple parameters can be separated by an ampersand (&). |
| Fragments | #status         | Fragments are processed by the browsers on the client-side to locate sections within the primary resource (e.g. a header or section on the page).                             |

## HTTP Flow

- DNS Resolution
- GET to the port (default `80`)
- In this case, the contents of index.html are read and returned by the web server as an HTTP response. The response also contains the status code (e.g. 200 OK)

## Curl

[cURL](https://curl.se/) (client URL) is a command-line tool and library that primarily supports HTTP

```sh
1fxe@htb[/htb]$ curl -h
Usage: curl [options...] <url>
 -d, --data <data>   HTTP POST data
 -h, --help <category> Get help for commands
 -i, --include       Include protocol response headers in the output
 -o, --output <file> Write to file instead of stdout
 -O, --remote-name   Write output to a file named as the remote file
 -s, --silent        Silent mode
 -u, --user <user:password> Server user and password
 -A, --user-agent <name> Send User-Agent <name> to server
 -v, --verbose       Make the operation more talkative

This is not the full help, this menu is stripped into categories.
Use "--help category" to get an overview of all categories.
Use the user manual `man curl` or the "--help all" flag for all options.
```

# HTTPS

Data transffered is encrypted

The client (web browser) sends a "client hello" packet, giving information about itself. After this, the server replies with "server hello", followed by a key exchange to exchange SSL certificates. The client verifies the key/certificate and sends one of its own. After this, an encrypted handshake is initiated to confirm whether the encryption and transfer are working correctly.

Once the handshake completes successfully, normal HTTP communication is continued, which is encrypted after that.

# HTTP Requests and Responses

