---
title: 3. adım, statik Visual Studio sayfalarda Flask öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask ile ilgili temel bilgiler, özellikle statik dosyaların nasıl hizmet ve uygulama sayfaları ekleneceklerini ve şablon devralmanın nasıl kullanılacalarını gösteren kılavuz
ms.date: 01/07/2019
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: ade4401c22decb840c5c263198574c435ebe6da4
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129968442"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>3. Adım: Flask uygulamasıyla statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma

**Önceki adım: [Görünümler ve sayfa şablonlarıyla bir Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)**

Bu öğreticinin önceki adımlarında, tek sayfalık kendi içinde HTML ile minimal bir Flask uygulaması oluşturma hakkında bilgi edindisiniz. Ancak modern web uygulamaları genellikle birçok sayfadan oluşur ve tutarlı stil ve davranış sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynakları kullanır.

Bu adımda şunların nasıl olduğunu öğreniriz:

> [!div class="checklist"]
> - Kolay Visual Studio ile farklı türlerde yeni dosyaları hızla eklemek için yeni öğe şablonları kullanma (3-1. adım)
> - Koddan statik dosyaları hizmet etme (3-2. adım, isteğe bağlı)
> - Uygulamaya başka sayfalar ekleme (3-3. adım)
> - Sayfalar arasında kullanılan bir üst bilgi ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma (3-4. adım)

## <a name="step-3-1-become-familiar-with-item-templates"></a>3.-1. Adım: Öğe şablonları hakkında bilgi sahibi olma

Flask uygulaması geliştirirken genellikle çok daha fazla Python, HTML, CSS ve JavaScript dosyası eklersiniz. Her dosya türü için (dağıtım için ihtiyaçweb.configdiğer *dosyalar gibi),* Visual Studio [](python-item-templates.md) başlamanız için kullanışlı öğe şablonları sağlar.

Kullanılabilir şablonları görmek için Çözüm Gezgini'ye **gidin,** öğeyi oluşturmak istediğiniz klasöre sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin:**

![Yeni öğe ekle iletişim kutusu Visual Studio](media/flask/step03-add-new-item-dialog.png)

Şablon kullanmak için istenen şablonu seçin, dosya için bir ad belirtin ve Tamam'ı **seçin.** Bu şekilde bir öğe eklemek, dosyayı otomatik olarak Visual Studio projenize ekler ve değişiklikleri kaynak denetimi için işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Hangi Visual Studio şablonlarını nasıl bilebilirsiniz?

Cevap: Visual Studio dosyası (*.pyproj*), bunu Python projesi olarak işaret alan bir proje türü tanımlayıcısı içerir. Visual Studio, yalnızca proje türüne uygun öğe şablonlarını göstermek için bu tür tanımlayıcısını kullanır. Bu şekilde Visual Studio her zaman sıralamak istemeden birçok proje türü için zengin bir öğe şablonu kümesi sebilirsiniz.

## <a name="step-3-2-serve-static-files-from-your-app"></a>3-2. Adım: Uygulamanıza statik dosyaları hizmet etme

Python ile derlen bir web uygulamasında (herhangi bir çerçeve kullanılarak), Python dosyalarınız her zaman web ana bilgisayarının sunucusunda çalıştırıldı ve hiçbir zaman kullanıcının bilgisayarına aktarıldı. Ancak CSS ve JavaScript gibi diğer dosyalar yalnızca tarayıcı tarafından kullanılır, bu nedenle ana bilgisayar sunucusu isten her istene olduğu gibi bunları gönderir. Bu tür dosyalar "statik" dosyalar olarak adlandırılır ve Flask bunları kod yazmanız gerekmeden otomatik olarak teslim eder. Örneğin, HTML dosyaları içinde, projesinde göreli bir yol kullanarak statik dosyalara başvurabilirsiniz. Bu adımın ilk bölümü, mevcut sayfa şablonunuz için bir CSS dosyası ekler.

Bir API uç noktası uygulaması aracılığıyla koddan statik bir dosya teslim etmek için Flask, statik *adlı* bir klasördeki göreli yolları (proje kökünde) kullanarak dosyalara başvurarak kullanışlı bir yöntem sağlar. Bu adımın ikinci bölümünde, basit bir statik veri dosyası kullanılarak bu yöntem gösterildi.

Her iki durumda da dosyaları statik olarak *düzenleyebilirsiniz.*

### <a name="use-a-static-file-in-a-template"></a>Şablonda statik dosya kullanma

1. Bu **Çözüm Gezgini,** Visual Studio projesinde **HelloFlask** klasörüne sağ tıklayın, Yeni klasör Ekle'yi  >  **seçin** ve klasöre adını `static` girin.

