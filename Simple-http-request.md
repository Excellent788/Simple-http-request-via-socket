```markdown
# Simple HTTP Request via Socket

This Python script allows you to make a basic HTTP request to a specified webpage using a socket connection. The script prompts you to enter the URL of the webpage you want to receive and then sends a GET request to that URL.

## Code

```python
import socket

url = input('Enter the URL of the webpage you want to receive')

if not url.startswith('http://'):
    url = 'http://' + url
    
host = url.split('/')[2]
path = '/' + '/'.join(url.split('/')[3:])

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((host, 80))

request = f'GET {path} HTTP/1.1\r\nHost: {host}\r\n\r\n'
s.send(request.encode())

response = s.recv(4097)
decoded_response = response.decode()

try:
    print(decoded_response)
except:
    pass
```

## How It Works

1. **Input URL**: The script starts by asking you to enter the URL of the webpage you want to receive. If the URL does not start with `http://`, it automatically adds it.
2. **Parse URL**: The script then parses the URL to extract the host and path.
3. **Create Socket**: A socket is created using the `socket` library.
4. **Connect to Host**: The socket connects to the host on port 80 (standard port for HTTP).
5. **Send Request**: The script constructs an HTTP GET request and sends it to the server.
6. **Receive Response**: The response from the server is received and decoded.
7. **Output Response**: Finally, the script prints the decoded response.

This script provides a basic understanding of how HTTP requests can be made using sockets in Python.

## Usage

To run this script, follow these steps:

1. Ensure you have Python installed on your system.
2. Copy the code into a Python file (e.g., `http_request.py`).
3. Open a terminal or command prompt.
4. Navigate to the directory containing the script.
5. Run the script using the command: `python http_request.py`.
6. Enter the URL of the webpage you want to receive when prompted.

## Example

```
Enter the URL of the webpage you want to receive: example.com
```

The script will output the response from the server.

## License

This project is licensed under the MIT License.
```
