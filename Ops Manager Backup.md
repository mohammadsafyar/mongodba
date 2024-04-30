##یکی از امکاناتی که ops manager در اختیار ما قرار میده امکان گرفتن  **snapshots and point-in-time recovery** در  **MongoDB replica sets and sharded clusters.** می باشد 


در هر سرور Ops Manager که به عنوان یک Daemon پشتیبان‌گیری فعال می‌شود، دایرکتوری را که برای ذخیره پایگاه‌های داده اصلی استفاده می‌شود، ایجاد کنید.بهتر هستش:
برای این منظور روی یک پارتیشن دیسک محلی اختصاصی شود.
قابل نوشتن توسط کاربر mongodb-mms باشد

جهت راه اندازی backup snapshut  مراحل زیر را به ترتیب انجام می دهیم 

## Create the Ops Manager backup data directory

```bash
sudo mkdir /data/backupDaemon
```

```bash
sudo chown mongodb-mms:mongodb-mms /data/backupDaemon
```

فعال کردن activate Backup از قسمت سرور بر روی همه ای سرور های که میخواد امکان بکاب گیری بر روی انها فعال شود 