1. Statik klasöre sağ **tıklayın ve** Yeni öğe **Ekle'yi**  >  **seçin.** Görüntülenen iletişim kutusunda Stil Sayfası şablonunu seçin, dosyaya **adını** ve `site.css` Tamam'ı **seçin.** **Site.css** dosyası projede görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki görüntüye benzer görünse:

    ![Dosyalarda gösterildiği gibi statik Çözüm Gezgini](media/flask/step03-static-file-structure.png)

1. *site.css içeriğini aşağıdaki* kodla değiştirin ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın *şablonlarının/index.html* dosyasının içeriğini aşağıdaki kodla değiştirin. Bu kod, 2. adımda kullanılan öğesini stil sınıfına başvurulan bir `<strong>` `<span>` ile `message` değiştirir. Stil sınıfını bu şekilde kullanmak, öğenin stilini oluşturma konusunda çok daha fazla esneklik sağlar.

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. Sonuçları gözlemlemek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun ve 2. adımda açıklanmıştır) dısanız değişikliklerinizi kaynak [denetimine işlenin.](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)

### <a name="serve-a-static-file-from-code"></a>Koddan statik dosya hizmet etme

Flask, projenin statik klasöründeki herhangi bir dosyaya başvurmak için koddan `serve_static_file` çağırabilirsiniz adlı bir *işlev* sağlar. Aşağıdaki işlem statik veri dosyası döndüren basit bir API uç noktası oluşturur.

1. Henüz bunu yapmadıysanız, statik  bir klasör oluşturun: Çözüm Gezgini 'de, **Visual Studio** projesinde **HelloFlask** klasörüne sağ tıklayın, Yeni klasör Ekle'yi seçin ve   >  klasöre adını `static` girin.

1. Statik *klasörde,* aşağıdaki içeriklere sahip *data.json* adlı bir statik JSON veri dosyası oluşturun (bu, anlamsız örnek verilerdir):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. Bu *views.py*, yöntemini kullanarak statik veri dosyasını döndüren /api/data yolu ile bir işlev `send_static_file` ekleyin:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uygulamayı çalıştırın ve statik dosyanın döndürül olduğunu görmek için /api/data uç noktasına gidin. Bitirin ve uygulamayı durdurun.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: Statik dosyaları düzenlemek için herhangi bir kural var mı?

Cevap: Statik klasörünüzdeki diğer CSS, JavaScript ve HTML dosyalarını *istediğiniz* gibi abilirsiniz. Statik dosyaları düzenlemenin tipik bir yolu yazı *tipleri,* betikler *ve* içerik *(stil* sayfaları ve diğer dosyalar için) adlı alt klasörler oluşturmaktır.

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Soru: Nasıl yaparım? API'de URL değişkenlerini ve sorgu parametrelerini nasıl işleyebilirsiniz?

Cevap: Soru için 1-4. adımda yanıtı [görme: Flask,](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables) değişken URL yolları ve sorgu parametreleriyle nasıl çalışır?

## <a name="step-3-3-add-a-page-to-the-app"></a>3-3. Adım: Uygulamaya sayfa ekleme

Uygulamaya başka bir sayfa eklemek şu anlama gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfanın işaretlemesi için bir şablon ekleyin.
- Flask projesinin urls.py *ekleyin.*

Aşağıdaki adımlar "HelloFlask" projesine bir "Hakkında" sayfası ve giriş sayfasından bu sayfaya bağlantılar ekler:

1. Bu **Çözüm Gezgini** şablonlar klasörüne  sağ tıklayın, Yeni öğe Ekle'yi seçin, HTML Sayfası öğesi şablonunu seçin, dosyayı olarak adlar ve  >    `about.html` Tamam'ı **seçin.**

    > [!Tip]
    > Ekle **menüsünde Yeni** Öğe komutu görünmüyorsa, uygulamanın hata ayıklama modundan çıka Visual Studio emin olun. 

1. Giriş sayfasının *about.html* aşağıdaki işaretlemeyle değiştirin (giriş sayfasının açık bağlantısını 3-4. adımda basit bir gezinti çubuğuyla değiştirirsiniz):

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. Uygulamanın views.py *dosyasını* açın ve şablonu kullanan `about` adlı bir işlev ekleyin:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. *Templates/index.html* dosyasını açın ve öğenin hemen içinde aşağıdaki satırı ekleyen Hakkında sayfasına (yine bu bağlantıyı 3-4. adımda bir gezinti çubuğuyla `<body>` değiştirirsiniz):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Dosya Tüm Dosyaları Kaydet menü **komutunu kullanarak**  >  **tüm dosyaları** kaydedin veya Ctrl Shift S  + **tuşlarına** + **basın.** (Teknik olarak, bu adım projeyi proje içinde çalıştırarak dosyaları otomatik Visual Studio gerekli değildir. Yine de bu, hakkında bilgili olmak için iyi bir komut!)

