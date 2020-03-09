---
title: Django Öğreticisi 2. adımda Visual Studio, görünümleri ve şablonların öğrenin
titleSuffix: ''
description: Visual Studio projeleri, özellikle bir uygulama oluşturma ve görünümleri ve şablonlar kullanma adımları bağlamında Django temel bilgileri bir kılavuz.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5befdfb5f6974ff7b042319121a27c3628757b6e
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409418"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>2\. adım: görünümleri ve şablonların bir Django uygulaması oluşturma

**Önceki adım: [Visual Studio projesi ve çözümü oluşturma](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Visual Studio projesinde şimdiye kadar olan özellikler, bir veya daha fazla Docgo *uygulaması*çalışabilen bir docgo *projesinin*yalnızca site düzeyi bileşenleridir. Sonraki adım, ilk uygulamanızı tek bir sayfayla oluşturmaktır.

Bu adımda, daha fazla bilgi için nasıl:

> [!div class="checklist"]
> - Tek bir sayfayla bir Django uygulaması oluşturma (Adım 2 - 1)
> - Django projesi (Adım 2-2) uygulamayı çalıştırma
> - HTML (Adım 2-3) kullanarak görünüm işlemek
> - Django sayfası şablonu (Adım 2-4) kullanarak görünüm işlemek

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>2-1. adım: bir varsayılan yapı ile uygulama oluşturma

Bir Django uygulaması belirli bir amaç için ilgili dosyaları içeren ayrı bir Python paketidir. Django projesi yansıtan bir web ana bilgisayarı bir tek etki alanı adı ayrı giriş noktalarından herhangi bir sayıda verebilen olgu herhangi bir sayıda uygulamaları içerebilir. Örneğin, contoso.com gibi bir etki alanı için Docgo projesi `www.contoso.com`bir uygulama, support.contoso.com için ikinci bir uygulama ve docs.contoso.com için üçüncü bir uygulama içerebilir. Bu durumda, Docgo projesi site düzeyinde URL yönlendirme ve ayarlarını işler ( *URLs.py* ve *Settings.py* dosyalarında), her uygulamanın kendi ayrı stil ve kendi iç yönlendirme, görünümler, modeller, statik dosyalar ve yönetim arabirimi aracılığıyla davranışı vardır.

Bir Django uygulaması genellikle standart bir dosya kümesi ile başlar. Visual Studio öğe şablonları aynı amaca hizmet eder bir tümleşik menü komutu ile birlikte bir Django projesi içinde bir Django uygulaması başlatılamadı sağlar:

- Şablonlar: **Çözüm Gezgini**, projeye sağ tıklayın ve > **Yeni öğe** **Ekle** ' yi seçin. **Yeni öğe Ekle** Iletişim kutusunda **docgo 1,9 uygulama** şablonunu seçin, **ad** alanında uygulama adını belirtin ve **Tamam**' ı seçin.

- Tümleşik komut: **Çözüm Gezgini**' de projeye sağ tıklayın ve > **docgo uygulaması** **Ekle** ' yi seçin. Bu komut için bir ad ister ve Django 1.9 uygulaması oluşturur.

    ![Bir Django uygulaması eklemek için menü komutu](media/django/step02-add-django-app-command.png)

Her iki yöntemi kullanarak, "HelloDjangoApp" adı ile bir uygulama oluşturun. Sonuç, aşağıdaki tabloda açıklanan öğeleri içeren bu ada sahip, projenizdeki bir klasördür.

![Çözüm Gezgini'nde Django uygulama dosyaları](media/django/step02-django-app-in-solution-explorer.png)

| Öğe | Açıklama |
| --- | --- |
| **\_\_init\_\_. Kopyala** | Uygulamayı bir paket olarak tanımlayan dosya. |
| **geçişler** | Django ile hizalamak için veritabanını güncelleştiren komut dosyaları depolayan bir klasör için modelleri değiştirir. Geçerli modelleri eşleşmesi Django'nın Geçiş Araçları veritabanının önceki bir sürümüne sonra gerekli değişiklikleri uygulayın. Modellerinizi üzerinde odaklanma tutun migrations'ı kullanma ve temel alınan veritabanı şemasını işlemek Django olanak tanır. Geçişler adım 6 ' da ele alınmıştır. Şimdilik, klasör yalnızca bir *\_\_init\_\_. Kopyala* dosyası içerir (klasörün kendi Python paketini tanımladığını gösterir). |
| **şablonları** | Uygulama adıyla eşleşen bir klasör içinde tek bir dosya *index. html* Içeren Docgo sayfa şablonları için bir klasör. (Visual Studio 2017 15,7 ve önceki sürümlerde dosya doğrudan *Şablonlar* altında bulunur ve adım 2-4 alt klasörü oluşturmanızı söyler.) Şablonlar, görünümün dinamik olarak bir sayfayı işlemek için bilgi ekleyebileceği HTML bloklarıdır. *Index. html*içinde `{{ content }}` gibi sayfa şablonu "değişkenler", bu makalenin ilerleyen kısımlarında açıklandığı gibi dinamik değerler için yer tutuculardır (2. adım). Genellikle Django uygulamaları, uygulama adıyla eşleşen bir alt klasöre yerleştirerek, şablon için bir ad alanı oluşturun. |
| **admin.py** | Uygulamayı genişletmek Python dosyası yönetim arabirimi (6. adıma bakın), temel ve bir veritabanındaki verileri düzenlemek için kullanılır. Başlangıçta, bu dosya yalnızca `from django.contrib import admin`ifadesini içerir. Varsayılan olarak, Docgo, *URLs.py*içindeki mevcut girişlerin açıklamasını kaldırarak, docgo projesinin *Settings.py* dosyasındaki girişler aracılığıyla standart bir yönetim arabirimi içerir. |
| **apps.py** | (Bu tablodan sonraki, aşağıya bakın) uygulaması için bir yapılandırma sınıfı tanımlayan bir Python dosyası. |
| **models.py** | Veri nesneleri, işlevleri, görünümleri uygulamanın temel veritabanıyla etkileşim tarafından tanımlanan modelleridir (6. adıma bakın). Django veritabanı bağlantı katmanı sağladığından uygulamalar kendilerini bu ayrıntılarla ilgilendiriyor gerekmez. *Models.py* dosyası, modellerinizin oluşturulacağı varsayılan bir yerdir ve başlangıçta yalnızca `from django.db import models`ifadesini içerir. |
| **tests.py** | Temel yapısını birim testleri içeren bir Python dosyası. |
| **views.py** | Genellikle, web bir HTTP isteğini alıp bir HTTP yanıt sayfaları düşüncelerinizi görünümleridir. Görünümleri genellikle web tarayıcıları nasıl görüntüleneceğini bildiğiniz HTML olarak işlemenizi, ancak bir görünüm mutlaka (Ara formu gibi) görünür olmak zorunda değildir. Bir görünümü olan sorumluluğundadır tarayıcıya göndermek için HTML oluşturmak için bir Python işlevi tarafından tanımlanır. *Views.py* dosyası, görünümlerin oluşturulacağı varsayılan bir yerdir ve başlangıçta yalnızca `from django.shortcuts import render`ifadesini içerir. |

*Apps.py* Içeriği "Hellodocgoapp" adı kullanılırken şöyle görünür:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Soru: bir Django uygulaması Visual Studio'da uygulama oluşturma komut satırında yapılan çağrılardan farklı oluşturuyor?

Yanıt: **add** > **docgo App** komutunu çalıştırma veya docgo uygulama şablonuyla > **Yeni öğe** **Ekle** ' nin kullanılması, docgo komutu `manage.py startapp <app_name>`ile aynı dosyaları oluşturur. Visual Studio'da uygulama oluşturmanın avantajı, uygulama klasörü ve tüm dosyalar projeye otomatik olarak tümleştirilir içindir. Aynı Visual Studio komut, projenizdeki herhangi bir sayıda uygulamaları oluşturmak için kullanabilirsiniz.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>2-2. adım: uygulamayı Django projeden çalıştırın

Bu noktada, projeyi Visual Studio 'da yeniden çalıştırırsanız (araç çubuğu düğmesini **kullanarak veya hata** **ayıklamayı > başlatırsanız**), yine de varsayılan sayfayı görürsünüz. Bir uygulamaya özgü sayfa tanımlama ve uygulama Django projeye eklemek gerektiği için hiçbir uygulama içeriği görünür:

1. *Merhaba Docgoapp* klasöründe, "index" adlı bir görünümü tanımlayan aşağıdaki kodla eşleşecek şekilde *views.py* değiştirin:

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. *BasicProject* klasöründe (adım 1 ' de oluşturulur), *URLs.py* öğesini en azından aşağıdaki kodla eşleşecek şekilde değiştirin (isterseniz, komutlarıaçıklamalarını koruyabilirsiniz):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Her URL modelinde, Docgo 'nun belirli siteyle ilgili URL 'Leri yönlendirdiğini (yani `https://www.domain.com/`izleyen bölüm) açıklayan görünümler açıklanmaktadır. Normal ifade `^$` ile başlayan `urlPatterns` ilk giriş, "/" site kökünün yönlendirimiyle. İkinci girdi, `^home$` özel olarak "/Home" yollar. Herhangi bir sayıda üretim aynı görünüme sahip olabilir.

1. **Hello, Docgo** iletisini görmek için projeyi yeniden çalıştırın! Görünümü tarafından tanımlandığı şekilde. İşiniz bittiğinde, sunucunun durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine işleme

Kodunuzda değişiklikler yaptık ve başarıyla sınanmıştır olduğundan, kaynak denetimine yaptığınız değişiklikleri kaydedin ve gözden geçirmek için harika bir zaman sunulmuştur. Bu öğreticinin sonraki adımlarında, kaynak denetimine yeniden kaydetmeye uygun sürelerinin anımsatmak ve tekrar bu bölüme bakın.

1. **Takım Gezgini**gittiği, Visual Studio 'nun alt kısmındaki (aşağıda daire içinde) bulunan değişiklikler düğmesini seçin.

    ![Visual Studio durum çubuğunda kaynak denetim değişikliklerini düğmesine](media/django/step02-source-control-changes-button.png)

1. **Takım Gezgini**, "Ilk Docgo uygulaması oluşturma" gibi bir teslim iletisi girin ve **Tümünü Yürüt**' ü seçin. Kayıt tamamlandığında, **karma > yerel olarak oluşturulan bir Ileti tamamlama \<görürsünüz. Değişikliklerinizi sunucuyla paylaşmak için eşitleyin.** Değişiklikleri uzak deponuza göndermek istiyorsanız **Eşitle**' yi ve ardından **giden işlemeler**altında **Gönder** ' i seçin. Ayrıca, uzak göndermeden önce birden çok yerel işlemeleri birikebilir.

    ![Uzak Ekip Gezgini'nde yürütmeler gönderin](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Soru: Yönlendirme dizeleri için önce 'r' öneki nedir?

Yanıt: 'R' ön ek Python dizesinde "ham", dize içindeki herhangi bir karakter kaçış değil Python bildirir anlamına gelir. Normal ifadeler çok sayıda özel karakter kullandığından, ' r ' önekini kullanmak Bu dizelerin bir dizi '\\' kaçış karakteri içerenden çok daha kolay olmasını sağlar.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Soru: Neler ^ ve $ karakterlerini, URL yönlendirme girişleri anlamına gelir?

Cevap: URL düzenlerini tanımlayan normal ifadelerde, ^ "satır başlangıcı" ve $ "satır sonu" anlamına gelir ve burada URL 'Ler site köküne (`https://www.domain.com/`sonraki bölüm) görelidir. Normal ifade `^$` etkin bir şekilde "boş" anlamına gelir ve bu nedenle `https://www.domain.com/` tam URL 'SI ile eşleşir (site köküne hiçbir şey eklenmez). `^home$` `https://www.domain.com/home/`tam olarak eşleşir. (Django kullanmaz sondaki / desen eşleştirme.)

`^home`olduğu gibi normal ifadede sondaki $ kullanmıyorsanız, URL deseninin "Home", "ödevi", "Homestead" ve "home192837" gibi "Home" ile başlayan *herhangi* bir URL ile eşleşir.

Farklı normal ifadelerle denemeler yapmak için [pythex.org](https://www.pythex.org)adresindeki [regex101.com](https://regex101.com) gibi çevrimiçi araçları deneyin.

## <a name="step-2-3-render-a-view-using-html"></a>2-3. adım: HTML kullanarak görünüm işlemek

Şimdiye kadar *views.py* sahip olduğunuz `index` işlevi, sayfa için düz metın bir HTTP yanıtından daha fazla şey oluşturuyor. Çoğu gerçek web sayfaları, doğal olarak, genellikle canlı verileri bir araya getiren zengin HTML sayfaları ile yanıt verir. İçeriği dinamik olarak oluşturmak için gerçekten bir işlevi kullanarak bir görünüm tanımlamak için birincil nedenidir.

`HttpResponse` bağımsız değişkeni yalnızca bir dize olduğundan, bir dize içinde istediğiniz HTML 'yi oluşturabilirsiniz. Basit bir örnek olarak, `index` işlevini aşağıdaki kodla değiştirin (varolan `from` deyimlerini koruyarak), bu, sayfayı her yenilemenizde güncelleştirilmiş dinamik içeriği kullanarak bir HTML yanıtı oluşturur:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

"**Hello Docgo!** " gibi bir iletiyi görmek için projeyi yeniden çalıştırın. Pazartesi, 16 Nisan 2018 16:28:10 üzerinde ". Güncelleştirme zamanı ve içeriğin her bir istekle üretiliyor onaylamak için sayfayı yenileyin. İşiniz bittiğinde, sunucunun durdurun.

> [!Tip]
> Projeyi durdurma ve yeniden başlatmanın bir kısayolu, hata **ayıklama** > **Yeniden Başlat** menü komutunu (**CTRL**+**SHIFT**+**F5**) veya hata ayıklama araç çubuğundaki **Yeniden Başlat** düğmesini kullanmaktır:
>
> ![Visual Studio'da hata ayıklama araç çubuğundan yeniden başlatın](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>2-4. adım: bir sayfası şablonu kullanarak görünüm işlemek

HTML kod oluşturma için çok küçük sayfaları düzgün çalışır, ancak sayfaları daha karmaşık hale geldikçe genellikle "sayfa şablonları, ardından eklediğiniz" sayfanızın (birlikte, CSS ve JavaScript dosyalarına yapılan başvurular) statik HTML parçaları dinamik korumak istediğiniz kod tarafından oluşturulan içerikleri. Önceki bölümde, yalnızca `now.strftime` çağrısının tarih ve saati dinamiktir. Bu, diğer tüm içeriklerin bir sayfa şablonuna yerleştirilebileceği anlamına gelir.

Bir Docgo sayfa şablonu, `{{ content }}`gibi `{{` ve `}}`tarafından ayırıcı olan "değişkenler" adlı bir dizi değiştirme belirteci içerebilen bir HTML bloğudur. Django'nın şablon oluşturma modülü kodda sağlayan dinamik içerik değişkenleri sonra değiştirir.

Aşağıdaki adımlarda, şablonların kullanımı gösterilmektedir:

1. Docgo projesini içeren *BasicProject* klasörünün altında, *Settings.py* dosyasını açın ve `INSTALLED_APPS` listesine "hellodocgoapp" uygulama adını ekleyin. Listeye uygulama ekleme, Django projesi içeren bir uygulama bu ada sahip bir klasör olduğunu bildirir:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Ayrıca, *Settings.py*içinde, `TEMPLATES` nesnesinin aşağıdaki satırı (varsayılan olarak dahildir) içerdiğinden emin olun. Bu, Docgo 'nun yüklü bir uygulamanın *Şablonlar* klasöründeki şablonları aramasını sağlar:

    ```json
    'APP_DIRS': True,
    ```

1. *Merhaba Docgoapp* klasöründe, bir değişken `{{ content }}`olduğunu gözlemlemek için *Templates/HelloDjangoApp/index.html* sayfa şablonu dosyasını (veya vs 2017 15,7 ve önceki sürümlerde *Templates/index.html* ) açın:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. *Merhaba Docgoapp* klasöründe *views.py* ' ı açın ve `index` işlevini `django.shortcuts.render` yardımcı işlevini kullanan aşağıdaki kodla değiştirin. `render` Yardımcısı, sayfa şablonlarıyla çalışmak için basitleştirilmiş bir arabirim sağlar. Tüm mevcut `from` deyimlerini saklamayı unutmayın.

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    `render`ilk bağımsız değişkeni, görebileceğiniz gibi, istek nesnesidir ve sonra uygulamanın *Şablonlar* klasörü içindeki şablon dosyasının göreli yolu gelir. Bir şablon dosyası destekliyorsa, görünüm için uygun olarak adlandırılır. `render` üçüncü bağımsız değişkeni, daha sonra şablonun başvurduğu değişkenlerin bir sözlüğüdür. Sözlüğe nesne ekleyebilirsiniz, bu durumda şablondaki bir değişken `{{ object.property }}`başvurabilir.

1. Projeyi çalıştırın ve çıktıyı gözlemleyin. Şablon çalıştığını gösteren adım 2-2 görülen benzer bir ileti görmeniz gerekir.

    Bununla birlikte, `content` özelliğinde kullandığınız HTML 'nin yalnızca düz metin olarak işlediğini gözlemleyin çünkü `render` işlevi otomatik olarak HTML 'den çıkar. Kaçış otomatik ekleme saldırılarına karşı yanlışlıkla güvenlik açıklarını önlemeye: geliştiriciler genellikle bir sayfadan giriş toplayın ve şablon yer tutucu aracılığıyla başka bir değer olarak kullanın. Kaçış Ayrıca, yeniden HTML sayfası şablonu ve kodunun dışında tutmak en iyi olduğunu anımsatıcı işlevi görür. Neyse ki, bu ek değişkenleri oluşturmak üzere basit ayıklamadır gerektiğinde. Örneğin, bir sayfa başlığı ekleyen ve sayfa şablonunda tüm biçimlendirmeyi tutan aşağıdaki biçimlendirmeyle eşleşecek şekilde *index. html* ' yi *Şablonlar* ile değiştirin:

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    Daha sonra, sayfa şablonundaki tüm değişkenler için değerler sağlamak üzere `index` görünüm işlevini aşağıdaki şekilde yazın:

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. Sunucusunu durdurmak ve projeyi yeniden başlatın ve sayfa artık doğru şekilde işlediğinden inceleyin:

    ![Şablon kullanarak çalışan uygulama](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 sürüm 15,7 ve önceki sürümler: son bir adım olarak, şablonlarınızı uygulamanız ile aynı adlı bir alt klasöre taşıyın. Bu, bir ad alanı oluşturur ve projeye ekleyebileceğiniz diğer uygulamalarla olası çakışmaları önler. (VS 2017 'deki şablonlar 15.8 + bunu sizin için otomatik olarak yapın.) Diğer bir deyişle, *Merhaba Docgoapp*adlı *şablonlarda* bir alt klasör oluşturun, *index. html* dosyasını bu alt klasöre taşıyın ve `index` görünüm işlevini, şablonun yeni yoluna ( *HelloDjangoApp/index.html*) başvuracak şekilde değiştirin. Ardından projeyi çalıştırın, sayfanın düzgün bir şekilde oluşturulduğunu doğrulayın ve sunucuyu durdur.

1. Değişikliklerinizi kaynak denetimine kaydedin ve isterseniz, uzak deponuzu [adım 2-2](#commit-to-source-control)' de açıklandığı gibi güncelleştirin.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: şablonların ayrı bir dosyada olmam gerekir mi?

Yanıt: şablonları genellikle ayrı HTML dosyalarında korunsa de satır içi şablonu kullanabilirsiniz. Ayrı bir dosya kullanarak, ancak işaretleme ve kod arasında NET bir ayrım sağlamak için önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: şablonları .html dosya uzantısını kullanmalıdır?

Cevap: `render` işlevine ikinci bağımsız değişkende dosyanın tam yolunu her zaman tanımlayacağından, sayfa şablonu dosyaları için *. html* uzantısı tamamen isteğe bağlıdır. Ancak, Visual Studio (ve diğer düzenleyiciler), genellikle, sayfa şablonlarının tamamen HTML olmaması durumunda kod tamamlama ve *. html* dosyalarıyla söz dizimi renklendirme gibi özellikler sağlar.

Aslında, Django projesi ile çalışırken, Visual Studio otomatik olarak düzenlediğiniz HTML dosyası aslında bir Django şablonudur algılar ve bazı otomatik tamamlama özellikleri sağlar. Örneğin, `{#`bir Docgo sayfa şablonu açıklaması yazmaya başladığınızda, Visual Studio otomatik olarak kapanış `#}` karakterleri verir. **Açıklama seçimi** ve **seçim komutlarının açıklamasını kaldırın** ( **düzenleme** > **GELIŞMIŞ** menüsünde ve araç çubuğunda), HTML açıklamaları yerine şablon açıklamalarını de kullanır.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Soru: Proje çalıştırabilir, şablon bulunamayan bir hata görüyorum. Ne oldu?

Cevap: şablonun bulunamadığını belirten hatalar görürseniz, uygulamayı `INSTALLED_APPS` listesinde Docgo projesinin *Settings.py* eklediğinizden emin olun. Bu giriş olmadan Docgo, uygulamanın *Şablonlar* klasörünü aramak için bilgi vermez.

### <a name="question-why-is-template-namespacing-important"></a>Soru: Şablon namespacing neden önemlidir?

Cevap: Docgo `render` işlevinde başvurulan bir şablonu ararken, ilk bulduğu dosyayı göreli yol ile eşleşen bir dosya kullanır. Aynı klasör yapılarını için şablonları kullanın. aynı projede birden fazla Django uygulamaları varsa, tek bir uygulama, yanlışlıkla başka bir uygulamadan şablon kullanacağınız olasıdır. Bu tür hatalardan kaçınmak için her zaman bir uygulamanın *Şablonlar* klasörü altında, herhangi bir yinelemeyi önlemek için uygulamanın adıyla eşleşen bir alt klasör oluşturun.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Daha ayrıntılı şekilde inceleyin

- [Ilk Docgo uygulamanızı yazma, Bölüm 1-görünümler](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Dahil ve devralma gibi Docgo şablonlarının daha fazla özelliği için bkz [. docgo şablonu dili](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Inlearning (LinkedIn) için [normal ifade eğitimi](https://www.linkedin.com/learning/topics/regular-expressions)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
