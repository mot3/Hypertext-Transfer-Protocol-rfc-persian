# URI References

ارجاعات URI برای مشخص کردن مقصد درخواست‌ها، انجام تغییر مسیر و تعریف روابط استفاده می‌شوند.
برخی اصطلاحات مرتبط با ساختار URI از استاندارد اصلی آن گرفته شده‌اند.
همچنین قوانینی برای مسیرهای مطلق و نسبی تعریف شده است تا نحوه‌ی کار با آدرس‌های مختلف مشخص شود.

> URI-reference = <URI-reference, see [URI], Section 4.1>
> absolute-URI  = <absolute-URI, see [URI], Section 4.3>
> relative-part = <relative-part, see [URI], Section 4.2>
> authority     = <authority, see [URI], Section 3.2>
> uri-host      = <host, see [URI], Section 3.2.2>
> port          = <port, see [URI], Section 3.2.3>
> path-abempty  = <path-abempty, see [URI], Section 3.3>
> segment       = <segment, see [URI], Section 3.3>
> query         = <query, see [URI], Section 3.4>
>
> absolute-path = 1*( "/" segment )
> partial-URI   = relative-part [ "?" query ]

در HTTP، هر بخشی که از آدرس‌های URI استفاده می‌کند، مشخص می‌کند چه نوع URI قابل قبول است: کامل، نسبی یا ترکیبی از این دو.
اگر چیزی به‌طور خاص گفته نشود، آدرس‌های URI نسبت به آدرس مقصد (target URI) تفسیر می‌شوند.
توصیه می‌شود که همه‌ی فرستنده‌ها و گیرنده‌ها بتوانند حداقل آدرس‌هایی با طول ۸۰۰۰ بایت را پشتیبانی کنند.
البته این یعنی در بعضی مواقع اندازه‌ی بعضی بخش‌ها (مثلاً خط درخواست در HTTP/1.1) ممکن است بزرگ‌تر از حالت معمول شود.