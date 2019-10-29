---
title: Visual Studio adım 3, statik dosya ve sayfalarda Flask öğreticisi hakkında bilgi edinin
titleSuffix: ''
description: Visual Studio projeleri bağlamında, özellikle statik dosyaları nasıl kullanacağınızı, uygulamaya sayfa eklemeyi ve şablon devralmayı kullanmayı gösteren Flask temelleri hakkında bir anlatım.
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
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985179"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance"></a>3\. Adım: statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma

**Önceki adım: [görünümler ve sayfa şablonlarıyla Flask uygulaması oluşturma](learn-flask-visual-studio-step-02-create-app.md)**

Bu öğreticinin önceki adımlarında, kendine dahil edilen HTML 'nin tek bir sayfası ile en az bir Flask uygulaması oluşturmayı öğrendiniz. Ancak modern Web Apps, genellikle birçok sayfadan oluşur ve tutarlı stil oluşturma ve davranış sağlamak için CSS ve JavaScript dosyaları gibi paylaşılan kaynakları kullanır.

Bu adımda şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Uygun ortak kod ile farklı türlerdeki yeni dosyaları hızlıca eklemek için Visual Studio öğe şablonlarını kullanın (adım 3-1)
> - Koddan statik dosyaları sunma (adım 3-2, isteğe bağlı)
> - Uygulamaya ek sayfalar ekleme (adım 3-3)
> - Sayfalarda kullanılan bir başlık ve gezinme çubuğu oluşturmak için şablon devralmayı kullanın (adım 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>Adım 3-1: öğe şablonları hakkında bilgi sahibi olun

Flask uygulaması geliştirirken, genellikle birçok Python, HTML, CSS ve JavaScript dosyası eklersiniz. Her dosya türü için (Ayrıca, dağıtım için ihtiyaç duyduğunuz *Web. config* gibi diğer dosyalar), Visual Studio başlamanıza olanak sağlamak için uygun [öğe şablonları](python-item-templates.md) sağlar.

Kullanılabilir şablonları görmek için **Çözüm Gezgini**gidin, öğeyi oluşturmak istediğiniz klasöre sağ tıklayın, **Ekle** > **Yeni öğe**' yi seçin:

![Visual Studio 'da yeni öğe Ekle iletişim kutusu](media/flask/step03-add-new-item-dialog.png)

Bir şablon kullanmak için, istediğiniz şablonu seçin, dosya için bir ad belirtin ve **Tamam**' ı seçin. Bu şekilde bir öğe eklemek, dosyayı otomatik olarak Visual Studio projenize ekler ve kaynak denetimi için değişiklikleri işaretler.

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>Soru: Visual Studio hangi öğe şablonlarının önereceğimizi nasıl bilir?

Cevap: Visual Studio proje dosyası ( *. pyproj*), bir Python projesi olarak işaretleyen bir proje türü tanımlayıcısı içerir. Visual Studio yalnızca proje türü için uygun olan öğe şablonlarını göstermek için bu tür tanımlayıcısını kullanır. Bu şekilde, Visual Studio her seferinde her seferinde sıralama yapmanızı istemeden birçok proje türü için zengin bir öğe şablonları kümesi sağlayabilir.

## <a name="step-3-2-serve-static-files-from-your-app"></a>Adım 3-2: uygulamanızdan statik dosyaları sunma

Python ile derlenen bir Web uygulamasında (herhangi bir Framework kullanılarak), Python dosyalarınız her zaman Web ana bilgisayarı sunucusunda çalışır ve bir kullanıcının bilgisayarına hiçbir zaman aktarılmaz. Ancak, CSS ve JavaScript gibi diğer dosyalar yalnızca tarayıcı tarafından kullanılır, bu nedenle ana bilgisayar sunucusu bu dosyaları istendiği zaman olduğu gibi teslim eder. Bu tür dosyalar "static" dosyalar olarak adlandırılır ve Flask bunları herhangi bir kod yazmaya gerek kalmadan otomatik olarak teslim edebilir. Örneğin, HTML dosyaları içinde, yalnızca projedeki göreli bir yol kullanarak statik dosyalara başvurabilirsiniz. Bu adımdaki ilk bölüm, var olan sayfa şablonunuza bir CSS dosyası ekler.

Bir API uç noktası uygulamasıyla olduğu gibi koddan statik bir dosya teslim etmeniz gerektiğinde, Flask *statik* adlı bir klasör içinde (proje kökünde) göreli yollar kullanarak dosyalara başvurmanızı sağlayan kullanışlı bir yöntem sağlar. Bu adımdaki ikinci bölüm, bir basit statik veri dosyası kullanarak bu yöntemi gösterir.

Her iki durumda da, istediğiniz gibi dosyaları *statik* olarak düzenleyebilirsiniz.

### <a name="use-a-static-file-in-a-template"></a>Şablonda statik dosya kullanma

1. **Çözüm Gezgini**, Visual Studio projesindeki **Helloflask** klasörüne sağ tıklayın, > **Yeni klasör** **Ekle** ' yi seçin ve klasörü `static`olarak adlandırın.

1. **Statik** klasöre sağ tıklayın ve > **Yeni öğe** **Ekle** ' yi seçin. Görüntülenen iletişim kutusunda, **stil sayfası** şablonunu seçin, dosyayı `site.css`olarak adlandırın ve **Tamam**' ı seçin. **Site. css** dosyası projede görünür ve düzenleyicide açılır. Klasör yapınız aşağıdaki görüntüye benzer görünmelidir:

    ![Çözüm Gezgini gösterildiği gibi statik dosya yapısı](media/flask/step03-static-file-structure.png)

1. *Site. css* içeriğini aşağıdaki kodla değiştirin ve dosyayı kaydedin:

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. Uygulamanın *Templates/index.html* dosyasının içeriğini aşağıdaki kodla değiştirin ve bu, adım 2 ' de kullanılan `<strong>` öğesinin `message` Style sınıfına başvuran bir `<span>` ile değiştirir. Bu şekilde bir stil sınıfı kullanmak, öğe stillendirme konusunda çok daha fazla esneklik sağlar.

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

1. Sonuçları gözlemlemek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun ve isterseniz kaynak denetimine yaptığınız değişiklikleri kaydedin ( [Adım 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)' de açıklandığı gibi).

### <a name="serve-a-static-file-from-code"></a>Koddan statik bir dosya sunma

Flask, projenin *statik* klasörü içindeki herhangi bir dosyaya başvurmak üzere koddan çağrabileceğiniz `serve_static_file` adlı bir işlev sağlar. Aşağıdaki işlem, statik bir veri dosyası döndüren basit bir API uç noktası oluşturur.

1. Daha önce yapmadıysanız, bir *statik* klasör oluşturun: **Çözüm Gezgini**, Visual Studio projesindeki **helloflask** klasörüne sağ tıklayın, > **Yeni klasör** **Ekle** ' yi seçin ve klasörü `static`olarak adlandırın.

1. *Statik* klasörde, *Data. JSON* adlı statik bir JSON veri dosyası oluşturun (anlamsız örnek veriler):

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. *Views.py*içinde `send_static_file` yöntemi kullanılarak statik veri dosyasını döndüren Route/api/Data adlı bir işlev ekleyin:

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. Uygulamayı çalıştırın ve statik dosyanın döndürüldüğünden emin olmak için/api/Data uç noktasına gidin. İşiniz bittiğinde uygulamayı durdurun.

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>Soru: statik dosyaları düzenlemek için herhangi bir kural var mı?

Yanıt: diğer CSS, JavaScript ve HTML dosyalarını *statik* klasörünüze ekleyebilirsiniz, ancak istediğiniz gibi. Statik dosyaları düzenlemenin tipik bir yolu, *yazı tipleri*, *betikler*ve *içerik* (stil sayfaları ve diğer dosyalar için) adlı alt klasörler oluşturmaktır.

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>Soru: bir API 'de URL değişkenlerini ve sorgu parametrelerini işlemek Nasıl yaparım??

Cevap: adım 1-4: soru için bkz. adım [: nasıl Flask, DEĞIŞKEN URL rotalarıyla ve sorgu parametreleriyle nasıl çalışır?](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>Adım 3-3: uygulamaya bir sayfa ekleme

Uygulamaya başka bir sayfa eklemek aşağıdakiler anlamına gelir:

- Görünümü tanımlayan bir Python işlevi ekleyin.
- Sayfa işaretlemesi için bir şablon ekleyin.
- Flask projesinin *URLs.py* dosyasına gerekli yönlendirmeyi ekleyin.

Aşağıdaki adımlarda "HelloFlask" projesine bir "About" sayfası ve bu sayfanın giriş sayfasından bağlantıları verilmiştir:

1. **Çözüm Gezgini**, **Şablonlar** klasörüne sağ tıklayın, > **Yeni öğe** **Ekle** ' yi seçin, **HTML sayfası** öğe şablonunu seçin, dosyayı `about.html`olarak adlandırın ve **Tamam**' ı seçin.

    > [!Tip]
    > **Yeni öğe** komutu **Ekle** menüsünde görünmezse, Visual Studio 'nun hata ayıklama modundan çıkmasını sağlamak için uygulamayı durdurduğunuzdan emin olun.

1. For *. html* içeriğini aşağıdaki biçimlendirmeyle değiştirin (adım 3-4 ' de basit bir gezinti çubuğu ile giriş sayfasına yönelik açık bağlantıyı değiştirirsiniz):

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

1. Uygulamanın *views.py* dosyasını açın ve şablonu kullanan `about` adlı bir işlev ekleyin:

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. *Templates/index.html* dosyasını açın ve hakkında hemen `<body>` öğesi içinde aşağıdaki satırı ekleyin (Bu bağlantıyı, adım 3-4 ' deki bir gezinti çubuğu ile değiştirirsiniz):

    ```html
    <div><a href="about">About</a></div>
    ```

1. Tüm dosyaları > **Dosya** kullanarak Tümünü Kaydet menü komutunu **kaydedin** veya **CTRL**+**SHIFT**+**S**tuşlarına basın. (Teknik olarak, Visual Studio 'da projeyi çalıştırmak için bu adım gerekli değildir. dosyaları otomatik olarak kaydeder. Bununla birlikte, bunun hakkında bilgi edinmek için iyi bir komuttur!)

1. Sonuçları gözlemlemek ve sayfalar arasında gezinmeyi denetlemek için projeyi çalıştırın. Bittiğinde uygulamayı durdurun.

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>Soru: bir sayfa işlevinin adı Flask 'ye göre mi?

Yanıt: Hayır, çünkü Flask 'nin bir yanıt oluşturmak için işlevi çağırdığı URL 'Leri belirleyen `@app.route` dekoratör. Geliştiriciler genellikle yol ile eşleşen işlev adı ile eşleşir, ancak bu tür eşleştirme gerekli değildir.

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>Adım 3-4: başlık ve gezinti çubuğu oluşturmak için şablon devralmayı kullanma

Modern Web Apps, her sayfada açık gezinti bağlantıları sağlamak yerine genellikle bir marka üst bilgisi ve en önemli sayfa bağlantılarını, açılan menüleri vb. sağlayan bir gezinti çubuğu kullanır. Üst bilgi ve gezinti çubuğunun tüm sayfalarda aynı olduğundan emin olmak için, her sayfa şablonunda aynı kodu yinelemek istemezsiniz. Bunun yerine, tüm sayfalarınızın ortak parçalarını tek bir yerde tanımlamak isteyebilirsiniz.

Flask 'nın şablon oluşturma sistemi (varsayılan olarak Jınja), birden çok şablon genelinde belirli öğeleri yeniden kullanmak için iki yol sağlar: dahil ve devralma.

- *Dahil* olmak üzere, başvuran şablonda belirli bir yere eklediğiniz sözdizimini `{% include <template_path> %}`kullanarak eklediğiniz diğer sayfa şablonlarıdır. Ayrıca, kodda dinamik olarak yolu değiştirmek istiyorsanız bir değişkeni de kullanabilirsiniz. Eklemeleri genellikle sayfanın gövdesinde, paylaşılan şablonu sayfada belirli bir konumda çekmek için kullanılır.

- *Devralma* , başvuran şablonun üzerinde derleneceği paylaşılan temel şablonu belirtmek için bir sayfa şablonunun başındaki `{% extends <template_path> %}` kullanır. Devralma genellikle, bir uygulamanın sayfalarına yönelik olarak paylaşılan bir düzen, gezinme çubuğu ve diğer yapıları tanımlamak için kullanılır. bu nedenle, şablonlar yalnızca temel şablonun *bloklar*olarak adlandırılan belirli bölgelerini eklemesi veya değiştirmesi gerekir.

Her iki durumda da `<template_path>`, uygulamanın *Şablonlar* klasörüne (`../` veya `./` de izin verilir) göredir.

Temel şablon, `{% block <block_name> %}` ve `{% endblock %}` etiketlerini kullanarak *blokları* ayırıcıları. Başvurulan bir şablon daha sonra aynı blok adına sahip Etiketler kullanıyorsa, blok içeriği temel şablonun üzerine yazar.

Aşağıdaki adımlarda devralma gösterilmektedir:

1. Uygulamanın *Şablonlar* klasöründe, *Layout. html*adlı yeni bir html dosyası oluşturun **( > ** **Yeni öğe** bağlam menüsünü veya **Add** > **HTML sayfası**' nı kullanarak) ve içeriğini aşağıdaki biçimlendirme ile değiştirin. Bu şablonun, başvuran sayfaların yerini almak için gereken "içerik" adlı bir blok içerdiğini görebilirsiniz:

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

1. *Templates/index.html* öğesini temel şablona başvuracak ve içerik bloğunu geçersiz kılacak şekilde değiştirin. Devralma kullanarak bu şablonu basit hale getirebilirsiniz:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. Ayrıca, *Templates/about.html* öğesini temel şablona başvuracak ve içerik bloğunu geçersiz kılacak şekilde değiştirin:

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. Sonuçları gözlemlemek için sunucuyu çalıştırın. Bitince sunucuyu kapatın.

    ![Gezinti çubuğunu gösteren uygulama çalıştırılıyor](media/flask/step03-nav-bar.png)

1. Uygulamada önemli değişiklikler yapıldığından, [değişikliklerinizi kaynak denetimine kaydetmek](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)iyi bir zaman alabilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Tam Flask Web projesi şablonunu kullanın](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>Daha derin git

- [Web uygulamasını Azure App Service dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- Denetim akışı gibi Jınja şablonlarının daha fazla özelliği için bkz. [Jınja Template Designer belgeleri](http://jinja.palletsprojects.com/en/2.10.x/templates/) (Jinja.pocoo.org)
- `url_for`kullanma hakkında ayrıntılı bilgi için Flask uygulama nesnesi belgeleri içindeki [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for) (Flask.pocoo.org) bölümüne bakın.
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-Flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
