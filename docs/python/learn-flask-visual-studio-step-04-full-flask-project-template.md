---
title: Visual Studio adım 4, web proje şablonları Flask öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask temellerinin bir walkthrough, özellikle Flask Web Projesi ve Flask / Yeşim Web Projesi şablonları tarafından sağlanan özellikleri.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9f4c165f3e882cea71ee4aaff9f2358c27ce6a2b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957323"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>Adım 4: Flask Web Projesi şablonuna tam olarak kullanın

**Önceki adım: [Statik dosyalara hizmet edin, sayfa ekleyin ve şablon kalıtımını kullanın](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Visual Studio'daki "Blank Flask App Project" şablonu üzerine bir uygulama oluşturarak Flask'ın temellerini keşfettiğinize göre, "Flask Web Project" şablonu tarafından üretilen dolgun uygulamayı kolayca anlayabilirsiniz.

Bu adımda şimdi:

> [!div class="checklist"]
> - "Flask Web Project" şablonu kullanarak daha dolgun bir Flask web uygulaması oluşturun ve proje yapısını inceleyin (adım 4-1)
> - Temel sayfa şablonundan devralan ve jQuery ve Bootstrap (adım 4-2) gibi statik JavaScript kitaplıklarını kullanan üç sayfadan oluşan proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama
> - Şablon tarafından sağlanan URL yönlendirmesini anlama (adım 4-3)

Bu makale, Jinja yerine Yeşim templating motoru kullanarak "Flask Web Project" ile aynı olan bir uygulama üreten "Flask/Jade Web Project" şablonu için de geçerlidir. Bu makalenin sonunda ek ayrıntılar yer alabilirsiniz.

## <a name="step-4-1-create-a-project-from-the-template"></a>Adım 4-1: Şablondan proje oluşturma

1. Visual Studio'da **Solution Explorer'a**gidin, bu eğitimde daha önce oluşturulan **LearningFlask** çözümüne sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, bunun yerine **Dosya** > **Yeni** > **Projesi'ni** seçin.)

1. Yeni proje iletişim kutusunda, **Flask Web Project** şablonunu arayın ve seçin, projeyi "FlaskWeb" olarak arayın ve **Tamam'ı**seçin.

1. Şablon yine bir *requirements.txt* dosyası içerdiğinden, Visual Studio bu bağımlılıkları nereye yükleyebileceğinizi sorar. Seçeneği seçin, **sanal ortama yükle**ve Sanal Ortam **Ekle** iletişim kutusunda varsayılanları kabul etmek için **Oluştur'u** seçin.

1. Visual Studio sanal ortamı ayarlamayı bitirdikten sonra, **Solution Explorer'daki** projeyi sağ tıklatarak ve Başlangıç Projesi olarak **Set'i**seçerek **FlaskWeb** projesini Visual Studio çözümü için varsayılan olarak ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklamayı başlattığınızda çalıştırılan şeydir.

    ![Başlangıç projesi olarak FlaskWeb projesini gösteren Çözüm Gezgini](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. **Hata Ayıklama** > **Hata Ayıklama** **(F5)** seçeneğini belirleyin veya sunucuyu çalıştırmak için araç çubuğundaki **Web Sunucusu** düğmesini kullanın:

    ![Visual Studio'da web sunucusu araç çubuğu düğmesini çalıştırın](media/flask/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama, gezinme çubuğunu kullanarak arasında gezindiğiniz Ana Sayfa, Hakkında ve İletişim olmak üzere üç sayfadan oluşur. Uygulamanın farklı bölümlerini incelemek için bir veya iki dakika ayırın. **Oturum Açma** komutu aracılığıyla uygulamayla kimlik doğrulaması yapmak için daha önce oluşturulan süper kullanıcı kimlik bilgilerini kullanın.

    ![Flask Web Project uygulamasının tam tarayıcı görünümü](media/flask/step04-full-app-desktop-view.png)

1. "Flask Web Project" şablonu tarafından oluşturulan uygulama, mobil form etkenlerini barındıran duyarlı mizanpaj için Bootstrap'ı kullanır. Bu yanıt verme yeteneğini görmek için tarayıcıyı dar bir görünüme yeniden boyutlandırArak içeriğin dikey olarak işlenmesini ve gezinme çubuğunun menü simgesine dönüşmesini sağlar:

    ![Flask Web Project uygulamasının mobil (dar) görünümü](media/flask/step04-full-app-mobile-view.png)

1. Takip eden bölümler için uygulamayı çalışır durumda bırakabilirsiniz.

    Uygulamayı durdurmak ve kaynak [denetiminde değişiklikler yapmak](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)istiyorsanız, önce **Team Explorer'da** **Değişiklikler** sayfasını açın , sanal ortam için klasörü sağ tıklatın (muhtemelen **env),** ve **bu yerel öğeleri yoksay'ı**seçin.

### <a name="examine-what-the-template-creates"></a>Şablonun ne oluşturduğunu inceleme

"Flask Web Project" şablonu aşağıdaki yapıyı oluşturur. İçeriği, önceki adımlarda oluşturduğunuz şeye çok benzer. Fark, "Flask Web Project" şablonu, duyarlı tasarım için jQuery ve Bootstrap içerdiğinden *statik* klasörde daha fazla yapı içeriyor olmasıdır. Şablon ayrıca bir Kişi sayfası ekler. Genel olarak, bu öğreticide önceki adımları izlediyseniz, şablondaki her şey tanıdık olmalıdır.

- Proje kökündeki dosyalar:
  - *runserver.py,* uygulamayı bir geliştirme sunucusunda çalıştırmak için bir komut dosyası.
  - *requirements.txt* Flask 0.x bir bağımlılık içeren.
- *FlaskWeb* klasörü tüm uygulama dosyalarını içerir:
  - init.py uygulama kodunu Python modülü olarak işaretler, Flask nesnesini oluşturur ve uygulamanın görünümlerini içeri iter. * \_ \_\_ *
  - *views.py* sayfaları işlemek için kod içerir.
  - *Statik* klasör, *içerik* (CSS dosyaları), *yazı tipleri* (yazı tipi dosyaları) ve komut dosyaları (JavaScript dosyaları) adlı alt *klasörleri* içerir.
  - *Şablonlar* klasörü *about.html, contact.html*ve *index.html* ile birlikte her *layout.html*genişletmek belirli sayfalar için bir *layout.html* temel şablonu içerir. *contact.html*

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Soru: Visual Studio projeleri arasında sanal bir ortamı paylaşmak mümkün mü?

Cevap: Evet, ancak bunu farklı projelerin zaman içinde farklı paketler kullanma olasılığının yüksek olduğu bilinciyle yapın ve bu nedenle paylaşılan bir sanal ortam, onu kullanan tüm projeler için tüm paketleri içermelidir.

Bununla birlikte, varolan bir sanal ortamı kullanmak için aşağıdakileri yapın:

1. Visual Studio bağımlılıkları yüklemek istendiğinde, ben onları kendim seçeneği **yükleyeceğim** seçin.
1. **Çözüm Gezgini'nde** **Python Ortamları** düğümüne sağ tıklayın ve **Varolan Sanal Ortam Ekle'yi**seçin.
1. Sanal ortamı içeren klasöre gidin ve seçin, ardından **Tamam'ı**seçin.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Adım 4-2: Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama

Projeyi çalıştırırken gözlemlediğiniz gibi, uygulama üç görünüm içerir: Ev, İletişim ve İletişim. Bu görünümlerin kodu *FlaskWeb/views.py*bulunur. Her görünüm işlevi `flask.render_template` yalnızca şablona giden yol ve şablona verilebilmek için değerler için bağımsız değişken bir liste yle çağırır. Örneğin, Hakkında sayfası `about` işlev (olan dekoratör URL yönlendirme sağlar) tarafından işlenir:

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

`home` Ve `contact` işlevleri hemen hemen aynıdır, benzer dekoratörler ve biraz farklı argümanlar ile.

Şablonlar uygulamanın *şablonlar* klasöründe bulunur. Temel şablon, *layout.html*, en kapsamlı. Gerekli tüm statik dosyaları (JavaScript ve CSS) ifade eder, diğer sayfaların geçersiz kaktEttiği "içerik" adlı bir bloğu tanımlar ve "komut dosyaları" adlı başka bir blok sağlar. *layout.html'den* aşağıdaki açıklamalı alıntılar bu belirli alanları gösterir:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
    {% block scripts %}{% endblock %}

</body>
</html>
```

Tek tek sayfa şablonları, *about.html,* *contact.html*, ve *index.html*, her temel şablon *düzeni.html*genişletmek . *about.html* en basit ve `{% extends %}` `{% block content %}` ve etiketleri gösterir:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* ve *contact.html* aynı yapıyı kullanın ve "içerik" bloğunda daha uzun içerik sağlayın.

## <a name="the-flaskjade-web-project-template"></a>Flask/Jade Web Project şablonu

Bu makalenin başında belirtildiği gibi, Visual Studio görsel olarak "Flask Web Project" tarafından üretilen ne aynı bir uygulama oluşturur bir "Flask / Yeşim Web Projesi" şablonu sağlar. Birincil fark, daha kısa bir dil ile aynı kavramları uygulayan Jinja bir uzantısıdır Yeşim cazip motoru, kullanır. Özellikle, Yeşim etiketleri yerine etiketleri kullanır {% %} sınırlayıcılar, örneğin, ve anahtar kelimeler kullanarak CSS stilleri ve HTML öğeleri başvurmanızı sağlar.

Yeşim'i etkinleştirmek için, proje şablonu önce *requirements.txt'deki*pyjade paketini içerir.

Uygulamanın * \_ \_\_\_init .py* dosyası için bir satır içerir

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

Şablonlar klasöründe *.html* şablonları yerine *.jade* dosyalarını görürsünüz ve *views.py'daki* `flask.render_template` *görünümler* bu dosyalara çağrılarında ''''''ya' göndermeyapar. Aksi takdirde görünümkodu aynıdır.

*.jade* dosyalarından birini açarken, şablonun daha kısa ifadesini görebilirsiniz. Örneğin, "Flask/Jade Web Project" şablonu tarafından oluşturulan *şablonların/layout.jade'in* içeriği aşağıda verilmiştir:

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

Ve burada *şablonlar içeriği / about.jade*, yer `#{ <name>}` sahipleri için kullanımını gösteren:

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Hangibirinin sizin için en uygun olduğunu görmek için hem Jinja hem de Yeşim sözdizimi ile deneme çekinmeyin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Anketler Flask Web Projesi şablonu](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Daha derine inin

- [İlk Flask uygulaması, bölüm 4 yazma - formlar ve genel görünümleri](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [Yeşim GitHib (Dokümantasyon)](https://github.com/liuliqiang/pyjade) (github.com)
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