1. Sonuçları gözlemlemek ve sayfalar arasındaki gezintiyi kontrol etmek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Soru: Sayfa işlevinin adı Flask için önemli mi?

Cevap: Hayır, çünkü Flask'in yanıt oluşturmak için işlevini çağıran URL'leri belirleyen dekoratör `@app.route` olmasıdır. Geliştiriciler genellikle işlev adını yol ile eşleştirmektedir ancak bu tür eşleştirmeler gerekli değildir.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>3-4. Adım: Üst bilgi ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma

Modern web uygulamaları, her sayfada açık gezinti bağlantıları kullanmak yerine genellikle en önemli sayfa bağlantılarını, açılan menüleri ve diğer öğeleri sağlayan bir marka üst bilgisi ve gezinti çubuğu kullanır. Üst bilgi ve gezinti çubuğunun tüm sayfalarda aynı olduğundan emin olmak için, her sayfa şablonunda aynı kodu yinelemek istemiyorsanız. Bunun yerine tüm sayfalarınızı ortak bölümlerini tek bir yerde tanımlamak istiyor siniz.

Flask'in şablon oluşturma sistemi (varsayılan olarak Jinja), belirli öğeleri birden çok şablonda yeniden kullanmak için iki yol sağlar: ekleme ve devralma.

- *Eklemeler,* söz dizimi kullanarak başvuran şablonda belirli bir yere ekley istediğiniz diğer sayfa `{% include <template_path> %}` şablonlarıdır. Yolu kodda dinamik olarak değiştirmek için değişken de kullanabilirsiniz. Eklemeler genellikle bir sayfanın gövdesinde, paylaşılan şablonu sayfada belirli bir konuma çekmek için kullanılır.

- *Devralma,* başvuran şablonun daha sonra üzerinde derlemesi yapılan paylaşılan bir temel şablon belirtmek için sayfa şablonunun başında `{% extends <template_path> %}` kullanır. Devralma genellikle bir uygulamanın sayfaları için paylaşılan düzen, gezinti çubuğu ve diğer yapıları tanımlamak için kullanılır. Bu şekilde başvuran şablonların yalnızca bloklar olarak adlandırılan temel şablonun belirli alanlarını eklemesi veya değiştirmesi *gerekir.*

Her iki durumda `<template_path>` da, uygulamanın *templates klasörüne göredir* ( `../` veya buna da izin `./` verilir).

Temel şablon, ve etiketlerini *kullanarak blokların* `{% block <block_name> %}` çizgilerini `{% endblock %}` oluşturur. Başvuran bir şablon aynı blok adına sahip etiketleri kullanıyorsa, blok içeriği temel şablonun içeriğini geçersiz kılar.

Aşağıdaki adımlar devralmayı gösterir:

1. Uygulamanın *templates* klasöründe, layout.htmladlı yeni bir HTML dosyası oluşturun (Yeni öğe ekle bağlam menüsünü veya HTML Sayfası Ekle' menüsünü kullanarak) ve içeriğini aşağıdaki  >     >  işaretlemeyle değiştirin. ** Bu şablonun, başvuran sayfaların değiştirmesi gereken "content" adlı bir blok içerdiğini görüyorsunuz:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
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

1. Temel şablona başvurmak index.htmlve içerik bloğuna geçersiz kılmak için *şablonları/şablonları* değiştirme. Devralmayı kullanarak bu şablonun basit hale gelir:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Temel şablona da başvurmak about.htmlve içerik bloğuna geçersiz kılmak için *şablonları/şablonları* değiştirme:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları gözlemlemek için sunucuyu çalıştırın. Bittiğinde sunucuyu kapatın.

    ![Gezinti çubuğunu gösteren çalışan uygulama](media/flask/step03-nav-bar.png)

1. Uygulamada önemli değişiklikler yaptığınız için, değişikliklerinizi kaynak denetimine [işlemenin zamanı geldi.](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)

## <a name="next-steps"></a>Sonraki adımlar

Şu kaynaklarla daha derin gidebilirsiniz:

- [Web uygulamasını Azure App Service dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Denetim akışı gibi Jınja şablonlarının daha fazla özelliği için bkz. [Jınja Template Designer belgeleri](http://jinja.palletsprojects.com/en/2.10.x/templates/) (Jinja.pocoo.org)
- Kullanımıyla ilgili ayrıntılar için `url_for` , bkz. Flask uygulama nesnesi belgeleri içindeki [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) (Flask.pocoo.org)
- GitHub eğitim kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
