---
title: Visual Studio adım 2, görünümler ve sayfa şablonları Django öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temellerinin bir walkthrough, özellikle bir uygulama oluşturma adımları ve görünümler ve şablonlar kullanarak.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302863"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>Adım 2: Görünümler ve sayfa şablonları içeren bir Django uygulaması oluşturun

**Önceki adım: [Visual Studio projesi ve çözümü oluşturma](learn-django-in-visual-studio-step-01-project-and-solution.md)**

Visual Studio projesinde şimdiye kadar sahip olduğunuz şey, bir veya daha fazla Django *uygulaması*çalıştırabilen bir Django *projesinin*yalnızca site düzeyindeki bileşenleridir. Bir sonraki adım, tek bir sayfa ile ilk uygulama nızı oluşturmaktır.

Bu adımda şimdi nasıl öğrenmek:

> [!div class="checklist"]
> - Tek sayfalı bir Django uygulaması oluşturma (adım 2-1)
> - Uygulamayı Django projesinden çalıştırın (adım 2-2)
> - HTML kullanarak görünüm oluşturma (adım 2-3)
> - Django sayfa şablonu kullanarak görünüm oluşturma (adım 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>Adım 2-1: Varsayılan yapıya sahip bir uygulama oluşturma

Django uygulaması, belirli bir amaç için ilgili dosya kümesini içeren ayrı bir Python paketidir. Bir Django projesi, bir web ana bilgisayarTek bir etki alanı adından ayrı giriş noktaları herhangi bir sayıda hizmet verebilir gerçeğini yansıtan uygulamalar, herhangi bir sayıda içerebilir. Örneğin, contoso.com gibi bir etki alanı için bir Django projesi, support.contoso.com için ikinci bir uygulama ve docs.contoso.com için `www.contoso.com`üçüncü bir uygulama içerebilir. Bu durumda, Django projesi site düzeyinde URL yönlendirme ve ayarları *(urls.py* ve *settings.py* dosyalarında) işlerken, her uygulama kendi iç yönlendirmesi, görünümleri, modelleri, statik dosyaları ve yönetim arabirimi aracılığıyla kendi farklı stil ve davranışına sahiptir.

Bir Django uygulaması genellikle standart bir dosya kümesiyle başlar. Visual Studio, bir Django projesi nde bir Django uygulamasını başlatmanın yanı sıra aynı amaca hizmet eden tümleşik bir menü komutu yla birlikte öğe şablonları sağlar:

- Şablonlar: **Çözüm Gezgini'nde**projeyi sağ tıklatın ve**Yeni öğe ekle'yi** **Add** > seçin. Yeni **Öğe Ekle** iletişim kutusunda, **Django 1.9 App** şablonu seçin, **Ad** alanında uygulama adını belirtin ve **Tamam'ı**seçin.

- Tümleşik komut: **Solution Explorer'da**projeyi sağ tıklatın ve**Django ekle uygulamasını**seçin. **Add** >  Bu komut sizi bir ad ister ve bir Django 1.9 uygulaması oluşturur.

    ![Django uygulaması eklemek için menü komutu](media/django/step02-add-django-app-command.png)

Her iki yöntemi de kullanarak "HelloDjangoApp" adında bir uygulama oluşturun. Sonuç, projenizde aşağıdaki tabloda açıklandığı gibi öğeleri içeren bu ada sahip bir klasördür.

![Çözüm Explorer'daki Django uygulama dosyaları](media/django/step02-django-app-in-solution-explorer.png)

| Öğe | Açıklama |
| --- | --- |
| **\_\_init\_\_.py** | Uygulamayı paket olarak tanımlayan dosya. |
| **Geçiş** | Django'nun, modellerdeki değişikliklerle hizalamak üzere veritabanını güncelleştiren komut dosyalarını depoladığı klasör. Django'nun geçiş araçları, veritabanının önceki herhangi bir sürümüne gerekli değişiklikleri uygulayarak geçerli modellere uymasını sağlar. Geçişleri kullanarak, modellerinize odaklanın ve Django'nun temel veritabanı şemasını ele alamasına izin verin. Göçler 6. şimdilik, klasör sadece bir * \_ \_\_\_init .py* dosyası içerir (klasörün kendi Python paketini tanımladığını gösterir). |
| **şablonları** | Django sayfası için bir klasör, uygulama adıyla eşleşen bir klasör içinde tek bir dosya *index.html* içeren şablonlar. (Visual Studio 2017 15.7 ve öncesi, dosya doğrudan *şablonlar* altında yer almaktadır ve adım 2-4 alt klasörü oluşturmanızı emreder.) Şablonlar, görünümlerin bir sayfayı dinamik olarak işlemek için bilgi ekleyebileceği HTML bloklarıdır. Sayfa şablonu "değişkenler", `{{ content }}` *index.html*gibi, bu makalede (adım 2) daha sonra açıklandığı gibi dinamik değerler için yer tutuculardır. Genellikle Django uygulamaları, şablonları uygulama adıyla eşleşen bir alt klasöre yerleştirerek şablonları için bir ad alanı oluşturur. |
| **admin.py** | Uygulamanın veritabanındaki verileri tohumlamak ve düzenleyen için kullanılan yönetim arabirimini (bkz. adım 6) genişletdiğiniz Python dosyası. Başlangıçta, bu dosya yalnızca `from django.contrib import admin`deyimi içerir. Varsayılan olarak, Django, Django projesinin *settings.py* dosyasındaki girişler aracılığıyla standart bir yönetim arabirimi içerir ve *urls.py'daki*varolan girişleri açıklamadan geçirerek açabilirsiniz. |
| **apps.py** | Uygulama için yapılandırma sınıfını tanımlayan bir Python dosyası (bu tablodan sonra aşağıya bakın). |
| **models.py** | Modeller, görünümlerin uygulamanın temel veritabanıyla etkileşimde bulunduğu işlevlerle tanımlanan veri nesneleridir (bkz. adım 6). Django, uygulamaların bu ayrıntılarla ilgilenmesi gerekmemesi için veritabanı bağlantı katmanı sağlar. *models.py* dosyası, modellerinizi oluşturmak için varsayılan bir yerdir ve `from django.db import models`başlangıçta yalnızca deyimi içerir. |
| **tests.py** | Birim testlerinin temel yapısını içeren bir Python dosyası. |
| **views.py** | Görünümler, genellikle bir HTTP isteği alan ve bir HTTP yanıtını döndüren web sayfaları olarak düşündüğünüz görünümlerdir. Görünümler genellikle web tarayıcılarının nasıl görüntüleneceğini bildiği HTML olarak işlenir, ancak görünümün mutlaka görünür olması gerekmez (ara form gibi). Görünüm, sorumluluğu HTML'yi tarayıcıya göndermek olan bir Python işlevi tarafından tanımlanır. views.py *views.py* dosyası, görünümler oluşturmak için varsayılan bir yerdir ve `from django.shortcuts import render`başlangıçta yalnızca deyimi içerir. |

"HelloDjangoApp" adı verirken *apps.py* içeriği aşağıdaki gibi görünür:

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>Soru: Visual Studio'da bir Django uygulaması oluşturmak komut satırında bir uygulama oluşturmaktan farklı mıdır?

Cevap:**Django** **ekle** > uygulama komutunu çalıştırmak veya Django uygulaması şablonuyla**Yeni Öğe** `manage.py startapp <app_name>` **Ekle'yi** > kullanmak Django komutuyla aynı dosyaları üretir. Visual Studio'da uygulama oluşturmanın yararı, uygulama klasörü ve tüm dosyalarının projeye otomatik olarak entegre edilmiş olmasıdır. Projenizde istediğiniz sayıda uygulama oluşturmak için aynı Visual Studio komutunu kullanabilirsiniz.

## <a name="step-2-2-run-the-app-from-the-django-project"></a>Adım 2-2: Uygulamayı Django projesinden çalıştırın

Bu noktada, projeyi Visual Studio'da yeniden çalıştırıyorsanız (araç çubuğu düğmesini veya **Hata** > **Ayıklama Hata Ayıklama'yı**kullanarak), yine de varsayılan sayfayı görürsünüz. Uygulamaya özgü bir sayfa tanımlamanız ve uygulamayı Django projesine eklemeniz gerektiğinden uygulama içeriği görünmez:

1. *HelloDjangoApp* klasöründe, "dizin" adlı bir görünümü tanımlayan aşağıdaki kodla eşleşecek *şekilde views.py* değiştirin:

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. *BasicProject* klasöründe (adım 1'de oluşturulmuş), aşağıdaki kodu en az eşleşecek *şekilde urls.py* değiştirin (isterseniz öğretici yorumları saklayabilirsiniz):

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    Her URL deseni, Django'nun belirli site göreli URL'leri (diğer `https://www.domain.com/`bir şekilde izleyen bölüm) ile yollarını izlediği görünümleri açıklar. Normal ifadeyle `urlPatterns` `^$` başlayan ilk giriş, site kökü için yönlendirmedir, "/". İkinci giriş, `^home$` özellikle "/ev" rotaları. Aynı görünüme giden herhangi bir sayıda yönlendirme niz olabilir.

1. **Merhaba, Django** mesajını görmek için projeyi tekrar çalıştırın! görünümü tarafından tanımlandığı gibi. İşin izlendiğinde sunucuyu durdurun.

### <a name="commit-to-source-control"></a>Kaynak denetimine bağlanma

Kodunuzda değişiklikler yaptığınız ve bunları başarıyla sınadığınız için, değişikliklerinizi gözden geçirmek ve kaynak denetimine işlemek için harika bir zaman. Bu öğreticideki sonraki adımlar, kaynak denetimine yeniden bağlanmanız için uygun zamanları hatırlatır ve sizi bu bölüme geri yönlendirir.

1. **Team Explorer'a**yönlendirilen Visual Studio'nun (aşağıda daire içine alınmış) altındaki değişiklikler düğmesini seçin.

    ![Visual Studio durum çubuğundaki kaynak denetimi değişiklikleri düğmesi](media/django/step02-source-control-changes-button.png)

1. **Takım Gezgini'nde**,"İlk Django uygulamasını oluştur" gibi bir ileti ileti girin ve **Tümünü İşle'yi**seçin. Commit tamamlandığında, yerel olarak oluşturulan karma> bir ileti ** \<görürsünüz. Değişikliklerinizi sunucuyla paylaşmak için eşitleyin.** Değişiklikleri uzak deponuza itmek istiyorsanız, **Eşitle'yi**seçin ve **ardından Giden Taahhütler**altında **Itme'yi** seçin. Ayrıca, uzak bir zamana basmadan önce birden çok yerel taahhüt de biriktirebilirsiniz.

    ![Takım Gezgini'nde uzaklara itme taahhüdü](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>Soru: Yönlendirme dizelerinden önce 'r' öneki nedir?

Cevap: Python'daki bir dizedeki 'r' öneki "ham" anlamına gelir ve Python'a dize içindeki karakterlerden kaçmasını bildirir. Normal ifadeler birçok özel karakter kullandığından, 'r' önekini kullanmak, bu dizeleri bir dizi\\' kaçış karakteri içermelerine göre okumayı çok daha kolay hale getirir.

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>Soru: URL yönlendirme girişlerinde ^ ve $ karakterleri ne anlama gelir?

Cevap: URL desenlerini tanımlayan normal ifadelerde^ "satır başlangıcı" anlamına gelir ve $ yine URL'lerin site köküne (izleyen `https://www.domain.com/`bölüme) görece olduğu "satır sonu" anlamına gelir. Normal ifade `^$` etkili bir şekilde "boş" anlamına `https://www.domain.com/` gelir ve bu nedenle tam URL ile eşleşir (site köküne hiçbir şey eklenmez). Desen `^home$` tam `https://www.domain.com/home/`olarak eşleşir. (Django desen eşleştirme deseni / izleme kullanmaz.)

Eğer normal bir ifade de `^home`bir iz $ kullanmazsanız, o zaman URL desen "ev", "ev", "homestead" ve "home192837" gibi "ev" ile başlayan herhangi *bir* URL eşleşir.

Farklı normal ifadeleri denemek için, [pythex.org](https://www.pythex.org) [regex101.com](https://regex101.com) gibi çevrimiçi araçları deneyin.

## <a name="step-2-3-render-a-view-using-html"></a>Adım 2-3: HTML kullanarak görünüm oluşturma

Şimdiye `index` kadar *views.py* sahip olduğunuz işlev, sayfa için düz metin HTTP yanıtından başka bir şey oluşturmaz. Çoğu gerçek dünya web sayfaları, tabii ki, genellikle canlı verileri içeren zengin HTML sayfaları ile yanıt. Gerçekten de, bir işlevi kullanarak bir görünümü tanımlamak için birincil nedeni böylece dinamik olarak bu içeriği oluşturabilirsiniz.

Bağımsız değişken `HttpResponse` sadece bir dize olduğundan, bir dize içinde istediğiniz herhangi bir HTML oluşturabilirsiniz. Basit bir örnek olarak, işlevi, sayfayı `index` her `from` yenilediğiniz de güncellenen dinamik içeriği kullanarak bir HTML yanıtı oluşturan aşağıdaki kodla (varolan ifadeleri tutma) değiştirin:

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

"Merhaba**Django!** 16 Nisan 2018 Pazartesi 16:28:10". Saati güncellemek ve her istekte içeriğin oluşturulduğunu doğrulamak için sayfayı yenileyin. İşin izlendiğinde sunucuyu durdurun.

> [!Tip]
> Projeyi durdurma ve yeniden başlatmanın kısayolu, Hata > **Ayıklama** Menüsü komutunu **(Ctrl**+**Shift**+**F5)** veya hata ayıklama araç çubuğundaki **Yeniden Başlat** düğmesini kullanmaktır: **Debug**
>
> ![Visual Studio'da hata ayıklama araç çubuğundaki yeniden başlatma düğmesi](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>Adım 2-4: Sayfa şablonu kullanarak görünüm oluşturma

Kodda HTML oluşturmak çok küçük sayfalar için iyi çalışır, ancak sayfalar daha karmaşık hale geldikçe genellikle sayfanızın statik HTML bölümlerini (CSS ve JavaScript dosyalarına yapılan atıflarla birlikte) "sayfa şablonları" olarak korumak istersiniz ve içine dinamik eklersiniz, kod tarafından oluşturulan içerik. Önceki bölümde, yalnızca aramanın `now.strftime` tarih ve saati dinamiktir, bu da diğer tüm içeriğin bir sayfa şablonuna yerleştirilebileceği anlamına gelir.

Django sayfa şablonu, "değişkenler" `{{` `}}`olarak adlandırılan ve ' da `{{ content }}`olduğu gibi . Django'nun baştan çıkarıcı modülü daha sonra değişkenleri kod olarak sağladığınız dinamik içerikle değiştirir.

Aşağıdaki adımlar sayfa şablonlarının kullanımını gösterir:

1. Django projesini içeren *BasicProject* klasörü altında, *settings.py* dosyayı açın ve `INSTALLED_APPS` "HelloDjangoApp" uygulama adını listeye ekleyin. Uygulamayı listeye eklemek, Django projesine bu adı taşıyan bir uygulama içeren bir klasör olduğunu söyler:

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. Ayrıca *settings.py,* nesnenin `TEMPLATES` django'ya yüklü bir uygulamanın *şablonlar* klasöründe şablonları aramasını sağlayan aşağıdaki satırı (varsayılan olarak dahil) içerdiğinden emin olun:

    ```json
    'APP_DIRS': True,
    ```

1. *HelloDjangoApp* klasöründe, *templates/HelloDjangoApp/index.html* sayfası şablon dosyasını (veya vs 2017 15.7 ve daha önce `{{ content }}` *templates/index.html)* açın ve bir değişken içerdiğini gözlemleyin:

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. *HelloDjangoApp* klasöründe, *views.py* açın `index` ve işlevi `django.shortcuts.render` yardımcı işlevi kullanan aşağıdaki kodla değiştirin. Yardımcı, `render` sayfa şablonlarıyla çalışmak için basitleştirilmiş bir arabirim sağlar. Varolan `from` tüm ifadeleri sakladığından emin olun.

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

    Gördüğünüz `render`gibi, ilk bağımsız değişken, uygulamanın *şablonlar* klasöründeki şablon dosyasına göreli yol tarafından izlenen istek nesnesidir. Uygunsa desteklediği görünüm için bir şablon dosyası adlandırılır. Üçüncü bağımsız `render` değişken, şablonun atıfta bulunduğu değişkenler sözlüğüdür. Sözlükte nesneler ekleyebilirsiniz, bu durumda şablondaki bir değişken `{{ object.property }}`.

1. Projeyi çalıştırın ve çıktıyı gözlemleyin. 2-2. adımda görülenve şablonun çalıştığını belirten benzer bir ileti görmeniz gerekir.

    Ancak, `render` işlev otomatik olarak HTML `content` kaçar, çünkü özellik kullanılan HTML yalnızca düz metin olarak işlenir gözlemleyin. Otomatik kaçış, enjeksiyon saldırılarına karşı kazara güvenlik açıklarını önler: geliştiriciler genellikle bir sayfadan giriş toplar ve şablon yer tutucu aracılığıyla başka bir sayfada değer olarak kullanır. Kaçmak, HTML'yi sayfa şablonunda ve kodun dışında tutmanın yine en iyisi olduğunu da hatırlatmaktadır. Neyse ki, gerektiğinde ek değişkenler oluşturmak için basit bir konudur. Örneğin, sayfa başlığı ekleyen ve sayfa şablonundaki tüm biçimlendirmeyi saklayan aşağıdaki biçimlendirmeyle eşleşecek *şablonlarla* *index.html'i* değiştirin:

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

    Ardından, `index` sayfa şablonundaki tüm değişkenler için değerler sağlamak için görünüm işlevini aşağıdaki gibi yazın:

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

1. Sunucuyu durdurun ve projeyi yeniden başlatın ve sayfanın artık düzgün şekilde görüntülenin:

    ![Şablonu kullanarak uygulama çalıştırma](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 sürüm 15.7 ve daha önceki sürüm: Son adım olarak, şablonlarınızı uygulamanızla aynı adlandırılmış bir alt klasöre taşıyın, bu da bir ad alanı oluşturur ve projeye ekleyebileceğiniz diğer uygulamalarla olası çakışmaları önler. (VS 2017 15.8+ şablonları bunu sizin için otomatik olarak yapar.) Diğer bir deyişle, *HelloDjangoApp*adlı *şablonlarda* bir alt klasör oluşturun, *index.html'i* bu alt klasöre taşıyın ve şablonun `index` yeni yoluna başvurmak için görünüm işlevini değiştirin, *HelloDjangoApp/index.html.* Ardından projeyi çalıştırın, sayfanın düzgün işleyip işlemediğini doğrulayın ve sunucuyu durdurun.

1. Değişikliklerinizi kaynak denetimine bağla ve istenirse, [adım 2-2](#commit-to-source-control)altında açıklandığı gibi uzaktan deponuzu güncelleştirin.

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>Soru: Sayfa şablonları ayrı bir dosyada olmak zorunda mı?

Yanıt: Şablonlar genellikle ayrı HTML dosyalarında muhafaza edilebilse de, satır içinde şablon da kullanabilirsiniz. Ancak, biçimlendirme ve kod arasında temiz bir ayrım sağlamak için ayrı bir dosya kullanılması önerilir.

### <a name="question-must-templates-use-the-html-file-extension"></a>Soru: Şablonlar .html dosya uzantısını kullanmalı mı?

Cevap: Sayfa şablonu dosyalarının *.html* uzantısı tamamen isteğe bağlıdır, çünkü `render` her zaman işleve ikinci bağımsız değişkende dosyaya giden tam göreli yolu tanımlarsınız. Ancak, Visual Studio (ve diğer editörler) genellikle sayfa şablonları kesinlikle HTML olmadığı gerçeğini ağır basar *.html* dosyaları ile kod tamamlama ve sözdizimi renklendirme gibi özellikler verir.

Aslında, bir Django projesiyle çalışırken Visual Studio, düzenlediğiniz HTML dosyasının aslında bir Django şablonu olduğunu otomatik olarak algılar ve belirli otomatik tamamlama özellikleri sağlar. Örneğin, bir Django sayfası şablonu yorum `{#`yazmaya başladığınızda, Visual `#}` Studio otomatik olarak kapanış karakterleri verir. **Yorum Seçimi** ve **Yorumsuz Seçim** komutları **(Gelişmiş'i** **Edit** > menüsünde ve araç çubuğunda) HTML yorumları yerine şablon açıklamaları da kullanır.

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>Soru: Projeyi çalıştırdığımda şablonun bulunamadığı bir hata görüyorum. Ne oldu?

Yanıt: Şablonun bulunamadığı hataları görürseniz, uygulamayı Django projesinin *listedeki settings.py* eklediğinizden `INSTALLED_APPS` emin olun. Bu giriş olmadan, Django uygulamanın *şablonlar* klasörüne bakmayı bilemez.

### <a name="question-why-is-template-namespacing-important"></a>Soru: Şablon adaralığı neden önemlidir?

Cevap: Django `render` işlevde atıfta bulunulan bir şablon aradığında, önce göreli yola uyan hangi dosyayı bulursa onu kullanır. Aynı projede şablonlar için aynı klasör yapılarını kullanan birden fazla Django uygulamanız varsa, bir uygulamanın istemeden başka bir uygulamadan şablon kullanması olasıdır. Bu tür hataları önlemek için, her zaman bir uygulamanın *şablonlar* klasörünün altında, herhangi bir yinelemeyi önlemek için uygulamanın adıyla eşleşen bir alt klasör oluşturun.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Statik dosyalara hizmet, sayfa ekleme ve şablon kalıtımını kullanma](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>Daha derine inin

- [İlk Django uygulaması, bölüm 1 yazma - views](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) (docs.djangoproject.com)
- Içerir ve devralma gibi Django şablonlarının daha fazla yeteneği için Bkz. [Django şablon dili](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- [inLearning](https://www.linkedin.com/learning/topics/regular-expressions) (LinkedIn) üzerinde düzenli ifade eğitimi
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
