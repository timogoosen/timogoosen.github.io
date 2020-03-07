## Allow Stuff

If SELinux blocks incoming HTTP Requests
* [PHP Curl to Localhost Returns Permissions Denied on Open Port](https://stackoverflow.com/questions/46672070/php-curl-to-localhost-returns-permission-denied-on-an-open-port)

```
# setsebool httpd_can_network_connect 1 -P

```
