---
title: 2. adım, görünümler Visual Studio sayfa şablonunda Django öğreticisi hakkında bilgi edinebilirsiniz
titleSuffix: ''
description: Özel olarak bir uygulama oluşturma ve görünümleri ve şablonları kullanma Visual Studio Django temel bilgilerine yönelik kılavuz.
ms.date: 11/19/2018
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 669c3dfb552024002569a83460dda6877219da20
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972238"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>2. Adım: Görünümler ve sayfa şablonlarıyla Django uygulaması oluşturma

**Önceki adım: [Visual Studio proje ve çözüm oluşturma](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Şu ana kadar Visual Studio *Django* projesinin bir veya daha fazla Django uygulaması çalıştıracak site düzeyinde *bileşenleridir.* Sonraki adım, tek bir sayfayla ilk uygulamanızı oluşturmak olacak.

Bu adımda şimdi şunların nasıl olduğunu öğreniriz:

> [!div class="checklist"]
> - Tek sayfalı bir Django uygulaması oluşturma (2-1. adım)
> - Uygulamayı Django projesinden çalıştırma (2-2. adım)
> - HTML kullanarak bir görünümü işleme (2-3. adım)
> - Django sayfa şablonu kullanarak görünümü işleme (2-4. adım)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>2-1. Adım: Varsayılan yapıya sahip bir uygulama oluşturma

Django uygulaması, belirli bir amaca yönelik bir dizi ilgili dosya içeren ayrı bir Python paketidir. Bir Django projesi, bir web ana bilgisayarının tek bir etki alanı adına göre herhangi bir sayıda ayrı giriş noktası hizmetine sahip olduğunu yansıtan herhangi bir sayıda uygulama içerebilir. Örneğin, contoso.com gibi bir etki alanı için Django projesi için bir uygulama, support.contoso.com için ikinci bir uygulama `www.contoso.com` ve docs.contoso.com. Bu durumda, Django projesi site düzeyinde URL yönlendirme ve ayarlarını *(urls.py* ve *settings.py* dosyalarında) ele alırken, her uygulama kendi iç yönlendirme, görünümler, modeller, statik dosyalar ve yönetim arabirimi aracılığıyla kendi benzersiz stil ve davranışına sahiptir.

Django uygulaması genellikle standart bir dosya kümesiyle başlar. Visual Studio Django projesi içinde bir Django uygulamasını başlatmak için öğe şablonlarının yanı sıra aynı amaca hizmet eden tümleşik bir menü komutu sağlar:

- Şablonlar: **Çözüm Gezgini,** projeye sağ tıklayın ve Yeni öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim** kutusunda **Django 1.9 Uygulama** şablonunu seçin, Ad alanında uygulama **adını** belirtin ve Tamam'ı **seçin.**

- Tümleşik komut: **Çözüm Gezgini,** projeye sağ tıklayın ve   >  **Django uygulaması ekle'yi seçin.** Bu komut sizden bir ad istenir ve bir Django 1.9 uygulaması oluşturur.

    ![Django uygulaması eklemek için menü komutu](media/django/step02-add-django-app-command.png)

İki yöntemden birini kullanarak "HelloDjangoApp" adıyla bir uygulama oluşturun. Sonuç, projenizin bu adı içeren ve aşağıdaki tabloda açıklandığı gibi öğeleri içeren bir klasördür.

![Çözüm Gezgini'daki Django uygulama Çözüm Gezgini](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| Öğe | Açıklama |
| --- | --- |
| **\_\_init \_ \_ .py** | Uygulamayı paket olarak tanımlayan dosya. |
| **Geçiş** | Django'nun veritabanını modellerde yapılan değişikliklerle uyumlu olacak şekilde güncelleştiren betikleri depolaya bir klasör. Ardından Django'nun geçiş araçları, veritabanının önceki herhangi bir sürümüne gerekli değişiklikleri uygulayarak geçerli modellere eş olur. Geçişleri kullanarak modellerinize odaklanmanız ve Django'nun temel alınan veritabanı şemasını işlemesine izin verirsiniz. Geçişler 6. adımda ele alınmıştır; şimdilik, klasör yalnızca bir *\_ \_ init \_ \_ .py* dosyası içerir (klasörün kendi Python paketini tanımladığına işaret ediyor). |
| **templates** | Uygulama adıyla eşleşen bir klasör içinde tek bir dosya içeren *Djangoindex.html* şablonları klasörü. (Visual Studio 2017 15.7 ve önceki sürümlerde dosya doğrudan  şablonların altında yer almaktadır ve 2-4. adımda size alt klasörü oluşturma talimatı ve ardından 2.4. adım yer almaktadır.) Şablonlar, görünümlerin sayfayı dinamik olarak işlemek için bilgi ekleyabildikleri HTML bloklarıdır. index.htmlgibi sayfa şablonu "değişkenleri", bu makalenin devamlarında (2. adım) açıklanan dinamik değerler için `{{ content }}` yer tutuculardır. ** Django uygulamaları genellikle şablonları için uygulama adıyla eşleşen bir alt klasöre yerleştirerek bir ad alanı oluşturur. |
| **admin.py** | Uygulamanın yönetim arabirimini genişletilen Python dosyası (bkz. 6. adım). Bu dosya, veritabanındaki verilerin çekirdeğini oluşturmak ve düzenlemek için kullanılır. Başlangıçta, bu dosya yalnızca deyimini `from django.contrib import admin` içerir. Varsayılan olarak, Django, Django projesinin *settings.py* dosyasındaki girdiler aracılığıyla standart bir yönetim arabirimi içerir. Bu arabiriminde mevcut girdileri kaldırarak *urls.py.* |
| **apps.py** | Uygulama için yapılandırma sınıfını tanımlayan bir Python dosyası (bu tablodan sonra aşağıya bakın). |
| **models.py** | Modeller, görünümlerin uygulamanın temel alınan veritabanıyla etkileşim kurduğu işlevler tarafından tanımlanan veri nesneleridir (bkz. 6. adım). Django, uygulamaların bu ayrıntılarla kendilerini endişeye sokan veritabanı bağlantı katmanını sağlar. Models.py  dosyası, modellerinizi oluşturmak için varsayılan bir yerdir ve başlangıçta yalnızca deyimini `from django.db import models` içerir. |
| **tests.py** | Birim testlerinin temel yapısını içeren bir Python dosyası. |
| **views.py** | Görünümler, genellikle bir HTTP isteği alan ve bir HTTP yanıtı dönüşen web sayfaları olarak düşünebilirsiniz. Görünümler genellikle web tarayıcılarının görüntülemeyi bildiğiniz HTML olarak işler, ancak bir görünümün görünür olması gerekmez (ara form gibi). Görünüm, html'yi tarayıcıya göndermek için işlemek olan bir Python işlevi tarafından tanımlanır. Views.py  dosyası, görünümlerin oluşturulacak varsayılan bir yerdir ve başlangıçta yalnızca deyimini `from django.shortcuts import render` içerir. |
::: moniker-end

::: moniker range=">=vs-2019"
| Öğe | Açıklama |
| --- | --- |
| **\_\_init \_ \_ .py** | Uygulamayı paket olarak tanımlayan dosya. |
| **Geçiş** | Django'nun veritabanını modellerde yapılan değişikliklerle uyumlu olacak şekilde güncelleştiren betikleri depolaya bir klasör. Ardından Django'nun geçiş araçları, veritabanının önceki herhangi bir sürümüne gerekli değişiklikleri uygulayarak geçerli modellere eş olur. Geçişleri kullanarak modellerinize odaklanmanız ve Django'nun temel alınan veritabanı şemasını işlemesine izin verirsiniz. Geçişler [Django belgelerinde ele alınmıştır;](https://docs.djangoproject.com/en/3.2/topics/migrations/) şimdilik, klasör yalnızca bir *\_ \_ init \_ \_ .py* dosyası içerir (klasörün kendi Python paketini tanımladığına işaret ediyor). |
| **templates** | Uygulama adıyla eşleşen bir klasör içinde tek bir dosya içeren *Djangoindex.html* şablonları klasörü. (Visual Studio 2017 15.7 ve önceki sürümlerde dosya doğrudan  şablonların altında yer almaktadır ve 2-4. adımda size alt klasörü oluşturma talimatı ve ardından 2.4. adım yer almaktadır.) Şablonlar, görünümlerin sayfayı dinamik olarak işlemek için bilgi ekleyabildikleri HTML bloklarıdır. index.htmlgibi sayfa şablonu "değişkenleri", bu makalenin devamlarında (2. adım) açıklanan dinamik değerler için `{{ content }}` yer tutuculardır. ** Django uygulamaları genellikle şablonları için uygulama adıyla eşleşen bir alt klasöre yerleştirerek bir ad alanı oluşturur. |
| **admin.py** | Bir veritabanındaki verilerin çekirdeğini oluşturmak ve düzenlemek için kullanılan uygulamanın yönetim arabirimini genişletilen Python dosyası. Başlangıçta, bu dosya yalnızca deyimini `from django.contrib import admin` içerir. Varsayılan olarak, Django, Django projesinin *settings.py* dosyasındaki girdiler aracılığıyla standart bir yönetim arabirimi içerir. Bu arabiriminde mevcut girdileri kaldırarak *urls.py.* |
| **apps.py** | Uygulama için yapılandırma sınıfını tanımlayan bir Python dosyası (bu tablodan sonra aşağıya bakın). |
| **models.py** | Modeller, görünümlerin uygulamanın temel veritabanıyla etkileşim kurduğu işlevler tarafından tanımlanan veri nesneleridir. Django, uygulamaların bu ayrıntılarla kendilerini endişeye sokan veritabanı bağlantı katmanını sağlar. Models.py  dosyası, modellerinizi oluşturmak için varsayılan bir yerdir ve başlangıçta yalnızca deyimini `from django.db import models` içerir. |
| **tests.py** | Birim testlerinin temel yapısını içeren bir Python dosyası. |
| **views.py** | Görünümler, genellikle bir HTTP isteği alan ve bir HTTP yanıtı dönüşen web sayfaları olarak düşünebilirsiniz. Görünümler genellikle web tarayıcılarının görüntülemeyi bildiğiniz HTML olarak işler, ancak bir görünümün görünür olması gerekmez (ara form gibi). Görünüm, html'yi tarayıcıya göndermek için işlemek olan bir Python işlevi tarafından tanımlanır. Views.py  dosyası, görünümlerin oluşturulacak varsayılan bir yerdir ve başlangıçta yalnızca deyimini `from django.shortcuts import render` içerir. |
::: moniker-end

Uygulamanın *içeriği apps.py* "HelloDjangoApp" adı kullanılırken aşağıdaki gibi görünür:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Soru: Bir Django uygulamasını Visual Studio komut satırına uygulama oluşturmaktan farklı bir şey mi?

Cevap: Django uygulama ekle komutunu çalıştırma veya Django uygulama şablonuyla Yeni Öğe Ekle komutunu kullanarak   >     >   Django komutuyla aynı dosyaları `manage.py startapp <app_name>` üretir. Uygulamayı uygulama klasöründe oluşturmanın Visual Studio avantajı, uygulama klasörünün ve tüm dosyalarının projeyle otomatik olarak tümleştirilmiş olduğudır. Projenize herhangi bir Visual Studio oluşturmak için aynı Visual Studio komutunu kullanabilirsiniz.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>2.-2. Adım: Uygulamayı Django projesinden çalıştırma

Bu noktada projeyi bir kez daha Visual Studio (araç çubuğu düğmesini veya Hata Ayıklamayı Başlat) kullanarak) varsayılan  >  sayfayı görmeye devam edebilirsiniz. Uygulamaya özgü bir sayfa tanımlamanız ve uygulamayı Django projesine eklemeniz gerek olduğundan hiçbir uygulama içeriği görüntülanmaz:

1. *HelloDjangoApp* klasöründe, *"index" views.py* bir görünümü tanımlayan aşağıdaki kodla eş değerle eşleşmesi için aşağıdaki kodu değiştirebilirsiniz:

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. *BasicProject* klasöründe (1. adımda oluşturulur), *urls.py* en azından aşağıdaki kodla eşşecek şekilde (1. adımda oluşturulur) değiştirerek açıklamalarını koruyabilirsiniz:

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Her URL düzeni, Django'nun belirli site göreli URL'lerini (yani takip eden bölümü) yönlendiren görünümleri `https://www.domain.com/` açıklar. içinde normal `urlPatterns` ifadeyle başlayan ilk giriş, `^$` "/" site kökü için yönlendirmedir. İkinci girdi, `^home$` özellikle "/Home" yollar. Aynı görünümde herhangi bir sayıda üretim akışı olabilir.

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

    Ancak, özellikte kullandığınız HTML 'nin `content` yalnızca düz metin olarak işlediğini gözlemleyin, çünkü `render` işlev OTOMATIK olarak HTML 'den çıkar. Otomatik kaçış, yanlışlıkla güvenlik açıklarına ekleme saldırıları önler: geliştiriciler genellikle bir sayfadan giriş toplar ve bir şablon yer tutucusu aracılığıyla başka bir değer olarak bu değeri kullanır. Kaçış Ayrıca, HTML 'nin sayfa şablonunda ve kodun dışında tutulması için daha iyi bir anımsatıcı işlevi görür. Neyse ki, gerektiğinde ek değişkenler oluşturmanın basit bir önemi vardır. Örneğin, bir sayfa başlığı ekleyen ve sayfa şablonunda tüm biçimlendirmeyi tutan aşağıdaki biçimlendirmeyle eşleşecek şekilde *Şablonlar* ile *index.html* değiştirin:

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

1. <a name="template-namespacing"></a>Visual Studio 2017 sürüm 15,7 ve önceki sürümler: son bir adım olarak, şablonlarınızı uygulamanız ile aynı adlı bir alt klasöre taşıyın. bu, bir ad alanı oluşturur ve projeye ekleyebileceğiniz diğer uygulamalarla olası çakışmaları önler. (VS 2017 'deki şablonlar 15.8 + bunu sizin için otomatik olarak yapın.) Diğer bir deyişle, *Merhaba docgoapp* adlı *şablonlarda* bir alt klasör oluşturun, *index.html* bu alt klasöre taşıyın ve `index` Görünüm Işlevini, şablonun yeni yoluna, *Merhaba docgoapp/index.html* başvuracak şekilde değiştirin. Ardından projeyi çalıştırın, sayfanın düzgün şekilde işlediğini doğrulayın ve sunucuyu durdurun.

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
