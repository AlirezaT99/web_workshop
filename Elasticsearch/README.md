<div dir="rtl">

## Elasticsearch

<p align=center><img width=300 src="./assets/Elastic_logo_main.png" /></p>

### 📝فهرست
  - مقدمه
  - معرفی Elastic Stack (ELK)
  - توزیع‌شدگی و مقیاس‌پذیری
  - نگاشت پویا (Dynamic mapping)
  - امکانات نرمال‌سازی
  - امکان ذخیره‌ی انواع مختلف داده‌ها
  - امکانات جستجوی پیشرفته
  - معرفی اصطلاحات
  - نصب و راه‌اندازی
  - بارگذاری اسناد
  - انواع مختلف داده
  - انواع و اقسام مختلف جستجو
  - ابزارهای آنالیز متن
  - پرسش‌های تجمیعی
  - آشنایی با bulk
  

### ✍️نویسندگان
  - [علیرضا تاجمیرریاحی](https://github.com/AlirezaT99)
  - [سپهر صفری](https://github.com/sepehrs1378)
  - [پرهام صارمی](https://github.com/parhamsaremi)
<hr>

## مقدمه

## ...

<p align=center><img width=600 src="./assets/elasticsearch-logo.png" /></p>

## نصب و راه‌اندازی
در این بخش به بررسی نحوه‌ی راه‌اندازی elasticsearchو kibana خواهیم پرداخت.
<br>
ابتدا از
[اینجا](https://www.elastic.co/downloads/elasticsearch)
و
[اینجا](https://www.elastic.co/downloads/kibana)
الستیک‌سرچ و کیبانا را نصب کنید. (یا از طریق apt و yum)
<br>
حال با اجرای
`bin/elasticsearch`
(یا `bin\elasticsearch.bat` در ویندوز) الستیک‌سرچ را اجرا کنید.
<br>
همچنین با اجرای
`bin/kibana`
(یا `bin\kibana.bat` در ویندوز) کیبانا اجرا می‌شود.
> تجربه: اگر روی ویندوز هستید بررسی کنید اسم فولدر حاوی فایل‌ها دارای اسپیس نباشد :|
<br>
الستیک‌سرچ بطور پیش‌فرض روی پورت 9200 اجرا می‌شود و با استفاده از

<div dir="ltr">
  
  ```bash
  curl http://localhost:9200/
  ```
</div>
می‌توانید از اجرا شدن آن مطمئن شوید.
<br>
همچنین kibana بطور پیش‌فرض روی پورت 5601 اجرا می‌شود و با رفتن به
http://localhost:5601
با صفحه‌ی زیر مواجه خواهید شد:
<br>
<p align=center><img src="./assets/kibana-homepage.png" /></p>
<br>
اکنون می‌توانید از منوی سمت چپ صفحه در قسمت management وارد Dev Tools شوید. محیط Dev Tools مطابق عکس زیر می باشد:
<br>
<p align=center><img src="./assets/devtools.png" /></p>

## بارگذاری اسناد
اکنون در Dev Tools با اجرای درخواست زیر می‌توانیم اولین index خود را بسازیم.
<br>
(ساختن index می‌تواند دارای تنظیماتی مانند مشخص کردن mapping  باشد که در
[این لینک](https://www.elastic.co/guide/en/elasticsearch/reference/current/indices-create-index.html)
به آن بیشتر پرداخته شده. همچنین اسم index باید ویژگی‌هایی مانند lowercase بودن یا نداشتن کاراکترهای ویژه دارد که مطالعه‌ی همین لینک می‌تواند برای آن مفید باشد).

<div dir="ltr">
 
```http
PUT /sample-posts
```
</div>
خروجی:

<div dir="ltr">
 
```json
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "sample-posts"
}
```
</div>
حال می‌توانیم اولین داکیومنت را مطابق مثال زیر در آن بریزیم:

<div dir="ltr">
 
```http
POST /sample-posts/_doc
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": """quia et suscipit
suscipit recusandae consequuntur expedita et cum
reprehenderit molestiae ut ut quas totam
nostrum rerum est autem sunt rem eveniet architecto"""
}
```
</div>
در عکس dev tools در قسمت قبل می‌توانید response مربوط به درخواست فوق (بدنه و زمان و کد) را مشاهده کنید :)

</div>
