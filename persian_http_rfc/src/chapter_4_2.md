# HTTP-Related URI Schemes

فهرست رسمی شیوه‌های (scheme) URI را سازمان IANA در این آدرس نگهداری می‌کند: <https://www.iana.org/assignments/uri-schemes>

| URI Scheme | Description                        | Section |
|------------|------------------------------------|---------|
| http       | Hypertext Transfer Protocol        | 4.2.1   |
| https      | Hypertext Transfer Protocol Secure | 4.2.2   |

اگرچه درخواست‌ها می‌توانند هر شیوه‌ی URI را هدف قرار دهند، اما شیوه‌های "http" و "https" به طور خاص برای سرورهای HTTP رایج هستند.
البته، وجود یک آدرس "http" یا "https" لزوماً به این معنا نیست که حتماً در آن مبدأ، سروری مشغول به کار است یا به درخواست‌ها پاسخ می‌دهد.
هر کسی می‌تواند یک URI بسازد، حتی اگر هیچ سروری وجود نداشته باشد یا آن سرور هنوز آن آدرس را به یک منبع خاص وصل نکرده باشد.
به دلیل ساختار واگذار شده‌ی نام‌های دامنه و آدرس‌های IP، فضای نامی (namespace) به صورت توزیع‌شده (federated) عمل می‌کند، چه سروری وجود داشته باشد یا نه.

## 4.2.1. http URI Scheme

شیوه‌ی URI با نام "http" برای ایجاد شناسه‌ها در یک فضای نام سلسله‌مراتبی تعریف شده که تحت مدیریت یک سرور مبدأ (origin server) است که ممکن است روی یک پورت مشخص، منتظر اتصال‌های TCP باشد.

> http-URI = "http" "://" authority path-abempty [ "?" query ]

سرور مبدأ برای یک آدرس "http" از بخش authority شناسایی می‌شود؛ این بخش شامل یک شناسه‌ی میزبان (host) و در صورت نیاز شماره‌ی پورت است.
اگر شماره‌ی پورت خالی باشد یا اصلاً نیامده باشد، به طور پیش‌فرض پورت ۸۰ (که برای سرویس‌های وب در نظر گرفته شده) استفاده می‌شود.
سرور مبدأ مشخص می‌کند چه کسی حق دارد به صورت معتبر به درخواست‌های مربوط به آن منبع پاسخ دهد.
فرستنده‌ها نباید URIهایی با شناسه‌ی میزبان خالی ایجاد کنند.
دریافت‌کننده‌هایی که چنین URIای را دریافت می‌کنند، باید آن را نامعتبر تشخیص دهند و رد کنند.
در نهایت، مسیر (path) و پرس‌وجو (query) مشخص می‌کنند که در فضای نام سرور مبدأ، کدام منبع هدف قرار گرفته است.

## 4.2.2. https URI Scheme

شیوه‌ی URI با نام "https" برای ایجاد شناسه‌هایی تعریف شده که در یک فضای نام سلسله‌مراتبی قرار دارند و تحت مدیریت سروری هستند که روی یک پورت مشخص منتظر اتصال TCP است و می‌تواند ارتباط امن (TLS) برای HTTP برقرار کند.
در اینجا "امن بودن" یعنی سرور هویت خودش را به عنوان نماینده‌ی authority مشخص شده ثابت کرده باشد و ارتباط HTTP بین کلاینت و سرور هم از نظر محرمانگی و صحت داده محافظت شده باشد.

> https-URI = "https" "://" authority path-abempty [ "?" query ]

سرور مبدأ در آدرس‌های "https" از طریق بخش authority شناسایی می‌شود که شامل نام میزبان (host) و در صورت نیاز شماره‌ی پورت است. اگر شماره‌ی پورت مشخص نشده باشد، به طور پیش‌فرض پورت ۴۴۳ استفاده می‌شود (که برای HTTP روی TLS رزرو شده است).
سرور مبدأ تعیین می‌کند چه کسی حق پاسخ معتبر به درخواست‌های مربوط به یک منبع را دارد.
فرستنده‌ها نباید URIای با شناسه‌ی میزبان خالی ایجاد کنند، و دریافت‌کننده‌ها هم باید چنین URIهایی را نامعتبر بدانند و رد کنند.
مسیر (path) و پرس‌وجو (query) مشخص می‌کنند که در فضای نام سرور مبدأ کدام منبع هدف قرار گرفته است.

کلاینت باید اطمینان حاصل کند که درخواست‌های HTTP برای منابع "https" قبل از ارسال، امن شده باشند و فقط پاسخ‌های امن را بپذیرد.
توجه داشته باشید که روش‌های رمزنگاری قابل قبول برای کلاینت و سرور معمولاً طی مذاکره تعیین می‌شوند و ممکن است در طول زمان تغییر کنند.
منابعی که از طریق "https" در دسترس هستند، هویتی مشترک با منابع "http" ندارند؛ این دو کاملاً جدا از هم و در فضای نام متفاوتی هستند.
البته برخی از توسعه‌های HTTP، مثل پروتکل Cookie، این اجازه را می‌دهند که اطلاعاتی که توسط یک سرویس روی یک دامنه تنظیم شده، روی سرویس‌های دیگر همان دامنه هم تاثیر بگذارد.
این نوع توسعه‌ها باید با دقت زیادی طراحی شوند تا از انتقال ناخواسته‌ی اطلاعات از یک ارتباط امن به یک ارتباط ناامن جلوگیری شود.

