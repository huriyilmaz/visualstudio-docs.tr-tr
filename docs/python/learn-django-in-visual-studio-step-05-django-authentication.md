---
title: Visual Studio, 5. adım, kimlik doğrulamasında Django öğreticisi hakkında bilgi edinin
titleSuffix: ''
description: Django web uygulaması şablonları tarafından sağlanan Visual Studio özellikle kimlik doğrulama özellikleri bağlamında Django temel Project izlenecek yol.
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
ms.openlocfilehash: 17a6ee7cbf622eb90debd961ba36f159bf7fbc6c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625388"
---
# <a name="step-5-authenticate-users-in-django"></a>5. Adım: Django'da kullanıcıların kimliğini doğrulama

**Önceki adım: [Tam Django Web Project kullanın](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

::: moniker range="vs-2017"
Kimlik doğrulaması web uygulamaları için yaygın bir ihtiyaç olduğundan, "Django Web Project" şablonu temel bir kimlik doğrulama akışı içerir. (Bu öğreticinin 6. adımlarında ele alınan "Django Web Project Yoklamaları" şablonu da aynı akışı içerir.) Django proje şablonlarını kullanırken, Visual Studio Django projesinin projesinde kimlik doğrulaması için gerekli tüm modülleri *settings.py.*
::: moniker-end

::: moniker range=">=vs-2019"
Kimlik doğrulaması web uygulamaları için yaygın bir ihtiyaç olduğundan, "Django Web Project" şablonu temel bir kimlik doğrulama akışı içerir. Django proje şablonlarının herhangi birini kullanırken, Visual Studio Django projesinin projesinde kimlik doğrulaması için gerekli tüm modülleri *settings.py.*
::: moniker-end

Bu adımda şunları öğreniriz:

> [!div class="checklist"]
> - Visual Studio şablonlarında sağlanan kimlik doğrulama akışını kullanma (5-1. adım)

## <a name="step-5-1-use-the-authentication-flow"></a>5-1. Adım: Kimlik doğrulama akışını kullanma

Aşağıdaki adımlarda kimlik doğrulama akışı alıştırması ve projenin ilgili bölümleri açık bir şekilde anlatılacaktır:

1. Proje kökünde yer alanreadme.html (yönetici) hesabı oluşturmak için yönergeleri henüz uygulamadıysanız, şimdi uygulayın.

1. Hata AyıklamaYı Başlat Hata Visual Studio ( F5 ) kullanarak uygulamayı farklı  >  **bir** **dosyadan çalıştırın.** Uygulama tarayıcıda göründüğünde gezinti **çubuğunun** sağ üst kısmında Oturum aç'ın görüntülendiğinden dikkat edin.

    ![Django Web uygulaması sayfasında Project denetimi](media/django/step05-login-control.png)

1. *Templates/app/layout.html* öğesinin etiketini `<div class="navbar ...>` içerdiğine dikkat `{% include app/loginpartial.html %}` edin. Etiket, Django'nun şablon oluşturma sistemine, bu noktada dahil edilen dosyanın içeriklerini `{% include %}` içeren şablonda çekmesini sağlar.

1. *Şablonları/uygulama/loginpartial.html* açın ve kullanıcının kimlik doğrulamasından geçene bağlı olarak farklı kullanıcı arabirimi öğelerini işlemek için koşullu etiketi ve etiketi nasıl `{% if user.is_authenticated %}` `{% else %}` kullandığını gözlemlemek için:

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. Uygulamayı ilk kez başlatan hiçbir kullanıcının kimliği doğrulanmamış olduğundan, bu şablon kodu yalnızca "oturum açma" göreli yolunun "Oturum aç" bağlantısını işler. Önceki bölümde *urls.py* gösterildiği gibi, bu yol görünüme `django.contrib.auth.views.login` eşlenmiş. Bu görünüm aşağıdaki verileri alır:

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    Burada, `template_name` oturum açma sayfasının şablonunu tanımlar, bu durumda *templates/app/login.html.* `extra_context`özelliği, şablona verilen varsayılan bağlam verilerine eklenir. Son olarak, oturum açma bilgileriyle birlikte kullanmak üzere bir `authentication_form` form sınıfı belirtir; şablonda nesne olarak `form` görünür. Varsayılan değer `AuthenticationForm` `django.contrib.auth.views` (from) değeridir; Visual Studio  proje şablonu bunun yerine uygulamanın forms.py kullanır:

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    Gördüğünüz gibi, bu form sınıfı yer tutucu metin eklemek için kullanıcı adı ve parola alanlarından türetilen `AuthenticationForm` ve özellikle geçersiz kılar. Bu Visual Studio, parola gücü doğrulaması ekleme gibi formu özelleştirmek istediğiniz varsayımı temel alan bu açık kodu içerir.

1. Ardından, oturum açma sayfasına gidilen uygulama,login.html *işler.* değişkenleri ve `{{ form.username }}` `{{ form.password }}` formlarını `CharField` 'den `BootstrapAuthenticationForm` işler. Ayrıca doğrulama hatalarını göstermek için yerleşik bir bölüm ve bu hizmetleri eklemeyi seçerseniz sosyal oturum açmalar için hazır bir öğe de vardır.

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. Formu gönderdiğinizde Django kimlik bilgilerinizin (süper kullanıcının kimlik bilgileri gibi) kimliğini doğrulamaya çalışır. Kimlik doğrulaması başarısız olursa geçerli sayfada kalır ancak true `form.errors` olarak ayarlanır. Kimlik doğrulaması başarılı olursa, Django "sonraki" alanında göreli URL'ye (bu durumda giriş sayfası `<input type="hidden" name="next" value="/" />` ) `/` gidin.

1. Şimdi, giriş sayfası yeniden işlenecek olduğunda, `user.is_authenticated` şablon loginpartial.htmltrue olur. Sonuç olarak, Bir Merhaba **(kullanıcı adı) iletisi ve** Oturumu Kapat **iletisiyle karşınıza çıkar.** Kimlik doğrulamasını `user.is_authenticated` kontrol etmek için uygulamanın diğer kısımlarında kullanabilirsiniz.

    ![Django Web uygulaması sayfasında Hello iletisi Project denetimi](media/django/step05-logoff-control.png)

1. Kimliği doğrulanmış kullanıcının belirli kaynaklara erişim yetkisi olup olmadığını kontrol etmek için veritabanınıza kullanıcıya özgü izinleri alasınız. Daha fazla bilgi için [bkz. Django kimlik doğrulama sistemini kullanma](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Django belgeleri).

1. Özellikle süper kullanıcı veya yönetici, "/admin/" ve "/admin/doc/" url'lerini kullanarak yerleşik Django yönetici arabirimlerine erişme yetkisine sahiptir. Bu arabirimleri etkinleştirmek için şunları yapın:

    1. docutils Python paketini ortamınıza yükleyin. Bunu yapmak için harika bir *yol,requirements.txt* dosyanıza "docutils" eklemek ve ardından **Çözüm Gezgini'de** projeyi genişletmek, **Python** Ortamları düğümünü genişletmek ve ardından requirements.txt'den yükle seçeneğini kullanarak kullanmakta olduğunu ortama **sağ tıklamaktır.**

    1. Django projesinin *proje* urls.py ve varsayılan yorumları aşağıdaki girdilerden kaldırın:

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. Django projesinin settings.py *koleksiyonuna* gidin `INSTALLED_APPS` ve `'django.contrib.admindocs'` ekleyin.

    1. Uygulamayı yeniden başlattıktan sonra "/admin/" ve "/admin/doc/" hesaplarına gidin ve ek kullanıcı hesapları oluşturma gibi görevleri gerçekleştirin.

        ![Django yönetici arabirimi](media/django/step05-administrator-interface.png)

1. Kimlik doğrulama akışının son bölümü oturumu kapatmadır. oturum açmaloginpartial.htmlgördüğünüz *gibi,* Oturumu kapat bağlantısı yalnızca yerleşik görünümü tarafından işilen "/login" göreli URL'sinde bir POST  `django.contrib.auth.views.logout` yapar. Bu görünüm herhangi bir kullanıcı arabirimi görüntülemez ve yalnızca giriş sayfasına ("^logout$" *deseni urls.py* gösterildiği gibi) gidin. Oturum kapatma sayfası görüntülemek için önce URL desenini aşağıdaki gibi değiştirin ve bir "template_name" özelliği ekleyin ve "next_page" özelliğini kaldırın:

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Ardından, *aşağıdaki (minimum) loggedoff.htmlşablonlar/uygulama/uygulama* şablonları oluşturun:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Sonuç aşağıdaki gibi görünür:

    ![Oturum kapatma sayfası eklendi](media/django/step05-logged-off-page.png)

1. Bitirin, sunucuyu durdurun ve değişikliklerinizi bir kez daha kaynak denetimine işlenin.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Soru: Öğelerde görünen {% csrf_token %} etiketinin amacı \<form\> nedir?

Cevap: Etiket, Django'nun yerleşik siteler arası istek sahtecilik `{% csrf_token %}` [(csrf) korumasını](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django belgeleri) içerir. Bu etiketi genellikle form gibi POST, PUT veya DELETE isteği yöntemlerini içeren herhangi bir öğeye eklersiniz. Şablon işleme işlevi ( `render` ) ardından gerekli korumayı ekler.

## <a name="next-steps"></a>Sonraki adımlar

::: moniker range="vs-2017"
- [Polls Django Web Project kullanma](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> Bu öğretici boyunca Visual Studio çözümlerinizi kaynak denetimine sunuyorsanız, şimdi başka bir işleme yapmak için iyi bir zamandır. Çözümünüz, [microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)GitHub öğretici kaynak koduyla eşleşmeli.

Artık Visual Studio'de "Blank Django Web Project" ve "Django Web Project" şablonlarının tamamını Visual Studio. Görünümleri ve şablonları kullanma gibi Django ile ilgili tüm temel bilgileri öğrendinuz ve yönlendirme, kimlik doğrulaması ve veritabanı modellerini kullanma hakkında bilginiz var. Artık ihtiyacınız olan görünümlere ve modellere sahip kendi web uygulamasını oluşturabileceksiniz.

Geliştirme bilgisayarınızda web uygulaması çalıştırma, uygulamayı müşterileriniz için kullanılabilir hale uygulamanın yalnızca bir adımıdır. Sonraki adımlar aşağıdaki görevleri içerebilir:

- Web uygulamasını üretim sunucusuna dağıtın, örneğin Azure App Service. Bkz. [Azure App Service.](publishing-python-web-applications-to-azure-from-visual-studio.md).

- templates/404.htmladlı bir şablon oluşturarak 404 *sayfasını özelleştirin.* Django, mevcut olduğunda varsayılan şablonu yerine bu şablonu kullanır. Daha fazla bilgi için Django [belgelerinde](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) Hata görünümleri'ne bakın.

- Tests.py'da *birim testleri yazma;* Visual Studio proje şablonları bunlar için başlangıç noktaları sağlar ve Django belgelerinde İlk Django uygulamanızı [yazma, 5.](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) bölüm - [Django'da](https://docs.djangoproject.com/en/2.0/topics/testing/) test etme ve Test etme bölümünde daha fazla bilgi bulabilirsiniz.

- Uygulamayı SQLite'dan PostgreSQL, MySQL ve SQL Server (bunların hepsi Azure'da barındırabilirsiniz) gibi üretim düzeyinde bir veri deposuna değiştirme. SQLite (sqlite.org) ne zaman kullanılır? konusunda açıklandığı gibi, [SQLite](https://www.sqlite.org/whentouse.html) günde 100.000'den az isabete sahip düşük ve orta ölçekli trafik siteleri için iyi çalışır, ancak daha yüksek birimler için önerilmez. Ayrıca tek bir bilgisayarla da sınırlıdır, bu nedenle yük dengeleme ve coğrafi çoğaltma gibi çok sunuculu senaryolarda kullanılamaz. Django'nun diğer veritabanları için desteği hakkında bilgi için bkz. [Veritabanı kurulumu.](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup) Tablolar ve bloblar [gibi Azure depolama hizmetleriyle](/azure/python/) çalışmak üzere Python için Azure SDK'yı da kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım işlem hattı Azure DevOps. Kaynak denetimiyle (Azure Repos veya GitHub veya başka bir yerde) çalışmaya ek olarak, birim testlerinizi yayın için önkul olarak otomatik olarak çalıştırmak üzere bir Azure DevOps Project yapılandırabilirsiniz ve ayrıca işlem hattını üretime dağıtmadan önce ek testler için bir hazırlama sunucusuna dağıtacak şekilde yapılandırabilirsiniz. Azure DevOps, App Analizler gibi izleme çözümleriyle tümleştirildi ve çevik planlama araçlarıyla döngünin tamamını kapatıyor. Daha fazla bilgi için Azure DevOps projesiyle Python için [CI/CD](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) işlem hattı oluşturma ve ayrıca genel [Azure DevOps bakın.](/azure/devops/?view=vsts&preserve-view=true)
::: moniker-end
## <a name="go-deeper"></a>Daha derine gitme

- [Django'da kullanıcı kimlik doğrulaması](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- GitHub öğreticisi: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
