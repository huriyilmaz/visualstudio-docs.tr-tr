---
title: 3. adım, statik Visual Studio sayfalarda Django öğreticisi hakkında bilgi edinebilirsiniz
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django ile ilgili temel bilgiler, özellikle statik dosyaların nasıl hizmet olacağını, uygulamaya sayfa eklip şablon devralmanın nasıl kullan olacağını gösteren kılavuz
ms.date: 01/25/2022
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: edc624c2e862f18ade5889aa275874e946c5164a
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886494"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-django-app"></a>3. Adım: Django uygulamasıyla statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma

**Önceki adım: [Görünümler ve sayfa şablonlarıyla Django uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)**

Bu öğreticinin önceki adımlarında, tek sayfalık kendi içinde HTML ile minimal bir Django uygulaması oluşturma hakkında bilgi edindisiniz. Ancak modern web uygulamaları genellikle birçok sayfadan oluşur ve tutarlı stil ve davranış sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynakları kullanır.

Bu adımda şunların nasıl olduğunu öğreniriz:

> [!div class="checklist"]
> - Kolay Visual Studio farklı türlerde yeni dosyaları hızla eklemek için yeni öğe şablonları kullanma (3-1. adım)
> - Django projesini statik dosyaları hizmet edecek şekilde yapılandırma (3-2. adım)
> - Uygulamaya başka sayfalar ekleme (3-3. adım)
> - Sayfalar arasında kullanılan bir üst bilgi ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma (3-4. adım)

## <a name="step-3-1-become-familiar-with-item-templates"></a>3.-1. Adım: Öğe şablonları hakkında bilgi sahibi olma

Django uygulaması geliştirirken genellikle çok daha fazla Python, HTML, CSS ve JavaScript dosyası eklersiniz. Her dosya türü (dağıtım için ihtiyaçweb.configgibi diğer dosyalar **) için Visual Studio başlamanız için kullanışlı öğe şablonları sağlar.[](python-item-templates.md)

Kullanılabilir şablonları görmek için **Çözüm Gezgini'a** gidin, öğeyi oluşturmak istediğiniz klasöre sağ tıklayın ve **EkleYeni Öğe'yi** >  seçin:

![Yeni öğe ekle iletişim kutusu Visual Studio](media/django/step03-add-new-item-dialog.png)

Şablon kullanmak için istenen şablonu seçin, dosya için bir ad belirtin ve Tamam'ı **seçin**. Bu şekilde bir öğe eklemek, dosyayı otomatik olarak Visual Studio projenize ekler ve değişiklikleri kaynak denetimi için işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Hangi Visual Studio şablonlarını nasıl bilebilirsiniz?

Cevap: Visual Studio dosyası (*.pyproj*) bunu Python projesi olarak işaret alan bir proje türü tanımlayıcısı içerir. Visual Studio, yalnızca proje türüne uygun öğe şablonlarını göstermek için bu tür tanımlayıcısını kullanır. Bu şekilde Visual Studio her zaman sıralamak istemeden birçok proje türü için zengin bir öğe şablonu kümesi sebilirsiniz.

## <a name="step-3-2-serve-static-files-from-your-app"></a>3-2. Adım: Uygulamanıza statik dosyaları hizmet etme

Python ile derlen bir web uygulamasında (herhangi bir çerçeve kullanılarak), Python dosyalarınız her zaman web ana bilgisayarının sunucusunda çalıştırıldı ve hiçbir zaman kullanıcının bilgisayarına aktarıldı. Ancak CSS ve JavaScript gibi diğer dosyalar yalnızca tarayıcı tarafından kullanılır, bu nedenle ana bilgisayar sunucusu isten her durumda olduğu gibi bunları teslim ediyor. Bu tür dosyalar "statik" dosyalar olarak adlandırılır ve Django herhangi bir kod yazmanız gerekmeden bunları otomatik olarak teslim eder.

Django projesi, Django projesinin projesinde yer alan şu satırlar sayesinde varsayılan  olarak uygulamanın statik klasöründen statik dosyaları *settings.py:*

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

Dosyaları, statik içinde istediğiniz herhangi *bir klasör yapısını* kullanarak düzenleyebilir ve ardından bu klasör içindeki göreli yolları kullanarak dosyalara başvurabilirsiniz. Bu işlemi göstermek için, aşağıdaki adımlar uygulamaya bir CSS dosyası ekler ve ardından bu stil *index.htmlkullanın:*

1. Bu **Çözüm Gezgini**, Visual Studio projesinde **HelloDjangoApp** klasörüne sağ tıklayın, **EkleYeni** >  klasör'e tıklayın ve klasöre adını girin`static`.

1. Statik klasöre sağ **tıklayın ve** **EkleYeni** **öğe'yi** >  seçin. Görüntülenen iletişim kutusunda Stil Sayfası şablonunu **seçin**, dosyaya adını ve ardından Tamam'ı `site.css`**seçin**. **Site.css** dosyası projede görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki görüntüye benzer görünse:

    ![Dosyalarda gösterildiği gibi statik Çözüm Gezgini](media/django/step03-static-file-structure.png)

