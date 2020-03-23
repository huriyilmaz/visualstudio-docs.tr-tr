---
title: Visual Studio adım 3, statik dosya ve sayfalar django öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temellerinin bir walkthrough, özellikle statik dosyaları hizmet nasıl gösteren, uygulamaya sayfaları eklemek ve şablon devralma kullanın
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 54a80ef606a553846ef5be7a86ed4183f3ffde57
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62958267"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Adım 3: Statik dosyalara hizmet edin, sayfa ekleyin ve şablon kalıtımını kullanın

**Önceki adım: [Görünümler ve sayfa şablonları içeren bir Django uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)**

Bu öğreticinin önceki adımlarında, tek bir bağımsız HTML sayfasıyla en az Bir Django uygulaması oluşturmayı öğrendiniz. Ancak modern web uygulamaları genellikle birçok sayfadan oluşur ve tutarlı stil ve davranış sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynaklardan yararlanılır.

Bu adımda, nasıl öğreneceksiniz:

> [!div class="checklist"]
> - Kullanışlı ortak kodla farklı türde yeni dosyaları hızla eklemek için Visual Studio öğe şablonlarını kullanın (adım 3-1)
> - Statik dosyalara hizmet edecek Şekilde Django projesini yapılandırın (adım 3-2)
> - Uygulamaya ek sayfa ekleme (adım 3-3)
> - Sayfalar arasında kullanılan bir üstbilgi ve gezinme çubuğu oluşturmak için şablon kalıbı kullanma (adım 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Adım 3-1: Öğe şablonlarını tanıma

Bir Django uygulaması geliştirdikçe, genellikle çok daha fazla Python, HTML, CSS ve JavaScript dosyaları eklersiniz. Her dosya türü için (ve dağıtım için ihtiyaç duyabileceğiniz *web.config* gibi diğer dosyalar için), Visual Studio başlamanız için kullanışlı [öğe şablonları](python-item-templates.md) sağlar.

Kullanılabilir şablonları görmek için **Çözüm Gezgini'ne**gidin , öğeyi oluşturmak istediğiniz klasöre sağ tıklayın,**Yeni Öğe** **Ekle'yi** > seçin:

![Visual Studio'da yeni öğe iletişim kutusu ekleme](media/django/step03-add-new-item-dialog.png)

Şablon kullanmak için istenen şablonu seçin, dosya için bir ad belirtin ve **Tamam'ı**seçin. Bu şekilde bir öğe eklemek, dosyayı Visual Studio projenize otomatik olarak ekler ve kaynak denetimi değişikliklerini işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Visual Studio hangi öğe şablonlarının sunacağını nasıl biliyor?

Cevap: Visual Studio proje dosyası (*.pyproj*) python projesi olarak işaretleyen bir proje türü tanımlayıcısı içerir. Visual Studio, yalnızca proje türüne uygun öğe şablonlarını göstermek için bu tür tanımlayıcıyı kullanır. Bu şekilde, Visual Studio her zaman bunları sıralamak için sormadan birçok proje türleri için öğe şablonları zengin bir dizi sağlayabilir.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Adım 3-2: Uygulamanızdan statik dosyalara hizmet

Python ile oluşturulmuş bir web uygulamasında (herhangi bir çerçeve kullanarak), Python dosyalarınız her zaman web barındırıcının sunucusunda çalışır ve hiçbir zaman kullanıcının bilgisayarına aktarılmez. Ancak CSS ve JavaScript gibi diğer dosyalar yalnızca tarayıcı tarafından kullanılır, bu nedenle ana bilgisayar sunucusu istendiğinde olduğu gibi sunar. Bu tür dosyalar "statik" dosyalar olarak adlandırılır ve Django bunları herhangi bir kod yazmaya gerek kalmadan otomatik olarak teslim edebilir.

Bir Django projesi, Django projesinin *settings.py*bu satırlar sayesinde, uygulamanın *statik* klasöründen statik dosyaları sunmak için varsayılan olarak yapılandırılır:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

İstediğiniz *statik* içindeki herhangi bir klasör yapısını kullanarak dosyaları düzenleyebilir ve ardından dosyalara başvurmak için bu klasöriçindeki göreli yolları kullanabilirsiniz. Bu işlemi göstermek için, aşağıdaki adımlar uygulamaya bir CSS dosyası ekleyin ve ardından *index.html* şablonundaki stil sayfasını kullanın:

1. **Solution Explorer'da**Visual Studio projesindeki **HelloDjangoApp** klasörüne sağ tıklayın, Yeni `static`klasör**ekle'yi** **Add** > seçin ve klasöre isim vereyim.

1. **Statik** klasöre sağ tıklayın ve Yeni öğe **ekle'yi** > **New item**seçin. Görünen iletişim **kutusunda, Stylesheet** şablonu seçin, dosyayı `site.css`adlandırın ve **Tamam'ı**seçin. **site.css** dosyası projede görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki resme benzer görünmelidir:

    ![Çözüm Gezgini'nde gösterildiği gibi statik dosya yapısı](media/django/step03-static-file-structure.png)

1. *site.css* içeriğini aşağıdaki kodla değiştirin ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın *templates/HelloDjangoApp/index.html* dosyasının içeriğini, adım 2'de kullanılan `<strong>` öğeyi `message` stil sınıfına `<span>` başvuran bir öğeyle değiştiren aşağıdaki kodla değiştirin. Stil sınıfını bu şekilde kullanmak, öğeyi şekillendirmede size çok daha fazla esneklik sağlar. (VS 2017 15.7 ve daha öncelerini kullanırken *index.html'i* *şablonlarda* bir alt klasöre taşıtmadıysanız, 2-4 adımdaki [şablon ad aralığına](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) bakın.)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Sonuçları gözlemlemek için projeyi çalıştırın. Yapıldığında sunucuyu durdurun ve değişikliklerinizi kaynak denetimine işleyin [(adım 2'de](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)açıklandığı gibi).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Soru: {% yük statik dosyaları %} etiketinin amacı nedir?

Cevap: `{% load staticfiles %}` Satır gibi `<head>` elemanlar statik dosyalara `<body>`atıfta önce gereklidir ve . Bu bölümde gösterilen örnekte, "staticfiles" statik dosyalara başvurmak için `{% static %}` sözdizimini kullanmanıza olanak tanıyan özel bir Django şablon etiketi kümesini ifade eder.  Olmadan, `{% load staticfiles %}`uygulama çalıştığında bir özel durum görürsünüz.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: Statik dosyaları düzenlemek için herhangi bir kural var mı?

Cevap: *Statik* klasörünüze istediğiniz gibi diğer CSS, JavaScript ve HTML dosyalarını ekleyebilirsiniz. Statik dosyaları düzenlemenin tipik bir yolu, *yazı tipleri,* *komut dosyaları*ve *içerik* (stil sayfaları ve diğer dosyalar için) adlı alt klasörler oluşturmaktır. Her durumda, bu klasörleri başvurularda `{% static %}` dosyaya göreli yola eklemeyi unutmayın.

## <a name="step-3-3-add-a-page-to-the-app"></a>Adım 3-3: Uygulamaya sayfa ekleme

Uygulamaya başka bir sayfa eklemek aşağıdaki anlamına gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfanın biçimlendirmesi için bir şablon ekleyin.
- Django projesinin *urls.py* dosyasına gerekli yönlendirmeyi ekleyin.

Aşağıdaki adımlar "HelloDjangoApp" projesine bir "Hakkında" sayfası ve ana sayfadan bu sayfaya bağlantılar ekleyin:

1. **Solution Explorer'da** **şablonlar/HelloDjangoApp** klasörüne sağ tıklayın,**Yeni öğe** **ekle'yi** > seçin, `about.html`HTML **Sayfa** öğesi şablonu seçin, dosyayı adlandırın ve **Tamam'ı**seçin.

    > [!Tip]
    > Yeni **Öğe** Komutu **Ekle** menüsünde görünmüyorsa, Visual Studio'nun hata ayıklama modundan çıkması için sunucuyu durdurduğunuzdan emin olun.

1. *about.html'in* içeriğini aşağıdaki biçimlendirmeyle değiştirin (ana sayfadaki açık bağlantıyı adım 3-4'te basit bir gezinme çubuğuyla değiştirirsiniz):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Uygulamanın *views.py* dosyasını açın ve `about` şablonu kullanan bir işlev ekleyin:

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

1. Django projesinin *urls.py* dosyasını açın ve `urlPatterns` diziye aşağıdaki satırı ekleyin:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. *templates/HelloDjangoApp/index.html* dosyasını açın ve Hakkında `<body>` sayfaya bağlantı vermek için öğenin altına aşağıdaki satırı ekleyin (yine, bu bağlantıyı adım 3-4'te bir gezinme çubuğuyla değiştirirsiniz):

    ```html
    <div><a href="about">About</a></div>
    ```

1. **Dosya** > **Kaydet Tüm** menü komutunu kullanarak tüm dosyaları kaydedin veya **Ctrl**+**Shift**+**S**tuşuna basın. (Teknik olarak, Visual Studio'da proje yi çalıştıran bu adım akadar değil, dosyaları otomatik olarak kaydeder. Yine de, bilmek iyi bir komut!)

1. Sonuçları gözlemlemek ve sayfalar arasında gezinmeyi denetlemek için projeyi çalıştırın. Bittiğinde sunucuyu kapatın.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Soru: Ana sayfaya bağlantı için "dizin" kullanmayı denedim, ancak işe yaramadı. Neden?

Cevap: *views.py* görünüm işlevi adlandırılmış `index`olsa da, Django projesinin *urls.py* dosyasındaki URL yönlendirme desenleri dize "dizin" dizeyle eşleşen düzenli bir ifade içermez. Bu dizeyle eşleşebilmek için desen `^index$`için başka bir giriş eklemeniz gerekir.

Bir sonraki bölümde gösterildiği gibi, bir desenin `{% url '<pattern_name>' %}` *adına* başvurmak için sayfa şablonundaki etiketi kullanmak çok daha iyidir ve bu durumda Django sizin için uygun URL'yi oluşturur. Örneğin, `<div><a href="home">Home</a></div>` *about.html'i* `<div><a href="{% url 'index' %}">Home</a></div>`' yi . 'Dizin' kullanımı burada çalışır, çünkü *urls.py'daki* ilk URL deseni aslında 'dizin' `name='index'` (bağımsız değişken indeks' olarak adlandırılır). İkinci modele başvurmak için 'ev' de kullanabilirsiniz.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Adım 3-4: Üstbilgi ve gezinme çubuğu oluşturmak için şablon kalıbı kullanma

Modern web uygulamaları, her sayfada açık gezinme bağlantılarına sahip olmak yerine genellikle bir marka üstbilgive en önemli sayfa bağlantıları, açılır menüler ve benzeri sağlayan bir gezinti çubuğu kullanır. Üstbilgi ve gezinme çubuğunun tüm sayfalarda aynı olduğundan emin olmak için, her sayfa şablonunda aynı kodu yinelemek istemezsiniz. Bunun yerine, tüm sayfalarınızın ortak bölümlerini tek bir yerde tanımlamak istiyorsunuz.

Django'nun baştan çıkarıcı sistemi, belirli öğeleri birden çok şablon arasında yeniden kullanmak için iki araç sağlar: içerir ve devralma.

- *Sözdizimini* `{% include <template_path> %}`kullanarak başvuru şablonuna belirli bir yere eklediğiniz diğer sayfa şablonları içerir. Yolu kodda dinamik olarak değiştirmek istiyorsanız, bir değişken de kullanabilirsiniz. İçerekler genellikle sayfadaki belirli bir konumda paylaşılan şablonu çekmek için bir sayfanın gövdesinde kullanılır.

- `{% extends <template_path> %}` *Devralma,* başvuru şablonunun üzerine inşa ettiği paylaşılan temel şablonu belirtmek için sayfa şablonunun başında kullanır. Devralma genellikle, başvuru şablonlarının *yalnızca blok*adı verilen temel şablonun belirli alanlarını eklemesi veya değiştirmesi gerektiği gibi, bir uygulamanın sayfaları için paylaşılan düzeni, gezinme çubuğunu ve diğer yapıları tanımlamak için kullanılır.

Her iki `<template_path>` durumda da, uygulamanın *şablonlar* `../` klasörüne göredir (veya `./` ayrıca izin verilir).

Temel şablon, blokları kullanarak `{% block <block_name> %}` ve `{% endblock %}` etiketleri gösterir. Yönlendiren bir şablon aynı blok ada sahip etiketler kullanıyorsa, engelleme içeriği temel şablonunkini geçersiz kılar.

Aşağıdaki adımlar kalıtım gösterir:

1. Uygulamanın *şablonları/HelloDjangoApp* klasöründe, *düzen.html*adı verilen yeni bir HTML dosyası **(Yeni öğe** bağlamı **ekle** > menüsünü kullanarak veya**HTML Sayfası** **Ekle'yi** > kullanarak) oluşturun ve içeriğini aşağıdaki biçimlendirmeyle değiştirin. Bu şablonun, yönlendiren sayfaların değiştirmesi gereken tek şey olan "içerik" adlı bir blok içerdiğini görebilirsiniz:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
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

1. Uygulamanın *statik/site.css* dosyasına aşağıdaki stilleri ekleyin (bu izlenecek yol burada duyarlı tasarımı göstermeye çalışmıyor; bu stiller sadece ilginç bir sonuç oluşturmak içindir):

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

1. Temel şablona başvurmak ve içerik bloğunu geçersiz kılmak için *templates/HelloDjangoApp/index.html* değiştirin. Devralma kullanarak bu şablonun basitleştiğini görebilirsiniz:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Temel şablona başvurmak ve içerik bloğunu geçersiz kılmak için *templates/HelloDjangoApp/about.html* değiştirin:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları gözlemlemek için sunucuyu çalıştırın. Bittiğinde sunucuyu kapatın.

    ![Gezinme çubuğunu gösteren uygulama çalıştırma](media/django/step03-nav-bar.png)

1. Uygulamada önemli değişiklikler yaptığınız için, [değişikliklerinizi kaynak denetimine işlemek için](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)yine iyi bir zaman.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Tam Django Web Projesi şablonunu kullanma](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Daha derine inin

- [Web uygulamasını Azure Uygulama Hizmetine dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [İlk Django uygulaması, bölüm 3 (görünümler)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com) yazma
- Denetim akışı gibi Django şablonlarının daha fazla özelliği için Bkz. [Django şablon dili](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- `{% url %}` Etiketi kullanma hakkında ayrıntılı bilgi için, [Django şablonları başvurusu için Yerleşik şablon etiketleri ve filtreleri](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) içindeki [url'ye](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) bakın (docs.djangoproject.com)
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
