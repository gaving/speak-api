# Espeak-based serverless API for IPA transcriptions

An API for requesting [espeak](http://espeak.sourceforge.net/) IPA
transcriptions.

## Build

 * Log into a Amazon Linux machine (e.g. an EC2 instance)
 * Install dev packages: `sudo yum groupinstall "Development Tools"`
 * Download the source from http://espeak.sourceforge.net
 * Unzip and switch to the `src` directory
 * In the file `src/speech.h`, comment out the line `#define USE_PORTAUDIO`
 * In `src/Makefile`, set the `AUDIO` variable to `sada`
 * Run `make speak`

## Usage

```
~/Sandbox/speak-api% http https://qobmuykvqg.execute-api.eu-west-1.amazonaws.com/dev/ipa -- text="happy" language=en                                                                          ツ  18:32
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Connection: keep-alive
Content-Length: 33
Content-Type: application/json
Date: Mon, 06 Nov 2017 18:32:33 GMT
Via: 1.1 2a3894d93a2a1e3b94fb6ed07542ad37.cloudfront.net (CloudFront)
X-Amz-Cf-Id: ANFWIPyzCcXwcmkGn6E1bl8vRp3HzWpRpu-vho-KcXCgk3pfYP4ZbA==
X-Amzn-Trace-Id: sampled=0;root=1-5a00aac0-fc84fff15e76f8639094ef06
X-Cache: Miss from cloudfront
x-amzn-RequestId: da4c69c4-c320-11e7-a062-432e04318018

{
    "language": "en",
    "text": "hˈapi"
}
```
