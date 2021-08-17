---
title: adım 2, görünümler ve sayfa şablonunda docgo öğreticisini öğrenin Visual Studio
titleSuffix: ''
description: Visual Studio projeler bağlamında, özellikle bir uygulama oluşturma ve görünümleri ve şablonları kullanma adımları hakkında bir adım adım yönergeler.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 306e560c0f27b7ae17f71ddb82cb651fa46a1c97
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038558"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>2. Adım: görünümler ve sayfa şablonlarıyla bir Docgo uygulaması oluşturma

**önceki adım: [Visual Studio bir proje ve çözüm oluşturma](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Visual Studio projesinde şimdiye kadar olan özellikler, bir ya da daha fazla docgo *uygulaması* çalışabilen bir docgo *projesinin* yalnızca site düzeyi bileşenleridir. Sonraki adım, ilk uygulamanızı tek bir sayfa ile oluşturmaktır.

Bu adımda şu adımları öğrenebilirsiniz:

> [!div class="checklist"]
> - Tek sayfalı bir Docgo uygulaması oluşturma (adım 2-1)
> - Uygulamayı Docgo projesinden çalıştırın (adım 2-2)
> - HTML kullanarak bir görünüm işleme (adım 2-3)
> - Docgo sayfa şablonu kullanarak bir görünüm işleme (adım 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Adım 2-1: varsayılan yapıyla uygulama oluşturma

Docgo uygulaması, belirli bir amaç için ilgili dosyalar kümesi içeren ayrı bir Python paketidir. Bir Docgo projesi herhangi bir sayıda uygulama içerebilir ve bu da bir Web konağının tek bir etki alanı adından herhangi bir sayıda ayrı giriş noktasına hizmeti verebildiği olguyu yansıtır. Örneğin, contoso.com gibi bir etki alanı için bir Docgo projesi, için bir uygulama `www.contoso.com` , support.contoso.com için ikinci bir uygulama ve docs.contoso.com için bir üçüncü uygulama içerebilir. Bu durumda, Docgo projesi site düzeyinde URL yönlendirme ve ayarlarını işler ( *URLs.py* ve *Settings.py* dosyalarında), her uygulamanın kendi ayrı stil ve kendi iç yönlendirme, görünümler, modeller, statik dosyalar ve yönetim arabirimi aracılığıyla davranışı vardır.

Bir Docgo uygulaması genellikle standart bir dosya kümesiyle başlar. Visual Studio, aynı amaca hizmet eden tümleşik bir menü komutuyla birlikte docgo projesi içinde docgo uygulamasını başlatmak için öğe şablonları sağlar:

- Şablonlar: **Çözüm Gezgini**, projeye sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** Iletişim kutusunda **docgo 1,9 uygulama** şablonunu seçin, **ad** alanında uygulama adını belirtin ve **Tamam**' ı seçin.

- Tümleşik komut: **Çözüm Gezgini**' de projeye sağ tıklayın ve   >  **docgo uygulaması** Ekle ' yi seçin. Bu komut sizden bir ad ister ve bir Docgo 1,9 uygulaması oluşturur.

    ![Docgo uygulaması ekleme menü komutu](media/django/step02-add-django-app-command.png)

Her iki yöntemi kullanarak, "Hellodocgoapp" adlı bir uygulama oluşturun. Sonuç, aşağıdaki tabloda açıklandığı gibi öğeleri içeren bu ada sahip projenizdeki bir klasördür.

![Çözüm Gezgini 'de docgo uygulama dosyaları](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| Öğe | Açıklama |
| --- | --- |
| **\_\_init \_ \_ . Kopyala** | Uygulamayı paket olarak tanımlayan dosya. |
| **geçişler** | Docgo 'nun, modellerdeki değişikliklerle uyum sağlamak üzere veritabanını güncelleştiren betikleri sakladığı bir klasör. Docgo 'nun geçiş araçları, geçerli modellerle eşleşecek şekilde veritabanının önceki bir sürümüne gerekli değişiklikleri uygular. Geçişleri kullanarak, yaptığınız geçişlerinizi modellerinize koruyun ve temel veritabanı şemasını Docgo 'ya izin verin. Geçişler adım 6 ' da ele alınmıştır. Şimdilik, klasör yalnızca bir *\_ \_ init \_ \_ . Kopyala* dosyası içerir (klasörün kendi Python paketini tanımladığını gösterir). |
| **templates** | Uygulama adıyla eşleşen bir klasör içinde tek bir dosya *index.html* Içeren Docgo sayfa şablonları için bir klasör. (Visual Studio 2017 15,7 ve önceki sürümlerde, dosya doğrudan *şablonlar* altında bulunur ve adım 2-4 alt klasörü oluşturmanızı söyler.) Şablonlar, görünümün dinamik olarak bir sayfayı işlemek için bilgi ekleyebileceği HTML bloklarıdır. index.html içindeki gibi sayfa şablonu "değişkenleri", `{{ content }}` Bu makalenin ilerleyen kısımlarında açıklandığı gibi dinamik değerler için yer tutuculardır (2. adım).  Genellikle Docgo uygulamaları, uygulama adıyla eşleşen bir alt klasöre yerleştirerek şablonları için bir ad alanı oluşturur. |
| **admin.py** | Uygulamanın yönetim arabirimini genişletmenizi sağlayan Python dosyası (bkz. 6. adım), bir veritabanındaki verileri tohum ve düzenlemek için kullanılır. Başlangıçta, bu dosya yalnızca ifadesini içerir, `from django.contrib import admin` . Varsayılan olarak, Docgo, *URLs.py* içindeki mevcut girişlerin açıklamasını kaldırarak, docgo projesinin *Settings.py* dosyasındaki girişler aracılığıyla standart bir yönetim arabirimi içerir. |
| **apps.py** | Uygulama için bir yapılandırma sınıfı tanımlayan Python dosyası (bu tablodan sonra aşağıya bakın). |
| **models.py** | Modeller, uygulamanın temel alınan veritabanıyla etkileşime geçen görünümler tarafından tanımlanan veri nesneleridir (bkz. 6. adım). Docgo, uygulamaların bu ayrıntılarla ilgilenmesini gerektirmeyen veritabanı bağlantısı katmanını sağlar. *Models.py* dosyası, modellerinizin oluşturulacağı varsayılan bir yerdir ve başlangıçta yalnızca ifadesini içerir `from django.db import models` . |
| **tests.py** | Birim testlerinin temel yapısını içeren bir Python dosyası. |
| **views.py** | Görünümler, genellikle bir HTTP isteği alıp HTTP yanıtı döndüren Web sayfaları olarak düşündüğünüzden oluşur. Görünümler genellikle Web tarayıcılarının nasıl görüntüleneceğini bildiğiniz HTML olarak işlenir, ancak bir görünümün görünür olması gerekmez (bir ara form gibi). Bir görünüm bir Python işlevi tarafından tanımlanır ve bu da sorumluluğu tarayıcıya gönderilmek üzere HTML 'yi işlemek için kullanılır. *Views.py* dosyası, görünümlerin oluşturulacağı ve başlangıçta yalnızca deyimin bulunduğu varsayılan bir yerdir `from django.shortcuts import render` . |
::: moniker-end

::: moniker range=">=vs-2019"
| Öğe | Açıklama |
| --- | --- |
| **\_\_init \_ \_ . Kopyala** | Uygulamayı paket olarak tanımlayan dosya. |
| **geçişler** | Docgo 'nun, modellerdeki değişikliklerle uyum sağlamak üzere veritabanını güncelleştiren betikleri sakladığı bir klasör. Docgo 'nun geçiş araçları, geçerli modellerle eşleşecek şekilde veritabanının önceki bir sürümüne gerekli değişiklikleri uygular. Geçişleri kullanarak, yaptığınız geçişlerinizi modellerinize koruyun ve temel veritabanı şemasını Docgo 'ya izin verin. Geçişler, [Docgo belgelerinde](https://docs.djangoproject.com/en/3.2/topics/migrations/)ele alınmıştır. Şimdilik, klasör yalnızca bir *\_ \_ init \_ \_ . Kopyala* dosyası içerir (klasörün kendi Python paketini tanımladığını gösterir). |
| **templates** | Uygulama adıyla eşleşen bir klasör içinde tek bir dosya *index.html* Içeren Docgo sayfa şablonları için bir klasör. (Visual Studio 2017 15,7 ve önceki sürümlerde, dosya doğrudan *şablonlar* altında bulunur ve adım 2-4 alt klasörü oluşturmanızı söyler.) Şablonlar, görünümün dinamik olarak bir sayfayı işlemek için bilgi ekleyebileceği HTML bloklarıdır. index.html içindeki gibi sayfa şablonu "değişkenleri", `{{ content }}` Bu makalenin ilerleyen kısımlarında açıklandığı gibi dinamik değerler için yer tutuculardır (2. adım).  Genellikle Docgo uygulamaları, uygulama adıyla eşleşen bir alt klasöre yerleştirerek şablonları için bir ad alanı oluşturur. |
| **admin.py** | Bir veritabanındaki verileri tohum ve düzenlemek için kullanılan, uygulamanın yönetim arabirimini genişletmenizi sağlayan Python dosyası. Başlangıçta, bu dosya yalnızca ifadesini içerir, `from django.contrib import admin` . Varsayılan olarak, Docgo, *URLs.py* içindeki mevcut girişlerin açıklamasını kaldırarak, docgo projesinin *Settings.py* dosyasındaki girişler aracılığıyla standart bir yönetim arabirimi içerir. |
| **apps.py** | Uygulama için bir yapılandırma sınıfı tanımlayan Python dosyası (bu tablodan sonra aşağıya bakın). |
| **models.py** | Modeller, uygulamanın temel alınan veritabanıyla etkileşime geçen görünümler tarafından tanımlanan veri nesneleridir. Docgo, uygulamaların bu ayrıntılarla ilgilenmesini gerektirmeyen veritabanı bağlantısı katmanını sağlar. *Models.py* dosyası, modellerinizin oluşturulacağı varsayılan bir yerdir ve başlangıçta yalnızca ifadesini içerir `from django.db import models` . |
| **tests.py** | Birim testlerinin temel yapısını içeren bir Python dosyası. |
| **views.py** | Görünümler, genellikle bir HTTP isteği alıp HTTP yanıtı döndüren Web sayfaları olarak düşündüğünüzden oluşur. Görünümler genellikle Web tarayıcılarının nasıl görüntüleneceğini bildiğiniz HTML olarak işlenir, ancak bir görünümün görünür olması gerekmez (bir ara form gibi). Bir görünüm bir Python işlevi tarafından tanımlanır ve bu da sorumluluğu tarayıcıya gönderilmek üzere HTML 'yi işlemek için kullanılır. *Views.py* dosyası, görünümlerin oluşturulacağı ve başlangıçta yalnızca deyimin bulunduğu varsayılan bir yerdir `from django.shortcuts import render` . |
::: moniker-end

*Apps.py* Içeriği "Hellodocgoapp" adı kullanılırken şöyle görünür:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>soru: komut satırında uygulama oluşturmaktan farklı Visual Studio ' de bir docgo uygulaması oluşturuluyor mu?

Cevap:   >  **docgo uygulaması** Ekle komutunu çalıştırma veya   >  docgo uygulama şablonuyla **Yeni öğe** Ekle ' nin kullanılması docgo komutuyla aynı dosyaları oluşturur `manage.py startapp <app_name>` . uygulamayı Visual Studio oluşturma avantajı, uygulama klasörünün ve tüm dosyalarının proje ile otomatik olarak tümleştirildiği bir avantajdır. projenizde herhangi bir sayıda uygulama oluşturmak için aynı Visual Studio komutunu kullanabilirsiniz.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Adım 2-2: uygulamayı Docgo projesinden çalıştırma

bu noktada, projeyi Visual Studio yeniden çalıştırırsanız (araç çubuğu **düğmesini veya hata ayıklama**  >  **başlatma hata ayıklamayı** kullanarak), yine de varsayılan sayfayı görürsünüz. Uygulamaya özgü bir sayfa tanımlamanız ve uygulamayı Docgo projesine eklemeniz gerektiğinden hiçbir uygulama içeriği görünmez:

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

    Her URL modelinde, Docgo 'nun belirli siteyle ilgili URL 'Leri yönlendirdiğini (diğer bir deyişle, izleyen bölüm) açıklayan görünümler açıklanmaktadır `https://www.domain.com/` . `urlPatterns`Normal ifadeyle başlayan ilk giriş, `^$` "/" site kökünün yönlendirimiyle. İkinci girdi, `^home$` özellikle "/Home" yollar. Aynı görünümde herhangi bir sayıda üretim akışı olabilir.

1. **Hello, Docgo** iletisini görmek için projeyi yeniden çalıştırın! görünümü tarafından tanımlandığı gibi. İşiniz bittiğinde sunucuyu durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine Kaydet

Kodunuzda değişiklik yaptığınız ve bunları başarıyla test ettiğiniz için, değişiklikleri gözden geçirmek ve kaynak denetimine uygulamak harika bir süredir. Bu öğreticideki sonraki adımlar, kaynak denetimine yeniden kaydolmasını ve bu bölüme geri dönebilmeniz için uygun zamanları hatırlatır.

1. **Takım Gezgini** giden Visual Studio (aşağıda daire içinde) altındaki değişiklikler düğmesini seçin.

    ![Visual Studio durum çubuğunda kaynak denetimi değişiklikleri düğmesi](media/django/step02-source-control-changes-button.png)

1. **Takım Gezgini**, "Ilk Docgo uygulaması oluşturma" gibi bir teslim iletisi girin ve **Tümünü Yürüt**' ü seçin. Tamamlama tamamlandığında **yerel olarak oluşturulan bir Ileti kaydı görürsünüz \<hash> . Değişikliklerinizi sunucuyla paylaşmak için eşitleyin.** Değişiklikleri uzak deponuza göndermek istiyorsanız **Eşitle**' yi ve ardından **giden işlemeler** altında **Gönder** ' i seçin. Ayrıca, uzaktan göndermeden önce birden çok yerel işleme de birikmeniz gerekir.

    ![Takım Gezgini 'da yürütmeleri uzak 'a gönderme](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Soru: yönlendirme dizelerinden önce ' r ' öneki nedir?

Cevap: Python 'daki bir dizedeki ' r ' öneki "RAW" anlamına gelir, bu da Python 'un dize içindeki herhangi bir karakteri atmamasını sağlar. Normal ifadeler çok sayıda özel karakter kullandığından, ' r ' önekini kullanmak Bu dizelerin bir dizi ' ' kaçış karakteri içerenden çok daha kolay olmasını sağlar \\ .

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Soru: URL yönlendirme girişlerinde ^ ve $ karakterlerinin anlamı nedir?

Cevap: URL düzenlerini tanımlayan normal ifadelerde, ^ "satır başlangıcı" ve $ "satır sonu" anlamına gelir ve burada URL 'Ler site köküne (izleyen bölüm) göre değişir `https://www.domain.com/` . Normal ifade `^$` etkin bir şekilde "boş" anlamına gelir ve bu nedenle tam URL ile eşleşir `https://www.domain.com/` (site köküne hiçbir şey eklenmez). Desenler `^home$` tam olarak eşleşir `https://www.domain.com/home/` . (Docgo, sondaki/ın örüntüme düzeniyle eşleştirmeyi kullanmaz.)

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
> ![Visual Studio hata ayıklama araç çubuğundaki yeniden Başlat düğmesi](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Adım 2-4: sayfa şablonu kullanarak bir görünüm Işleme

Kodda HTML oluşturma çok küçük sayfalar için sorunsuz çalışıyor, ancak sayfalar daha karmaşık bir şekilde elde ederken, daha sonra dinamik, kod tarafından oluşturulan içerik eklediğiniz "sayfa şablonları" olarak sayfanızın statik HTML parçalarını (CSS ve JavaScript dosyalarına başvurularıyla birlikte) korumak istersiniz. Önceki bölümde yalnızca çağrının Tarih ve saati `now.strftime` dinamiktir. Bu, diğer tüm içeriklerin bir sayfa şablonuna yerleştirilebileceği anlamına gelir.

Bir Docgo sayfa şablonu, ' `{{` de olduğu gibi ve tarafından ayırıcı olan "değişkenler" adlı herhangi bir sayıda değiştirme belirteci içerebilen BIR HTML bloğudur `}}` `{{ content }}` . Docgo 'nın şablon oluşturma modülü daha sonra değişkenleri kodda sağladığınız Dinamik içerikle değiştirir.

Aşağıdaki adımlarda sayfa şablonlarının kullanımı gösterilmektedir:

1. Docgo projesini içeren *BasicProject* klasörünün altında, *Settings.py* dosyasını açın ve "Hellodocgoapp" uygulama adını `INSTALLED_APPS` listeye ekleyin. Uygulamanın listeye eklenmesi, Docgo projesine, bir uygulama içeren bu adın bir klasörü olduğunu söyler:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Ayrıca, *Settings.py*' de, `TEMPLATES` nesnenin aşağıdaki satırı (varsayılan olarak dahildir) içerdiğinden emin olun. Bu, docgo 'nun yüklü bir uygulamanın *Şablonlar* klasöründeki şablonları aramasını sağlar:

    ```json
    'APP_DIRS': True,
    ```

1. *Merhaba docgoapp* klasöründe, bir değişken içerdiğini gözlemlemek için *Templates/hellodocgoapp/index.html* sayfa şablonu dosyasını (veya vs 2017 15,7 ve önceki sürümlerde *Şablonlar/index.html* ) açın `{{ content }}` :

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. *Merhaba Docgoapp* klasöründe *views.py* ' ı açın ve `index` işlevi, yardımcı işlevini kullanan aşağıdaki kodla değiştirin `django.shortcuts.render` . `render`Yardımcı, sayfa şablonlarıyla çalışmak için basitleştirilmiş bir arabirim sağlar. Tüm mevcut deyimleri tutmaya dikkat edin `from` .

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

    İçin ilk bağımsız değişken, `render` görebileceğiniz gibi, istek nesnesidir ve sonra uygulamanın *Şablonlar* klasörü içindeki şablon dosyasının göreli yolu gelir. Uygunsa, desteklediği görünüm için bir şablon dosyası adlandırılır. Üçüncü bağımsız değişkeni, `render` daha sonra şablonun başvurduğu değişkenlerin bir sözlüğüdür. Sözlüğe nesne ekleyebilirsiniz, bu durumda şablondaki bir değişken başvuru yapabilir `{{ object.property }}` .

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

1. <a name="template-namespacing"></a>Visual Studio 2017 sürüm 15,7 ve önceki sürümler: son bir adım olarak, şablonlarınızı uygulamanız ile aynı adlı bir alt klasöre taşıyın. bu, bir ad alanı oluşturur ve projeye ekleyebileceğiniz diğer uygulamalarla olası çakışmaları önler. (VS 2017 'deki şablonlar 15.8 + bunu sizin için otomatik olarak yapın.) Diğer bir deyişle, *Merhaba docgoapp* adlı *şablonlarda* bir alt klasör oluşturun, *index.html* 'yi bu alt klasöre taşıyın ve `index` Görünüm Işlevini, şablonun yeni yoluna, *Merhaba docgoapp/index.html* öğesine başvuracak şekilde değiştirin. Ardından projeyi çalıştırın, sayfanın düzgün şekilde işlediğini doğrulayın ve sunucuyu durdurun.

1. Değişikliklerinizi kaynak denetimine kaydedin ve isterseniz, uzak deponuzu [adım 2-2](#commit-to-source-control)' de açıklandığı gibi güncelleştirin.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: sayfa şablonlarının ayrı bir dosyada olması gerekir mi?

Cevap: Şablonlar genellikle ayrı HTML dosyalarında tutulabilse de, bir satır içi şablonu da kullanabilirsiniz. Ancak, biçimlendirme ve kod arasında temiz ayrımı sürdürmek için, ayrı bir dosya kullanılması önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: Şablonlar .html dosya uzantısını kullanmalıdır mi?

Cevap: işlev şablonu dosyaları için *.html* uzantısı tamamen isteğe bağlıdır, çünkü her zaman işleve ikinci bağımsız değişkende dosyanın tam yolunu belirleyebilirsiniz `render` . ancak, Visual Studio (ve diğer düzenleyiciler), genellikle, sayfa şablonlarının tamamen HTML olmadığı gerçeğini izleyen *.html* dosyalarla kod tamamlama ve söz dizimi renklendirme gibi özellikler sağlar.

aslında, bir docgo projesiyle çalışırken, düzenlemekte olduğunuz HTML dosyası gerçekte bir docgo şablonu olduğunda Visual Studio otomatik olarak algılar ve belirli otomatik tamamlanmış özellikleri sağlar. örneğin, bir docgo sayfa şablonu açıklaması yazmaya başladığınızda `{#` Visual Studio otomatik olarak kapanış `#}` karakterleri verir. **Açıklama seçimi** ve **seçim komutlarının açıklamasını kaldırın** (   >  **Gelişmiş** düzenleme menüsünde ve araç çubuğunda), HTML açıklamaları yerine şablon açıklamalarını de kullanır.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Soru: projeyi çalıştırdığımda, şablonun bulunamadığını belirten bir hata görüyorum. Ne oldu?

Cevap: şablonun bulunamadığını belirten hatalar görürseniz, uygulamayı listede Docgo projesinin *Settings.py* eklediğinizden emin olun `INSTALLED_APPS` . Bu giriş olmadan Docgo, uygulamanın *Şablonlar* klasörünü aramak için bilgi vermez.

### <a name="question-why-is-template-namespacing-important"></a>Soru: Template namespacing neden önemlidir?

Cevap: Docgo, işlevde başvurulan bir şablonu ararken `render` , ilk bulduğu dosyayı göreli yol ile eşleşen bir dosya kullanır. Şablonlar için aynı klasör yapılarını kullanan aynı projede birden çok Docgo uygulamanız varsa, bu, bir uygulamanın başka bir uygulamadaki bir şablonu yanlışlıkla kullanması olasıdır. Bu tür hatalardan kaçınmak için her zaman bir uygulamanın *Şablonlar* klasörü altında, herhangi bir yinelemeyi önlemek için uygulamanın adıyla eşleşen bir alt klasör oluşturun.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Daha derin git

- [Ilk Docgo uygulamanızı yazma, Bölüm 1-görünümler](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Dahil ve devralma gibi Docgo şablonlarının daha fazla özelliği için bkz [. docgo şablonu dili](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Inlearning (LinkedIn) için [normal ifade eğitimi](https://www.linkedin.com/learning/topics/regular-expressions)
- GitHub eğitim kaynak kodu: [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
