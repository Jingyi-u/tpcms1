# tpcms1
https://gitee.com/happy_source/tpcms/releases/tag/v6.0.0

nginx conf:

server {
    listen      80;
    server_name localhost 127.0.0.1;
    index index.php index.html;
    root /var/www/html/public;
    client_max_body_size 100m;

    # 伪静态支持
    location / {
        try_files $uri $uri/ @rewrite;
    }

    location @rewrite {
        # 此处的rewrite规则将URL重写为index.php的查询字符串
        # 例如: /some-controller/some-action 将被重写为 /index.php?s=some-controller/some-action
        rewrite ^/(.*)$ /index.php?s=/$1 last;
    }


    location ~ \.php($|/) {
        fastcgi_pass   127.0.0.1:9000; # PHP-FPM 监听地址和端口
        fastcgi_index  index.php;
        include        fastcgi_params; # 包含fastcgi的参数设置
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_param  PATH_INFO       $fastcgi_path_info;
        fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
}

<img width="965" alt="image" src="https://github.com/user-attachments/assets/a4554984-4e85-41e8-8b8c-71fefca92131">
<script>alert(1)</script>
<img width="1133" alt="image" src="https://github.com/user-attachments/assets/beb4d71a-4777-4f01-9a60-b9874aa84552">
<img width="896" alt="image" src="https://github.com/user-attachments/assets/2020156a-caf2-4015-8c9a-657fad59fd87">

xss vuln
