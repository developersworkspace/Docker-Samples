# Running Jenkins in a Docker Container

"The leading open source automation server, Jenkins provides hundreds of plugins to support building, deploying and automating any project." ~ Jenkins

## Getting Started

By running the following command you'll have a Jenkins instance running on port 8080 with a volume mounted to
'/jenkins' directory on the host machine.

`docker run -d -p 8080:8080 -p 50000:50000 -v /jenkins:/var/jenkins_home jenkins`

If you want to run Node commands in your Jenkins build you'll have to install Node along with the packages you require. This can be done by running the following commands which will install Node with a few npm packages such as mocha, typescript, gulp, istanbul and @angular/cli.

`git clone https://github.com/developersworkspace/Docker-Samples.git`

`cd Docker-Samples/Jenkins`

`docker run -d -p 8080:8080 -p 50000:50000 -v /jenkins:/var/jenkins_home ./`

## Troubleshooting

### Wrong volume permissions?

`sudo chmod -R 777 /jenkins`

The MIT License (MIT)
=====================

Copyright © `2017` `Barend Erasmus`

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the “Software”), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.