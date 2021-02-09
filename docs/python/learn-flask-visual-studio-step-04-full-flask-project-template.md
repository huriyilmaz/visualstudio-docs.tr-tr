---
title: Visual Studio adım 4, Web projesi şablonlarındaki Flask öğreticisi hakkında bilgi edinin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Flask temel bilgileri, özellikle Flask Web projesi ve Flask/Jade Web projesi şablonları tarafından sunulan özellikler.
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ef9154a34ddd08e7e0a4b9434f7f748b2603aef4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882875"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>4. Adım: tam Flask Web projesi şablonunu kullanma

**Önceki adım: [statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

Artık Visual Studio 'daki "boş Flask uygulama projesi" şablonuyla bir uygulama oluşturarak Flask 'nin temel bilgilerini incelediğinize göre, "Flask Web projesi" şablonu tarafından üretilen Fuller uygulamasını kolayca anlayabilirsiniz.

Bu adımda Şu anda şunları yapabilirsiniz:

> [!div class="checklist"]
> - "Flask Web projesi" şablonunu kullanarak Fuller Flask Web uygulaması oluşturma ve proje yapısını İnceleme (adım 4-1)
> - Temel sayfa şablonundan alınan ve jQuery ve Bootstrap gibi statik JavaScript kitaplıklarını kullanan üç sayfadan oluşan, proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın (adım 4-2)
> - Şablon tarafından sunulan URL yönlendirmesini anlayın (adım 4-3)

Bu makale ayrıca, Jınja yerine Jade şablon oluşturma altyapısı kullanılarak "Flask Web projesi" ile özdeş bir uygulama üreten "Flask/Jade Web projesi" şablonuna de uygulanır. Bu makalenin sonunda ek ayrıntılar eklenmiştir.

## <a name="step-4-1-create-a-project-from-the-template"></a>Adım 4-1: Şablondan proje oluşturma

1. Visual Studio 'da **Çözüm Gezgini** gidin, bu öğreticide daha önce oluşturulan **learningflask** çözümüne sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin. (Alternatif olarak, yeni bir çözüm kullanmak isterseniz **Dosya**  >  ' yı seçin. **Yeni**  >  Bunun yerine **Proje** .)

1. Yeni proje iletişim kutusunda **Flask Web projesi** şablonunu arayıp seçin, "flaskweb" projesini çağırın ve **Tamam**' ı seçin.

1. Şablon bir *requirements.txt* dosyası Içerdiğinden, Visual Studio bu bağımlılıkların nereye yükleneceğini sorar. **Bir sanal ortama yükleyip**, sanal **ortam ekle** iletişim kutusunda Varsayılanları kabul etmek için **Oluştur** seçeneğini belirleyin.

