---
title: IIS için Python web uygulamalarını yapılandırma
description: Python web uygulamalarını Windows sanal makinesinden Internet Information Services ile çalışacak şekilde yapılandırma.
ms.date: 12/06/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 551cff18849f0e8ad9fcd6f2c1e08561291b177f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957382"
---
# <a name="configure-python-web-apps-for-iis"></a>IIS için Python web uygulamalarını yapılandırma

Internet Information Services (IIS) windows bilgisayarında bir web sunucusu olarak kullanırken [(Azure'daki Windows sanal makineleri](/azure/architecture/reference-architectures/n-tier/windows-vm)dahil), Python uygulamalarının Python kodunu düzgün bir şekilde işleyebilmeleri için *web.config* dosyalarına belirli ayarlar eklemesi gerekir. Bilgisayarın kendisi de Python web uygulaması gerektirir herhangi bir paket ile birlikte yüklü olmalıdır.

> [!Note]
> Bu makalede, daha önce Windows'da Azure Uygulama Hizmeti'nde Python yapılandırma kılavuzu yer alıyordu. Bu senaryoda kullanılan Python uzantıları ve Windows ana bilgisayarları Linux'taki Azure Uygulama Hizmeti lehine küçümsülme lerine neden olmuştur. Daha fazla bilgi için [bkz.](publishing-python-web-applications-to-azure-from-visual-studio.md) Önceki makalede, ancak, Python [uzantıları ile Windows'da Uygulama Hizmetini Yönetme](managing-python-on-azure-app-service.md)hala kullanılabilir.

## <a name="install-python-on-windows"></a>Windows'a Python'u yükleme

Bir web uygulamasını çalıştırmak için, öncelikle Python'un gerekli [sürümünü, Python'u Yükle yorumlayıcılarında](installing-python-interpreters.md)açıklandığı şekilde doğrudan Windows ana bilgisayar makinesine yükleyin.

Daha sonraki adımlar `python.exe` için tercümanın konumunu kaydedin. Kolaylık sağlamak için, bu konumu PATH ortamı değişkeninize ekleyebilirsiniz.

## <a name="install-packages"></a>Paketleri yükleme

Özel bir ana bilgisayar kullanırken, uygulamanızı sanal bir ortam yerine çalıştırmak için genel Python ortamını kullanabilirsiniz. Buna göre, uygulamanızın tüm gereksinimlerini yalnızca bir komut isteminde `pip install -r requirements.txt` çalıştırarak genel ortama yükleyebilirsiniz.

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Python yorumlayıcısını işaret etmek için web.config'i ayarlayın

Uygulamanızın *web.config* dosyası, Windows'ta çalışan IIS (7+) web sunucusuna Python isteklerini HttpPlatform (önerilir) veya FastCGI aracılığıyla nasıl işlemesi gerektiği konusunda talimat verir. Visual Studio sürümleri 2015 ve önceki otomatik olarak bu değişiklikleri yapmak. Visual Studio 2017 ve sonrası *kullanırken, web.config'i* el ile değiştirmeniz gerekir.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyicisini yapılandırma

HttpPlatform modülü soket bağlantılarını doğrudan bağımsız bir Python işlemine geçirir. Bu geçiş, istediğiniz herhangi bir web sunucusunu çalıştırmanızı sağlar, ancak yerel bir web sunucusu çalıştıran bir başlangıç komut dosyası gerektirir. Komut dosyasını `<httpPlatform>` *web.config*öğesinde belirtirsiniz, `processPath` öznitelik site uzantısının Python yorumlayıcısına `arguments` ve öznitelik komut dosyanıza ve sağlamak istediğiniz bağımsız değişkenlere işaret eder:

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

Burada `HTTP_PLATFORM_PORT` gösterilen ortam değişkeni, yerel sunucunuzun localhost'tan gelen bağlantılar için dinlemesi gereken bağlantı noktasını içerir. Bu örnek, bu durumda, `SERVER_PORT`istenirse başka bir ortam değişkeninin nasıl oluşturulacak olduğunu da gösterir.

### <a name="configure-the-fastcgi-handler"></a>FastCGI işleyicisini yapılandırın

FastCGI istek düzeyinde çalışan bir arayüzdür. IIS gelen bağlantıları alır ve her isteği bir veya daha fazla kalıcı Python işlemlerinde çalışan bir WSGI uygulamasına iletir.

