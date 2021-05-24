---
title: Visual Studio adım 2, görünümler ve sayfa şablonunda Docgo öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında, özellikle bir uygulama oluşturma ve görünümleri ve şablonları kullanma adımları için Docgo 'nun temel bilgileri.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 196b15dff25681a23c05118a02f19109e09e3959
ms.sourcegitcommit: 5fe2462ffc33c7ece9cf3a179fb598354c916e1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2021
ms.locfileid: "110320478"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>2. Adım: görünümler ve sayfa şablonlarıyla bir Docgo uygulaması oluşturma

**Önceki adım: [Visual Studio projesi ve çözümü oluşturma](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Visual Studio projesinde şimdiye kadar olan özellikler, bir veya daha fazla Docgo *uygulaması* çalışabilen bir docgo *projesinin* yalnızca site düzeyi bileşenleridir. Sonraki adım, ilk uygulamanızı tek bir sayfa ile oluşturmaktır.

Bu adımda şu adımları öğrenebilirsiniz:

> [!div class="checklist"]
> - Tek sayfalı bir Docgo uygulaması oluşturma (adım 2-1)
> - Uygulamayı Docgo projesinden çalıştırın (adım 2-2)
> - HTML kullanarak bir görünüm işleme (adım 2-3)
> - Docgo sayfa şablonu kullanarak bir görünüm işleme (adım 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Adım 2-1: varsayılan yapıyla uygulama oluşturma

Docgo uygulaması, belirli bir amaç için ilgili dosyalar kümesi içeren ayrı bir Python paketidir. Bir Docgo projesi herhangi bir sayıda uygulama içerebilir ve bu da bir Web konağının tek bir etki alanı adından herhangi bir sayıda ayrı giriş noktasına hizmeti verebildiği olguyu yansıtır. Örneğin, contoso.com gibi bir etki alanı için bir Docgo projesi, için bir uygulama `www.contoso.com` , support.contoso.com için ikinci bir uygulama ve docs.contoso.com için bir üçüncü uygulama içerebilir. Bu durumda, Docgo projesi site düzeyinde URL yönlendirme ve ayarlarını işler ( *URLs.py* ve *Settings.py* dosyalarında), her uygulamanın kendi ayrı stil ve kendi iç yönlendirme, görünümler, modeller, statik dosyalar ve yönetim arabirimi aracılığıyla davranışı vardır.

Bir Docgo uygulaması genellikle standart bir dosya kümesiyle başlar. Visual Studio, aynı amaca hizmet eden tümleşik bir menü komutuyla birlikte bir Docgo projesi içinde Docgo uygulamasını başlatmak için öğe şablonları sağlar:

- Şablonlar: **Çözüm Gezgini**, projeye sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. Yeni Öğe **Ekle iletişim** kutusunda **Django 1.9 Uygulama** şablonunu seçin, Ad alanında uygulama **adını** belirtin ve Tamam'ı **seçin.**

- Tümleşik komut: **Çözüm Gezgini,** projeye sağ tıklayın ve Django **uygulaması**  >  **ekle'yi seçin.** Bu komut sizden bir ad istenir ve bir Django 1.9 uygulaması oluşturur.

    ![Django uygulaması eklemek için menü komutu](media/django/step02-add-django-app-command.png)

İki yöntemden birini kullanarak "HelloDjangoApp" adıyla bir uygulama oluşturun. Sonuç, projenizin bu adı içeren ve aşağıdaki tabloda açıklandığı gibi öğeleri içeren bir klasördür.

![Çözüm Gezgini'daki Django uygulama Çözüm Gezgini](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| Öğe | Açıklama |
| --- | --- |
| **\_\_init \_ \_ .py** | Uygulamayı paket olarak tanımlayan dosya. |
| **Geçiş** | Django'nun veritabanını modellerde yapılan değişikliklerle uyumlu olacak şekilde güncelleştiren betikleri depolaya bir klasör. Ardından Django'nun geçiş araçları, veritabanının önceki herhangi bir sürümüne gerekli değişiklikleri uygulayarak geçerli modellere eş olur. Geçişleri kullanarak modellerinize odaklanmanız ve Django'nun temel alınan veritabanı şemasını işlemesine izin verirsiniz. Geçişler 6. adımda ele alınmıştır; şimdilik, klasör yalnızca bir *\_ \_ init \_ \_ .py* dosyası içerir (klasörün kendi Python paketini tanımladığına işaret ediyor). |
| **templates** | Uygulama adıyla eşleşen bir klasör içinde tek bir dosya içeren *Djangoindex.htm* şablonları klasörü. (Visual Studio 2017 15.7 ve önceki sürümlerde dosya doğrudan  şablonların altında yer almaktadır ve 2-4. adımda size alt klasör oluşturma talimatı vemektedir.) Şablonlar, görünümlerin sayfayı dinamik olarak işlemek için bilgi ekleyabildikleri HTML bloklarıdır. index.html'de olduğu gibi sayfa şablonu "değişkenler", bu makalenin devamlarında (2. adım) açıklanan dinamik değerler için `{{ content }}` yer tutuculardır.  Django uygulamaları genellikle şablonları için uygulama adıyla eşleşen bir alt klasöre yerleştirerek bir ad alanı oluşturur. |
| **admin.py** | Uygulamanın yönetim arabirimini genişletilen Python dosyası (bkz. 6. adım). Bu dosya, veritabanındaki verilerin çekirdeğini oluşturmak ve düzenlemek için kullanılır. Başlangıçta, bu dosya yalnızca ifadesini içerir, `from django.contrib import admin` . Varsayılan olarak, Docgo, *URLs.py* içindeki mevcut girişlerin açıklamasını kaldırarak, docgo projesinin *Settings.py* dosyasındaki girişler aracılığıyla standart bir yönetim arabirimi içerir. |
| **apps.py** | Uygulama için bir yapılandırma sınıfı tanımlayan Python dosyası (bu tablodan sonra aşağıya bakın). |
| **models.py** | Modeller, uygulamanın temel alınan veritabanıyla etkileşime geçen görünümler tarafından tanımlanan veri nesneleridir (bkz. 6. adım). Docgo, uygulamaların bu ayrıntılarla ilgilenmesini gerektirmeyen veritabanı bağlantısı katmanını sağlar. *Models.py* dosyası, modellerinizin oluşturulacağı varsayılan bir yerdir ve başlangıçta yalnızca ifadesini içerir `from django.db import models` . |
| **tests.py** | Birim testlerinin temel yapısını içeren bir Python dosyası. |
| **views.py** | Görünümler, genellikle bir HTTP isteği alıp HTTP yanıtı döndüren Web sayfaları olarak düşündüğünüzden oluşur. Görünümler genellikle Web tarayıcılarının nasıl görüntüleneceğini bildiğiniz HTML olarak işlenir, ancak bir görünümün görünür olması gerekmez (bir ara form gibi). Bir görünüm bir Python işlevi tarafından tanımlanır ve bu da sorumluluğu tarayıcıya gönderilmek üzere HTML 'yi işlemek için kullanılır. *Views.py* dosyası, görünümlerin oluşturulacağı ve başlangıçta yalnızca deyimin bulunduğu varsayılan bir yerdir `from django.shortcuts import render` . |
::: moniker-end

::: moniker range=">=vs-2019"
| Öğe | Açıklama |
| --- | --- |
| **\_\_init \_ \_ . Kopyala** | Uygulamayı paket olarak tanımlayan dosya. |
| **geçişler** | Docgo 'nun, modellerdeki değişikliklerle uyum sağlamak üzere veritabanını güncelleştiren betikleri sakladığı bir klasör. Docgo 'nun geçiş araçları, geçerli modellerle eşleşecek şekilde veritabanının önceki bir sürümüne gerekli değişiklikleri uygular. Geçişleri kullanarak modellerinize odaklanmanız ve Django'nun temel alınan veritabanı şemasını işlemesine izin verirsiniz. Geçişler [Django belgelerinde ele alınmıştır;](https://docs.djangoproject.com/en/3.2/topics/migrations/) şimdilik, klasör yalnızca bir *\_ \_ init \_ \_ .py* dosyası içerir (klasörün kendi Python paketini tanımladığına işaret ediyor). |
| **templates** | Uygulama adıyla eşleşen bir klasör içinde tek bir dosya içeren *Djangoindex.htm* şablonları klasörü. (Visual Studio 2017 15.7 ve önceki sürümlerde dosya doğrudan  şablonların altında yer almaktadır ve 2-4. adımda size alt klasör oluşturma talimatı vemektedir.) Şablonlar, görünümlerin sayfayı dinamik olarak işlemek için bilgi ekleyabildikleri HTML bloklarıdır. index.html'de olduğu gibi sayfa şablonu "değişkenler", bu makalenin devamlarında (2. adım) açıklanan dinamik değerler için `{{ content }}` yer tutuculardır.  Django uygulamaları genellikle şablonları için uygulama adıyla eşleşen bir alt klasöre yerleştirerek bir ad alanı oluşturur. |
| **admin.py** | Bir veritabanındaki verilerin çekirdeğini oluşturmak ve düzenlemek için kullanılan uygulamanın yönetim arabirimini genişletilen Python dosyası. Başlangıçta, bu dosya yalnızca deyimini `from django.contrib import admin` içerir. Varsayılan olarak, Django, Django projesinin *settings.py* dosyasındaki girdiler aracılığıyla standart bir yönetim arabirimi içerir. Bu arabiriminde mevcut girdileri kaldırarak *urls.py.* |
| **apps.py** | Uygulama için yapılandırma sınıfını tanımlayan bir Python dosyası (bu tablodan sonra aşağıya bakın). |
| **models.py** | Modeller, görünümlerin uygulamanın temel veritabanıyla etkileşim kurduğu işlevler tarafından tanımlanan veri nesneleridir. Django, uygulamaların bu ayrıntılarla kendilerini endişeye sokan veritabanı bağlantı katmanını sağlar. Models.py  dosyası, modellerinizi oluşturmak için varsayılan bir yerdir ve başlangıçta yalnızca deyimini `from django.db import models` içerir. |
| **tests.py** | Birim testlerinin temel yapısını içeren bir Python dosyası. |
| **views.py** | Görünümler, genellikle bir HTTP isteği alıp HTTP yanıtı döndüren Web sayfaları olarak düşündüğünüzden oluşur. Görünümler genellikle Web tarayıcılarının nasıl görüntüleneceğini bildiğiniz HTML olarak işlenir, ancak bir görünümün görünür olması gerekmez (bir ara form gibi). Bir görünüm bir Python işlevi tarafından tanımlanır ve bu da sorumluluğu tarayıcıya gönderilmek üzere HTML 'yi işlemek için kullanılır. *Views.py* dosyası, görünümlerin oluşturulacağı ve başlangıçta yalnızca deyimin bulunduğu varsayılan bir yerdir `from django.shortcuts import render` . |
::: moniker-end

*Apps.py* Içeriği "Hellodocgoapp" adı kullanılırken şöyle görünür:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Soru: Visual Studio 'da komut satırında uygulama oluşturmaktan farklı bir Docgo uygulaması oluşturuluyor mu?

Cevap:   >  **docgo uygulaması** Ekle komutunu çalıştırma veya   >  docgo uygulama şablonuyla **Yeni öğe** Ekle ' nin kullanılması docgo komutuyla aynı dosyaları oluşturur `manage.py startapp <app_name>` . Visual Studio 'da uygulama oluşturmanın avantajı, uygulama klasörünün ve tüm dosyalarının proje ile otomatik olarak tümleştirildiği bir avantajdır. Projenizde herhangi bir sayıda uygulama oluşturmak için aynı Visual Studio komutunu kullanabilirsiniz.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Adım 2-2: uygulamayı Docgo projesinden çalıştırma

Bu noktada, projeyi Visual Studio 'da yeniden çalıştırırsanız (araç çubuğu **düğmesini veya hata ayıklama**  >  **başlatma hata ayıklamayı** kullanarak), yine de varsayılan sayfayı görürsünüz. Uygulamaya özgü bir sayfa tanımlamanız ve uygulamayı Docgo projesine eklemeniz gerektiğinden hiçbir uygulama içeriği görünmez:

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

    Her URL modelinde, Docgo 'nun belirli siteyle ilgili URL 'Leri yönlendirdiğini (diğer bir deyişle, izleyen bölüm) açıklayan görünümler açıklanmaktadır `https://www.domain.com/` . `urlPatterns`Normal ifadeyle başlayan ilk giriş, `^$` "/" site kökünün yönlendirimiyle. İkinci giriş, `^home$` özellikle "/home" yolunu gösterir. Aynı görünüme herhangi bir sayıda yönlendirmeye sahip olabilirsiniz.

1. Projeyi yeniden çalıştırarak Merhaba **Django!** görünüm tarafından tanımlandığı gibi. Bitiren sunucuyu durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine işleme

Kodunuz üzerinde değişiklikler yaptığınız ve bunları başarıyla test ettiyebilirsiniz. Şimdi değişikliklerinizi gözden geçirebilirsiniz ve kaynak denetimine işebilirsiniz. Bu öğreticinin sonraki adımlarında, kaynak denetimine yeniden işlemeniz için uygun zamanları anımsatır ve bu bölüme geri dönersiniz.

1. Uygulamanın (aşağıda daire içine Visual Studio) altındaki değişiklikler düğmesini seçin ve bu düğmeyi **Takım Gezgini.**

    ![Kaynak denetimi durum çubuğundaki Visual Studio değişiklikleri düğmesi](media/django/step02-source-control-changes-button.png)

1. Bu **Takım Gezgini**"İlk Django uygulamasını oluştur" gibi bir işleme iletisi girin ve Hepsini **İşle'yi seçin.** Yürütme tamamlandığında, Yerel olarak oluşturulmuş bir Commit **\<hash> iletisiyle karşılanır. Değişikliklerinizi sunucuyla paylaşmak için eşitle.** Değişiklikleri uzak deponıza itmek için Eşitle'yi ve **ardından** Giden Commit'ler altında **Gönder'i seçin.**  Ayrıca, uzak işlemeye itmeden önce birden çok yerel işleme toplayarak da biriktirin.

    ![Uzak depolamada uzak işlemeleri Takım Gezgini](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Soru: Yönlendirme dizelerinden önceki 'r' ön eki nedir?

Cevap: Python'daki bir dizedeki 'r' ön eki, Python'a dize içindeki hiçbir karakterden kaçış karakterine kaçış karakteri verme talimatını verecek şekilde "raw" anlamına gelir. Normal ifadeler çok sayıda özel karakter kullandığından, 'r' önekini kullanmak, bu dizelerin okunmalarını birkaç ' ' kaçış karakteri içermelerine \\ göre çok daha kolay hale getirir.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Soru: URL yönlendirme girişlerinde ^ ve $ karakterleri ne anlama geliyor?

Yanıt: URL desenlerini tanımlayan normal ifadelerde ^ "satırın başlangıcı" ve $ ise "satır sonu" anlamına gelir; burada URL'ler site köküne (izleyen bölüm) `https://www.domain.com/` göredir. Normal ifade `^$` etkin bir şekilde "boş" anlamına gelir ve bu nedenle tam URL ile eşleşir `https://www.domain.com/` (site köküne hiçbir şey eklenmez). Desenler `^home$` tam olarak eşleşir `https://www.domain.com/home/` . (Docgo, sondaki/ın örüntüme düzeniyle eşleştirmeyi kullanmaz.)

Normal ifadede ' de olduğu gibi sondaki $ kullanmıyorsanız `^home` , URL deseninin "Home", "ödev", "Homestead" ve "home192837" gibi "Home" ile başlayan *Tüm* URL 'ler eşleşir.

Farklı normal ifadelerle denemeler yapmak için [pythex.org](https://www.pythex.org)adresindeki [regex101.com](https://regex101.com) gibi çevrimiçi araçları deneyin.

## <a name="step-2-3-render-a-view-using-html"></a>Adım 2-3: HTML kullanarak bir görünüm Işleme

Şimdiye `index` kadar *views.py* sahip olduğunuz işlev, sayfa için düz metin bir HTTP yanıtından daha fazla şey oluşturuyor. Birçok gerçek dünyada Web sayfası, genellikle canlı verileri birleştiren zengin HTML sayfalarıyla yanıt verir. Aslında, bir işlevi kullanarak bir görünüm tanımlamanın birincil nedeni, bu içeriği dinamik olarak oluşturabilir.

Bağımsız değişkeni `HttpResponse` yalnızca bir dize olduğundan, bir dize içinde ISTEDIĞINIZ HTML 'yi oluşturabilirsiniz. Basit bir örnek olarak, `index` aşağıdaki kodla (var olan `from` deyimleri koruyarak), sayfayı her yenilediğiniz zaman güncelleştirilmiş dinamik içeriği kullanarak bir HTML yanıtı oluşturan şu kodla değiştirin:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

"**Hello Docgo!** " gibi bir iletiyi görmek için projeyi yeniden çalıştırın. Pazartesi günü, 16 Nisan 2018, 16:28:10 ". Zamanı güncelleştirmek ve içeriğin her istekle birlikte oluşturulduğunu onaylamak için sayfayı yenileyin. İşiniz bittiğinde sunucuyu durdurun.

> [!Tip]
> Projeyi durdurma ve yeniden başlatmanın bir kısayolu, hata **ayıklama**  >  **yeniden başlatma** menü komutunu (**CTRL** + **SHIFT** + **F5**) veya hata ayıklama araç çubuğundaki **Yeniden Başlat** düğmesini kullanmaktır:
>
> ![Visual Studio 'da hata ayıklama araç çubuğunda yeniden Başlat düğmesi](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Adım 2-4: sayfa şablonu kullanarak bir görünüm Işleme

Kodda HTML oluşturmak çok küçük sayfalarda düzgün çalışır, ancak sayfalar daha karmaşık hale geldi olarak, normalde sayfanın statik HTML bölümlerini (CSS ve JavaScript dosyalarına başvurular ile birlikte) daha sonra dinamik, kod tarafından oluşturulan içerik ekley istediğiniz "sayfa şablonları" olarak korumak istersiniz. Önceki bölümde yalnızca çağrının tarih ve saati dinamiktir ve diğer tüm içerik bir sayfa `now.strftime` şablonuna yerleştirilebilirsiniz.

Django sayfa şablonu, ve ile ile olarak çizili "değişkenler" olarak adlandırılan herhangi bir sayıda değiştirme belirteci içeren bir HTML `{{` `}}` `{{ content }}` bloğudur. Daha sonra Django'nun templating modülü, değişkenleri kodda sizin için dinamik içerikle değiştirir.

Aşağıdaki adımlar sayfa şablonlarının kullanımını gösteriyor:

1. Django projesini içeren *BasicProject* klasörünün altında *settings.py* dosyasını açın ve "HelloDjangoApp" uygulama adını listeye `INSTALLED_APPS` ekleyin. Uygulamayı listeye eklemek, Django projesine bu adla bir uygulama içeren bir klasör olduğunu söyler:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Ayrıca *settings.py,* nesnesinin Django'ya yüklü bir uygulamanın templates klasöründe şablonları araması talimatı olan aşağıdaki satırı (varsayılan olarak dahil `TEMPLATES` edilir) *içerdiğini* emin olun:

    ```json
    'APP_DIRS': True,
    ```

1. Bir değişken içerdiğini gözlemlemek için *HelloDjangoApp* klasöründe *templates/HelloDjangoApp/index.html* sayfa şablonu dosyasını (veya VS 2017 15.7 ve önceki sürümlerde *templates/index.html)* `{{ content }}` açın:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. *HelloDjangoApp* klasöründe views.py  açın ve işlevini `index` yardımcı işlevi kullanan aşağıdaki `django.shortcuts.render` kodla değiştirin. Yardımcı, `render` sayfa şablonlarıyla çalışmak için basitleştirilmiş bir arabirim sağlar. Mevcut tüm deyimleri `from` tutmayı unutmayın.

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

    için ilk bağımsız değişken, gördüğünüz gibi istek nesnesidir ve ardından uygulamanın templates klasöründeki şablon `render` dosyasının *göreli yoludur.* Uygunsa, desteklediği görünüm için bir şablon dosyası adlandırılmıştır. Üçüncü bağımsız değişkeni, `render` daha sonra şablonun başvurduğu değişkenlerin bir sözlüğüdür. Sözlüğe nesne ekleyebilirsiniz, bu durumda şablondaki bir değişken başvuru yapabilir `{{ object.property }}` .

1. Projeyi çalıştırın ve çıktıyı gözlemleyin. Bu şekilde, şablonun çalışıp çalışmadığını belirten, 2-2 adımında görülen benzer bir ileti görmeniz gerekir.

    Ancak, özellikte kullandığınız HTML 'nin `content` yalnızca düz metin olarak işlediğini gözlemleyin, çünkü `render` işlev OTOMATIK olarak HTML 'den çıkar. Otomatik kaçış, yanlışlıkla güvenlik açıklarına ekleme saldırıları önler: geliştiriciler genellikle bir sayfadan giriş toplar ve bir şablon yer tutucusu aracılığıyla başka bir değer olarak bu değeri kullanır. Kaçış Ayrıca, HTML 'nin sayfa şablonunda ve kodun dışında tutulması için daha iyi bir anımsatıcı işlevi görür. Neyse ki, gerektiğinde ek değişkenler oluşturmanın basit bir önemi vardır. Örneğin, bir sayfa başlığı ekleyen ve sayfa şablonunda tüm biçimlendirmeyi tutan aşağıdaki işaretlerle eşleşecek şekilde *index.html* 'yi *şablonlarla* değiştirin:

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

    Ardından `index` , sayfa şablonundaki tüm değişkenler için değerler sağlamak üzere görünüm işlevini aşağıdaki şekilde yazın:

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

1. Sunucuyu durdurup projeyi yeniden başlatın ve sayfanın artık düzgün şekilde işlediğini gözlemleyin:

    ![Şablonu kullanarak uygulamayı çalıştırma](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 sürüm 15,7 ve önceki sürümler: son bir adım olarak, şablonlarınızı uygulamanız ile aynı adlı bir alt klasöre taşıyın. Bu, bir ad alanı oluşturur ve projeye ekleyebileceğiniz diğer uygulamalarla olası çakışmaları önler. (VS 2017 'deki şablonlar 15.8 + bunu sizin için otomatik olarak yapın.) Diğer bir deyişle, *Merhaba docgoapp* adlı *şablonlarda* bir alt klasör oluşturun, *index.html* 'yi bu alt klasöre taşıyın ve `index` Görünüm Işlevini, şablonun yeni yoluna, *Merhaba docgoapp/index.html* öğesine başvuracak şekilde değiştirin. Ardından projeyi çalıştırın, sayfanın düzgün şekilde işlediğini doğrulayın ve sunucuyu durdurun.

1. Değişikliklerinizi kaynak denetimine kaydedin ve isterseniz, uzak deponuzu [adım 2-2](#commit-to-source-control)' de açıklandığı gibi güncelleştirin.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: Sayfa şablonlarının ayrı bir dosyada olması gerekir mi?

Cevap: Şablonlar genellikle ayrı HTML dosyalarında korunsa da satır içi şablon da kullanabilirsiniz. Ancak işaretleme ile kod arasında temiz bir ayrım yapmak için ayrı bir dosya kullanılması önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: Şablonlar .html dosya uzantısını kullanmalı mı?

Cevap: sayfa şablonu dosyaları için *.html* uzantısı tamamen isteğe bağlıdır çünkü her zaman işlevin ikinci bağımsız değişkende dosyanın tam göreli yolunu `render` tanımlayabilirsiniz. Ancak Visual Studio (ve diğer düzenleyiciler) genellikle *.html* dosyalarıyla kod tamamlama ve söz dizimi renklendirmesi gibi özellikler sunar. Bu özellik, sayfa şablonlarının tamamen HTML olmadığının ağır basıyor olmasıdır.

Aslında bir Django projesiyle çalışırken, Visual Studio html dosyasının aslında bir Django şablonu olduğunu otomatik olarak algılar ve belirli otomatik tamamlama özellikleri sağlar. Örneğin, bir Django sayfa şablonu açıklaması yazmaya `{#` başladığınızda, Visual Studio otomatik olarak kapatma karakterleri `#}` verir. Açıklama **Seçimi ve** **Açıklama Seçimini Kaldır komutları** (Gelişmiş Menüyü Düzenle menüsünde ve araç çubuğunda) HTML açıklamalarının yerine şablon   >   açıklamalarını da kullanır.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Soru: Projeyi çalıştırarak şablonun bulunamadı hatasıyla karşılaştım. Ne oldu?

Cevap: Şablonun bulunamaysinde hatalar görüyorsanız, uygulamayı Django projesinin listesine *settings.py* emin `INSTALLED_APPS` olun. Bu giriş olmadan Django, uygulamanın templates klasörüne *bakarak bilgi edinmeden* önce bu klasöre bakabilirsiniz.

### <a name="question-why-is-template-namespacing-important"></a>Soru: Şablon adları neden önemlidir?

Cevap: Django, işlevde başvurulan bir şablona bakarak önce göreli yol ile eşleşen `render` dosyayı kullanır. Aynı projede şablonlar için aynı klasör yapılarını kullanan birden çok Django uygulamanız varsa, büyük olasılıkla bir uygulama başka bir uygulamanın şablonlarını kullanmak ister. Bu tür hatalardan kaçınmak için her zaman bir uygulamanın *Şablonlar* klasörü altında, herhangi bir yinelemeyi önlemek için uygulamanın adıyla eşleşen bir alt klasör oluşturun.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Daha derin git

- [Ilk Docgo uygulamanızı yazma, Bölüm 1-görünümler](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Dahil ve devralma gibi Docgo şablonlarının daha fazla özelliği için bkz [. docgo şablonu dili](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Inlearning (LinkedIn) için [normal ifade eğitimi](https://www.linkedin.com/learning/topics/regular-expressions)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
