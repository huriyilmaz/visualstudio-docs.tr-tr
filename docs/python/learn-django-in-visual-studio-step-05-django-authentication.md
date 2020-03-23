---
title: Visual Studio, adım 5, kimlik doğrulama Django öğretici öğrenin
titleSuffix: ''
description: Visual Studio projeleri bağlamında Django temellerinin bir walkthrough, Özellikle Django Web Project şablonları tarafından sağlanan kimlik doğrulama özellikleri.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62957891"
---
# <a name="step-5-authenticate-users-in-django"></a>Adım 5: Django'daki kullanıcıları doğrulama

**Önceki adım: [Tam Django Web Projesi şablonu kullanın](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

Kimlik doğrulama web uygulamaları için ortak bir gereksinim olduğundan, "Django Web Project" şablonu temel bir kimlik doğrulama akışı içerir. (Bu öğreticinin 6. Django proje şablonlarından herhangi birini kullanırken, Visual Studio Django projesinin *settings.py*kimlik doğrulama için gerekli tüm modülleri içerir.

Bu adımda öğrenmek:

> [!div class="checklist"]
> - Visual Studio şablonlarında sağlanan kimlik doğrulama akışını niçin kullanırsınız (adım 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Adım 5-1: Kimlik doğrulama akışını kullanma

Aşağıdaki adımlar kimlik doğrulama akışını çalıştırın ve projenin ilgili bölümlerini açıklar:

1. Bir süper kullanıcı (yönetici) hesabı oluşturmak için proje kökündeki *readme.html* dosyasındaki yönergeleri zaten izlemediyseniz, bunu şimdi yapın.

1. **Hata Ayıklama** > Başlat Hata**Ayıklama** **(F5)** kullanarak Visual Studio'dan uygulamayı çalıştırın. Uygulama tarayıcıda göründüğünde, **Oturum Açma'nın** gezinme çubuğunun sağ üst tarafında göründüğünü gözlemleyin.

    ![Django Web Project uygulama sayfasında oturum açma denetimi](media/django/step05-login-control.png)

1. *templates/app/layout.html* açın ve `<div class="navbar ...>` öğenin etiketi `{% include app/loginpartial.html %}`içerdiğini gözlemleyin. Etiket, `{% include %}` Django'nun cazip sistemine, içerdiği şablondaki bu noktada dahil edilen dosyanın içeriğini çekmesini bildirir.

1. *templates/app/loginpartial.html* açın ve kullanıcının kimlik `{% if user.is_authenticated %}` doğrulaması `{% else %}` olup olmadığına bağlı olarak farklı Kullanıcı Arabirimi öğelerini işlemek için bir etiketle birlikte koşullu etiketi nasıl kullandığını gözlemleyin:

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

1. Uygulamayı ilk başlattığınızda hiçbir kullanıcının kimliği doğrulandığından, bu şablon kodu yalnızca göreli "oturum açma" yolunun "oturum açma" bağlantısını işler. *urls.py* belirtildiği gibi (önceki bölümde gösterildiği gibi), bu rota `django.contrib.auth.views.login` görünüme eşlenir. Bu görünüm aşağıdaki verileri alır:

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

    Burada, `template_name` oturum açma sayfası için şablonu tanımlar, bu durumda *templates/app/login.html.* Özellik, `extra_context` şablona verilen varsayılan bağlam verilerine eklenir. Son `authentication_form` olarak, oturum açma ile kullanılacak bir form sınıfı belirtir; şablonda `form` nesne olarak görünür. Varsayılan değer `AuthenticationForm` (from); `django.contrib.auth.views` Visual Studio proje şablonu bunun yerine uygulamanın *forms.py* dosyasında tanımlanan formu kullanır:

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

    Gördüğünüz gibi, bu form sınıfı yer `AuthenticationForm` tutucu metin eklemek için kullanıcı adı ve parola alanlarını türetir ve özellikle geçersiz kılar. Visual Studio şablonu, parola gücü doğrulama ekleme gibi formu özelleştirmek istediğiniz varsayımıüzerine bu açık kodu içerir.

1. Giriş sayfasına gidince, uygulama *login.html* şablonuna işlenir. Değişkenler `{{ form.username }}` ve `{{ form.password }}` `CharField` formları işlemek `BootstrapAuthenticationForm`. Ayrıca doğrulama hatalarını gösteren yerleşik bir bölüm ve bu hizmetleri eklemeyi seçerseniz sosyal oturum açmalar için hazır bir öğe de vardır.

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

1. Formu gönderdiğinizde, Django kimlik bilgilerinizin (süper kullanıcının kimlik bilgileri gibi) kimliğini doğrulamaya çalışır. Kimlik doğrulama başarısız olursa, geçerli sayfada `form.errors` kalır, ancak doğru olarak ayarlanır. Kimlik doğrulaması başarılı olursa, Django bu durumda ana sayfa `<input type="hidden" name="next" value="/" />`olan "sonraki" alandaki göreli URL'ye gider (`/`).

1. Şimdi, ana sayfa yeniden işlendiğinde, `user.is_authenticated` *loginpartial.html* şablonu işlendiğinde özellik doğrudur. Sonuç olarak, bir **Merhaba (kullanıcı adı)** iletisi görürsünüz ve **oturumu kapatın.** Kimlik doğrulamayı denetlemek için uygulamanın diğer bölümlerinde kullanabilirsiniz. `user.is_authenticated`

    ![Merhaba mesaj ve Django Web Project uygulama sayfasında giriş kontrolü](media/django/step05-logoff-control.png)

1. Kimlik doğrulaması yapılan kullanıcının belirli kaynaklara erişmeye yetkili olup olmadığını denetlemek için veritabanınızdan kullanıcıya özel izinler almanız gerekir. Daha fazla bilgi için Bkz. [Django kimlik doğrulama sistemini (Django](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) dokümanları) kullanma.

1. Süper kullanıcı veya yönetici, özellikle, göreli URL'leri "/admin/" ve "/admin/doc/" kullanarak yerleşik Django yönetici arabirimlerine erişmeye yetkilidir. Bu arabirimleri etkinleştirmek için aşağıdakileri yapın:

    1. Docutils Python paketini ortamınıza yükleyin. Bunu yapmanın harika bir yolu *gereksinimleri.txt* dosyasına "docutils" eklemektir, sonra **Solution Explorer,** projeyi genişletmek, **Python Ortamları** düğümünü genişletmek, sonra sağ kullandığınız ortama tıklayın **requirements.txt**seçin .

    1. Django projesinin *urls.py* açın ve varsayılan yorumları aşağıdaki girişlerden kaldırın:

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

    1. Django projesinin *settings.py* dosyasında, koleksiyona `INSTALLED_APPS` gidin `'django.contrib.admindocs'`ve ekleyin.

    1. Uygulamayı yeniden başlattığınızda , "/admin/" ve "/admin/doc/" adreslerine gidebilir ve ek kullanıcı hesapları oluşturma gibi görevleri gerçekleştirebilirsiniz.

        ![Django yönetici arayüzü](media/django/step05-administrator-interface.png)

1. Kimlik doğrulama akışının son bölümü kapalı gündür. *Loginpartial.html'de*de görebileceğiniz gibi, **Oturum kapatma** bağlantısı, yerleşik görünüm `django.contrib.auth.views.logout`tarafından işlenen göreli URL "/login"e bir POST yapar. Bu görünüm herhangi bir UI görüntülenmez ve yalnızca ana sayfaya doğru (urls.py "^logout$" deseni *için* gösterildiği gibi) gezinir. Bir oturum kapatma sayfası görüntülemek istiyorsanız, önce "template_name" özelliği eklemek ve "next_page" özelliğini kaldırmak için URL deseni aşağıdaki gibi değiştirin:

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Ardından aşağıdaki (minimal) içeriklerle *templates/app/loggedoff.html* oluşturun:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Sonuç aşağıdaki gibi görünür:

    ![Sayfa dan günlüğe eklendi](media/django/step05-logged-off-page.png)

1. Tüm işiniz bittiğinde, sunucuyu durdurun ve değişikliklerinizi bir kez daha kaynak denetimine bağla.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Soru: Form \<\> öğelerinde görünen {% csrf_token %} etiketinin amacı nedir?

Cevap: `{% csrf_token %}` Etiket, Django'nun yerleşik [çapraz site isteği sahteciliği (csrf) koruması](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django dokümanları) içerir. Bu etiketi genellikle form gibi POST, PUT veya DELETE istek yöntemlerini içeren herhangi bir öğeye eklersiniz. Şablon oluşturma işlevi`render`( ) sonra gerekli koruma ekler.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Anketler Django Web Projesi şablonu kullanın](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>Daha derine inin

- [Django'da kullanıcı kimlik doğrulaması](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- GitHub'da Öğretici kaynak kodu: [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
