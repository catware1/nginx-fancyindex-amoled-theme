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
        root /var/www/files-unavail; # это я высрал на случай если шара по NFS. отдельный index.html который
                                     # намекнёт пользователю что тут вроде бы как должны лежать файлы
                                     # и при этом сервер NFS оказался недоступен. 
        internal;
    }

    location / {
        try_files $uri $uri/ =404;
        fancyindex on;
        fancyindex_localtime on;
        fancyindex_exact_size off;
        fancyindex_header "/nginx-fancyindex-amoled-theme/header.html";
        fancyindex_footer "/nginx-fancyindex-amoled-theme/footer.html";
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
# тутор для самых маленьких
```
1) качаем нужные пакеты (это для Debian, остальные ищите сами)

sudo apt install libnginx-mod-http-fancyindex

2) вписывай конфиг выше, подредактировав его на свой вкус.
параметр fancyindex_ignore скрывает определенный каталог
из общего списка (в вебе) (но не убирает способа достучаться
до него - идеально чтобы прятать какие то мелочные файлы или папки,
которые не должны мозолить глазки)
```

# УВАГА (внимание)

короче, там дохуя чего осталось ещё от меня, так что поправьте header.html, footer.html и styles.css на свой вкус, не будьте чушпанами

СПАСИБО ЗА ВНИМАНИЕ

![cat nihuia sebe](https://files.underbed.ru/CDN/cat.gif)
