---
title: 3. adım, statik Visual Studio sayfalarda Flask öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask ile ilgili temel bilgiler, özellikle statik dosyaların nasıl hizmet ve uygulama sayfaları ekleneceklerini ve şablon devralmayı nasıl kullanabileceğini gösteren kılavuz
ms.date: 01/26/2022
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: b326049887d4e1a8b92847cfc0aca0fb23bf609a
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886793"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>3. Adım: Flask uygulamasıyla statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma

**Önceki adım: [Görünümler ve sayfa şablonlarıyla bir Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)**

Bu öğreticinin önceki adımlarında, tek sayfalık kendi içinde HTML ile minimal bir Flask uygulaması oluşturma hakkında bilgi edindisiniz. Ancak modern web uygulamaları genellikle birçok sayfadan oluşur ve tutarlı stil ve davranış sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynakları kullanır.

Bu adımda şunların nasıl olduğunu öğreniriz:

> [!div class="checklist"]
> - Kolay Visual Studio farklı türlerde yeni dosyaları hızla eklemek için yeni öğe şablonları kullanma (3-1. adım)
> - Koddan statik dosyaları hizmet etme (3-2. adım, isteğe bağlı)
> - Uygulamaya başka sayfalar ekleme (3-3. adım)
> - Sayfalar arasında kullanılan bir üst bilgi ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma (3-4. adım)

## <a name="step-3-1-become-familiar-with-item-templates"></a>3.-1. Adım: Öğe şablonları hakkında bilgi sahibi olma

Flask uygulaması geliştirirken genellikle çok daha fazla Python, HTML, CSS ve JavaScript dosyası eklersiniz. Her dosya türü (dağıtım için ihtiyaçweb.configgibi diğer dosyalar **) için Visual Studio başlamanız için kullanışlı öğe şablonları sağlar.[](python-item-templates.md)

Kullanılabilir şablonları görmek için **Çözüm Gezgini'a** gidin, öğeyi oluşturmak istediğiniz klasöre sağ tıklayın ve **EkleYeni Öğe'yi** >  seçin:

![Yeni öğe ekle iletişim kutusu Visual Studio](media/flask/step03-add-new-item-dialog.png)

Şablon kullanmak için istenen şablonu seçin, dosya için bir ad belirtin ve Tamam'ı **seçin**. Bu şekilde bir öğe eklemek, dosyayı otomatik olarak Visual Studio projenize ekler ve değişiklikleri kaynak denetimi için işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Hangi Visual Studio şablonlarını nasıl bilebilirsiniz?

Cevap: Visual Studio dosyası (*.pyproj*) bunu Python projesi olarak işaret alan bir proje türü tanımlayıcısı içerir. Visual Studio, yalnızca proje türüne uygun öğe şablonlarını göstermek için bu tür tanımlayıcısını kullanır. Bu şekilde Visual Studio her zaman sıralamak istemeden birçok proje türü için zengin bir öğe şablonu kümesi sebilirsiniz.

## <a name="step-3-2-serve-static-files-from-your-app"></a>3-2. Adım: Uygulamanıza statik dosyaları hizmet etme

Python ile derlen bir web uygulamasında (herhangi bir çerçeve kullanılarak), Python dosyalarınız her zaman web ana bilgisayarının sunucusunda çalıştırıldı ve hiçbir zaman kullanıcının bilgisayarına aktarıldı. Ancak CSS ve JavaScript gibi diğer dosyalar yalnızca tarayıcı tarafından kullanılır, bu nedenle ana bilgisayar sunucusu isten her durumda olduğu gibi bunları teslim ediyor. Bu tür dosyalar "statik" dosyalar olarak adlandırılır ve Flask bunları kod yazmanız gerekmeden otomatik olarak teslim eder. Örneğin, HTML dosyalarının içinde, projesinde göreli bir yol kullanarak statik dosyalara başvurabilirsiniz. Bu adımın ilk bölümü, mevcut sayfa şablonunuz için bir CSS dosyası ekler.

Bir API uç noktası uygulaması aracılığıyla koddan statik bir dosya teslim etmek için Flask, *statik adlı bir* klasördeki göreli yolları (proje kökünde) kullanarak dosyalara başvurarak kullanışlı bir yöntem sağlar. Bu adımın ikinci bölümünde, basit bir statik veri dosyası kullanılarak bu yöntem gösterildi.

Her iki durumda da, dosyaları statik altında *nasıl olur da* böyle düzenleyebilirsiniz.

### <a name="use-a-static-file-in-a-template"></a>Şablonda statik dosya kullanma

