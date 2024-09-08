# android-programing
## Coroutines and LaunchedEffectsin Jetpack Compose
* DisposableEffect
```
DisposableEffect(Unit) {
        val listener = ViewTreeObserver.OnPreDrawListener {
            val insets = ViewCompat.getRootWindowInsets(view)

            isKeyboardVisible = insets?.isVisible(WindowInsetsCompat.Type.ime()) ?: false

            true
        }

        view.viewTreeObserver.addOnPreDrawListener(listener)

        onDispose {
            view.viewTreeObserver.removeOnPreDrawListener(listener)
        }
    }
```
 توضیح کلی کد:
این قطعه کد کاتلین از DisposableEffect و WindowInsets برای تشخیص تغییر وضعیت کیبورد در یک کامپوننت Compose استفاده می‌کند. به طور خاص، این کد یک OnPreDrawListener به ViewTreeObserver اضافه می‌کند که هر زمان که یک فریم جدید برای نمایش آماده می‌شود، فراخوانی می‌شود. در این listener، وضعیت کیبورد بررسی شده و متغیر isKeyboardVisible بر اساس آن به‌روزرسانی می‌شود.

تجزیه کد به بخش‌های مختلف:
### DisposableEffect(Unit) { ... }:

DisposableEffect یک کامپوزیت Compose است که به شما اجازه می‌دهد تا یک بلوک کد را پس از ترکیب شدن کامپوننت اجرا کنید و همچنین یک عمل پاکسازی (cleanup) را هنگام از بین رفتن کامپوننت انجام دهید.
در اینجا، کلید Unit استفاده شده است، به این معنی که این بلوک کد فقط یک بار اجرا می‌شود و هنگام از بین رفتن کامپوننت، عمل پاکسازی انجام خواهد شد.
### val listener = ViewTreeObserver.OnPreDrawListener { ... }:

یک OnPreDrawListener تعریف می‌شود که هر زمان که یک فریم جدید برای نمایش آماده می‌شود، فراخوانی خواهد شد.
### val insets = ViewCompat.getRootWindowInsets(view):

                                                                                                                              ViewCompat.getRootWindowInsets(view) اینسِت‌های ریشه پنجره را دریافت می‌کند. اینسِت‌ها اطلاعاتی در مورد فضای اشغال شده توسط عناصر سیستم مانند کیبورد، نوار وضعیت و غیره را ارائه می‌دهند
### isKeyboardVisible = insets?.isVisible(WindowInsetsCompat.Type.ime()) ?: false:

این خط بررسی می‌کند که آیا کیبورد قابل مشاهده است یا خیر. اگر insets غیرنول باشد، بررسی می‌کند که آیا نوع اینسِت WindowInsetsCompat.Type.ime() است یا خیر. اگر اینطور باشد، isKeyboardVisible را به true تنظیم می‌کند، در غیر این صورت به false تنظیم می‌شود.
## view.viewTreeObserver.addOnPreDrawListener(listener):

listener به ViewTreeObserver اضافه می‌شود تا هر زمان که یک فریم جدید برای نمایش آماده شود، فراخوانی شود.
### onDispose { view.viewTreeObserver.removeOnPreDrawListener(listener) }:

این بلوک کد در DisposableEffect قرار دارد و هنگام از بین رفتن کامپوننت اجرا می‌شود. در این بلوک، listener از ViewTreeObserver حذف می‌شود تا از نشت حافظه جلوگیری شود.
### عملکرد کلی کد
#### هنگام ترکیب شدن کامپوننت:
DisposableEffect اجرا شده و لیستنر به ViewTreeObserver اضافه می‌شود
#### هر زمان که یک فریم جدید برای نمایش آماده می‌شود:
لیستنر فراخوانی می شود
اینسِت‌های ریشه پنجره دریافت می‌شوند.
وضعیت کیبورد بررسی شده و isKeyboardVisible به‌روزرسانی می‌شود.
#### هنگام از بین رفتن کامپوننت:لیستنر از ViewTreeObserver حذف می شود تا از نشت حافظه جلوگیری کند
