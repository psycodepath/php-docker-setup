# my php docker setup

### About
This is my initial docker development setup for php applications. 
This project is just meant to be as a boilerplate, and it is definitely not
production ready.

This project is run on a Windows 10 machine inside a WSL2 ubuntu 20.04 LTS 
version. 

### How to: 
_Make SSL work_: 
Use [mkcert](https://github.com/FiloSottile/mkcert) to generate your ssl certs. 
If you are using windows + wsl2 as well, you first need to install (or download) 
mkcert on windows and run ```mkcert --install.``` After the root CA's are created you 
can have a look where  the root certificates are installed with ```mkcert -CÀROOT ```. 
(You will need to copy those in the next step inside your WSL 2 installation). 

Install  [mkcert](https://github.com/FiloSottile/mkcert) inside your WSL2 instance 
as well (you can but do not have to use the linux brew method). 
Run the ```mkcert --install``` command here as well and after the root ca's 
are created here as well, you will check the installation path 
with ```mkcert -CAROOT``` as well and delete those (but keep the folder). 

Copy your windows CA's over inside the linux CA folder, and you are ready to 
create trusted certificates for your local machine. In this example project 
the following command is used to create the necessary certificates 
```mkcert localhost 127.0.0.1 ::1 ``` which creates the certificates needed for my 
local development needs. You can add one more host domains by simply adding them 
afterwards. The ssl certificates should be placed inside the ./docker/nginx/ folder. 

__FYI:__ if you run another mkcert command as the one mentioned above, you probably
need to change the ./docker/nginx/nginx.conf and the ./docker-compose.yml because the
name of the certificates might have changed


### License

Copyright 2021 Steffen Frosch

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.