1. Bu **Çözüm Gezgini**, Visual Studio projesinde **HelloFlask** klasörüne sağ tıklayın, **EkleYeni** >  klasör'e tıklayın ve klasöre adını girin`static`.

1. Statik klasöre sağ **tıklayın ve** **EkleYeni** **öğe'yi** >  seçin. Görüntülenen iletişim kutusunda Stil Sayfası şablonunu **seçin**, dosyaya adını ve ardından Tamam'ı `site.css`**seçin**. **Site.css** dosyası projede görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki görüntüye benzer görünse:

    ![Dosyalarda gösterildiği gibi statik Çözüm Gezgini](media/flask/step03-static-file-structure.png)

1. *site.css içeriğini aşağıdaki* kodla değiştirin ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın *şablonlarının/index.html* dosyasının içeriğini aşağıdaki kodla değiştirin. Bu kod, `<strong>` 2 `<span>` `message` . adımda kullanılan öğesini stil sınıfına başvurulan bir ile değiştirir. Stil sınıfını bu şekilde kullanmak, öğenin stilini oluşturma konusunda çok daha fazla esneklik sağlar.

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

1. Sonuçları gözlemlemek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun ve [2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control). adımda açıklanmıştır.

### <a name="serve-a-static-file-from-code"></a>Koddan statik dosya hizmet etme

Flask, projenin statik klasöründeki `serve_static_file` herhangi bir dosyaya başvurmak için koddan çağırabilirsiniz adlı bir *işlev* sağlar. Aşağıdaki işlem, statik veri dosyası döndüren basit bir API uç noktası oluşturur.

1. Henüz bunu yapmadıysanız statik klasör oluşturun: **Çözüm Gezgini'de Visual Studio** projesinde **HelloFlask** klasörüne sağ tıklayın,  > **EkleYeni klasör'dür'dür** ve klasörünü olarak ad girin`static`.

1. Statik *klasörde,* aşağıdaki içeriklere sahip *data.json* adlı bir statik JSON veri dosyası oluşturun (bu, anlamsız örnek verilerdir):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. Bu *views.py* yöntemini kullanarak statik veri dosyasını döndüren /api/data yolu ile bir işlev `send_static_file` ekleyin:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uygulamayı çalıştırın ve statik dosyanın döndürül olduğunu görmek için /api/data uç noktasına gidin. Bitirinca uygulamayı durdurun.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: Statik dosyaları düzenlemek için herhangi bir kural var mı?

Cevap: Statik klasörünüzdeki diğer CSS, JavaScript ve HTML dosyalarını *istediğiniz* gibi abilirsiniz. Statik dosyaları düzenlemenin tipik bir yolu yazı *tipleri,* betikler ve *içerik (stil* sayfaları ve diğer dosyalar için) adlı alt klasörler oluşturmaktır.

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Soru: Nasıl yaparım? API'de URL değişkenlerini ve sorgu parametrelerini nasıl işleyebilirsiniz?

