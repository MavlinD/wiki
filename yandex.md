### [справка](https://yandex.ru/dev/disk/api/concepts/about.html)  
### [полигон (можно отправлять реальные запросы)](https://yandex.ru/dev/disk/poligon/)  

```shell
# запрос списока файлов на диске в папке приложения
http https://cloud-api.yandex.net/v1/disk/resources?path=app:/ 'Authorization: OAuth <token>'
```
```shell
# пример запроса на загрузку файла по ссылке, ссылка действует 30 мин, авторизация не требуется  
http https://cloud-api.yandex.net/v1/disk/resources/upload  'Authorization: OAuth <token>' path==app:/test.txt
# загрузка файла
cat /home/mdv/test.txt | http  --follow --timeout 3600 PUT 'https://uploader60j.disk.yandex.net:443/upload-target/20220728T145015.080.utd.5fats6xsuej0oz98t5hjrfo9k-k60j.5598813' \
 Content-Type:'text/plain'
```
```shell
# запрос ссылки на скачивание файла
http --follow --timeout 3600 GET 'https://cloud-api.yandex.net/v1/disk/resources/download?path=1C/Договоры.json' Authorization:'OAuth <token>'
 ```
```shell
# скачивание файла
http --follow --timeout 3600 GET 'https://downloader.disk.yandex.ru/disk/1dd1bb015b9b267d4fe25ff010cfc5ab49c250046154d37143b5ee819c35ea8b/62e3eea7/ltuYM8UcpLyR_DCPaQbFgzCUQ14m8HRd6Gz4qdl_oKGUT4itWAwNpPV5sri1-BndGOy4SlsY_A52kG0DiR4sMw%3D%3D?uid=160428047&filename=%D0%94%D0%BE%D0%B3%D0%BE%D0%B2%D0%BE%D1%80%D1%8B.json&disposition=attachment&hash=&limit=0&content_type=text%2Fplain&owner_uid=160428047&fsize=3068&hid=9ec61d06c0c3dfb02e2c57ba4167f959&media_type=text&tknv=v2&etag=80549e9b9f0286589738d61792f4b351' \
 Cookie:'yandexuid=267232951658151080'
```

Примечание: 
* Токен доступа предоставляется макробанком.
* В примерах использован консольный HTTP клиент [httpie](https://httpie.io/docs/cli), обычно его нужно установить дополнительно.  
