# Heroku-Deployment for java webapp
### Đây là bài viết hướng dẫn deploy website lên trên heroku host.
**Đầu tiên** thì chúng ta cần tạo tài khoản trên heroku và tải heroku CLI
![image](https://user-images.githubusercontent.com/85113374/131202102-4bda4c14-7b1d-4a62-a151-6578421cc133.png)

Đây là giao diện sign up của web heroku

Sau đó thì chúng ta tạo **file war** của dự án web. Bây giờ chúng ta sẽ tiến tới phần hay ho, đó là sử dụng heroku CLI để tạo app và deploy project.

***Sau khi đã có file war thì chúng ta sẽ mở terminal/command line lên và gõ:***

`heroku login -i`

Đây là lệnh để login vào heroku thông qua terminal mà không phải vào qua browser, mọi người có thể google để tìm hiểu thêm.

***Sau đó ta tạo một app trên heroku bằng lệnh:***

`heroku create app-name`

câu lệnh trên sẽ tạo ra một app có tên là app-name app name sẽ là tên app của bạn, bạn có thể đặt bất kì tên nào mà bạn muốn miễn là tuân theo quy tắt đặt tên của heroku đó là: không viết hoa, không kí tự đặt biệt và các từ ngăn cách nhau bởi dấu "-"

**Sau khi đã có app chúng ta có thể check lại với lệnh:**

`heroku apps`

Lệnh này sẽ hiện thị danh sách những app đang có trên heroku của bạn.

**Sau khi đã double check thì sẽ đến bước deploy:**

`heroku plugins:install java`

Đây là câu lệnh sẽ cài đặt java trên hosting của heroku. Mặc định thì host của heroku sẽ là java bản là java 6 nên nếu cần chọn phiên bản thì các bạn lưu ý làm theo hướng dẫn này, ở đây thì mình sẽ chỉ nói bằng cách deploy native thôi còn những thứ khác sẽ để các bạn tự tìm hiểu thêm

[Heroku java]https://devcenter.heroku.com/articles/java-support#supported-java-versions

***Tiếp theo, ta sẽ deploy war file lên trên heroku:***

`heroku war:deploy <Direct path to war file> --app app-name`

<Direct path to war file> (Đường dẫn tới war file) thường sẽ là thư mục target của dự án, các bạn copy đường dẫn đó và bỏ vào đây
Đây là kết quả sau khi gõ lệnh trên:
 
```
 8.5.57/webapps/App/ShoppingCart.war --app shoppingcartjava
 
 ›   Warning: heroku update available from 7.35.1 to 7.42.4.
 
Uploading ShoppingCart.war
 
-----> Packaging application...
 
       - app: shoppingcartjava
 
       - including: webapp-runner.jar
 
       - including: ShoppingCart.war
 
-----> Creating build...
 
       - file: slug.tgz
 
       - size: 21MB
 
-----> Uploading build...
 
       - success
 
-----> Deploying...
 
remote: 
 
remote: -----> heroku-deploy app detected
 
remote: -----> Installing JDK 1.8... done
 
remote: -----> Discovering process types
 
remote:        Procfile declares types -> web
 
remote: 
 
remote: -----> Compressing...
 
remote:        Done: 72.3M
 
remote: -----> Launching...
 
remote:        Released v3
 
remote:        https://shoppingcartjava.herokuapp.com/ deployed to Heroku
 
remote: 
 
-----> Done
```
 
`heroku open --app app-name`
 
 Đây là câu lệnh dùng để mở app và hưởng thụ kết quả. Vậy là chúng ta đã deploy xong một webapp java lên heroku rồi. Ngoài ra thì phiên bản tomcat/java sẽ cần phải chỉnh lại theo ý muốn của chúng ta. Đây là link để tìm hiểu thêm về vấn đề đó:
 
 [tomcat heroku]https://devcenter.heroku.com/articles/configuring-war-deployment-with-the-heroku-toolbelt