Cevap: Soru için 1-4. adımda yanıtı görme [: Flask, değişken URL yolları ve sorgu parametreleriyle nasıl çalışır?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>3-3. Adım: Uygulamaya sayfa ekleme

Uygulamaya başka bir sayfa eklemek şu anlama gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfanın işaretlemesi için bir şablon ekleyin.
- Flask projesinin *urls.py ekleyin.*

Aşağıdaki adımlar "HelloFlask" projesine bir "Hakkında" sayfası ve giriş sayfasından bu sayfaya bağlantılar ekler:

1. Bu **Çözüm Gezgini** şablonlar klasörüne sağ tıklayın, **EkleYeni** >  öğe'yi seçin, **HTML Sayfası** öğesi şablonunu seçin, dosyayı olarak ad `about.html`girin ve Tamam'ı **seçin**.

    > [!Tip]
    > Ekle **menüsünde Yeni** Öğe komutu görünmüyorsa, uygulamanın hata  ayıklama modundan çıka Visual Studio emin olun.

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

1. Uygulamanın *views.py dosyasını açın* ve şablonu kullanan adlı `about` bir işlev ekleyin:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. Templates */index.html* `<body>` dosyasını açın ve Hakkında sayfasına bağlantı oluşturmak için öğenin hemen içinde aşağıdaki satırı ekleyin (yine bu bağlantıyı 3-4. adımda bir gezinti çubuğuyla değiştirirsiniz):

    ```html
    <div><a href="about">About</a></div>
    ```

1. DosyaSave All menü komutunu **kullanarak** >  **tüm** dosyaları kaydedin veya **CtrlShiftS tuşlarına**+ **basın**+. (Teknik olarak, bu adım projeyi otomatik olarak kaydederken proje Visual Studio gerekli değildir. Yine de bu, hakkında bilgili olmak için iyi bir komut!)

1. Sonuçları gözlemlemek ve sayfalar arasındaki gezintiyi kontrol etmek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Soru: Sayfa işlevinin adı Flask için önemli mi?

Cevap: Hayır, çünkü Flask'in yanıt oluşturmak için işlevini çağıran URL'leri `@app.route` belirleyen dekoratör olmasıdır. Geliştiriciler genellikle işlev adını yol ile eşleştirmektedir ancak bu tür eşleştirmeler gerekli değildir.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>3-4. Adım: Üst bilgi ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma

Modern web uygulamaları, her sayfada açık gezinti bağlantıları kullanmak yerine genellikle en önemli sayfa bağlantılarını, açılan menüleri ve diğer öğeleri sağlayan bir marka üst bilgisi ve gezinti çubuğu kullanır. Üst bilgi ve gezinti çubuğunun tüm sayfalarda aynı olduğundan emin olmak için, her sayfa şablonunda aynı kodu tekrarlamak istemiyorsanız. Bunun yerine tüm sayfalarınızı ortak bölümlerini tek bir yerde tanımlamak istiyor siniz.

Flask'in şablon oluşturma sistemi (varsayılan olarak Jinja), belirli öğeleri birden çok şablonda yeniden kullanmak için iki yol sağlar: ekleme ve devralma.

- *Eklemeler* , söz dizimi kullanarak başvuran şablonda belirli bir yere ekley istediğiniz diğer sayfa şablonlarıdır `{% include <template_path> %}`. Yolu kodda dinamik olarak değiştirmek için değişken de kullanabilirsiniz. Eklemeler genellikle bir sayfanın gövdesinde, paylaşılan şablonu sayfada belirli bir konuma çekmek için kullanılır.

- *Devralma* , başvuran `{% extends <template_path> %}` şablonun daha sonra üzerinde derlemesi yapılan paylaşılan bir temel şablon belirtmek için sayfa şablonunun başında kullanır. Devralma genellikle bir uygulamanın sayfaları için paylaşılan düzen, gezinti çubuğu ve diğer yapıları tanımlamak için kullanılır; bu şekilde başvuran şablonların yalnızca blok olarak adlandırılan temel şablonun belirli alanlarını eklemesi veya değiştirmesi *gerekir*.

Her iki durumda da `<template_path>` , uygulamanın *templates klasörüne göredir* ( veya`../` buna `./` da izin verilir).

Temel şablon, ve etiketlerini *kullanarak blokların* çizgilerini `{% block <block_name> %}` `{% endblock %}` oluşturur. Başvuran bir şablon aynı blok adına sahip etiketleri kullanıyorsa, blok içeriği temel şablonun içeriğini geçersiz kılar.

Aşağıdaki adımlar devralmayı gösterir:

1. Uygulamanın *templates* klasöründelayout.htmladlı yeni bir HTML dosyası oluşturun (**Yeni** >  öğe ekle bağlam menüsünü veya **AddHTML** >  Sayfasını kullanarak) *ve* içeriğini aşağıdaki işaretlemeyle değiştirin. Bu şablonun, başvuran sayfaların değiştirmesi gereken "content" adlı bir blok içerdiğini görüyorsunuz:

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

1. Temel *şablona başvurmak index.html* ve içerik bloğuna geçersiz kılmak için şablonları/şablonları değiştirme. Devralmayı kullanarak bu şablonun basit hale gelir:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Şablonları */about.html* şablonu da ifade etmek ve içerik bloğuna geçersiz kılmak için değiştirme:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları gözlemlemek için sunucuyu çalıştırın. Bittiğinde sunucuyu kapatın.

    ![Gezinti çubuğunu gösteren çalışan uygulama](media/flask/step03-nav-bar.png)

1. Uygulamada önemli değişiklikler yaptığınız için, değişikliklerinizi kaynak denetimine [işlemenin zamanı geldi](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control).

## <a name="next-steps"></a>Sonraki adımlar

Şu kaynaklarla daha derin gidebilirsiniz:

- [Web uygulamasını Azure App Service dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Denetim akışı gibi Jınja şablonlarının daha fazla özelliği için bkz. [Jınja Template Designer belgeleri](http://jinja.palletsprojects.com/en/2.10.x/templates/) (Jinja.pocoo.org)
- Kullanımıyla `url_for` ilgili ayrıntılar için, bkz. Flask uygulama nesnesi belgeleri içindeki [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) (Flask.pocoo.org)
- GitHub eğitim kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
