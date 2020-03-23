---
title: Azure Uygulama Hizmetinde Python'u Yapılandırma (Windows)
description: Azure Uygulama Hizmeti'ne Python yorumlayıcısı ve kitaplıkları nasıl yüklenir ve web uygulamalarını bu yorumculu yorumlayıcıya düzgün bir şekilde yönlendirecek şekilde yapılandırma.
ms.date: 01/07/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 7ffe0de939eba8af38c132fc3de5c96a9499e3f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535988"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Azure Uygulama Hizmeti'nde (Windows) Python ortamı nasıl ayarlanır?

> [!Important]
> Microsoft, [Linux'ta App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)doğrudan dağıtım lehine bu makalede açıklandığı gibi Windows App Service için Python uzantıları küçümsülvardır.

[Azure Uygulama Hizmeti,](https://azure.microsoft.com/services/app-service/) ister bir tarayıcı üzerinden erişilen siteler olsun, ister kendi istemcileriniz tarafından kullanılan REST API'leri veya olay tetikleyici işlemler olsun, web uygulamaları için hizmet olarak platform olarak bir tekliftir. Uygulama Hizmeti, uygulamaları uygulamak için Python'u kullanmayı tamamen destekler.

Azure Uygulama Hizmeti için özelleştirilebilir Python desteği, her biri Python çalışma zamanının belirli bir sürümünü içeren bir Uygulama Hizmeti *sitesi uzantısı* kümesi olarak sağlanır. Daha sonra, bu makalede açıklandığı gibi, istenen paketleri doğrudan bu ortama yükleyebilirsiniz. Uygulama Hizmeti'ndeki ortamı özelleştirerek, web uygulaması projelerinizdeki paketleri korumanız veya uygulama koduyla yüklemeniz gerekmez.

> [!Tip]
> Uygulama Hizmeti varsayılan olarak Sunucudaki kök klasörlere Yüklü Python 2.7 ve Python 3.4'e sahip olsa da, bu ortamlarda paketleri özelleştiremez veya yükleyemezsiniz ve bunların varlığına bağlı olamazsınız. Bunun yerine, bu makalede açıklandığı gibi, denetlediğiniz bir site uzantısı na güvenmeniz gerekir.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Azure portalı üzerinden bir Python sürümü seçin

1. Azure portalında web uygulamanız için bir Uygulama Hizmeti oluşturun.
1. Uygulama Hizmeti'nin sayfasında, Geliştirme **Araçları** bölümüne gidin, **Uzantılar'ı**seçin, ardından **+ Ekle'yi**seçin.
1. Listede aşağı doğru istediğiniz Python sürümünü içeren uzantıya gidin:

    ![Python uzantılarını gösteren azure portalı](media/python-on-azure-extensions.png)

    > [!Tip]
    > Python'un eski bir sürümüne ihtiyacınız varsa ve site uzantılarında listelenmezseniz, bir sonraki bölümde açıklandığı gibi Azure Kaynak Yöneticisi aracılığıyla yüklemeye devam edebilirsiniz.

1. Uzantıyı seçin, yasal koşulları kabul edin ve sonra **Tamam'ı**seçin.
1. Yükleme tamamlandığında portalda bir bildirim görüntülenir.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Azure Kaynak Yöneticisi aracılığıyla bir Python sürümü seçin

Azure Kaynak Yöneticisi şablonuyla bir Uygulama Hizmeti dağıtıyorsanız, site uzantısını kaynak olarak ekleyin. Özellikle, uzantı, [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22)türü `siteextensions` ve `resources` adı `resources`ile iç içe bir kaynak (altında bir nesne) olarak görünür.

Örneğin, `python361x64` (Python 3.6.1 x64) bir başvuru ekledikten sonra, şablonunuzun aşağıdaki gibi görünebilir (bazı özellikler atlanmıştır):

```json
"resources": [
  {
    "apiVersion": "2015-08-01",
    "name": "[parameters('siteName')]",
    "type": "Microsoft.Web/sites",

    // ...

    "resources": [
      {
        "apiVersion": "2015-08-01",
        "name": "python361x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
          "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
      },
      // ...
    ]
  }
```

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Python yorumlayıcısını işaret etmek için web.config'i ayarlayın

Site uzantısını yükledikten sonra (portal veya Azure Kaynak Yöneticisi şablonu aracılığıyla), uygulamanızın *web.config* dosyasını Python yorumlayıcısına yönlendirin. *web.config* dosyası, App Service'te çalışan IIS (7+) web sunucusuna Python isteklerini HttpPlatform (önerilir) veya FastCGI aracılığıyla nasıl işlemesi gerektiği konusunda talimat verir.

Site uzantısı *python.exe*için tam yol bularak başlayın, sonra oluşturmak ve uygun *web.config* dosyası değiştirin.

### <a name="find-the-path-to-pythonexe"></a>python.exe yolunu bul

Python site uzantısı *d:\home* altında sunucuda Python sürümü ve mimarisine uygun bir klasörde yüklenir (birkaç eski sürümler hariç). Örneğin, Python 3.6.1 x64 *d:\home\python361x64*yüklenir. Python yorumlayıcısına giden tam yol *d:\home\python361x64\python.exe*' dir.

Uygulama Hizmetinizde belirli yolu görmek için, App Service **sayfasındaki Uzanlar'ı** seçin ve ardından listedeki uzantıyı seçin.

![Azure Uygulama Hizmeti'ndeki uzantı listesi](media/python-on-azure-extension-list.png)

Bu eylem, uzantın yolu içeren açıklama sayfasını açar:

![Azure Uygulama Hizmeti'nde uzantı ayrıntıları](media/python-on-azure-extension-detail.png)

Uzantınca yolunu görmekte sorun yaşıyorsanız, konsolu kullanarak el ile bulabilirsiniz:

1. Uygulama Hizmeti sayfanızda **Geliştirme Araçları** > **Konsolu'nu**seçin.
1. Komutu `ls ../home` girin `dir ..\home` veya *Python361x64*gibi üst düzey uzantıları klasörlerini görmek için.
1. *Python.exe* `dir ..\home\python361x64` ve diğer yorumlayıcı dosyaları içerdiğini doğrulamak için bir `ls ../home/python361x64` komut girin.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyicisini yapılandırma

HttpPlatform modülü soket bağlantılarını doğrudan bağımsız bir Python işlemine geçirir. Bu geçiş, istediğiniz herhangi bir web sunucusunu çalıştırmanızı sağlar, ancak yerel bir web sunucusu çalıştıran bir başlangıç komut dosyası gerektirir. Komut dosyasını `<httpPlatform>` *web.config*öğesinde belirtirsiniz, `processPath` öznitelik site uzantısının Python yorumlayıcısına `arguments` ve öznitelik komut dosyanıza ve sağlamak istediğiniz bağımsız değişkenlere işaret eder:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
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

FastCGI istek düzeyinde çalışan bir arayüzdür. IIS gelen bağlantıları alır ve her isteği bir veya daha fazla kalıcı Python işlemlerinde çalışan bir WSGI uygulamasına iletir. [Wfastcgi paketi](https://pypi.io/project/wfastcgi) önceden yüklenmiş ve her Python site uzantısı ile yapılandırılmış, böylece kolayca *web.config* şişe çerçevedayalı bir web uygulaması için aşağıda gösterilen gibi kodu ekleyerek etkinleştirebilirsiniz. *Python.exe* ve *wfastcgi.py* için tam yolların `PythonHandler` anahtara yerleştirildiğini unutmayın:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <!-- The handler here is specific to Bottle; other frameworks vary. -->
    <add key="WSGI_HANDLER" value="app.wsgi_app()"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule"
           scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py"
           resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Burada `<appSettings>` tanımlanan ortam değişkenleri olarak uygulamanız için kullanılabilir:

- Değer `PYTHONPATH` serbestçe uzatılabilir, ancak uygulamanızın kökünü içermelidir.
- `WSGI_HANDLER`uygulamanızdan içe aktarılabilir bir WSGI uygulamasına işaret etmelidir.
- `WSGI_LOG`isteğe bağlıdır, ancak uygulamanızın hata ayıklanması için önerilir.

Şişe, Flask ve Django web uygulamaları için *web.config* içerikleri hakkında ek ayrıntılar için [Azure'a Yayımla'ya](publishing-python-web-applications-to-azure-from-visual-studio.md) bakın.

## <a name="install-packages"></a>Paketleri yükleme

Site uzantısı üzerinden yüklenen Python yorumlayıcısı Python ortamınızın yalnızca bir parçasıdır. Büyük olasılıkla bu ortamda da farklı paketler yüklemeniz gerekir.

Paketleri doğrudan sunucu ortamına yüklemek için aşağıdaki yöntemlerden birini kullanın:

| Yöntemler | Kullanım |
| --- | --- |
| [Azure App Service Kudu konsolu](#azure-app-service-kudu-console) | Paketleri etkileşimli olarak yükler. Paketler saf Python olmalı veya tekerlekleri yayımlamalıdır. |
| [Kudu REST API](#kudu-rest-api) | Paket yüklemesini otomatikleştirmek için kullanılabilir.  Paketler saf Python olmalı veya tekerlekleri yayımlamalıdır. |
| Uygulama yla paketle | Paketleri doğrudan projenize yükleyin ve uygulamanızın bir parçasıymış gibi Uygulama Hizmeti'ne dağıtın. Kaç tane bağımlılığınız olduğu ve bunları ne sıklıkta güncelleştirdiğinize bağlı olarak, bu yöntem çalışma dağıtımını başlatmanın en kolay yolu olabilir. Kitaplıkların sunucudaki Python sürümüyle eşleşmesi gerektiğini, aksi takdirde dağıtımdan sonra belirsiz hatalar gördüğünüzü unutmayın. Bununla ilgili olarak, Python'un App Service site uzantılarındaki sürümleri python.org'da yayımlanan sürümlerle tamamen aynı olduğundan, yerel geliştirme için uyumlu bir sürümünü kolayca edinebilirsiniz. |
| Sanal ortamlar | Desteklenmiyor. Bunun yerine, bundling `PYTHONPATH` kullanın ve paketlerin konumuna işaret etmek için ortam değişkenini ayarlayın. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service Kudu konsolu

[Kudu konsolu,](https://github.com/projectkudu/kudu/wiki/Kudu-console) App Service sunucusuna ve dosya sistemine doğrudan ve yüksek komut satırı erişimi sağlar. Bu hem değerli bir hata ayıklama aracıdır hem de paketleri yüklemek gibi CLI işlemlerine olanak tanır.

1. Geliştirme Araçları > **Gelişmiş** **Araçları'nı**seçerek Azure portalındaki Uygulama Hizmeti sayfanızdan Kudu'yu açın ve ardından **Git'i**seçin. Bu eylem, `.scm` eklenen ler dışında temel Uygulama Hizmeti URL'nizle aynı olan bir URL'ye yönlendirilir. Örneğin, temel URL'niz `https://vspython-test.azurewebsites.net/` Kudu'daysa `https://vspython-test.scm.azurewebsites.net/` (yer imi yapabilirsiniz):

    ![Azure Uygulama Hizmeti için Kudu konsolu](media/python-on-azure-console01.png)

1. Python yüklemenize girebileceğiniz ve hangi kitaplıkların zaten orada olduğunu görebileceğiniz konsolu açmak için **Hata Ayıklama konsolu** > **CMD'yi** seçin.

1. Tek bir paket yüklemek için:

    a. Paketi yüklemek istediğiniz Python yüklemeklasörüne gidin, örneğin *d:\home\python361x64*.

    b. Paketi `python.exe -m pip install <package_name>` yüklemek için kullanın.

    ![Azure Uygulama Hizmeti için Kudu konsolundan şişe yükleme örneği](media/python-on-azure-console02.png)

1. Uygulamanız için bir *gereksinim.txt'yi* sunucuya zaten dağıttıysanız, tüm bu gereksinimleri aşağıdaki gibi yükleyin:

    a. Paketi yüklemek istediğiniz Python yüklemeklasörüne gidin, örneğin *d:\home\python361x64*.

    b. `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` komutunu çalıştırın.

    Tam paket kümenizi hem yerel olarak hem de sunucuda yeniden oluşturmak kolay olduğundan *requirements.txt* kullanılması önerilir. *Gereksinimleri.txt* herhangi bir değişiklik dağıttıktan sonra konsolu ziyaret etmeyi unutmayın ve komutu yeniden çalıştırın.

> [!Note]
> App Service'te C derleyicisi bulunmadığından, yerel uzatma modüllerine sahip paketler için tekerleği yüklemeniz gerekir. Birçok popüler paketler kendi tekerlekleri sağlar. Kullanmayan paketler için, `pip wheel <package_name>` yerel geliştirme bilgisayarınızda kullanın ve ardından tekerleği sitenize yükleyin. Örneğin, [gereksinimlere sahip gerekli paketleri yönet'e bakın.txt](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Kudu REST API

Kudu konsolunu Azure portalı üzerinden kullanmak yerine, komutları Kudu REST API'ye `https://yoursite.scm.azurewebsites.net/api/command`göndererek uzaktan çalıştırabilirsiniz. Örneğin, `bottle` paketi yüklemek için aşağıdaki JSON'u şu şekilde `/api/command`gönderin:

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Komutlar ve kimlik doğrulama hakkında bilgi için [Kudu belgelerine](https://github.com/projectkudu/kudu/wiki/REST-API)bakın.

Azure CLI aracılığıyla `az webapp deployment list-publishing-profiles` komutu kullanarak kimlik bilgilerini de görebilirsiniz [(bkz. az webapp dağıtımı).](/cli/azure/webapp/deployment?view=azure-cli-latest#az-webapp-deployment-list-publishing-profiles) GitHub'da Kudu komutlarını deftere [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42)nakletmek için yardımcı kitaplık kullanılabilir.
