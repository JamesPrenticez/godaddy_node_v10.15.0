# godaddy_node_v10.15.0

https://stackoverflow.com/questions/40146067/i-have-godaddy-shared-web-hosting-i-need-to-host-node-js-website-can-host-site

Go to goDaddy and and reset you server and enable ssh
Host: 127.0.0.1
User: abc123
Pass: password

Download node V10.15.0 - https://nodejs.org/dist/v10.15.0/node-v10.15.0-linux-x64.tar.xz

Extract to your computer and navigate to bin/ and copy the node file to your desktop.

Windows 10 - Download PuTTy - https://www.putty.org/

Log in to Putty

Check the server in running linux 64bit with:
uname -a

cd ~
mkdir bin

Go to GoDaddy CPannel Admin Panel and find the File Manager

Upload the node file into the bin folder

cd ~
touch .htaccess
nano .htacess

Paste this:
`RewriteEngine on RewriteRule (.*) http://localhost:3000/$1 [P,L]`

CTR + X > save

Navigate to public_html/ in the file manager

Create app.js and paste:
`const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
res.statusCode = 200;
res.setHeader('Content-Type', 'text/plain');
res.end('NodeJS server running on Shared Hosting\n');
});

server.listen(port, hostname, () => {
console.log('Server running at http://${hostname}:${port}/');
});`
