---
title: 4. adım, web Visual Studio şablonunda Django öğreticisini öğrenin
titleSuffix: ''
description: Özellikle Django Web uygulaması şablonu tarafından sağlanan özellikler Visual Studio Django temel bilgileri Project izlenecek yol.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b95f4dec53abb1e4a02790b2434f6b8577115ec2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038532"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>4. Adım: Tam Django Web Project kullanın

**Önceki adım: [Statik dosyaları hizmet etme, sayfa ekleme ve şablon devralma kullanma](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

Visual Studio'da "Boş Django Web Project" şablonu üzerine bir uygulama kullanarak Django'nun temellerini inceleyene göre, "Django Web Project" şablonu tarafından üretilen daha dolu uygulamayı kolayca anlayabilirsiniz.

Bu adımda şimdi:

> [!div class="checklist"]
> - "Django Web uygulaması" şablonunu kullanarak daha eksiksiz bir Django web uygulaması Project proje yapısını inceleme (4-1. adım)
> - Bir temel sayfa şablonundan devralınan ve jQuery ve Bootstrap gibi statik JavaScript kitaplıklarını (4-2. adım) alan üç sayfadan oluşan proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama
> - Şablon tarafından sağlanan URL yönlendirmesini anlama (4-3. adım)

Şablon ayrıca 5. Adım'da ele alan temel kimlik doğrulamasını da sağlar.

## <a name="step-4-1-create-a-project-from-the-template"></a>4.-1. Adım: Şablondan proje oluşturma

1. Bu Visual Studio' **Çözüm Gezgini** gidin, bu öğreticide daha önce oluşturulan **LearningDjango** çözümüne sağ tıklayın ve Yeni Ekle'yi  >  **Project.** (Alternatif olarak, yeni bir çözüm kullanmak için Dosya'yi **seçin**  >  **Yeni**  >  **Project.)**

1. Yeni proje iletişim kutusunda **Django Web** uygulaması şablonunu arayın Project seçin, projeyi "DjangoWeb" olarak arayın ve Tamam'ı **seçin.**

1. Şablon yeniden bir dosya *requirements.txt,* Visual Studio bu bağımlılıkların nereye yüklen bir sorulup yüklenmey olduğunu sorar. Sanal ortama yükle **seçeneğini belirleyin ve Sanal Ortam** Ekle iletişim kutusunda **Oluştur'a** **seçerek** varsayılanları kabul edersiniz.

1. Sanal Visual Studio ayarlamayı tamamlarsanız, bir Django süper kullanıcısı (yani bir *yönetici)* oluşturmak için görüntülenenreadme.html'de verilen yönergeleri izleyin. Visual Studio projesine sağ tıklayın ve Python   >  **Django Create Superuser** komutunu seçin ve yönergeleri izleyin. Uygulamanın kimlik doğrulama özelliklerini yaparken kullanıcı adınızı ve parolanızı kaydetmeyi unutmayın.

1. **DjangoWeb** projesini Visual Studio'de bu projeye sağ tıklar ve Başlangıç  olarak ayarla'Çözüm Gezgini seçeneğini **Project.** Kalın yazıyla gösterilen başlangıç projesi, hata ayıklayıcıyı başlatan projedir.

    ![Çözüm Gezgini proje olarak DjangoWeb projesini gösteren web sitesi](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. Hata **AyıklamaYı** Başlat Hata Ayıklama ( F5 ) öğesini seçin veya sunucuyu çalıştırmak  >   için araç **çubuğundaki Web** Sunucusu düğmesini kullanın:

    ![Web sunucusu araç çubuğu düğmesini Visual Studio](media/django/run-web-server-toolbar-button.png)

1. Şablon tarafından oluşturulan uygulamada gezinti çubuğunu kullanarak gezinen Giriş, Hakkında ve Kişi olmak için üç sayfa vardır. Uygulamanın farklı bölümlerini incelemek için bir veya iki dakika zaman alır. Oturum aç komutuyla uygulamayla **kimlik doğrulaması yapmak** için daha önce oluşturulan süper kullanıcı kimlik bilgilerini kullanın.

    ![Django Web Uygulaması'nın tam Project görünümü](media/django/step04-full-app-desktop-view.png)

1. "Django Web uygulaması" şablonu Project, mobil form faktörlerine uyum sağlayacak hızlı yanıt veren düzen için Bootstrap kullanır. Bu yanıt verme hızını görmek için tarayıcıyı dar bir görünüme yeniden boyutlandırarak içerik dikey olarak işlenir ve gezinti çubuğu bir menü simgesine döner:

    ![Django Web uygulaması mobil (dar) Project görünümü](media/django/step04-full-app-mobile-view.png)

1. Aşağıdaki bölümler için uygulamayı çalışıyor bırakın.

    Uygulamayı durdurmak ve değişiklikleri [](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)kaynak denetimine işlemek için,  önce **Takım Gezgini'de** Değişiklikler sayfasını açın, sanal ortamın klasörüne sağ tıklayın (büyük olasılıkla **env)** ve Bu yerel öğeleri yoksay'ı **seçin.**

### <a name="examine-what-the-template-creates"></a>Şablonun oluşturduğu şeyi inceleme

En geniş düzeyde "Django Web Project" şablonu aşağıdaki yapıyı oluşturur:

- Proje kökünde dosyalar:
  - *manage.py,* Django yönetim yardımcı programı.
  - *db.sqlite3*, varsayılan bir SQLite veritabanıdır.
  - *requirements.txt* Django 1.x bağımlılığı içeren bir dosya.
  - *readme.htmoluşturdukta* görüntülenen l Visual Studio dosyası. Önceki bölümde not edinilen gibi, uygulama için bir süper kullanıcı (yönetici) hesabı oluşturmak için buradaki yönergeleri izleyin.
- Uygulama *klasörü* görünümler, modeller, testler, formlar, şablonlar ve statik dosyalar dahil olmak üzere tüm uygulama dosyalarını içerir (bkz. 4-2. adım). Normalde bu klasörü daha belirgin bir uygulama adı kullanmak için yeniden adlandırabilirsiniz.
- *DjangoWeb* (Django projesi) klasörü tipik Django proje dosyalarını içerir: *\_ \_ init \_ \_ .py*, *settings.py*, *urls.py*, ve *wsgi.py.* Proje şablonunu kullanarak *settings.py* ve veritabanı dosyası için zaten yapılandırılmıştır *ve urls.py* oturum açma formu da dahil olmak üzere tüm uygulama sayfalarına giden yollarla yapılandırılmıştır.

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>Soru: Sanal ortamı farklı projelerde paylaşmak mümkün Visual Studio?

Cevap: Evet, ancak farklı projelerin zaman içinde büyük olasılıkla farklı paketler kullanıyor olduğunu ve bu nedenle paylaşılan bir sanal ortamın bunu kullanan tüm projelerin tüm paketlerini içermesi gerektiğini farkındalığıyla bunu yap.

Bununla birlikte, mevcut bir sanal ortamı kullanmak için şunları yapın:

1. Bağımlılıkları Visual Studio yüklemeniz istendiğinde, Bunları **ben yükleyeceğim seçeneğini** belirleyin.
1. Uygulama **Çözüm Gezgini** Python Ortamları düğümüne sağ **tıklayın ve** Var Olan Sanal Ortamı **Ekle'yi seçin.**
1. sanal ortamı içeren klasöre gidin ve bu klasörü seçin ve tamam'ı **seçin.**

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>4.-2. Adım: Proje şablonu tarafından oluşturulan görünümleri ve sayfa şablonlarını anlama

Projeyi ne zaman çalıştırsanız uygulamanın üç görünüm içerdiğini gözlemlersiniz: Giriş, Hakkında ve kişi. Bu görünümlerin kodu *app/views klasöründe* bulunur. Her görünüm işlevi, `django.shortcuts.render` bir şablonun ve basit bir sözlük nesnesinin yolunu kullanarak çağrılar. Örneğin About sayfası işlevi tarafından `about` işleyebilirsiniz:

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

Şablonlar, uygulamanın *templates/app* klasöründe bulunur (ve genellikle uygulamayı  gerçek uygulamanın adıyla yeniden adlandırmak istersiniz). layout.htm *l* olan temel şablon, en kapsamlı şablondur. Tüm gerekli statik dosyaları (JavaScript ve CSS) ifade eder, diğer sayfaların geçersiz kılmasında "content" adlı bir blok tanımlar ve "scripts" adlı başka bir blok sağlar. Aşağıdaki açıklamalı alıntılarlayout.htm *alanları* gösterir:

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

Her biri l , *about.html*, *contact.html* veindex.htm *l* olan tek tek sayfa şablonları, temel şablonu l *layout.htmgenişleter.* *about.html* en basitidir ve ile `{% extends %}` etiketlerini `{% block content %}` gösterir:

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* ve *contact.htmaynı* yapıyı kullanır ve "içerik" bloğunda daha uzun içerik sağlar.

*Templates/app klasöründe,* kullanaraklogin.htm *l'ye* getirilenloginpartial.htm *l* ile birlikte dördüncü bir *layout.htmsayfasıdır.* `{% include %}` Bu şablon dosyaları, kimlik doğrulamasıyla ilgili 5. adımda ele alınmıştır.

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>Soru: Django sayfa şablonunda {% block %} ve {% endblock %} girintili olabilir mi?

Cevap: Evet, blok etiketlerini girintilerken Django sayfa şablonları düzgün çalışır, belki de bunları uygun üst öğeleriyle hizalarsınız. Bu şablonlar, Visual Studio proje şablonu tarafından oluşturulan sayfa şablonlarında girintilemez, böylece yerleştiriltikleri yeri net bir şekilde görebilirsiniz.

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>4.-3. Adım: Şablon tarafından oluşturulan URL yönlendirmesini anlama

"Django Web *urls.py"* şablonu tarafından oluşturulan Django projesinin Project dosyası aşağıdaki kodu içerir:

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

İlk üç URL deseni, doğrudan uygulamanın dosya `home` `contact` dosyasındaki , `about` ve *görünümlerine views.py* eşler. Diğer taraftan desenleri ve , uygulama tanımlı görünümler yerine yerleşik `^login/$` `^logout$` Django görünümlerini kullanır. yöntemine yapılan `url` çağrılar görünümü özelleştirmek için ek veriler de içerir. 5. adım bu çağrıları inceler.

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>Soru: Oluşturduğum projede "about" URL düzeni neden burada gösterildiği gibi '^about$' yerine '^about' kullanıyor?

Cevap: Normal ifadede sonda '$' ifadesinin olmaması, proje şablonunun birçok farklı sürümü için basit bir gözetimdi. URL düzeni "about" adlı bir sayfa için mükemmel çalışır, ancak sonda '$' olmadan URL düzeni "about=django", "about09876", "aboutoflaughter" gibi URL'lerle de eş görünür. Sonda '$', yalnızca "hakkında" ile eşleşen bir URL deseni oluşturmak *için* burada gösterilir.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Django'da kullanıcıların kimliğini doğrulama](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>Daha derine gitme

- [Web uygulamasını Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [İlk Django uygulamanızı yazma, bölüm 4 - formlar ve genel görünümler](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) (docs.djangoproject.com)
- GitHub öğreticisi: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
