# nginx-fancyindex-amoled-theme
модифицированная версия https://github.com/Naereen/Nginx-Fancyindex-Theme

# нахуя?
мне просто не сильно нравится ее темная версия, поэтому я решил выложить свою пиздатую версию.

Демонстрация: 

![52.145621 61.512345 под газовой трубой](https://files.underbed.ru/CDN/files_demo.png)

ссылка внизу на гитхаб если че ведет на оригинальное детище автора (Naereen/Nginx-Fancyindex-Theme)

# как присобачить эту хуйню к вашему ебейшему серверу

```
server {

    # SSL configuration

    # ...

    root /бла/бла/бла/нахуй;
    server_name files.zalupa.xyu;

    error_page 404 /404.html;
    location = /404.html {
        root /var/www/files-unavail;
        internal;
    }

    location / {
        try_files $uri $uri/ =404;
        fancyindex on;
        fancyindex_localtime on;
        fancyindex_exact_size off;
        fancyindex_header "/Nginx-Fancyindex-Theme-dark/header.html";
        fancyindex_footer "/Nginx-Fancyindex-Theme-dark/footer.html";
        fancyindex_ignore "hidden";
        fancyindex_ignore "Анапа 2007";
        fancyindex_ignore "Домашняя работа";
        fancyindex_ignore "гей порно";
        fancyindex_ignore "Nginx-Fancyindex-Theme-dark";
        fancyindex_ignore "HEADER.md";
        fancyindex_ignore "README.md";
        fancyindex_name_length 255;
    }
}

```