1. *site.css içeriğini aşağıdaki* kodla değiştirin ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın *templates/HelloDjangoApp/index.html* dosyasının içeriğini aşağıdaki kodla değiştirin. Bu kod, `<strong>` 2 `<span>` `message` . adımda kullanılan öğesini stil sınıfına başvurulan bir ile değiştirir. Stil sınıfını bu şekilde kullanmak, öğenin stilini oluşturma konusunda çok daha fazla esneklik sağlar. (VS 2017 15.7 ve önceki sürümleri kullanırken şablonlardaindex.html'ı şablonlarda bir alt klasöre taşınmadıysanız, 2-4. adımda şablon adlarını [](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) saydam hale getirmek için bkz.)** 

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load static %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Sonuçları gözlemlemek için projeyi çalıştırın. Bittiğinde sunucuyu durdurun ve değişikliklerinizi [2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control). adımda açıklanmıştır.

### <a name="question-what-is-the-purpose-of-the--load-static--tag"></a>Soru: {% load static %} etiketinin amacı nedir?

Cevap: ve `{% load static %}` gibi öğelerde statik dosyalara başvurulmadan önce satırı `<head>` gereklidir `<body>`. Bu bölümde gösterilen örnekte "staticfiles", statik dosyalara başvurmak için söz dizimi kullanmanızı sağlayan özel bir Django `{% static %}` şablon etiket kümesine başvurur.  olmadan `{% load static %}`, uygulama çalıştır geldiğinde bir özel durumla karşı karşına gelir.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: Statik dosyaları düzenlemek için herhangi bir kural var mı?

Cevap: Statik klasörünüzdeki diğer CSS, JavaScript ve HTML dosyalarını *istediğiniz* gibi abilirsiniz. Statik dosyaları düzenlemenin tipik bir yolu yazı *tipleri,* betikler ve *içerik (stil* sayfaları ve diğer dosyalar için) adlı alt klasörler oluşturmaktır. Her durumda, bu klasörleri başvurulara dosyanın göreli yoluna dahil edin `{% static %}` .

### <a name="question-can-i-complete-the-same-task-without-using-the--load-static--tag"></a>Soru: {% load static %} etiketini kullanmadan aynı görevi tamamlar musunuz?

Cevap: Evet, bunu siz de 24 saat içinde tamamlarız.

```html
<html>
    <head>
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="../../static/site.css" />
    </head>
    <body>
        <span class="message">{{ message }}</span>{{ content }}
    </body>
</html>
```

## <a name="step-3-3-add-a-page-to-the-app"></a>3-3. Adım: Uygulamaya sayfa ekleme

Uygulamaya başka bir sayfa eklemek şu anlama gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfanın işaretlemesi için bir şablon ekleyin.
- Gerekli yönlendirmeyi Django projesinin *urls.py ekleyin.*

Aşağıdaki adımlar "HelloDjangoApp" projesine bir "Hakkında" sayfası ve giriş sayfasından bu sayfaya bağlantılar ekler:

1. Bu **Çözüm Gezgini** **templates/HelloDjangoApp** klasörüne sağ tıklayın,  > **EkleYeni** öğe'yi seçin, **HTML Sayfası** öğe şablonunu seçin, dosyayı `about.html`olarak adlandırın ve Tamam'ı **seçin**.

    > [!Tip]
    > Ekle **menüsünde Yeni** Öğe komutu görünmüyorsa sunucuyu durdurarak  hata ayıklama modundan Visual Studio emin olun.

1. Giriş sayfasının *about.html* aşağıdaki işaretlemeyle değiştirin (giriş sayfasının açık bağlantısını 3-4. adımda basit bir gezinti çubuğuyla değiştirirsiniz):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load static %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Uygulamanın *views.py dosyasını açın* ve şablonu kullanan adlı `about` bir işlev ekleyin:

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. Django projesinin *urls.py dosyasını açın* ve dizisine aşağıdaki satırı `urlPatterns` ekleyin:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. templates */HelloDjangoApp/index.html* `<body>` dosyasını açın ve Hakkında sayfasına bağlantı oluşturmak için öğesinin altına aşağıdaki satırı ekleyin (yine bu bağlantıyı 3-4. adımda bir gezinti çubuğuyla değiştirirsiniz):

    ```html
    <div><a href="about">About</a></div>
    ```

1. DosyaSave All menü komutunu **kullanarak** >  **tüm** dosyaları kaydedin veya **CtrlShiftS tuşlarına**+ **basın**+. (Teknik olarak, bu adım projeyi otomatik olarak kaydederken proje Visual Studio gerekli değildir. Yine de bu, hakkında bilgili olmak için iyi bir komut!)

1. Sonuçları gözlemlemek ve sayfalar arasındaki gezintiyi kontrol etmek için projeyi çalıştırın. Bittiğinde sunucuyu kapatın.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Soru: Giriş sayfasının bağlantısı için "index" kullanmayı denedim ama işe koyulmadı. Neden?

Yanıt: *views.py'daki* `index`görünüm işlevi olarak adlandırılmış olsa da, Django projesinin *urls.py* dosyasındaki URL yönlendirme desenleri " index" dizesiyle eşleşen bir normal ifade içermemektedir. Bu dizeyle eşleşmesi için deseni için başka bir giriş eklemeniz gerekir `^index$`.

Bir sonraki bölümde gösterildiği gibi, bir desenin adına başvurmak için sayfa şablonunda etiketini kullanmak çok daha iyidir; bu durumda Django sizin için uygun URL'yi `{% url '<pattern_name>' %}` oluşturur. Örneğin, içinde yerine `<div><a href="home">Home</a></div>` *about.html*.`<div><a href="{% url 'index' %}">Home</a></div>` 'index' kullanımı burada işe yarar çünkü dizinde *ilk URL urls.py* 'index' olarak adlandırılmıştır ( `name='index'` bağımsız değişkeni nedeniyle). İkinci desene başvurmak için 'home' da kullanabilirsiniz.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>3-4. Adım: Üst bilgi ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma

Modern web uygulamaları, her sayfada açık gezinti bağlantıları kullanmak yerine genellikle en önemli sayfa bağlantılarını, açılan menüleri ve diğer öğeleri sağlayan bir marka üst bilgisi ve gezinti çubuğu kullanır. Üst bilgi ve gezinti çubuğunun tüm sayfalarda aynı olduğundan emin olmak için, her sayfa şablonunda aynı kodu tekrarlamak istemiyorsanız. Bunun yerine tüm sayfalarınızı ortak bölümlerini tek bir yerde tanımlamak istiyor siniz.

Django'nun şablon oluşturma sistemi, belirli öğeleri birden çok şablonda yeniden kullanmak için iki yol sağlar: ekleme ve devralma.

- *Eklemeler* , söz dizimi kullanarak başvuran şablonda belirli bir yere ekley istediğiniz diğer sayfa şablonlarıdır `{% include <template_path> %}`. Yolu kodda dinamik olarak değiştirmek için değişken de kullanabilirsiniz. Eklemeler genellikle bir sayfanın gövdesinde, paylaşılan şablonu sayfada belirli bir konuma çekmek için kullanılır.

- *Devralma* , başvuran `{% extends <template_path> %}` şablonun daha sonra üzerinde derlemesi yapılan paylaşılan bir temel şablon belirtmek için sayfa şablonunun başında kullanır. Devralma genellikle bir uygulamanın sayfaları için paylaşılan düzen, gezinti çubuğu ve diğer yapıları tanımlamak için kullanılır; bu şekilde başvuran şablonların yalnızca blok olarak adlandırılan temel şablonun belirli alanlarını eklemesi veya değiştirmesi *gerekir*.

Her iki durumda da `<template_path>` , uygulamanın *templates klasörüne göredir* ( veya`../` buna `./` da izin verilir).

Temel şablon, ve etiketlerini kullanarak blokların çizgilerini `{% block <block_name> %}` `{% endblock %}` oluşturur. Başvuran bir şablon aynı blok adına sahip etiketleri kullanıyorsa, blok içeriği temel şablonun içeriğini geçersiz kılar.

Aşağıdaki adımlar devralmayı gösterir:

1. Uygulamanın *templates/HelloDjangoApp* klasöründe *,layout.html* adlı yeni bir HTML dosyası oluşturun (**EkleYeni**  >  öğe bağlam menüsünü veya **AddHTML** >  Sayfasını kullanarak) ve içeriğini aşağıdaki işaretlemeyle değiştirin. Bu şablonun, başvuran sayfaların değiştirmesi gereken "content" adlı bir blok içerdiğini görüyorsunuz:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load static %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. Uygulamanın *static/site.css* dosyasına aşağıdaki stilleri ekleyin (bu kılavuz burada duyarlı tasarımı göstermeyi denemez; bu stiller yalnızca ilginç bir sonuç oluşturmak içindir):

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. Şablonları */HelloDjangoApp/index.html* temel şablona başvurmak ve içerik bloğuna geçersiz kılmak için değiştirme. Devralmayı kullanarak bu şablonun basit hale gelir:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Şablonları */HelloDjangoApp/about.html* da temel şablona başvurmak ve içerik bloğuna geçersiz kılmak için değiştirme:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları gözlemlemek için sunucuyu çalıştırın. Bittiğinde sunucuyu kapatın.

    ![Gezinti çubuğunu gösteren çalışan uygulama](media/django/step03-nav-bar.png)

1. Uygulamada önemli değişiklikler yaptığınız için, değişikliklerinizi kaynak denetimine [işlemenin zamanı](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control) geldi.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [tam docgo Web Project şablonunu kullanın](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Daha derin git

- [Web uygulamasını Azure App Service dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Ilk Docgo uygulamanızı yazma, Bölüm 3 (görünümler)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Denetim akışı gibi Docgo şablonlarının daha fazla özelliği için bkz [. docgo şablonu dili](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Etiketi kullanma `{% url %}` hakkında ayrıntılı bilgi için, bkz. [yerleşik şablon etiketleri ve filtrelerin](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) içindeki [URL](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) (docs.djangoproject.com)
- GitHub eğitim kaynak kodu: [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
