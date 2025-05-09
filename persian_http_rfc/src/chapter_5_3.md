# 5.3. Field Order

گیرنده می‌تواند چند خط فیلد با نام یکسان را که در یک بخش فیلد قرار دارند، بدون تغییر در معنای پیام، به یک خط فیلد ترکیب کند؛ به این صورت که هر مقدار خط فیلد بعدی را به مقدار خط فیلد اولیه به‌ترتیب اضافه کند و بین آن‌ها یک ویرگول (,) و فاصله‌ی اختیاری (OWS، تعریف‌شده در بخش ۵.۶.۳) قرار دهد. برای یکنواختی، بهتر است از ویرگول و فاصله (, ) استفاده شود.

از این رو، ترتیب دریافت خط‌های فیلد با نام یکسان، برای تفسیر مقدار فیلد مهم است؛ بنابراین یک پراکسی نباید ترتیب مقادیر این خط‌های فیلد را هنگام انتقال پیام تغییر دهد.

این بدان معناست که، با استثنای شناخته‌شده‌ای که در ادامه ذکر خواهد شد، فرستنده نباید چند خط فیلد با نام یکسان در یک پیام (چه در بخش‌های سرآیند و چه تریلر) تولید کند یا خط فیلدی را به پیامی اضافه کند که پیش از آن فیلدی با همان نام دارد، مگر اینکه تعریف آن فیلد به‌طور صریح اجازه دهد که چند مقدار خط فیلد به‌صورت فهرست جداشده با ویرگول ترکیب شوند (یعنی دست‌کم یکی از جایگزین‌های تعریف آن فیلد، یک فهرست جداشده با ویرگول را مجاز بداند، مانند قاعده‌ی ABNF از نوع #(values) تعریف‌شده در بخش ۵.۶.۱).

> نکته: در عمل، فیلد هدر «Set-Cookie» ([COOKIE]) اغلب در یک پیام پاسخ، در چندین خط فیلد ظاهر می‌شود و از نحو فهرست (list syntax) استفاده نمی‌کند. این کار با الزامات گفته‌شده درباره‌ی چندین خط فیلد با نام یکسان مغایرت دارد. از آنجا که این فیلد نمی‌تواند به یک مقدار فیلد واحد ترکیب شود، گیرنده‌ها باید هنگام پردازش فیلدها، «Set-Cookie» را به‌عنوان یک مورد خاص در نظر بگیرند. (برای جزئیات بیشتر، به پیوست A.2.3 از [Kri2001] مراجعه کنید.)

ترتیب دریافت خطوط فیلد با نام‌های متفاوت در یک بخش مهم نیست.
با این حال، رعایت این قاعده‌ی کاربردی توصیه می‌شود که هدرهایی که شامل داده‌های کنترلی اضافی هستند—for example, Host در درخواست‌ها و Date در پاسخ‌ها—در ابتدا ارسال شوند،
تا پیاده‌سازی‌ها بتوانند در سریع‌ترین زمان ممکن تصمیم بگیرند که آیا لازم است یک پیام را پردازش کنند یا خیر.

یک سرور نباید درخواست را به منبع هدف اعمال کند تا زمانی که کل بخش هدر درخواست را دریافت کرده باشد،
چرا که خطوط فیلدهای هدر بعدی ممکن است شامل شرط‌ها (conditionals)، اعتبارسنجی (authentication credentials)، یا فیلدهای تکراری فریبنده‌ای باشند که می‌توانند بر روند پردازش درخواست تأثیر بگذارند.
