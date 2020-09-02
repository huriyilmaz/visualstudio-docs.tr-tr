---
title: Visual Studio adım 4, Web proje şablonunda Docgo öğreticisini öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında, özellikle de Docgo Web projesi şablonu tarafından sunulan özellikler hakkında Docgo 'ya yönelik bir anlatım.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c778d830b20797962306700a5af938eb3a3bb142
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62961712"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>4. Adım: tam Docgo Web proje şablonunu kullanma

**Önceki adım: [statik dosyaları sunma, sayfa ekleme ve şablon devralmayı kullanma](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Visual Studio 'daki "boş Docgo Web projesi" şablonu üzerinde bir uygulama oluşturarak Socgo 'un temel bilgilerini incelediğinize göre, "Docgo Web projesi" şablonu tarafından üretilen Fuller uygulamasını kolayca anlayabilirsiniz.

Bu adımda Şu anda şunları yapabilirsiniz:

> [!div class="checklist"]
> - "Docgo Web projesi" şablonunu kullanarak bir Fuller Docgo Web uygulaması oluşturun ve proje yapısını inceleyin (adım 4-1)
> - Temel sayfa şablonundan alınan ve jQuery ve Bootstrap gibi statik JavaScript kitaplıklarını kullanan üç sayfadan oluşan, proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın (adım 4-2)
> - Şablon tarafından sunulan URL yönlendirmesini anlayın (adım 4-3)

Şablon Ayrıca, 5. adımda bahsedilen temel kimlik doğrulaması sağlar.

## <a name="step-4-1-create-a-project-from-the-template"></a>Adım 4-1: Şablondan proje oluşturma

1. Visual Studio 'da **Çözüm Gezgini**gidin, bu öğreticide daha önce oluşturulan **learningdocgo** çözümüne sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin. (Alternatif olarak, yeni bir çözüm kullanmak isterseniz **Dosya**  >  ' yı seçin. **Yeni**  >  Bunun yerine **Proje** .)

1. Yeni proje iletişim kutusunda **Docgo Web projesi** şablonunu arayıp seçin, "Docgoweb" projesini çağırın ve **Tamam**' ı seçin.

1. Şablon bir *requirements.txt* dosyası Içerdiğinden, Visual Studio bu bağımlılıkların nereye yükleneceğini sorar. **Bir sanal ortama yükleyip**, sanal **ortam ekle** iletişim kutusunda Varsayılanları kabul etmek için **Oluştur** seçeneğini belirleyin.

1. Visual Studio sanal ortamı ayarlamayı tamamladıktan sonra, bir Docgo süper kullanıcısı (diğer bir deyişle, bir yönetici) oluşturmak için görüntülenen *readme.html* 'teki yönergeleri izleyin. Visual Studio projesine sağ tıklayıp **Python**  >  **docgo süper kullanıcı oluştur** komutunu seçip istemleri takip edin. Uygulamanın kimlik doğrulama özelliklerini kullanırken kullandığınız kullanıcı adını ve parolayı kaydettiğinizden emin olun.