1. Visual Studio sanal ortamı ayarlamayı tamamladıktan sonra, **Çözüm Gezgini** ' de projeye sağ tıklayıp **Başlangıç projesi olarak ayarla**' yı seçerek **flaskweb** projesini Visual Studio çözümü için varsayılan olacak şekilde ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklayıcıyı başlattığınızda çalıştırılan şeydir.

    ![FlaskWeb projesini başlangıç projesi olarak gösteren Çözüm Gezgini](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. Sunucuyu çalıştırmak için **hata ayıklama**  >  **başlatma hata ayıklamayı Başlat** (**F5**) veya araç çubuğundaki **Web sunucusu** düğmesini seçin:

    ![Visual Studio 'da Web sunucusu araç çubuğu düğmesini Çalıştır](media/flask/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulamada, gezinti çubuğunu kullanma arasında gezinerek üç sayfa, giriş, bilgi ve Ilgili kişi bulunur. Uygulamanın farklı kısımlarını incelemek için bir dakika veya iki dakikanızı alın. Uygulamada **oturum açma** komutu aracılığıyla kimlik doğrulaması yapmak için, daha önce oluşturulan Süper Kullanıcı kimlik bilgilerini kullanın.

    ![Flask Web projesi uygulamasının tam tarayıcı görünümü](media/flask/step04-full-app-desktop-view.png)

1. "Flask Web projesi" şablonu tarafından oluşturulan uygulama, mobil form faktörlerine uyum sağlayan, yanıt veren düzen için önyükleme kullanır. Bu yanıt hızını görmek için, içeriğin dikey olarak oluşturmaları ve gezinti çubuğunun bir menü simgesine dönüşmemesi için tarayıcıyı dar bir görünüme yeniden boyutlandırın:

    ![Flask Web projesi uygulamasının mobil (dar) görünümü](media/flask/step04-full-app-mobile-view.png)

1. Uygulamanın, izleyen bölümler için çalışır durumda kalmasını sağlayabilirsiniz.

    Uygulamayı durdurmak ve [kaynak denetimine değişiklikleri uygulamak](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)istiyorsanız, önce **Takım Gezgini** içindeki **değişiklikler** sayfasını açın, sanal ortam (Belki de **env**) klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

### <a name="examine-what-the-template-creates"></a>Şablonun ne oluşturduğunu inceleyin

"Flask Web projesi" şablonu aşağıda yapıyı oluşturur. İçerik, önceki adımlarda oluşturduğunuz şeydir çok benzerdir. Fark, "Flask Web projesi" şablonunun *statik* klasörde daha fazla yapı içereceğinden, yanıt veren tasarıma yönelik jQuery ve Bootstrap içerdiğinden emin olur. Şablon ayrıca bir Iletişim sayfası ekler. Genel olarak, bu öğreticide önceki adımları izlediyseniz, şablondan her şey tanıdık gelmelidir.

- Proje kökündeki dosyalar:
  - *runserver.py*, uygulamayı bir geliştirme sunucusunda çalıştırmak için bir komut dosyası.
  - Flask 0. x üzerinde bir bağımlılık içeren *requirements.txt* .
- *Flaskweb* klasörü tüm uygulama dosyalarını içerir:
  - init.py, uygulama kodunu Python modülü olarak işaretler, Flask nesnesini oluşturur ve uygulamanın görünümlerini içeri aktarır. *\_ \_ \_ \_*
  - *views.py* sayfaların işlenmesi için kodu içerir.
  - *Statik* klasör *içerik* (CSS dosyaları), *yazı tipleri* (yazı tipi dosyaları) ve *betikler* (JavaScript dosyaları) adlı alt klasörleri içerir.
  - *Şablonlar* klasörü, her biri *layout.html*'yi genişleten belirli sayfalar *içinabout.html*, *contact.html* ve *index.html* ile birlikte *layout.html* temel şablonu içerir.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Soru: Visual Studio projeleri arasında sanal bir ortam paylaşmak mümkün mü?

Cevap: Evet, ancak farklı projelerin zaman içindeki farklı paketleri büyük olasılıkla kullandığı bir tanıma sahip olur ve bu nedenle paylaşılan bir sanal ortam, kendisini kullanan tüm projelere yönelik tüm paketleri içermelidir.

Bununla birlikte, mevcut bir sanal ortamı kullanmak için şunları yapın:

1. Visual Studio 'da bağımlılıkları yüklemek isteyip istemediğiniz sorulduğunda **kendim yükleyeceğim** seçeneğini belirleyin.
1. **Çözüm Gezgini**, **Python ortamları** düğümüne sağ tıklayın ve **var olan sanal ortamı Ekle**' yi seçin.
1. Adresine gidin ve sanal ortamı içeren klasörü seçip **Tamam**' ı seçin.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Adım 4-2: proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın

Projeyi çalıştırdığınızda gözlemleyeceksiniz, uygulama üç görünüm içerir: Home, hakkında ve Ilgili kişi. Bu görünümlerin kodu *Flaskweb/views. Kopyala* içinde bulunur. Her görünüm işlevi, şablona `flask.render_template` verilecek değerler için bir şablonun yolunu ve bağımsız değişken bir bağımsız değişken listesini çağırır. Örneğin, hakkında sayfası işlevi tarafından işlenir `about` (dekoratör, URL yönlendirme sağlar):

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

`home`Ve `contact` işlevleri, benzer dekoratlarla ve biraz farklı bağımsız değişkenlerle neredeyse aynıdır.

Şablonlar, uygulamanın *Şablonlar* klasöründe bulunur. Temel şablon *layout.html*, en kapsamlıdır. Tüm gerekli statik dosyalara (JavaScript ve CSS) başvurur, diğer sayfaların geçersiz kılındığı "içerik" adlı bir blok tanımlar ve "betikler" adlı başka bir blok sağlar. *layout.html* 'den aşağıdaki ek açıklamalı alıntıları 'ler şu özel alanlara sahip:

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

Tek tek sayfa şablonları, *about.html*, *contact.html* ve *index.html*, her biri temel şablonu *layout.html*'yi genişletir. *about.html* en basit olanıdır ve etiketlerini gösterir `{% extends %}` `{% block content %}` :

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* ve *contact.html* aynı yapıyı kullanır ve "içerik" bloğunda tablodan içerik sağlar.

## <a name="the-flaskjade-web-project-template"></a>Flask/Jade Web projesi şablonu

Bu makalenin başlangıcında belirtildiği gibi, Visual Studio "Flask/Jade Web projesi" şablonunu sağlar ve bu, "Flask Web projesi" tarafından üretildiklerle aynı şekilde görsel olarak özdeş bir uygulama oluşturur. Birincil fark, daha kısa bir dille aynı kavramları uygulayan Jınja uzantısı olan Jade şablon oluşturma altyapısını kullanmamanızdır. Özellikle, Jade, örneğin {%%} sınırlayıcılarının içine alınmış Etiketler yerine anahtar sözcükleri kullanır ve anahtar sözcükleri kullanarak CSS stillerine ve HTML öğelerine başvurmanıza imkan tanır.

Jade 'yi etkinleştirmek için, proje şablonu ilk olarak *requirements.txt* pyjade paketini içerir.

Uygulamanın *\_ \_ init \_ \_ . Kopyala* dosyası bir satır içerir

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

*Şablonlar* klasöründe,. *HTML* şablonları yerine *. jade* dosyalarını görürsünüz ve *views.py* 'deki görünümler, çağrılarında bu dosyalara başvurur `flask.render_template` . Aksi takdirde, görünümler kodu aynıdır.

*. Jade* dosyalarından birini açarak, bir şablonun daha fazla kısa ifadesini görebilirsiniz. Örneğin, "Flask/Jade Web projesi" şablonu tarafından oluşturulan *Şablonlar/Layout. Jade* içerikleri aşağıda verilmiştir:

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

Burada, yer tutucular için kullanımını gösteren *şablonların/about. Jade*'nin içeriği verilmiştir `#{ <name>}` :

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

Hem Jinja hem de Jade sözdizimleri ile denemeler yapıp sizin için en uygun olanı görebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Flask Web projesi şablonunu yokladığı](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)

## <a name="go-deeper"></a>Daha derin git

- [Ilk Flask uygulamanızı yazma, Bölüm 4-formlar ve genel görünümler](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- [GitHub üzerinde Jade (belgeler)](https://github.com/liuliqiang/pyjade) (GitHub.com)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-Flask](https://github.com/Microsoft/python-sample-vs-learning-flask)
