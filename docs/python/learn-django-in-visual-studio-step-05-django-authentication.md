---
title: Visual Studio 'da Docgo öğreticisini öğrenin, 5. adım, kimlik doğrulama
titleSuffix: ''
description: Visual Studio projeleri bağlamında, özellikle de Docgo Web projesi şablonları tarafından sağlandığı şekilde kimlik doğrulama özellikleri olan Docgo hakkında bir anlatım.
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bdc76b0a7b9d3f74da77b317faf31dae83706f04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62957891"
---
# <a name="step-5-authenticate-users-in-django"></a>5. Adım: Docgo 'da kullanıcıların kimliğini doğrulama

**Önceki adım: [tam Docgo Web proje şablonunu kullanma](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Kimlik doğrulaması Web uygulamaları için yaygın bir gereksinimdir, "Docgo Web projesi" şablonu temel bir kimlik doğrulama akışı içerir. (Bu öğreticinin 6. adımında açıklanan "Docgo Web projesini yoklamalar" şablonu aynı akışı da içerir.) Docgo proje şablonlarından herhangi birini kullanırken, Visual Studio Docgo projesinin *Settings.py*kimlik doğrulaması için gerekli tüm modülleri içerir.

Bu adımda şunları öğreneceksiniz:

> [!div class="checklist"]
> - Visual Studio şablonlarında sunulan kimlik doğrulama akışını kullanma (adım 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Adım 5-1: kimlik doğrulama akışını kullanma

Aşağıdaki adımlar, kimlik doğrulama akışını ve projenin dahil olduğu bölümleri anlatmaktadır:

1. Zaten bir süper kullanıcı (yönetici) hesabı oluşturmak için proje kökündeki *readme.html* dosyasındaki yönergeleri izlediyseniz, şimdi bunu yapın.

1. Visual Studio 'dan **hata ayıklama**  >  **başlatma hata ayıklamayı** (**F5**) kullanarak uygulamayı çalıştırın. Uygulama tarayıcıda göründüğünde, gezinti çubuğunun sağ üst köşesinde görüntülenen **günlük** ' i gözlemleyin.

    ![Docgo Web projesi uygulaması sayfasında oturum açma denetimi](media/django/step05-login-control.png)

1. *Templates/App/layout.html* ' i açın ve `<div class="navbar ...>` öğesinin etiketi içerdiğini gözlemleyin `{% include app/loginpartial.html %}` . `{% include %}`Etiketi, Docgo 'nun şablon oluşturma sisteminin, içerilen şablonun bu noktasında eklenen dosyanın içeriğini çekmesini sağlar.

1. *Şablonlar/App/loginpartial.html* ' i açın ve `{% if user.is_authenticated %}` `{% else %}` kullanıcının kimliği doğrulandığına bağlı olarak farklı kullanıcı arabirimi öğelerini işlemek için bir etiketle birlikte koşullu etiketi nasıl kullandığını gözlemleyin:

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

1. Uygulamayı ilk başlattığınızda hiçbir kullanıcının kimliği doğrulanmadığı için, bu şablon kodu yalnızca "oturum aç" göreli yoluna "oturum aç" bağlantısını işler. *URLs.py* ' de belirtildiği gibi (önceki bölümde gösterildiği gibi), bu yol `django.contrib.auth.views.login` görünüme eşlenir. Bu görünüm aşağıdaki verileri alır:

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

    Burada, `template_name` oturum açma sayfasının şablonunu, bu durumda *Templates/app/login.html*olarak tanımlar. `extra_context`Özelliği, şablona verilen varsayılan bağlam verilerine eklenir. Son olarak, `authentication_form` oturum açmayla birlikte kullanılacak bir form sınıfı belirtir; şablonda nesne olarak görünür `form` . Varsayılan değer `AuthenticationForm` (from `django.contrib.auth.views` ); bunun yerine Visual Studio proje şablonu, uygulamanın *Forms.py* dosyasında tanımlanan formu kullanır:

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

    Görebileceğiniz gibi, bu form sınıfı öğesinden türetilir `AuthenticationForm` ve özel olarak yer tutucu metni eklemek için Kullanıcı adı ve parola alanlarını geçersiz kılar. Visual Studio şablonu, bu açık kodu, formu özelleştirmek isteyebileceğiniz, örneğin parola gücü doğrulaması ekleme gibi bir şekilde içerir.

1. Oturum açma sayfasına gittiğinizde, uygulama *login.html* şablonunu işler. Değişkenleri `{{ form.username }}` ve `{{ form.password }}` `CharField` içindeki formları işleme `BootstrapAuthenticationForm` . Ayrıca, bu hizmetleri eklemeyi seçerseniz, doğrulama hatalarını göstermek için yerleşik bir bölüm ve sosyal oturumlar için hazır bir öğe vardır.

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

1. Formu gönderdiğinizde, Docgo kimlik bilgilerinizi (süper kullanıcının kimlik bilgileri gibi) doğrulamaya çalışır. Kimlik doğrulaması başarısız olursa, geçerli sayfada kalır, ancak `form.errors` doğru olarak ayarlanır. Kimlik doğrulaması başarılı olursa, Docgo "sonraki" alanındaki ilgili URL 'ye gider, `<input type="hidden" name="next" value="/" />` Bu durumda giriş sayfası ( `/` ) olur.

1. Artık, giriş sayfası tekrar işlendiğinde, `user.is_authenticated` *loginpartial.html* şablonu işlendiğinde özelliği true olur. Sonuç olarak, bir **Merhaba (Kullanıcı adı)** iletisi görürsünüz ve **Oturumu kapatın**. `user.is_authenticated`Kimlik doğrulamasını denetlemek için uygulamanın diğer bölümlerinde öğesini kullanabilirsiniz.

    ![Docgo Web projesi uygulaması sayfasında Merhaba ileti ve oturum kapatma denetimi](media/django/step05-logoff-control.png)

1. Kimliği doğrulanmış kullanıcının belirli kaynaklara erişme yetkisine sahip olup olmadığını denetlemek için, veritabanınıza kullanıcıya özgü izinleri almanız gerekir. Daha fazla bilgi için bkz. [docgo kimlik doğrulama sistemini kullanma](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (docgo belgeleri).

1. Özellikle süper kullanıcı veya yönetici, "/admin/" ve "/admin/doc/" göreli URL 'Leri kullanılarak yerleşik Docgo yönetici arabirimlerine erişme yetkisine sahiptir. Bu arabirimleri etkinleştirmek için aşağıdakileri yapın:

    1. Docutils Python paketini ortamınıza yükler. Bunu yapmanın harika bir yolu, *requirements.txt* dosyanıza "docutils" eklemek, ardından **Çözüm Gezgini**, projeyi genişletmeniz, **Python ortamları** düğümünü genişletmeniz ve ardından requirements.txtbir SELECT **yüklemesi **kullandığınız ortama sağ tıklamanız gerekir.

    1. Docgo projesinin *URLs.py* açın ve aşağıdaki girişlerden varsayılan açıklamaları kaldırın:

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

    1. Docgo projesinin *Settings.py* dosyasında, `INSTALLED_APPS` koleksiyona gidin ve ekleyin `'django.contrib.admindocs'` .

    1. Uygulamayı yeniden başlattığınızda, "/admin/" ve "/admin/doc/" adresine giderek ek kullanıcı hesapları oluşturma gibi görevleri gerçekleştirebilirsiniz.

        ![Docgo yönetici arabirimi](media/django/step05-administrator-interface.png)

1. Kimlik doğrulama akışının son bölümü günlüğe kaydediliyor. *loginpartial.html*'de görebileceğiniz gibi, **oturum kapatma** bağlantısı, yerleşik görünüm tarafından işlenen GÖRELI URL 'ye bir gönderi ("/Login") yapar `django.contrib.auth.views.logout` . Bu görünüm hiçbir Kullanıcı arabirimini göstermez ve yalnızca giriş sayfasına ("^ Logout $" deseninin *URLs.py* gösterildiği gibi) gider. Bir oturum kapatma sayfası göstermek istiyorsanız, önce URL deseninin "template_name" özelliği eklemek ve "next_page" özelliğini kaldırmak için aşağıdaki şekilde değiştirin:

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Ardından aşağıdaki (minimum) içerikle *Şablonlar/App/loggedoff.html* oluşturun:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Sonuç şu şekilde görünür:

    ![Oturumu açılmış sayfa eklendi](media/django/step05-logged-off-page.png)

1. İşiniz bittiğinde, sunucuyu durdurun ve değişikliklerinizi kaynak denetimine yeniden uygulayın.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Soru: öğelerde görüntülenen {% csrf_token%} etiketinin amacı nedir \<form\> ?

Cevap: `{% csrf_token %}` etiket docgo 'nun yerleşik [siteler arası istek sahteciliğini önleme (CSRF) koruması](https://docs.djangoproject.com/en/2.0/ref/csrf/) (docgo belgeleri) içerir. Bu etiketi genellikle form gibi POST, PUT veya DELETE istek yöntemlerini içeren herhangi bir öğeye eklersiniz. Şablon işleme işlevi ( `render` ) gerekli korumayı ekler.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Docgo Web proje şablonunu Yoklat ' i kullanın](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Daha derin git

- [Docgo 'Da Kullanıcı kimlik doğrulaması](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- GitHub 'daki öğretici kaynak kodu: [Microsoft/Python-Sample-vs-Learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
