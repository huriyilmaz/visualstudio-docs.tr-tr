---
title: Visual Studio adım 3, statik dosya ve sayfalarda Flask öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask temellerinin bir walkthrough, özellikle statik dosyaları hizmet, uygulamaya sayfaları eklemek ve şablon devralma kullanmak gösteren
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5aa952a00075cdad262803140ab4c0360f0c62a0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72985179"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>Adım 3: Statik dosyalara hizmet edin, sayfa ekleyin ve şablon kalıtımını kullanın

**Önceki adım: [Görünümler ve sayfa şablonları içeren bir Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)**

Bu öğreticinin önceki adımlarında, tek bir kendi kendine yeten HTML sayfasıyla en az flask uygulaması oluşturmayı öğrendiniz. Ancak modern web uygulamaları genellikle birçok sayfadan oluşur ve tutarlı stil ve davranış sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynaklardan yararlanılır.

Bu adımda, nasıl öğreneceksiniz:

> [!div class="checklist"]
> - Kullanışlı ortak kodla farklı türde yeni dosyaları hızla eklemek için Visual Studio öğe şablonlarını kullanın (adım 3-1)
> - Statik dosyaları koddan servis edin (adım 3-2, isteğe bağlı)
> - Uygulamaya ek sayfa ekleme (adım 3-3)
> - Sayfalar arasında kullanılan bir üstbilgi ve gezinme çubuğu oluşturmak için şablon kalıbı kullanma (adım 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Adım 3-1: Öğe şablonlarını tanıma

Bir Flask uygulaması geliştirdikçe, genellikle çok daha fazla Python, HTML, CSS ve JavaScript dosyaları eklersiniz. Her dosya türü için (ve dağıtım için ihtiyaç duyabileceğiniz *web.config* gibi diğer dosyalar için), Visual Studio başlamanız için kullanışlı [öğe şablonları](python-item-templates.md) sağlar.

Kullanılabilir şablonları görmek için **Çözüm Gezgini'ne**gidin , öğeyi oluşturmak istediğiniz klasöre sağ tıklayın,**Yeni Öğe** **Ekle'yi** > seçin:

![Visual Studio'da yeni öğe iletişim kutusu ekleme](media/flask/step03-add-new-item-dialog.png)

Şablon kullanmak için istenen şablonu seçin, dosya için bir ad belirtin ve **Tamam'ı**seçin. Bu şekilde bir öğe eklemek, dosyayı Visual Studio projenize otomatik olarak ekler ve kaynak denetimi değişikliklerini işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Visual Studio hangi öğe şablonlarının sunacağını nasıl biliyor?

Cevap: Visual Studio proje dosyası (*.pyproj*) python projesi olarak işaretleyen bir proje türü tanımlayıcısı içerir. Visual Studio, yalnızca proje türüne uygun öğe şablonlarını göstermek için bu tür tanımlayıcıyı kullanır. Bu şekilde, Visual Studio her zaman bunları sıralamak için sormadan birçok proje türleri için öğe şablonları zengin bir dizi sağlayabilir.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Adım 3-2: Uygulamanızdan statik dosyalara hizmet

Python ile oluşturulmuş bir web uygulamasında (herhangi bir çerçeve kullanarak), Python dosyalarınız her zaman web barındırıcının sunucusunda çalışır ve hiçbir zaman kullanıcının bilgisayarına aktarılmez. Ancak CSS ve JavaScript gibi diğer dosyalar yalnızca tarayıcı tarafından kullanılır, bu nedenle ana bilgisayar sunucusu istendiğinde olduğu gibi sunar. Bu tür dosyalar "statik" dosyalar olarak adlandırılır ve Flask bunları herhangi bir kod yazmaya gerek kalmadan otomatik olarak teslim edebilir. Örneğin, HTML dosyaları içinde, projedeki göreli bir yolu kullanarak statik dosyalara başvurabilirsiniz. Bu adımdaki ilk bölüm, varolan sayfa şablonuna bir CSS dosyası ekler.

API uç noktası uygulaması gibi koddan statik bir dosya teslim etmeniz gerektiğinde, Flask *statik* (proje kökünde) adlı bir klasördeki göreli yolları kullanarak dosyalara başvurmanızı sağlayan kullanışlı bir yöntem sağlar. Bu adımdaki ikinci bölüm, bu yöntemin basit bir statik veri dosyası kullanarak olduğunu göstermektedir.

Her iki durumda da, dosyaları istediğiniz gibi *statik* altında düzenleyebilirsiniz.

### <a name="use-a-static-file-in-a-template"></a>Şablonda statik dosya kullanma

1. **Solution Explorer'da**Visual Studio projesindeki **HelloFlask** klasörüne sağ tıklayın, Yeni `static`klasör**ekle'yi** **Add** > seçin ve klasöre isim seçin.

1. **Statik** klasöre sağ tıklayın ve Yeni öğe **ekle'yi** > **New item**seçin. Görünen iletişim **kutusunda, Stylesheet** şablonu seçin, dosyayı `site.css`adlandırın ve **Tamam'ı**seçin. **site.css** dosyası projede görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki resme benzer görünmelidir:

    ![Çözüm Gezgini'nde gösterildiği gibi statik dosya yapısı](media/flask/step03-static-file-structure.png)

1. *site.css* içeriğini aşağıdaki kodla değiştirin ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın *templates/index.html* dosyasının içeriğini, adım 2'de kullanılan `<strong>` öğeyi `message` stil sınıfına `<span>` başvuran bir öğeyle değiştiren aşağıdaki kodla değiştirin. Stil sınıfını bu şekilde kullanmak, öğeyi şekillendirmede size çok daha fazla esneklik sağlar.

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

1. Sonuçları gözlemlemek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun ve değişikliklerinizi kaynak denetimine işedin [(adım 2'de](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)açıklandığı gibi).

### <a name="serve-a-static-file-from-code"></a>Koddan statik bir dosya sunma

Flask, projenin `serve_static_file` *statik* klasöründeki herhangi bir dosyaya başvurmak için koddan çağırabileceğiniz bir işlev sağlar. Aşağıdaki işlem, statik bir veri dosyasını döndüren basit bir API bitiş noktası oluşturur.

1. Bunu daha önce yapmadıysanız, *statik* bir klasör oluşturun: **Solution Explorer'da**Visual Studio projesindeki **HelloFlask** klasörüne sağ `static`tıklayın, Yeni Klasör > **Ekle'yi**seçin ve klasörü adlandırın. **Add**

1. *Statik* klasörde, aşağıdaki içerikleri içeren (anlamsız örnek veriler) *data.json* adlı statik bir JSON veri dosyası oluşturun:

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. *views.py,* yöntemi kullanarak statik veri dosyasını döndüren rota /api/veri ile bir `send_static_file` işlev ekleyin:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uygulamayı çalıştırın ve statik dosyanın döndürüldünden haberdar olmak için /api/veri bitiş noktasına gidin. Bitirdiğinizde uygulamayı durdurun.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: Statik dosyaları düzenlemek için herhangi bir kural var mı?

Cevap: *Statik* klasörünüze istediğiniz gibi diğer CSS, JavaScript ve HTML dosyalarını ekleyebilirsiniz. Statik dosyaları düzenlemenin tipik bir yolu, *yazı tipleri,* *komut dosyaları*ve *içerik* (stil sayfaları ve diğer dosyalar için) adlı alt klasörler oluşturmaktır.

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Soru: BIR API'deki URL değişkenlerini ve sorgu parametrelerini nasıl işlerim?

Cevap: Soru için adım 1-4'teki cevaba [bakın: Flask değişken URL yolları ve sorgu parametreleri ile nasıl çalışır?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Adım 3-3: Uygulamaya sayfa ekleme

Uygulamaya başka bir sayfa eklemek aşağıdaki anlamına gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfanın biçimlendirmesi için bir şablon ekleyin.
- Flask projesinin *urls.py* dosyasına gerekli yönlendirmeyi ekleyin.

Aşağıdaki adımlar "HelloFlask" projesine bir "Hakkında" sayfası ve ana sayfadan bu sayfaya bağlantılar ekleyin:

1. **Çözüm Gezgini'nde** **şablonlar** klasörüne sağ tıklayın,**Yeni öğe** **ekle'yi** > seçin, **HTML Sayfa** öğesi şablonu seçin, dosyayı `about.html`adlandırın ve **Tamam'ı**seçin.

    > [!Tip]
    > Yeni **Öğe** komutu **Ekle** menüsünde görünmüyorsa, Visual Studio'nun hata ayıklama modundan çıkması için uygulamayı durdurduğunuzdan emin olun.

1. *about.html'in* içeriğini aşağıdaki biçimlendirmeyle değiştirin (ana sayfadaki açık bağlantıyı adım 3-4'te basit bir gezinme çubuğuyla değiştirirsiniz):

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

1. Uygulamanın *views.py* dosyasını açın ve `about` şablonu kullanan bir işlev ekleyin:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. *templates/index.html* dosyasını açın ve Hakkında sayfaya bağlanmak için `<body>` öğenin hemen içine aşağıdaki satırı ekleyin (yine, bu bağlantıyı adım 3-4'te bir gezinme çubuğuyla değiştirirsiniz):

    ```html
    <div><a href="about">About</a></div>
    ```

1. **Dosya** > **Kaydet Tüm** menü komutunu kullanarak tüm dosyaları kaydedin veya **Ctrl**+**Shift**+**S**tuşuna basın. (Teknik olarak, Visual Studio'da proje yi çalıştıran bu adım akadar değil, dosyaları otomatik olarak kaydeder. Yine de, bilmek iyi bir komut!)

1. Sonuçları gözlemlemek ve sayfalar arasında gezinmeyi denetlemek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Soru: Bir sayfa işlevinin adı Flask için önemli midir?

Cevap: Hayır, çünkü Flask'ın yanıt oluşturmak için işlevi çağırdığı URL'leri belirleyen dekoratördür. `@app.route` Geliştiriciler genellikle işlev adını rotayla eşleşir, ancak bu tür eşleştirme ler gerekli değildir.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Adım 3-4: Üstbilgi ve gezinme çubuğu oluşturmak için şablon kalıbı kullanma

Modern web uygulamaları, her sayfada açık gezinme bağlantılarına sahip olmak yerine genellikle bir marka üstbilgive en önemli sayfa bağlantıları, açılır menüler ve benzeri sağlayan bir gezinti çubuğu kullanır. Üstbilgi ve gezinme çubuğunun tüm sayfalarda aynı olduğundan emin olmak için, her sayfa şablonunda aynı kodu yinelemek istemezsiniz. Bunun yerine, tüm sayfalarınızın ortak bölümlerini tek bir yerde tanımlamak istiyorsunuz.

Flask'ın geçici sistemi (Varsayılan olarak Jinja) birden çok şablon arasında belirli öğeleri yeniden kullanmak için iki araç sağlar: içerir ve devralma.

- *Sözdizimini* `{% include <template_path> %}`kullanarak başvuru şablonuna belirli bir yere eklediğiniz diğer sayfa şablonları içerir. Yolu kodda dinamik olarak değiştirmek istiyorsanız, bir değişken de kullanabilirsiniz. İçerekler genellikle sayfadaki belirli bir konumda paylaşılan şablonu çekmek için bir sayfanın gövdesinde kullanılır.

- `{% extends <template_path> %}` *Devralma,* başvuru şablonunun üzerine inşa ettiği paylaşılan temel şablonu belirtmek için sayfa şablonunun başında kullanır. Devralma genellikle, başvuru şablonlarının *yalnızca blok*adı verilen temel şablonun belirli alanlarını eklemesi veya değiştirmesi gerektiği gibi, bir uygulamanın sayfaları için paylaşılan düzeni, gezinme çubuğunu ve diğer yapıları tanımlamak için kullanılır.

Her iki `<template_path>` durumda da, uygulamanın *şablonlar* `../` klasörüne göredir (veya `./` ayrıca izin verilir).

Temel şablon, *blokları* kullanarak `{% block <block_name> %}` ve `{% endblock %}` etiketleri gösterir. Yönlendiren bir şablon aynı blok ada sahip etiketler kullanıyorsa, engelleme içeriği temel şablonunkini geçersiz kılar.

Aşağıdaki adımlar kalıtım gösterir:

1. Uygulamanın *şablonlar* klasöründe, *düzen.html*adlı yeni bir HTML dosyası **(Yeni öğe** bağlamı **ekle** > menüsünü kullanarak veya**HTML Sayfası** **Ekle'yi** > kullanarak) oluşturun ve içeriğini aşağıdaki biçimlendirmeyle değiştirin. Bu şablonun, yönlendiren sayfaların değiştirmesi gereken tek şey olan "içerik" adlı bir blok içerdiğini görebilirsiniz:

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

1. Temel şablona başvurmak ve içerik bloğunu geçersiz kılmak için *templates/index.html* değiştirin. Devralma kullanarak bu şablonun basitleştiğini görebilirsiniz:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Temel şablona başvurmak ve içerik bloğunu geçersiz kılmak için *templates/about.html* değiştirin:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları gözlemlemek için sunucuyu çalıştırın. Bittiğinde sunucuyu kapatın.

    ![Gezinme çubuğunu gösteren uygulama çalıştırma](media/flask/step03-nav-bar.png)

1. Uygulamada önemli değişiklikler yaptığınız için, [değişikliklerinizi kaynak denetimine işlemek için](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)tekrar iyi bir zaman.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Flask Web Project şablonuna tam ını kullanma](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Daha derine inin

- [Web uygulamasını Azure Uygulama Hizmetine dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Jinja şablonlarının denetim akışı gibi daha fazla yeteneği için [Bkz. Jinja Şablon Tasarımcısı Belgeleri](http://jinja.palletsprojects.com/en/2.10.x/templates/) (jinja.pocoo.org)
- Kullanma `url_for`hakkında ayrıntılı bilgi için, Flask Application nesne sit belgesi (flask.pocoo.org) içindeki [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) bakın
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
