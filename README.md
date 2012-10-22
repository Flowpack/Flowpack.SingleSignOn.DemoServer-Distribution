# Quickstart

## DemoInstance:

* Run `./flow singlesignon:generatekeypair` to create a new OpenSSL key pair
* Add setting "TYPO3.SingleSignOn.Client.ssoClientKeyPairUuid" with the created UUID
* Add setting "TYPO3.SingleSignOn.Client.ssoClientIdentifier" with an identifier of the SSO client (has to match the client identifier on the SSO server)
* Export the public key of the client "./flow singlesignon:exportpublickey [uuid] > demoinstance.pub"

## DemoServer:

* Import the public key of the client "./flow security:importpublickey < ../DemoInstance/demoinstance.pub"
* Add a client with the given client identifier and uuid: "./flow client:add demoinstance [uuid]"
