---
title: Python'Azure App Service yapılandırma (Windows)
description: Python yorumlayıcısını ve kitaplıklarını Azure App Service ve web uygulamalarını bu yorumlayıcıya düzgün bir şekilde başvurarak yapılandırma.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f72607373f942f111f9e077156d7c100e81fb2b0
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431087"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Azure App Service'da Python ortamı ayarlama (Windows)

> [!Important]
> Microsoft, bu makalede açıklandığı gibi App Service'Windows için Python uzantılarını [Linux üzerinde App Service.](publishing-python-web-applications-to-azure-from-visual-studio.md)

[Azure App Service,](https://azure.microsoft.com/services/app-service/) web uygulamalarına bir tarayıcı üzerinden erişilen siteler, kendi istemcileriniz tarafından kullanılan REST API'leri veya olay tarafından tetiklenen işlemler için bir hizmet olarak platform teklifidir. App Service uygulama uygulamak için Python kullanmayı tam olarak destekler.

Her biri Python çalışma zamanının Azure App Service sürümünü içeren bir App Service *site* uzantıları kümesi olarak özelleştirilebilir Python desteği sağlanır. Daha sonra, bu makalede açıklandığı gibi istenen paketleri doğrudan bu ortama yükleyebilirsiniz. Uygulamanın kendisinde App Service özelleştirerek, paketleri web uygulaması projelerinize korumanız veya uygulama koduyla karşıya yüklemeniz gerek yoktur.

::: moniker range="<=vs-2017"
> [!Tip]
> App Service sunucu üzerinde kök klasörlerde varsayılan olarak Python 2.7 ve Python 3.4 yüklü olsa da, bu ortamlarda paketleri özelleştireye veya yüke yükeyesiniz ve bunların varlığına bağlı olamazsınız. Bunun yerine, bu makalede açıklandığı gibi, denetiminiz olan bir site uzantısına güvenebilirsiniz.
::: moniker-end

## <a name="choose-a-python-version-through-the-azure-portal"></a>Python sürümünü Azure portal

1. Web App Service için yeni bir uygulama Azure portal.
1. Uygulamanın App Service, Geliştirme Araçları bölümüne kaydırın, Uzantılar'ı ve ardından + Ekle'yi **seçin.**  
1. Listede aşağı kaydırarak istediğiniz Python sürümünü içeren uzantıya kaydırın:

    ![Azure portal Python uzantılarını gösteren dosya](media/python-on-azure-extensions.png)

    > [!Tip]
    > Python'ın daha eski bir sürümüne ihtiyacınız varsa ve site uzantılarında listelenmiş olarak görmüyorsanız, sonraki bölümde açıklandığı gibi Azure Resource Manager uygulama aracılığıyla yine de yükleyebilirsiniz.

1. Uzantıyı seçin, yasal koşulları kabul eder ve tamam'ı **seçin.**
1. Yükleme tamamlandığında portalda bir bildirim görüntülenir.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Python sürümünü Azure Resource Manager

Azure Resource Manager şablonuyla bir App Service dağıtıyorsanız, site uzantısını kaynak olarak ekleyin. Özellikle uzantı türüne sahip iç içe kaynak (altındaki `resources` `resources` nesne) olarak `siteextensions` görünür.

Örneğin, bir başvuru `python361x64` ekledikten sonra (Python 3.6.1 x64), şablonunuz aşağıdaki gibi olabilir (bazı özellikler atlanmıştır):

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

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>Python web.config işaret etmek için kümeyi ayarlama

Site uzantısını yükledikten sonra (portaldan veya Azure Resource Manager şablondan) sonra,  uygulamanınweb.configPython yorumlayıcıya işaret edersiniz. web.config dosyası, App Service üzerinde çalışan IIS (7+) web sunucusuna HttpPlatform (önerilen) veya FastCGI aracılığıyla Python isteklerini nasıl işlemesi gerektiği hakkında bilgi verir.

Site uzantısının dosyanın tam yolunu bularak *python.exe,* ardından uygunweb.config *oluşturun.*

### <a name="find-the-path-to-pythonexe"></a>Dosyanın yolunu python.exe

Python site uzantısı, sunucuya *d:\home* altındaki Python sürümüne ve mimarisine uygun bir klasöre yüklenir (birkaç eski sürüm dışında). Örneğin, Python 3.6.1 x64 *d:\home\python361x64 dizinine yüklenir.* Python yorumlayıcının tam yolu daha *sonra* d:\home\python361x64\python.exe.

Dosyanız üzerinde belirli bir yolu App Service  için, App Service sayfasında Uzantılar'ı seçin ve sonra listeden uzantıyı seçin.

![Azure App Service'da uzantı listesi](media/python-on-azure-extension-list.png)

Bu eylem, uzantının yolu içeren açıklama sayfasını açar:

![Uzantı ayrıntıları Azure App Service](media/python-on-azure-extension-detail.png)

Uzantının yolunu görme konusunda sorun varsa konsolunu kullanarak el ile bulabilirsiniz:

1. Geliştirme App Service Geliştirme Araçları **Konsolu'nu**  >  **seçin.**
1. `ls ../home` `dir ..\home` *Python361x64* gibi üst düzey uzantı klasörlerini görmek için veya komutunu girin.
1. Dosya ve diğer `ls ../home/python361x64` yorumlayıcı `dir ..\home\python361x64` dosyalarını içerdiğini doğrulamak *python.exe* veya gibi bir komut girin.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyicisini yapılandırma

HttpPlatform modülü yuva bağlantılarını doğrudan tek başına bir Python sürecine iletir. Bu geçiş, sizin gibi herhangi bir web sunucusunu çalıştırmaya olanak sağlar, ancak yerel bir web sunucusu çalıştıran bir başlangıç betiği gerektirir. Betiği, özniteliğin site uzantısının Python yorumlayıcıya, özniteliğin de betiğinize ve sağlamak istediğiniz bağımsız değişkenlere sahip olduğuweb.config`<httpPlatform>` ** `processPath` `arguments` öğesinde belirtirsiniz:

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

Burada `HTTP_PLATFORM_PORT` gösterilen ortam değişkeni, yerel sunucunuz tarafından localhost'tan gelen bağlantılar için dinlemesi gereken bağlantı noktasını içerir. Bu örnekte ayrıca, bu örnekte istenirse başka bir ortam değişkeninin nasıl oluşturulacakları da `SERVER_PORT` gösterir.

### <a name="configure-the-fastcgi-handler"></a>FastCGI işleyicisini yapılandırma

FastCGI, istek düzeyinde çalışan bir arabirimdir. IIS gelen bağlantıları alır ve her isteği bir veya daha fazla kalıcı Python işlemi içinde çalışan bir WSGI uygulamasına iletir. [wfastcgi](https://pypi.io/project/wfastcgi) paketi önceden yüklenmiş ve her Python site uzantısıyla yapılandırılmıştır, bu nedenle Kodu Bottle çerçevesini temel alan bir web uygulaması için aşağıda gösterilene benzer şekilde *web.config'a* dahil edebilirsiniz. python.exeve *wfastcgi.py* tam *yollarının* anahtara yerleştiril olduğunu `PythonHandler` unutmayın:

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

Burada `<appSettings>` tanımlanan, uygulamanıza ortam değişkenleri olarak kullanılabilir:

- değeri `PYTHONPATH` serbestçe genişletilmiş olabilir, ancak uygulamanın kökünü içermesi gerekir.
- `WSGI_HANDLER` , uygulamanıza aktarılabilir bir WSGI uygulamasına işaret etmek zorunda.
- `WSGI_LOG` isteğe bağlıdır, ancak uygulama hata ayıklaması için önerilir.

Bottle, Flask ve Django web *web.config* içeriği hakkında ek ayrıntılar için bkz. [Azure'da](publishing-python-web-applications-to-azure-from-visual-studio.md) yayımlama.

## <a name="install-packages"></a>Paketleri yükleme

Bir site uzantısı aracılığıyla yüklenmiş olan Python yorumlayıcı, Python ortamının yalnızca bir parçasıdır. Büyük olasılıkla bu ortama farklı paketler de yüklemeniz gerekir.

Paketleri doğrudan sunucu ortamına yüklemek için aşağıdaki yöntemlerden birini kullanın:

| Yöntemler | Kullanım |
| --- | --- |
| [Azure App Service Kudu konsolu](#azure-app-service-kudu-console) | Paketleri etkileşimli olarak yükleme. Paketler saf Python olmalı veya tekerlek yayımlamalı. |
| [Kudu REST API](#kudu-rest-api) | Paket yüklemesini otomatikleştirmek için kullanılabilir.  Paketler saf Python olmalı veya tekerlek yayımlamalı. |
| Uygulama ile paketle | Paketleri doğrudan projenize yükleyin ve ardından App Service parçası gibi uygulamanıza dağıtın. Kaç bağımlılığınız olduğu ve bunları ne sıklıkta güncelleştiriyorsanız, bu yöntem çalışan bir dağıtımın devam etmek için en kolay yolu olabilir. Kitaplıkların sunucu üzerinde Python sürümüyle eşleşmesi gerektiğini, aksi takdirde dağıtımdan sonra belirsiz hatalar göreceğiniz önerilir. Ancak, App Service site uzantılarında Python sürümleri, python.org sürümünde yayımlanan sürümlerle tam olarak aynı olduğundan, yerel geliştirme için kolayca uyumlu bir sürüm elde edebilirsiniz. |
| Sanal ortamlar | Desteklenmez. Bunun yerine, paketleme kullanın ve `PYTHONPATH` ortam değişkenlerini paketlerin konumunu işaret edecek şekilde ayarlayın. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service Kudu konsolu

[Kudu konsolu,](https://github.com/projectkudu/kudu/wiki/Kudu-console) App Service sunucusuna ve dosya sistemine doğrudan, yükseltilmiş komut satırı erişimi verir. Bu hem değerli bir hata ayıklama aracıdır hem de paketleri yükleme gibi CLI işlemlerine olanak sağlar.

1. Geliştirme Araçları Gelişmiş Araçlar'App Service'yi ve Azure portal'yi seçerek  >  kudu'ya **tıklayın.** Bu eylem, eklenenler dışında temel url'niz ile aynı App Service URL'ye `.scm` gidin. Örneğin, temel URL'niz `https://vspython-test.azurewebsites.net/` Kudu'nun `https://vspython-test.scm.azurewebsites.net/` üzerindedir (yer işareti ebilirsiniz):

    ![Azure App Service için Kudu konsolu](media/python-on-azure-console01.png)

1. Konsolu **açmak için Hata** ayıklama konsolu CMD'sini seçin. Burada Python yüklemenize gidin ve hangi  >   kitaplıkların zaten orada olduğunu göreceksiniz.

1. Tek bir paket yüklemek için:

    a. Paketi yüklemek istediğiniz Python yüklemesi klasörüne gidin, *örneğin: d:\home\python361x64.*

    b. Paket `python.exe -m pip install <package_name>` yüklemek için kullanın.

    ![Kudu konsolu üzerinden performans yükleme örneği Azure App Service](media/python-on-azure-console02.png)

1. Sunucunuza uygulamanıza önceden *requirements.txt* bir uygulama dağıttıysanız, bu gereksinimlerin hepsini aşağıdaki gibi yükleyin:

    a. Paketi yüklemek istediğiniz Python yüklemesi klasörüne gidin, *örneğin: d:\home\python361x64.*

    b. `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` komutunu çalıştırın.

    Tam *requirements.txt* kümenizi hem yerel olarak hem de sunucuda yeniden oluşturmak kolay olduğundanrequirements.txtkullanılması önerilir. Konsolda yapılan değişiklikleri dağıtarak konsolunu  ziyaretrequirements.txtkomutu yeniden çalıştırmayı unutmayın.

> [!Note]
> Derlemede C derleyicisi App Service, bu nedenle yerel uzantı modüllerine sahip tüm paketler için tekerleği yüklemeniz gerekir. Birçok popüler paket kendi tekerleklerini sağlar. Kullanmayan paketler için yerel geliştirme `pip wheel <package_name>` bilgisayarınızda kullanın ve tekerleği sitenize yükleyin. Bir örnek için, [bkz. Manage required packages with requirements.txt. ](managing-required-packages-with-requirements-txt.md)

### <a name="kudu-rest-api"></a>Kudu REST API

Azure portal aracılığıyla kudu konsolunu kullanmak yerine, komutu ' e göndererek kudu REST API aracılığıyla komutları uzaktan çalıştırabilirsiniz `https://yoursite.scm.azurewebsites.net/api/command` . Örneğin, paketini yüklemek için `bottle` AŞAĞıDAKI JSON 'ı öğesine gönderin `/api/command` :

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Komutlar ve kimlik doğrulama hakkında daha fazla bilgi için bkz. [kudu belgeleri](https://github.com/projectkudu/kudu/wiki/REST-API).

Ayrıca, `az webapp deployment list-publishing-profiles` Azure CLI aracılığıyla komutunu kullanarak kimlik bilgilerini görebilirsiniz (bkz. [az WebApp Deployment](/cli/azure/webapp/deployment?view=azure-cli-latest&preserve-view=true#az-webapp-deployment-list-publishing-profiles)). Kudu komutlarının nakledileceği bir yardımcı Kitaplık [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42)kullanılabilir.
