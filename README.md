# Token Authentication Example Code

Example implementations of MD5 based hash authentication for client requests on [BelugaCDN.com](https://www.belugacdn.com/).

Once `Token Authentication` has been enabled client requests require a "hash" as part of the URL. The hash is computed based on the requested URL and a secret key.

Example of a request without a hash:

```
curl -I 'http://test.belugacdn.com/test-video.mp4'  
HTTP/1.1 403 Forbidden  
```

Generate the hash of the requested URL using the provided PHP or Python example:

```
> php md5-authentication.php http://test.belugacdn.com/test-video.mp4
http://test.belugacdn.com/test-video.mp4?expires=1425631400&token=5a8a5f4576ce8878c27747d844321a5a
> python md5-authentication.py http://test.belugacdn.com/test-video.mp4
http://test.belugacdn.com/test-video.mp4?expires=1425631400&token=5a8a5f4576ce8878c27747d844321a5a
```

Example of a valid request:

```
> curl -I 'http://test.belugacdn.com/test-video.mp4?expires=1425631400&token=5a8a5f4576ce8878c27747d844321a5a'
HTTP/1.1 200 OK
```
