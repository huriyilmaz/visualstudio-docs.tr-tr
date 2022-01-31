---
title: Visual Studio, 5. adım, kimlik doğrulamasında docgo öğreticisini öğrenin
titleSuffix: ''
description: docgo Web Project şablonları tarafından sağlandığı gibi, özellikle kimlik doğrulama özellikleri olan Visual Studio projeler bağlamında docgo hakkında bir anlatım.
ms.date: 01/25/2022
ms.topic: tutorial
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 74a47f236e2a90c97e4bb96bd0f7127367306058
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886806"
---
# <a name="step-5-authenticate-users-in-django"></a>5. Adım: Docgo 'da kullanıcıların kimliğini doğrulama

**önceki adım: [tam docgo Web Project şablonunu kullanma](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

::: moniker range="vs-2017"
kimlik doğrulaması web uygulamaları için yaygın bir gereksinimdir, "docgo web Project" şablonu temel bir kimlik doğrulama akışı içerir. (bu öğreticinin 6. adımında açıklanan "docgo Web Project 'i yoklamıştır" şablonu aynı akışı da içerir.) docgo proje şablonlarından herhangi birini kullanırken Visual Studio, docgo projesinin *settings.py* kimlik doğrulaması için gerekli tüm modülleri içerir.
::: moniker-end

::: moniker range=">=vs-2019"
kimlik doğrulaması web uygulamaları için yaygın bir gereksinimdir, "docgo web Project" şablonu temel bir kimlik doğrulama akışı içerir. docgo proje şablonlarından herhangi birini kullanırken Visual Studio, docgo projesinin *settings.py* kimlik doğrulaması için gerekli tüm modülleri içerir.
::: moniker-end

Bu adımda şunları öğreneceksiniz:

> [!div class="checklist"]
> - Visual Studio şablonlarında belirtilen kimlik doğrulama akışını kullanma (adım 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>Adım 5-1: kimlik doğrulama akışını kullanma

Aşağıdaki adımlar, kimlik doğrulama akışını ve projenin dahil olduğu bölümleri anlatmaktadır:

1. Zaten bir süper kullanıcı (yönetici) hesabı oluşturmak için proje kökündeki *readme.html* dosyasındaki yönergeleri izlediyseniz, şimdi bunu yapın.

1. **hata ayıklama**  >  **başlatma hata ayıklaması** (**F5**) kullanarak Visual Studio uygulamayı çalıştırın. Uygulama tarayıcıda göründüğünde, gezinti çubuğunun sağ üst köşesinde görüntülenen **günlük** ' i gözlemleyin.

    ![docgo Web Project uygulaması sayfasında oturum açma denetimi](media/django/step05-login-control.png)

1. *Şablonlar/App/layout.html* açın ve öğesinin etiketi `{% include app/loginpartial.html %}` içerdiğini gözlemleyin `<div class="navbar ...>` . Etiketi, `{% include %}` Docgo 'nun şablon oluşturma sisteminin, içerilen şablonun bu noktasında eklenen dosyanın içeriğini çekmesini sağlar.

1. *Şablonlar/App/loginpartial.html* açın ve kullanıcının kimliği doğrulandığına bağlı olarak farklı kullanıcı arabirimi öğelerini işlemek için bir `{% else %}` etiketle birlikte koşullu etiketi `{% if user.is_authenticated %}` nasıl kullandığını gözlemleyin:

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

1. Uygulamayı ilk başlattığınızda hiçbir kullanıcının kimliği doğrulanmadığı için, bu şablon kodu yalnızca "oturum aç" göreli yoluna "oturum aç" bağlantısını işler. *URLs.py* ' de belirtildiği gibi (önceki bölümde gösterildiği gibi), bu yol görünüme eşlenir `django.contrib.auth.views.login` . Bu görünüm aşağıdaki verileri alır:

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

    `template_name`Burada, oturum açma sayfasının şablonunu, bu durumda *Şablonlar/uygulama/login.html* tanımlar. `extra_context`Özelliği, şablona verilen varsayılan bağlam verilerine eklenir. Son olarak, `authentication_form` oturum açmayla birlikte kullanılacak bir form sınıfı belirtir; şablonda nesne olarak `form` görünür. varsayılan değer `AuthenticationForm` (from `django.contrib.auth.views` ), bunun yerine Visual Studio proje şablonu, uygulamanın *forms.py* dosyasında tanımlanan formu kullanır:

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

    Görebileceğiniz gibi, bu form sınıfı öğesinden `AuthenticationForm` türetilir ve özel olarak yer tutucu metni eklemek için Kullanıcı adı ve parola alanlarını geçersiz kılar. Visual Studio şablonu, bu açık kodu, formu özelleştirmek isteyebileceğiniz, örneğin parola gücü doğrulaması ekleme gibi bir şekilde içerir.

1. Oturum açma sayfasına gittiğinizde, uygulama *login.html* şablonunu işler. Değişkenleri `{{ form.username }}` ve `{{ form.password }}` içindeki `BootstrapAuthenticationForm` formları işleme `CharField` . Ayrıca, bu hizmetleri eklemeyi seçerseniz, doğrulama hatalarını göstermek için yerleşik bir bölüm ve sosyal oturumlar için hazır bir öğe vardır.

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

1. Formu gönderdiğinizde, Docgo kimlik bilgilerinizi (süper kullanıcının kimlik bilgileri gibi) doğrulamaya çalışır. Kimlik doğrulaması başarısız olursa, geçerli sayfada kalır, ancak `form.errors` doğru olarak ayarlanır. Kimlik doğrulaması başarılı olursa, Docgo "sonraki" alanındaki `<input type="hidden" name="next" value="/" />` ılgılı URL 'ye gider, bu durumda giriş sayfası ( `/` ) olur.

1. Artık, giriş sayfası tekrar işlendiğinde, `user.is_authenticated` *loginpartial.html* şablonu işlendiğinde özelliği true olur. Sonuç olarak, bir **Merhaba (Kullanıcı adı)** iletisi görürsünüz ve **Oturumu kapatın**. Kimlik doğrulamasını denetlemek için uygulamanın diğer bölümlerinde öğesini kullanabilirsiniz `user.is_authenticated` .

    ![docgo Web Project uygulaması sayfasında merhaba ileti ve oturum kapatma denetimi](media/django/step05-logoff-control.png)

1. Kimliği doğrulanmış kullanıcının belirli kaynaklara erişme yetkisine sahip olup olmadığını denetlemek için, veritabanınıza kullanıcıya özgü izinleri almanız gerekir. Daha fazla bilgi için bkz. [docgo kimlik doğrulama sistemini kullanma](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (docgo belgeleri).

1. Özellikle süper kullanıcı veya yönetici, "/admin/" ve "/admin/doc/" göreli URL 'Leri kullanılarak yerleşik Docgo yönetici arabirimlerine erişme yetkisine sahiptir. Bu arabirimleri etkinleştirmek için aşağıdakileri yapın:

    1. Docutils Python paketini ortamınıza yükler. Bunu yapmanın harika bir yolu, *requirements.txt* dosyanıza "docutils" eklemek, ardından **Çözüm Gezgini**, projeyi genişletmeniz, **Python ortamları** düğümünü genişletmeniz ve ardından requirements.txtbir SELECT **yüklemesi** kullandığınız ortama sağ tıklamanız gerekir.

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

    1. Docgo projesinin *Settings.py* dosyasında, koleksiyona gidin `INSTALLED_APPS` ve ekleyin `'django.contrib.admindocs'` .

    1. Uygulamayı yeniden başlattığınızda, "/admin/" ve "/admin/doc/" adresine giderek ek kullanıcı hesapları oluşturma gibi görevleri gerçekleştirebilirsiniz.

        ![Docgo yönetici arabirimi](media/django/step05-administrator-interface.png)

1. Kimlik doğrulama akışının son bölümü günlüğe kaydediliyor. *loginpartial.html* görebileceğiniz gibi, **oturum kapatma** bağlantısı, yerleşik görünüm `django.contrib.auth.views.logout` tarafından IŞLENEN göreli URL 'ye bir gönderi ("/Login") yapar. Bu görünüm hiçbir Kullanıcı arabirimini göstermez ve yalnızca giriş sayfasına ("^ Logout $" deseninin *URLs.py* gösterildiği gibi) gider. Bir oturum kapatma sayfası göstermek istiyorsanız, önce URL deseninin "template_name" özelliği eklemek ve "next_page" özelliğini kaldırmak için aşağıdaki şekilde değiştirin:

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    Daha sonra aşağıdaki (minimum) içerikle *Şablonlar/uygulama/loggedoff.html* oluşturun:

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    Sonuç şu şekilde görünür:

    ![Oturumu açılmış sayfa eklendi](media/django/step05-logged-off-page.png)

1. İşiniz bittiğinde, sunucuyu durdurun ve değişikliklerinizi kaynak denetimine yeniden uygulayın.

### <a name="question-what-is-the-purpose-of-the--csrf_token--tag-that-appears-in-the-form-elements"></a>Soru: öğelerde görüntülenen \<form\> {% csrf_token%} etiketinin amacı nedir?

Cevap: `{% csrf_token %}` etiket docgo 'nun yerleşik [siteler arası istek sahteciliğini önleme (CSRF) koruması](https://docs.djangoproject.com/en/2.0/ref/csrf/) (docgo belgeleri) içerir. Bu etiketi genellikle form gibi POST, PUT veya DELETE istek yöntemlerini içeren herhangi bir öğeye eklersiniz. Şablon işleme işlevi ( `render` ) gerekli korumayı ekler.

## <a name="next-steps"></a>Sonraki adımlar

::: moniker range="vs-2017"
- [docgo Web Project şablonunu yoklayıp kullanın](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> bu öğreticinin tamamında Visual Studio çözümünüzü kaynak denetimine uyguladıysanız, başka bir işleme yapmak iyi bir zaman vardır. çözümünüz GitHub: [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)üzerindeki öğretici kaynak kodu ile eşleşmelidir.

artık, Visual Studio içindeki "boş docgo web Project" ve "docgo web Project" şablonlarının tamamını incelediniz. Görünümler ve Şablonlar kullanma gibi Docgo 'un tüm temel bilgilerini öğrendiniz ve veritabanı modellerini kullanarak, bir yönlendirme, kimlik doğrulama ve değişiklik yapabilirsiniz. Artık ihtiyacınız olan herhangi bir görünüm ve modelle kendinizinkini bir Web uygulaması oluşturabilmeniz gerekir.

Geliştirme bilgisayarınızda bir Web uygulaması çalıştırmak, uygulamayı müşterileriniz için kullanılabilir hale getirmek için yalnızca bir adımdır. Sonraki adımlarda aşağıdaki görevler bulunabilir:

- Web uygulamasını Azure App Service gibi bir üretim sunucusuna dağıtın. Bkz. [Azure App Service yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md).

- *Şablonlar/404.html* adlı bir şablon oluşturarak 404 sayfasını özelleştirin. Mevcut olduğunda, Docgo, varsayılan değer yerine bu şablonu kullanır. Daha fazla bilgi için, bkz. Docgo belgelerindeki [hata görünümleri](https://docs.djangoproject.com/en/2.0/ref/views/#error-views) .

- Birim testlerini *Tests.py*'de yazın; Visual Studio proje şablonları bunlar için başlangıç noktaları sağlar ve dmongo belgelerinde dmongo 'da [ilk dmongo uygulamanızı, 5. bölüm-test](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) ve [test](https://docs.djangoproject.com/en/2.0/topics/testing/) ' i yazarken daha fazla bilgi bulabilirsiniz.

- uygulamayı SQLite ' dan postgresql, MySQL ve SQL Server (tümü Azure üzerinde barındırılabilen) gibi bir üretim düzeyi veri deposu olarak değiştirin. SQLite (sqlite.org) [ne zaman kullanılacağı](https://www.sqlite.org/whentouse.html) konusunda açıklandığı gibi, SQLite, 100 ' den az KB/gün içinde düşük ve orta ölçekli trafik siteleri için uygundur, ancak daha yüksek birimler için önerilmez. Aynı zamanda tek bir bilgisayarla sınırlandırılmıştır, bu nedenle yük dengeleme ve coğrafi çoğaltma gibi çok sunuculu bir senaryoda kullanılamaz. Docgo 'nun diğer veritabanları için desteği hakkında bilgi için bkz. [veritabanı kurulumu](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup). Ayrıca, [Python Için Azure SDK 'sını](/azure/python/) tablolar ve Bloblar gibi Azure depolama hizmetleriyle birlikte çalışmak için de kullanabilirsiniz.

- Azure DevOps gibi bir hizmette sürekli tümleştirme/sürekli dağıtım işlem hattı ayarlayın. kaynak denetimi ile çalışmaya ek olarak (Azure Repos veya GitHub ya da başka bir yerde), birim testlerinizi bir ön koşul olarak otomatik olarak çalıştırmak için bir Azure DevOps Project yapılandırabilir ve ayrıca işlem hattını üretime dağıtmadan önce ek testler için bir hazırlama sunucusuna dağıtılacak şekilde yapılandırabilirsiniz. Azure DevOps, ayrıca, uygulama Analizler gibi izleme çözümleriyle tümleştirilir ve çevik planlama araçlarıyla tüm döngüyü kapatır. daha fazla bilgi için bkz. [Python için bir cı/CD işlem hattı oluşturma Azure DevOps projesi](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true) ve ayrıca genel [Azure DevOps belgeleri](/azure/devops/?view=vsts&preserve-view=true).
::: moniker-end
## <a name="go-deeper"></a>Daha derin git

- [Docgo 'Da Kullanıcı kimlik doğrulaması](https://docs.djangoproject.com/en/2.0/topics/auth/) (docs.djangoproject.com)
- GitHub eğitim kaynak kodu: [Microsoft/python-sample-vs-learning-docgo](https://github.com/Microsoft/python-sample-vs-learning-django)