Kullanmak için, ilk yüklemek ve [pypi.org/project/wfastcgi/](https://pypi.io/project/wfastcgi)açıklandığı gibi wfastcgi paketi yapılandırmak.

Ardından, uygulamanızın *web.config* dosyasını *python.exe* ve *wfastcgi.py* için tam `PythonHandler` yolları içerecek şekilde değiştirin. Aşağıdaki adımlar Python'un *c:\python36-32'de* yüklü olduğunu ve uygulama kodunuzc:\home\site\wwwroot; *c:\home\site\wwwroot* yollarınız için buna göre ayarlayın:

1. `PythonHandler` *Web.config'deki* girişi, yolun Python yükleme konumuyla eşleşerek değiştirin (tam ayrıntılar için [IIS Configuration Reference](https://www.iis.net/configreference) (iis.net) adresine bakın).

    ```xml
    <system.webServer>
      <handlers>
        <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
            scriptProcessor="c:\python36-32\python.exe|c:\python36-32\wfastcgi.py"
            resourceType="Unspecified" requireAccess="Script"/>
      </handlers>
    </system.webServer>
    ```

1. `<appSettings>` *web.config*bölümünde , için `WSGI_HANDLER`anahtar `WSGI_LOG` ekle , `PYTHONPATH`(isteğe bağlı) ve:

    ```xml
    <appSettings>
      <add key="PYTHONPATH" value="c:\home\site\wwwroot"/>
      <!-- The handler here is specific to Bottle; see the next section. -->
      <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
      <add key="WSGI_LOG" value="c:\home\LogFiles\wfastcgi.log"/>
    </appSettings>
    ```

    Bu `<appSettings>` değerler uygulamanız için ortam değişkenleri olarak kullanılabilir:

    - Değer `PYTHONPATH` serbestçe uzatılabilir, ancak uygulamanızın kökünü içermelidir.
    - `WSGI_HANDLER`uygulamanızdan içe aktarılabilir bir WSGI uygulamasına işaret etmelidir.
    - `WSGI_LOG`isteğe bağlıdır, ancak uygulamanızın hata ayıklanması için önerilir.

1. `WSGI_HANDLER` *web.config'deki* girişi kullandığınız çerçeveye uygun olarak ayarlayın:

    - **Şişe**: Aşağıda gösterildiği gibi sonra `app.wsgi_app` parantez olduğundan emin olun. Bu nesne bir değişken yerine bir işlev *(bkz. app.py)* olduğundan gereklidir:

        ```xml
        <!-- Bottle apps only -->
        <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
        ```

    - **Şişe**: Projenizin `<project_name>.app` `<project_name>` adı ile `WSGI_HANDLER` eşleşen değeri değiştirin. Runserver.py'daki ifadeye bakarak tam `from <project_name> import app` *tanımlayıcıyı*bulabilirsiniz. Örneğin, proje "FlaskAzurePublishExample" olarak adlandırılırsa, giriş aşağıdaki gibi görünür:

        ```xml
        <!-- Flask apps only: change the project name to match your app -->
        <add key="WSGI_HANDLER" value="flask_iis_example.app"/>
        ```

    - **Django : Django**projeleri için *web.config* için iki değişiklik gereklidir. İlk olarak, `WSGI_HANDLER` değeri `django.core.wsgi.get_wsgi_application()` değiştirin (nesne *wsgi.py* dosyasındadır):

        ```xml
        <!-- Django apps only -->
        <add key="WSGI_HANDLER" value="django.core.wsgi.get_wsgi_application()"/>
        ```

        İkinci olarak, projenizin `WSGI_HANDLER`adı ile `DjangoAzurePublishExample` değiştirerek aşağıdaki girişi ekleyin:

        ```xml
        <add key="DJANGO_SETTINGS_MODULE" value="django_iis_example.settings" />
        ```

1. **Yalnızca Django uygulamaları : Django**projesinin *settings.py* dosyasında, sitenizin `ALLOWED_HOSTS` URL etki alanını veya IP adresini aşağıda gösterildiği gibi ekleyin ve '1.2.3.4'ü URL veya IP adresinizle değiştirin:

    ```python
    # Change the URL or IP address to your specific site
    ALLOWED_HOSTS = ['1.2.3.4']
    ```

    Url'nizi diziye ekleyememesi, **DisallowedHost hata / Geçersiz HTTP_HOST\<üstbilgi: ' site URL'si\>'. ALLOWED_HOSTS '\<site\>URL'si ' eklemeniz gerekebilir.**

    Dizi boşolduğunda, Django'nun otomatik olarak 'localhost' ve '127.0.0.1' izin verdiğini, ancak üretim URL'nizi eklemenin bu özellikleri kaldırdığını unutmayın. Bu nedenle, *settings.py*ayrı geliştirme ve üretim kopyalarını korumak veya çalışma süresi değerlerini denetlemek için ortam değişkenlerini kullanmak isteyebilirsiniz.

## <a name="deploy-to-iis-or-a-windows-vm"></a>IIS'ye veya Windows VM'ye dağıtma

Projenizdeki doğru *web.config* dosyası yla, **Solution Explorer'da**projenin bağlam menüsünde **Yayımla** komutunu kullanarak ve seçenek, **IIS, FTP, vb.** seçerek IIS çalıştıran bilgisayara yayımlayabilirsiniz. Bu durumda, Visual Studio sadece sunucuya proje dosyalarını kopyalar; tüm sunucu tarafı yapılandırmadan siz sorumlusunuz.
