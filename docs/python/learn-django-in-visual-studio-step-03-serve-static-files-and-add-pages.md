---
title: Visual Studio adım 3, statik dosya ve sayfalarda Docgo öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında, özellikle statik dosyalar sunma, uygulamaya sayfa ekleme ve şablon devralmayı kullanma konuları hakkında bir adım adım yönergeler.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7aabfa91f7f6c6204919c4a06d2d3080b5174c5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942587"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-django-app"></a>3. Adım: statik dosyaları sunma, sayfa ekleme ve Docgo uygulamasıyla şablon devralmayı kullanma

**Önceki adım: [görünümler ve sayfa şablonlarıyla bir Docgo uygulaması oluşturma](learn-django-in-visual-studio-step-02-create-an-app.md)**

Bu öğreticinin önceki adımlarında, en az bir adet kendi kendine içerilen HTML 'nin tek bir sayfası ile en az bir Docgo uygulaması oluşturmayı öğrendiniz. Ancak modern Web Apps, genellikle birçok sayfadan oluşur ve tutarlı stil oluşturma ve davranış sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynakları kullanır.

Bu adımda şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Uygun ortak kod ile farklı türlerdeki yeni dosyaları hızlıca eklemek için Visual Studio öğe şablonlarını kullanın (adım 3-1)
> - Docgo projesini statik dosyaları sunacak şekilde yapılandırma (adım 3-2)
> - Uygulamaya ek sayfalar ekleme (adım 3-3)
> - Sayfalarda kullanılan bir başlık ve gezinme çubuğu oluşturmak için şablon devralmayı kullanın (adım 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Adım 3-1: öğe şablonları hakkında bilgi sahibi olun

Docgo uygulaması geliştirirken genellikle daha fazla Python, HTML, CSS ve JavaScript dosyası eklersiniz. Her dosya türü için (Ayrıca, dağıtım için ihtiyaç duyduğunuz *web.config* gibi diğer dosyalar), Visual Studio başlamanıza olanak sağlayacak uygun [öğe şablonları](python-item-templates.md) sağlar.

Kullanılabilir şablonları görmek için **Çözüm Gezgini** gidin, öğeyi oluşturmak istediğiniz klasörü sağ tıklatın,   >  **Yeni öğe** Ekle ' yi seçin:

![Visual Studio 'da yeni öğe Ekle iletişim kutusu](media/django/step03-add-new-item-dialog.png)

Bir şablon kullanmak için, istediğiniz şablonu seçin, dosya için bir ad belirtin ve **Tamam**' ı seçin. Bu şekilde bir öğe eklemek, dosyayı otomatik olarak Visual Studio projenize ekler ve kaynak denetimi için değişiklikleri işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Visual Studio hangi öğe şablonlarının önereceğimizi nasıl bilir?

Cevap: Visual Studio proje dosyası (*. pyproj*), bir Python projesi olarak işaretleyen bir proje türü tanımlayıcısı içerir. Visual Studio yalnızca proje türü için uygun olan öğe şablonlarını göstermek için bu tür tanımlayıcısını kullanır. Bu şekilde, Visual Studio her seferinde her seferinde sıralama yapmanızı istemeden birçok proje türü için zengin bir öğe şablonları kümesi sağlayabilir.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Adım 3-2: uygulamanızdan statik dosyaları sunma

Python ile derlenen bir Web uygulamasında (herhangi bir Framework kullanılarak), Python dosyalarınız her zaman Web ana bilgisayarı sunucusunda çalışır ve bir kullanıcının bilgisayarına hiçbir zaman aktarılmaz. Ancak, CSS ve JavaScript gibi diğer dosyalar yalnızca tarayıcı tarafından kullanılır, bu nedenle ana bilgisayar sunucusu bu dosyaları istendiği zaman olduğu gibi teslim eder. Bu tür dosyalar "static" dosyalar olarak adlandırılır ve Docgo, herhangi bir kod yazmaya gerek kalmadan bunları otomatik olarak teslim edebilir.

Docgo projesi varsayılan olarak uygulamanın *statik* klasöründen statik dosyaları sunacak şekilde yapılandırılır, bu satırlar docgo projesinin *Settings.py*:

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

İstediğiniz *statik* içindeki herhangi bir klasör yapısını kullanarak dosyaları düzenleyebilir ve ardından dosyalara başvurmak için bu klasörde göreli yollar kullanabilirsiniz. Bu işlemi göstermek için aşağıdaki adımlar uygulamaya bir CSS dosyası ekler ve sonra bu stil sayfasını *index.html* şablonunda kullanır:

1. **Çözüm Gezgini**, Visual Studio projesindeki **hellodocgoapp** klasörüne sağ tıklayın, yeni klasör Ekle ' yi seçin   >  ve klasörü adlandırın `static` .

1. **Statik** klasöre sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. Görüntülenen iletişim kutusunda, **stil sayfası** şablonunu seçin, dosyayı adlandırın `site.css` ve **Tamam**' ı seçin. **Site. css** dosyası projede görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki görüntüye benzer görünmelidir:

    ![Çözüm Gezgini gösterildiği gibi statik dosya yapısı](media/django/step03-static-file-structure.png)

1. *Site. css* içeriğini aşağıdaki kodla değiştirin ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın *Templates/Hellodocgoapp/index.html* dosyasının içeriğini aşağıdaki kodla değiştirin `<strong>` . Bu, adım 2 ' de kullanılan öğenin `<span>` Stil sınıfına başvuran bir ile değiştirilir `message` . Bu şekilde bir stil sınıfı kullanmak, öğe stillendirme konusunda çok daha fazla esneklik sağlar. (VS 2017 15,7 ve daha önceki bir sürümü kullanırken *index.html* 'yi *şablonlarda* bir alt klasöre taşımadığınız takdirde, adım 2-4 ' de [Template namespacing](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing) ' e bakın.)

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

1. Sonuçları gözlemlemek için projeyi çalıştırın. Tamamlandığında sunucuyu durdurun ve isterseniz kaynak denetimine yaptığınız değişiklikleri kaydedin ( [Adım 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)' de açıklandığı gibi).

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>Soru: {% Load staticfiles%} etiketinin amacı nedir?

Cevap: `{% load staticfiles %}` ve gibi öğelerde statik dosyalara başvurulmadan önce satır gerekir `<head>` `<body>` . Bu bölümde gösterilen örnekte, "staticfiles", `{% static %}` statik dosyalara başvurmak için söz dizimini kullanmanıza izin veren özel bir Docgo şablon etiketi kümesine başvurur.  Olmadan `{% load staticfiles %}` , uygulama çalışırken bir özel durum görürsünüz.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: statik dosyaları düzenlemek için herhangi bir kural var mı?

Yanıt: diğer CSS, JavaScript ve HTML dosyalarını *statik* klasörünüze ekleyebilirsiniz, ancak istediğiniz gibi. Statik dosyaları düzenlemenin tipik bir yolu, *yazı tipleri*, *betikler* ve *içerik* (stil sayfaları ve diğer dosyalar için) adlı alt klasörler oluşturmaktır. Her durumda, bu klasörleri başvurulara dosyanın göreli yoluna dahil etmeyi unutmayın `{% static %}` .

### <a name="question-can-i-complete-the-same-task-without-using-the--load-staticfiles--tag"></a>Soru: {% Load staticfiles%} etiketini kullanmadan aynı görevi tamamlayabilirim?

Cevap: Evet, bunu yapabilirsiniz.

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

## <a name="step-3-3-add-a-page-to-the-app"></a>Adım 3-3: uygulamaya bir sayfa ekleme

Uygulamaya başka bir sayfa eklemek aşağıdakiler anlamına gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfa işaretlemesi için bir şablon ekleyin.
- Gerekli yönlendirmeyi Docgo projesinin *URLs.py* dosyasına ekleyin.

Aşağıdaki adımlarda "Hellodocgoapp" projesine bir "hakkında" sayfası ve bu sayfanın giriş sayfasından bağlantıları verilmiştir:

1. **Çözüm Gezgini**, **Templates/hellodocgoapp** klasörüne sağ tıklayın, yeni öğe **Ekle**' yi seçin  >  , **HTML sayfası** öğe şablonunu seçin, dosyayı adlandırın `about.html` ve **Tamam**' ı seçin.

    > [!Tip]
    > **Yeni öğe** komutu **Ekle** menüsünde görünmezse, Visual Studio 'nun hata ayıklama modundan çıkmasını sağlamak için sunucuyu durdurduğunuzdan emin olun.

1. *about.html* öğesinin içeriğini aşağıdaki biçimlendirmeyle değiştirin (adım 3-4 ' de basit bir gezinti çubuğu ile giriş sayfasına yönelik açık bağlantıyı değiştirirsiniz):

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

1. Uygulamanın *views.py* dosyasını açın ve şablonu kullanan adlı bir işlev ekleyin `about` :

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

1. Docgo projesinin *URLs.py* dosyasını açın ve aşağıdaki satırı `urlPatterns` diziye ekleyin:

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. *Templates/Hellodocgoapp/index.html* dosyasını açın ve ilgili sayfanın altına aşağıdaki satırı ekleyin `<body>` (Bu bağlantıyı, adım 3-4 ' de bir gezinti çubuğu ile değiştirirsiniz):

    ```html
    <div><a href="about">About</a></div>
    ```

1. **Dosya**  >  **Tümünü Kaydet** menü komutunu kullanarak tüm dosyaları kaydedin veya **CTRL** + **+ Shift** + **S** tuşlarına basın. (Teknik olarak, Visual Studio 'da projeyi çalıştırmak için bu adım gerekli değildir. dosyaları otomatik olarak kaydeder. Bununla birlikte, bunun hakkında bilgi edinmek için iyi bir komuttur!)

1. Sonuçları gözlemlemek ve sayfalar arasında gezinmeyi denetlemek için projeyi çalıştırın. Bitince sunucuyu kapatın.

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>Soru: giriş sayfasının bağlantısı için "Dizin" kullanmaya çalıştım, ancak bu işe yaramadı. Neden?

Cevap: *views.py* içindeki görüntüleme Işlevi adlandırılmış olsa da `index` , docgo PROJESININ *URLs.py* dosyasındaki URL yönlendirme desenleri "index" dizesiyle eşleşen bir normal ifade içermez. Bu dizeyi eşleştirmek için, model için başka bir girdi eklemeniz gerekir `^index$` .

Sonraki bölümde gösterildiği gibi, `{% url '<pattern_name>' %}` bir düzenin *adına* başvurmak için sayfa şablonundaki etiketinin kullanılması çok daha iyidir. Bu durumda, docgo sızın için uygun URL 'yi oluşturur. Örneğin, `<div><a href="home">Home</a></div>` *about.html* ' de ile değiştirin `<div><a href="{% url 'index' %}">Home</a></div>` . *URLs.py* ' DEKI ilk URL deseninin, aslında ' index ' adlı (bağımsız değişkenin virtuale tarafından) olduğu için ' index ' kullanımı burada çalışıyor `name='index'` . İkinci düzene başvurmak için ' Home ' öğesini de kullanabilirsiniz.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Adım 3-4: başlık ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma

Modern Web Apps, her sayfada açık gezinti bağlantıları sağlamak yerine genellikle bir marka üst bilgisi ve en önemli sayfa bağlantılarını, açılan menüleri vb. sağlayan bir gezinti çubuğu kullanır. Üst bilgi ve gezinti çubuğunun tüm sayfalarda aynı olduğundan emin olmak için, her sayfa şablonunda aynı kodu yinelemek istemezsiniz. Bunun yerine, tüm sayfalarınızın ortak parçalarını tek bir yerde tanımlamak isteyebilirsiniz.

Docgo 'nın şablon oluşturma sistemi, birden çok şablon genelinde belirli öğeleri yeniden kullanmak için iki yol sağlar: dahil ve devralma.

- , Söz dizimi kullanılarak başvuran şablonda belirli bir yere eklediğiniz diğer sayfa şablonlarıyla *dahildir* `{% include <template_path> %}` . Ayrıca, kodda dinamik olarak yolu değiştirmek istiyorsanız bir değişkeni de kullanabilirsiniz. Eklemeleri genellikle sayfanın gövdesinde, paylaşılan şablonu sayfada belirli bir konumda çekmek için kullanılır.

- *Devralma* , `{% extends <template_path> %}` başvuran şablonun üzerinde derleneceği paylaşılan temel şablonu belirtmek için bir sayfa şablonunun başındaki öğesini kullanır. Devralma genellikle, bir uygulamanın sayfalarına yönelik olarak paylaşılan bir düzen, gezinme çubuğu ve diğer yapıları tanımlamak için kullanılır. bu nedenle, şablonlar yalnızca temel şablonun *bloklar* olarak adlandırılan belirli bölgelerini eklemesi veya değiştirmesi gerekir.

Her iki durumda da `<template_path>` uygulamanın *Şablonlar* klasörüne görelidir ( `../` veya `./` Ayrıca izin verilir).

Bir temel şablon `{% block <block_name> %}` , ve etiketlerini kullanarak blokları ayırıcıları `{% endblock %}` . Başvuruda bulunan bir şablon daha sonra aynı blok adına sahip Etiketler kullanıyorsa, blok içeriği temel şablonun üzerine yazar.

Aşağıdaki adımlarda devralma gösterilmektedir:

1. Uygulamanın *Templates/hellodocgoapp* klasöründe yeni bir HTML dosyası oluşturun (   >  **Yeni öğe** Ekle bağlam menüsünü kullanarak veya   >  **HTML sayfası** Ekle ' yi kullanarak) *layout.html* adlı adı ve içeriğini aşağıdaki biçimlendirmeyle değiştirin. Bu şablonun, başvuran sayfaların yerini almak için gereken "içerik" adlı bir blok içerdiğini görebilirsiniz:

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

1. Uygulamanın *static/site. css* dosyasına aşağıdaki stilleri ekleyin (Bu izlenecek yol, yanıt veren tasarımı göstermeye çalışmıyor; bu stiller yalnızca ilginç bir sonuç oluşturmak için kullanılır):

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

1. *Şablonları/Hellodocgoapp/index.html* 'yi, temel şablona başvuracak ve içerik bloğunu geçersiz kılacak şekilde değiştirin. Devralma kullanarak bu şablonu basit hale getirebilirsiniz:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. *Şablonları/Hellodocgoapp/about.html ' y* i aynı zamanda temel şablona başvuracak ve içerik bloğunu geçersiz kılacak şekilde değiştirin:

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları gözlemlemek için sunucuyu çalıştırın. Bitince sunucuyu kapatın.

    ![Gezinti çubuğunu gösteren uygulama çalıştırılıyor](media/django/step03-nav-bar.png)

1. Uygulamada önemli değişiklikler yapabileceğinizden, [değişikliklerinizi kaynak denetimine kaydetmek](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)iyi bir zaman alabilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Tam Docgo Web proje şablonunu kullanın](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>Daha derin git

- [Web uygulamasını Azure App Service dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Ilk Docgo uygulamanızı yazma, Bölüm 3 (görünümler)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) (docs.djangoproject.com)
- Denetim akışı gibi Docgo şablonlarının daha fazla özelliği için bkz [. docgo şablonu dili](https://docs.djangoproject.com/en/2.0/ref/templates/language/) (docs.djangoproject.com)
- Etiketi kullanma hakkında ayrıntılı bilgi için `{% url %}` , bkz. [yerleşik şablon etiketleri ve filtrelerin](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) içindeki [URL](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) (docs.djangoproject.com)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
