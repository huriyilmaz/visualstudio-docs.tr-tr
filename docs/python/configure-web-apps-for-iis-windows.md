---
title: IIS için Python web uygulamalarını yapılandırma
description: Python web uygulamalarını bir sanal makineden Internet Information Services çalıştıracak Windows yapılandırma.
ms.custom: devdivchpfy22
ms.date: 12/20/2021
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 973842bc0a149a1a292fb66c67c7bf8b974668df
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803303"
---
# <a name="configure-python-web-apps-for-iis"></a>IIS için Python web uygulamalarını yapılandırma

Internet Information Services (IIS) bir Windows bilgisayarda [(Azure'daki Windows](/azure/architecture/reference-architectures/n-tier/windows-vm)sanal makineleri dahil) bir web sunucusu olarak kullanırken, Python uygulamalarının Python kodunu düzgün bir şekilde işlemesi için Python uygulamaları *web.config* dosyalarında belirli ayarları içermesi gerekir. Bilgisayarda, web uygulamasının gerektirdiği paketlerle birlikte Python da yüklü olmalıdır.

> [!Note]
> Bu makalede daha önce python'ı Azure App Service yapılandırma Windows. Python uzantıları ve Windows bu senaryoda kullanılan python uzantıları ve Linux üzerinde Azure App Service. Daha fazla bilgi için [bkz. Python Uygulamalarını Azure App Service (Linux)](publishing-python-web-applications-to-azure-from-visual-studio.md). Ancak önceki makale, Python uzantılarıyla [App Service'Windows yönetme makalesinde hala kullanılabilir.](managing-python-on-azure-app-service.md)

## <a name="install-python-on-windows"></a>Windows üzerinde Python’ı yükleme

Bir web uygulamasını çalıştırmak için, önce Python yorumlayıcılarını yükleme konusunda açıklandığı gibi Windows Python ana [makinesine doğrudan Python sürümünü yükleyin.](installing-python-interpreters.md)

Sonraki adımlar için `python.exe` yorumlayıcının konumunu kaydetme. Kolaylık olması için bu konumu PATH ortam değişkeninize ebilirsiniz.

## <a name="install-packages"></a>Paketleri yükleme

Ayrılmış bir konak kullanırken, genel Python ortamını kullanarak sanal ortam yerine uygulama çalıştırabilirsiniz. Buna uygun olarak, yalnızca bir komut isteminde çalıştırarak tüm uygulama gereksinimlerinizi genel `pip install -r requirements.txt` ortama yükleyebilirsiniz.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Python web.config işaret etmek için kümeyi ayarlama

Uygulamanın *web.config* dosyası, Windows üzerinde çalışan IIS (7+) web sunucusuna HttpPlatform (önerilen) veya FastCGI aracılığıyla Python isteklerini nasıl işlemesi gerektiği hakkında bilgi verir. Visual Studio 2015 ve önceki sürümlerde bu değişiklikler otomatik olarak yapılır. Visual Studio 2017 ve sonraki bir 2017'web.configdeğiştirmeniz gerekir. 

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyicisini yapılandırma

HttpPlatform modülü yuva bağlantılarını doğrudan tek başına bir Python sürecine iletir. Bu geçiş, herhangi bir web sunucusunu çalıştırmaya olanak sağlar, ancak yerel bir web sunucusu çalıştıran bir başlangıç betiği gerektirir. Betiğiweb.configöğesinde belirtirsiniz; burada öznitelik site uzantısının Python yorumlayıcıya, öznitelik ise betiğinize ve sağlamak istediğiniz bağımsız `<httpPlatform>` ** `processPath` değişkenleri `arguments` belirtir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="c:\python36-32\python.exe"
                  arguments="c:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="c:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Burada `HTTP_PLATFORM_PORT` gösterilen ortam değişkeni, yerel sunucunuz tarafından localhost'tan gelen bağlantılar için dinlemesi gereken bağlantı noktasını içerir. Bu örnekte ayrıca, bu örnekte istenirse başka bir ortam değişkeninin nasıl oluşturulacakları da `SERVER_PORT` gösterir.

### <a name="configure-the-fastcgi-handler"></a>FastCGI işleyicisini yapılandırma

FastCGI, istek düzeyinde çalışan bir arabirimdir. IIS gelen bağlantıları alır ve her isteği bir veya daha fazla kalıcı Python işlemi içinde çalışan bir WSGI uygulamasına iletir.

Bunu kullanmak için önce wfastcgi paketini [pypi.org/project/wfastcgi/.](https://pypi.io/project/wfastcgi)

Ardından, uygulamanınweb.config *dosyasını* değiştirerek anahtarapython.exe *wfastcgi.py* yolunu `PythonHandler` bulun. Aşağıdaki adımlarda Python'ın *c:\python36-32'de* yüklü olduğu ve uygulama kodunuzun *c:\home\site\wwwroot konumunda olduğu varsayılacaktır.* yollarınızı uygun şekilde ayarlayın:

1. uygulama içinde girdisiniweb.configyolu Python yükleme konumuyla eşleysin (tam ayrıntılar için `PythonHandler` [bkz. IIS](https://www.iis.net/configreference) Yapılandırma  Başvurusu (iis.net) ).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. web.config`<appSettings>` *bölümünde*, (isteğe `WSGI_HANDLER` `WSGI_LOG` bağlı) ve için anahtarlar `PYTHONPATH` ekleyin:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Bu `<appSettings>` değerler uygulamanıza ortam değişkenleri olarak kullanılabilir:

    - değeri `PYTHONPATH` serbestçe genişletilmiş olabilir, ancak uygulamanın kökünü içermesi gerekir.
    - `WSGI_HANDLER` , uygulamanıza aktarılabilir bir WSGI uygulamasına işaret etmek gerekir.
    - `WSGI_LOG` isteğe bağlıdır, ancak uygulama hata ayıklaması için önerilir.

1. Giriş `WSGI_HANDLER` girişlerini *web.config* çerçeve için uygun şekilde ayarlayın:

    - **Bottle:** aşağıda gösterildiği gibi parantezleri `app.wsgi_app` olduğundan emin olun. Bu, nesne değişken yerine bir işlev (bkz. *app.py*) olduğundan gereklidir:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Flask:** `WSGI_HANDLER` değerini, `<project_name>.app` `<project_name>` projenizin adıyla eşleşen değerle değiştirir. Tanımlayıcının tam tanımlayıcısını bulmak için `from <project_name> import app` runserver.py.  Örneğin, proje "FlaskAzurePublishExample" olarak adlandırılmışsa girdi aşağıdaki gibi görünür:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="FlaskAzurePublishExample.app"/>
        ```

    - **Django:** Django *projeleriniweb.config* iki değişiklik gereklidir. İlk olarak değeri `WSGI_HANDLER` olarak `django.core.wsgi.get_wsgi_application()` (nesne,  wsgi.py dosyasındadır):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        İkinci olarak, için aşağıdaki girdinin altına ekleyin `WSGI_HANDLER` ve `DjangoAzurePublishExample` yerine projenizin adını yazın:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Yalnızca Django** uygulamaları: Django *projesinin settings.py* dosyasında, `ALLOWED_HOSTS` '1.2.3.4' yerine URL'nizi veya IP adresinizi yazın:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Url'nizi diziye ekleyemediyebilirsiniz. Şu hatayla sonuçlanır: **DisallowedHost , / Geçersiz HTTP_HOST üst bilgisi: ' \<site URL\> ' . '' 'yi \<site URL\> ALLOWED_HOSTS.**

    Dizi boş olduğunda Django otomatik olarak 'localhost' ve '127.0.0.1' izin verir, ancak üretim URL'nizi eklemek bu özellikleri kaldırır. Bu nedenle, ortamının ayrı geliştirme ve üretim kopyalarını settings.py veya çalışma *zamanı* değerlerini kontrol etmek için ortam değişkenlerini kullanabilirsiniz.

## <a name="deploy-to-iis-or-a-windows-vm"></a>IIS'ye veya Windows VM'ye dağıtma

Projenize *doğruweb.config* dosyasıyla, **Çözüm Gezgini**'de projenin bağlam menüsünde yayımla komutunu kullanarak ve IIS, FTP vb. seçeneğini kullanarak IIS çalıştıran bilgisayarda  **yayımlayın.** Bu durumda, Visual Studio proje dosyalarını sunucuya kopyalar; tüm sunucu tarafı yapılandırmaları sizin sorumluluğundadır.
