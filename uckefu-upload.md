# uckefu-upload

**Youkefu** used improper path concatenation in `WebIMController.java` and failed to perform proper file type validation for uploaded files, leading to an **Arbitrary File Upload** vulnerability.

path：/admin/webim/save.html

The filename was directly constructed by concatenating `"logo/"` with the `id` and other attributes.

![image-20250407100301180](img/image-20250407100301180.png)

Function point:

![image-20250407101118972](img/image-20250407101118972.png)

Target file(source file):

![image-20250407101237860](img/image-20250407101237860.png)

Modify the file type and content in the request packet.

![image-20250407101507039](img/image-20250407101507039.png)

Inject a malicious value into the `id` attribute.

![image-20250407101521799](img/image-20250407101521799.png)

Debugging revealed that the `id` value was successfully assigned.

![image-20250407101559404](img/image-20250407101559404.png)

Successfully overwrote the target file.

![image-20250407101626027](img/image-20250407101626027.png)

This vulnerability can be exploited to overwrite sensitive files such as crontab and SSH configurations for further attacks.