## 4.2.3. http(s) Normalization and Comparison 

آدرس‌هایی که با «http» یا «https» شروع می‌شوند، بر اساس روش‌های مشخص‌شده در بخش ۶ سند [URI] نرمال‌سازی (یکنواخت‌سازی) و مقایسه می‌شوند. برای هر کدام از این دو شیوه، مقدارهای پیش‌فرض خاصی وجود دارد که در همین نرمال‌سازی در نظر گرفته می‌شوند.
HTTP الزام نمی‌کند که حتماً از یک روش خاص برای مقایسه‌ی برابری آدرس‌ها استفاده شود. مثلاً یک کلید کش (cache key) ممکن است به‌صورت ساده، یا پس از نرمال‌سازی دستوری، یا بر اساس نرمال‌سازی خاص scheme مقایسه شود.

نرمال‌سازی بر پایه‌ی scheme برای آدرس‌های «http» و «https» شامل قوانین اضافی زیر است:

اگر شماره‌ی پورت برابر با پورت پیش‌فرض آن scheme باشد، حالت نرمال این است که پورت حذف شود.

اگر مسیر (path) خالی باشد و برای درخواست OPTIONS استفاده نشده باشد، معادل مسیر «/» در نظر گرفته می‌شود؛ پس شکل نرمال این است که مسیر «/» به‌صورت صریح آورده شود.

scheme (مثلاً http/https) و نام میزبان (host) نسبت به حروف بزرگ و کوچک حساس نیستند و معمولاً به صورت حروف کوچک نوشته می‌شوند؛ اما سایر اجزای آدرس حساس به حروف هستند.

کاراکترهایی که جزء مجموعه‌ی «رزرو نشده» هستند با نسخه‌ی کدشده‌ی درصدی (percent-encoded) خود برابر در نظر گرفته می‌شوند؛ پس در حالت نرمال نباید آن‌ها را کد کرد (رجوع شود به بخش‌های ۲.۱ و ۲.۲ سند [URI]).

برای نمونه، سه URI زیر با وجود تفاوت ظاهری‌شان، معادل هم در نظر گرفته می‌شوند:

> <http://example.com:80/~smith/home.html>  
> <http://EXAMPLE.com/%7Esmith/home.html>  
> <http://EXAMPLE.com:/%7esmith/home.html>

دو URI در HTTP که پس از نرمال‌سازی (با استفاده از هر روش) معادل باشند، می‌توانند به‌عنوان شناسه یک منبع واحد در نظر گرفته شوند و هر بخش از HTTP می‌تواند نرمال‌سازی را انجام دهد. به همین دلیل، منابع متمایز نباید توسط URIهای HTTP شناسایی شوند که پس از نرمال‌سازی (با استفاده از هر روشی که در بخش ۶.۲ از [URI] تعریف شده) معادل باشند.

## 4.2.4. Deprecation of userinfo in http(s) URIs 

قواعد عمومی URI برای authority همچنین شامل یک زیر‌کامپوننت userinfo ([URI], بخش ۳.۲.۱) برای گنجاندن اطلاعات احراز هویت کاربر در URI می‌باشد. در این زیر‌کامپوننت، استفاده از فرمت "کاربر:رمزعبور" منسوخ شده است. برخی پیاده‌سازی‌ها از این زیر‌کامپوننت برای پیکربندی داخلی اطلاعات احراز هویت، مانند در گزینه‌های فراخوانی دستورات، فایل‌های پیکربندی، یا لیست‌های بوکمارک استفاده می‌کنند، حتی اگر چنین استفاده‌ای ممکن است شناسه کاربر یا رمزعبور را فاش کند. فرستنده نباید زیر‌کامپوننت userinfo (و جداکننده "@" آن) را زمانی که یک URI "http" یا "https" به عنوان URI هدف یا مقدار فیلد در یک پیام تولید می‌شود، ایجاد کند. قبل از استفاده از یک URI "http" یا "https" که از منبع غیرقابل اعتماد دریافت شده، دریافت‌کننده باید برای وجود userinfo آن را تجزیه کرده و حضور آن را به‌عنوان خطا در نظر بگیرد؛ احتمالاً برای پنهان کردن authority به منظور حملات فیشینگ استفاده می‌شود.

## 4.2.5. http(s) References with Fragment Identifiers 

شناسه‌های fragment اجازه می‌دهند تا یک منبع ثانویه به‌طور غیرمستقیم شناسایی شود، بدون وابستگی به scheme URI، همانطور که در بخش ۳.۵ از [URI] تعریف شده است. برخی از عناصر پروتکلی که به URI ارجاع می‌دهند، اجازه گنجاندن یک fragment را می‌دهند، در حالی که برخی دیگر این اجازه را نمی‌دهند. این عناصر با استفاده از قاعده ABNF برای عناصری که fragment را مجاز می‌کنند متمایز می‌شوند؛ در غیر این صورت، از قاعده خاصی که fragments را رد می‌کند، استفاده می‌شود.

> توجه: بخش شناسه‌ی fragment جزئی از تعریف scheme برای یک scheme URI نیست (رجوع شود به بخش ۴.۳ از [URI])، بنابراین در تعاریف ABNF برای schemes "http" و "https" در بالا ظاهر نمی‌شود.