1. **Docgoweb** projesini, **Çözüm Gezgini** ' de projeye sağ tıklayıp **Başlangıç projesi olarak ayarla**' yı seçerek Visual Studio çözümü için varsayılan olacak şekilde ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklayıcıyı başlattığınızda çalıştırılan şeydir.

    ![Docgoweb projesini başlangıç projesi olarak gösteren Çözüm Gezgini](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Sunucuyu çalıştırmak için **hata ayıklama**  >  **başlatma hata ayıklamayı Başlat** (**F5**) veya araç çubuğundaki **Web sunucusu** düğmesini seçin:

    ![Visual Studio 'da Web sunucusu araç çubuğu düğmesini Çalıştır](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulamada, gezinti çubuğunu kullanma arasında gezinerek üç sayfa, giriş, bilgi ve Ilgili kişi bulunur. Uygulamanın farklı kısımlarını incelemek için bir dakika veya iki dakikanızı alın. Uygulamada **oturum açma** komutu aracılığıyla kimlik doğrulaması yapmak için, daha önce oluşturulan Süper Kullanıcı kimlik bilgilerini kullanın.

    ![Docgo Web projesi uygulamasının tam tarayıcı görünümü](media/django/step04-full-app-desktop-view.png)

1. "Docgo Web projesi" şablonu tarafından oluşturulan uygulama, mobil form faktörlerine uyum sağlayan, yanıt veren düzen için önyükleme kullanır. Bu yanıt hızını görmek için, içeriğin dikey olarak oluşturmaları ve gezinti çubuğunun bir menü simgesine dönüşmemesi için tarayıcıyı dar bir görünüme yeniden boyutlandırın:

    ![Docgo Web projesi uygulamasının mobil (dar) görünümü](media/django/step04-full-app-mobile-view.png)

1. Uygulamanın, izleyen bölümler için çalışır durumda kalmasını sağlayabilirsiniz.

    Uygulamayı durdurmak ve [kaynak denetimine değişiklikleri uygulamak](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)istiyorsanız, önce **Takım Gezgini**içindeki **değişiklikler** sayfasını açın, sanal ortam (Belki de **env**) klasörüne sağ tıklayın ve **Bu yerel öğeleri yoksay**' ı seçin.

### <a name="examine-what-the-template-creates"></a>Şablonun ne oluşturduğunu inceleyin

En geniş düzeyde, "Docgo Web projesi" şablonu aşağıdaki yapıyı oluşturur:

- Proje kökündeki dosyalar:
  - *Manage.py*, Docgo yönetim yardımcı programı.
  - Varsayılan bir SQLite veritabanı olan *DB. SQLite3*.
  - Docgo 1. x üzerinde bir bağımlılık içeren *requirements.txt* .
  - Projeyi oluşturduktan sonra Visual Studio 'da görüntülenen bir dosya olan *readme.html*. Önceki bölümde belirtildiği gibi, uygulama için bir süper kullanıcı (yönetici) hesabı oluşturmak için buradaki yönergeleri izleyin.
- *Uygulama* klasörü, görünümler, modeller, testler, formlar, şablonlar ve statik dosyalar dahil olmak üzere tüm uygulama dosyalarını içerir (bkz. Adım 4-2). Bu klasörü genellikle daha farklı bir uygulama adı kullanacak şekilde yeniden adlandırmanız gerekir.
- *Docgoweb* (docgo Projesi) klasörü, tipik docgo proje dosyalarını içerir: * \_ \_ init \_ \_ . Kopyala*, *Settings.py*, *URLs.py*ve *wsgi.py*. Proje şablonunu kullanarak, *Settings.py* zaten uygulama ve veritabanı dosyası için yapılandırılmıştır ve *URLs.py* , oturum açma formu dahil olmak üzere tüm uygulama sayfalarına yönelik yollarla zaten yapılandırılmıştır.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Soru: Visual Studio projeleri arasında sanal bir ortam paylaşmak mümkün mü?

Cevap: Evet, ancak farklı projelerin zaman içindeki farklı paketleri büyük olasılıkla kullandığı bir tanıma sahip olur ve bu nedenle paylaşılan bir sanal ortam, kendisini kullanan tüm projelere yönelik tüm paketleri içermelidir.

Bununla birlikte, mevcut bir sanal ortamı kullanmak için şunları yapın:

1. Visual Studio 'da bağımlılıkları yüklemek isteyip istemediğiniz sorulduğunda **kendim yükleyeceğim** seçeneğini belirleyin.
1. **Çözüm Gezgini**, **Python ortamları** düğümüne sağ tıklayın ve **var olan sanal ortamı Ekle**' yi seçin.
1. Adresine gidin ve sanal ortamı içeren klasörü seçip **Tamam**' ı seçin.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Adım 4-2: proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlayın

Projeyi çalıştırdığınızda gözlemleyeceksiniz, uygulama üç görünüm içerir: Home, hakkında ve Ilgili kişi. Bu görünümlerin kodu *App/views* klasöründe bulunur. Her görünüm işlevi `django.shortcuts.render` , bir şablon yolunu ve basit bir sözlük nesnesini çağırır. Örneğin, hakkında sayfası işlevi tarafından işlenir `about` :

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

Şablonlar uygulamanın *Şablonlar/uygulama* klasöründe bulunur (ve genellikle *uygulamayı* gerçek uygulamanızın adıyla yeniden adlandırmak istersiniz). Temel şablon *layout.html*, en kapsamlıdır. Tüm gerekli statik dosyalara (JavaScript ve CSS) başvurur, diğer sayfaların geçersiz kılındığı "içerik" adlı bir blok tanımlar ve "betikler" adlı başka bir blok sağlar. *layout.html* 'den aşağıdaki ek açıklamalı alıntıları 'ler şu özel alanlara sahip:

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

Tek tek sayfa şablonları, *about.html*, *contact.html*ve *index.html*, her biri temel şablonu *layout.html*'yi genişletir. *about.html* en basit olanıdır ve etiketlerini gösterir `{% extends %}` `{% block content %}` :

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* ve *contact.html* aynı yapıyı kullanır ve "içerik" bloğunda tablodan içerik sağlar.

*Şablonlar/App* klasöründe ayrıca, *layout.html* 'ye getirilen *loginpartial.html* ile birlikte *login.html*adlı dördüncü bir sayfa `{% include %}` . Bu şablon dosyaları, kimlik doğrulamasında 5. adımda ele alınmıştır.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Soru: {% Block%} ve {% endblock%}, Docgo sayfa şablonunda girintilenebilir mi?

Cevap: Evet, Docgo sayfa şablonları, blok etiketlerini girintilediğinizde ince çalışır, belki bunları uygun üst öğelerinde hizalayabilirsiniz. Bunlar, nereye yerleştirileceğini açıkça görebilmeniz için Visual Studio proje şablonu tarafından oluşturulan sayfa şablonlarında girintilenmez.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Adım 4-3: şablon tarafından oluşturulan URL yönlendirmesini anlama

"Docgo Web projesi" şablonu tarafından oluşturulan Docgo projesinin *URLs.py* dosyası aşağıdaki kodu içerir:

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

İlk üç URL deseni `home` , `contact` `about` uygulamanın *views.py* dosyasındaki, ve görünümleriyle doğrudan eşlenir. Desenler `^login/$` ve `^logout$` diğer yandan, uygulama tanımlı görünümler yerine yerleşik Docgo görünümlerini kullanın. Yöntemine yapılan çağrılar, `url` görünümü özelleştirmek için ek veriler de içerir. 5. adım bu çağrıları araştırır.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Soru: oluşturduğum projede neden "About" URL deseninin, burada gösterildiği gibi ' ^ about $ ' yerine ' ^ about ' kullanması gerekir mi?

Cevap: normal ifadede sondaki ' $ ' öğesinin olmaması, proje şablonunun birçok sürümünde basit bir bakış taşımıştı. URL deseninin "About" adlı bir sayfada kusursuz bir şekilde çalışması, ancak sondaki ' $ ' olmadan URL deseninin de "about = docgo", "about09876", "aboutoflaughter" vb. gibi URL 'Leri de eşleşmesi. ' $ ' Sonunda *yalnızca* "About" ile eşleşen bir URL deseninin oluşturulması gösterilmektedir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Docgo 'da kullanıcıların kimliğini doğrulama](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Daha derin git

- [Web uygulamasını Azure App Service dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [Ilk Docgo uygulamanızı yazma, 4. Bölüm-Forms ve genel görünümler](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
