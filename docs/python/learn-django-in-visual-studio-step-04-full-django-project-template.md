---
title: Visual Studio adım 4, web proje şablonu Django öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temellerinin bir walkthrough, özellikle Django Web Project şablonu tarafından sağlanan özellikler.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62961712"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>Adım 4: Tam Django Web Projesi şablonu kullanın

**Önceki adım: [Statik dosyalara hizmet edin, sayfa ekleyin ve şablon kalıtımını kullanın](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Visual Studio'daki "Blank Django Web Project" şablonu üzerine bir uygulama oluşturarak Django'nun temellerini keşfettiğinize göre, "Django Web Project" şablonu tarafından üretilen dolgun uygulamayı kolayca anlayabilirsiniz.

Bu adımda şimdi:

> [!div class="checklist"]
> - "Django Web Project" şablonu kullanarak daha dolgun bir Django web uygulaması oluşturun ve proje yapısını inceleyin (adım 4-1)
> - Temel sayfa şablonundan devralan ve jQuery ve Bootstrap (adım 4-2) gibi statik JavaScript kitaplıklarını kullanan üç sayfadan oluşan proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama
> - Şablon tarafından sağlanan URL yönlendirmesini anlama (adım 4-3)

Şablon, Adım 5'te kapsanan temel kimlik doğrulamasını da sağlar.

## <a name="step-4-1-create-a-project-from-the-template"></a>Adım 4-1: Şablondan proje oluşturma

1. Visual Studio'da **Solution Explorer'a**gidin, bu eğitimde daha önce oluşturulan **LearningDjango** çözümüne sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin. (Alternatif olarak, yeni bir çözüm kullanmak istiyorsanız, bunun yerine **Dosya** > **Yeni** > **Projesi'ni** seçin.)

1. Yeni proje iletişim kutusunda, **Django Web Project** şablonunu arayın ve seçin, projeyi "DjangoWeb" olarak arayın ve **Tamam'ı**seçin.

1. Şablon yine bir *requirements.txt* dosyası içerdiğinden, Visual Studio bu bağımlılıkları nereye yükleyebileceğinizi sorar. Seçeneği seçin, **sanal ortama yükle**ve Sanal Ortam **Ekle** iletişim kutusunda varsayılanları kabul etmek için **Oluştur'u** seçin.

1. Visual Studio sanal ortamı ayarlamayı bitirdikten sonra, bir Django süper kullanıcısı (yani bir yönetici) oluşturmak için görüntülenen *readme.html'deki* yönergeleri izleyin. Visual Studio projesine sağ tıklayın ve **Python** > **Django Create Superuser** komutunu seçin, ardından istemleri izleyin. Uygulamanın kimlik doğrulama özelliklerini kullanırken kullanıcı adınızı ve parolanızı kullandığınızda kaydettiğinizden emin olun.

1. **DjangoWeb** **projesini, Solution Explorer'daki** projeyi sağ tıklatarak ve **Başlangıç Projesi olarak Set'i**seçerek Visual Studio çözümü için varsayılan olarak ayarlayın. Kalın olarak gösterilen başlangıç projesi, hata ayıklamayı başlattığınızda çalıştırılan şeydir.

    ![DjangoWeb projesini başlangıç projesi olarak gösteren Çözüm Gezgini](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. **Hata Ayıklama** > **Hata Ayıklama** **(F5)** seçeneğini belirleyin veya sunucuyu çalıştırmak için araç çubuğundaki **Web Sunucusu** düğmesini kullanın:

    ![Visual Studio'da web sunucusu araç çubuğu düğmesini çalıştırın](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulama, gezinme çubuğunu kullanarak arasında gezindiğiniz Ana Sayfa, Hakkında ve İletişim olmak üzere üç sayfadan oluşur. Uygulamanın farklı bölümlerini incelemek için bir veya iki dakika ayırın. **Oturum Açma** komutu aracılığıyla uygulamayla kimlik doğrulaması yapmak için daha önce oluşturulan süper kullanıcı kimlik bilgilerini kullanın.

    ![Django Web Project uygulamasının tam tarayıcı görünümü](media/django/step04-full-app-desktop-view.png)

1. "Django Web Project" şablonu tarafından oluşturulan uygulama, mobil form etkenlerini barındıran duyarlı mizanpaj için Bootstrap'ı kullanır. Bu yanıt verme yeteneğini görmek için tarayıcıyı dar bir görünüme yeniden boyutlandırArak içeriğin dikey olarak işlenmesini ve gezinme çubuğunun menü simgesine dönüşmesini sağlar:

    ![Django Web Project uygulamasının mobil (dar) görünümü](media/django/step04-full-app-mobile-view.png)

1. Takip eden bölümler için uygulamayı çalışır durumda bırakabilirsiniz.

    Uygulamayı durdurmak ve kaynak [denetiminde değişiklikler yapmak](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)istiyorsanız, önce **Team Explorer'da** **Değişiklikler** sayfasını açın , sanal ortam için klasörü sağ tıklatın (muhtemelen **env),** ve **bu yerel öğeleri yoksay'ı**seçin.

### <a name="examine-what-the-template-creates"></a>Şablonun ne oluşturduğunu inceleme

En geniş düzeyde, "Django Web Project" şablonu aşağıdaki yapıyı oluşturur:

- Proje kökündeki dosyalar:
  - *manage.py*, Django idari programı.
  - *db.sqlite3*, varsayılan bir SQLite veritabanı.
  - *requirements.txt* Django 1.x bir bağımlılık içeren.
  - *readme.html*, projeyi oluşturduktan sonra Visual Studio'da görüntülenen bir dosya. Önceki bölümde belirtildiği gibi, uygulama için bir süper kullanıcı (yönetici) hesabı oluşturmak için buradaki yönergeleri izleyin.
- *Uygulama* klasörü görünümler, modeller, testler, formlar, şablonlar ve statik dosyalar dahil olmak üzere tüm uygulama dosyalarını içerir (bkz. adım 4-2). Genellikle daha farklı bir uygulama adı kullanmak için bu klasörü yeniden adnız.
- *DjangoWeb* (Django projesi) klasörü tipik Django proje dosyalarını içerir: * \_ \_\_\_init .py*, *settings.py*, *urls.py*, ve *wsgi.py*. Proje şablonu kullanılarak, *settings.py* zaten uygulama ve veritabanı dosyası için yapılandırılmıştır ve *urls.py* giriş formu da dahil olmak üzere tüm uygulama sayfalarına giden rotalarla zaten yapılandırılmıştır.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Soru: Visual Studio projeleri arasında sanal bir ortamı paylaşmak mümkün mü?

Cevap: Evet, ancak bunu farklı projelerin zaman içinde farklı paketler kullanma olasılığının yüksek olduğu bilinciyle yapın ve bu nedenle paylaşılan bir sanal ortam, onu kullanan tüm projeler için tüm paketleri içermelidir.

Bununla birlikte, varolan bir sanal ortamı kullanmak için aşağıdakileri yapın:

1. Visual Studio bağımlılıkları yüklemek istendiğinde, ben onları kendim seçeneği **yükleyeceğim** seçin.
1. **Çözüm Gezgini'nde** **Python Ortamları** düğümüne sağ tıklayın ve **Varolan Sanal Ortam Ekle'yi**seçin.
1. Sanal ortamı içeren klasöre gidin ve seçin, ardından **Tamam'ı**seçin.

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>Adım 4-2: Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama

Projeyi çalıştırırken gözlemlediğiniz gibi, uygulama üç görünüm içerir: Ev, İletişim ve İletişim. Bu görünümlerin kodu *uygulama/görünümler* klasöründe bulunur. Her görünüm işlevi `django.shortcuts.render` yalnızca bir şablona ve basit bir sözlük nesnesine giden yol ile çağırır. Örneğin, Hakkında sayfası `about` işlev tarafından işlenir:

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

Şablonlar uygulamanın *şablonları/uygulama* klasöründe bulunur (ve genellikle *uygulamayı* gerçek uygulamanızın adıyla yeniden adlandırmak istersiniz). Temel şablon, *layout.html*, en kapsamlı. Gerekli tüm statik dosyaları (JavaScript ve CSS) ifade eder, diğer sayfaların geçersiz kaktEttiği "içerik" adlı bir bloğu tanımlar ve "komut dosyaları" adlı başka bir blok sağlar. *layout.html'den* aşağıdaki açıklamalı alıntılar bu belirli alanları gösterir:

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

*Şablonlar / uygulama* klasöründe de dördüncü sayfa *login.html*, *loginpartial.html* ile birlikte `{% include %}`bu *layout.html* kullanarak getirdi . Bu şablon dosyaları kimlik doğrulama adım 5'te açıklanır.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Soru: Django sayfa şablonuna {% blok %} ve {% endblock %} girinti olabilir mi?

Cevap: Evet, Django sayfa şablonları, belki de uygun ana öğeleri içinde hizalamak için, girintisi etiketleri girintisi iyi çalışır. Visual Studio proje şablonu tarafından oluşturulan sayfa şablonlarında girintisi değildir, böylece nereye yerleştirildiklerini net bir şekilde görebilirsiniz.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>Adım 4-3: Şablon tarafından oluşturulan URL yönlendirmesini anlama

"Django Web Project" şablonu tarafından oluşturulan Django projesinin *urls.py* dosyası aşağıdaki kodu içerir:

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

İlk üç URL deseni, `home` `contact`uygulamanın `about` *views.py* dosyasındaki ve görünümlerle doğrudan eşlenir. Desenler `^login/$` ve `^logout$`, diğer taraftan, uygulama tanımlı görünümler yerine yerleşik Django görünümleri kullanın. `url` Yönteme yapılan çağrılar, görünümü özelleştirmek için ek veriler de içerir. Adım 5 bu aramaları araştırıyor.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Soru: Oluşturduğum projede, "hakkında" URL deseni neden burada gösterildiği gibi '^about$' yerine '^about' kullanıyor?

Cevap: Normal ifadede sondaki '$' eksikliği, proje şablonunun birçok sürümünde basit bir gözetimdi. URL deseni "hakkında" adlı bir sayfa için mükemmel derecede iyi çalışır, ancak '$' adlı URL deseni "about=django", "about09876", "aboutoflaughter" gibi URL'lerle de eşleşir. İzleyen '$' burada yalnızca "hakkında" eşleşen *only* bir URL deseni oluşturmak için gösterilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Django'daki kullanıcıları kimlik doğrulaması](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Daha derine inin

- [Web uygulamasını Azure Uygulama Hizmetine dağıtma](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [İlk Django uygulaması, bölüm 4 yazma - formlar ve genel görünümleri](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
