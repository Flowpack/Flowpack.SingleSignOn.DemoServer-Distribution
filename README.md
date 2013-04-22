# Quickstart

## DemoInstance:

* Run `./flow singlesignon:generatekeypair` to create a new OpenSSL key pair
* Add setting "Flowpack.SingleSignOn.Client.ssoServerEndpointUrl" with the URI of the SSO server endpoint (e.g. http://ssodemoserver.dev/sso/authentication)
* Add setting "Flowpack.SingleSignOn.Client.ssoClientKeyPairFingerprint" with the created fingerprint
* Add setting "Flowpack.SingleSignOn.Client.ssoClientIdentifier" with an identifier of the SSO client (has to match the client identifier on the SSO server)
* Export the public key of the client "./flow singlesignon:exportpublickey [fingerprint] > demoinstance.pub"

## DemoServer:

* Import the public key of the client "./flow security:importpublickey < ../DemoInstance/demoinstance.pub"
* Add a client with the given client identifier and key fingerprint: "./flow client:add demoinstance [fingerprint]"
* Generate key pair for server "./flow singlesignon:generatekeypair"
* Add setting "Flowpack.SingleSignOn.Server.ssoServerKeyPairFingerprint" with the fingerprint of the generated public key
* Export server public key: "./flow singlesignon:exportpublickey e1879766_2a5b_4d5d_b2b9_30918dd18ef9 > demoserver.pub"

## DemoInstance

* Import server public key: "/flow security:importpublickey < ../DemoServer/demoserver.pub"
* Add setting "Flowpack.SingleSignOn.Client.ssoServerPublicKeyFingerprint" with the imported key's fingerprint

License and Author
------------------
Copyright (c) 2013 Christopher Hlubek, Robert Lemke

Permission is hereby granted, free of charge, to any person obtaining a copy of this
software and associated documentation files (the "Software"), to deal in the
Software without restriction, including without limitation the rights to use, copy,
modify, merge, publish, distribute, sublicense, and/or sell copies of the Software,
and to permit persons to whom the Software is furnished to do so, subject to the
following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A
PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF
CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE
OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
