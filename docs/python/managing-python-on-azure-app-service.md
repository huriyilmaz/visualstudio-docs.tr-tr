---
title: Azure App Service (Windows) üzerinde Python yapılandırma
description: Azure App Service bir Python yorumlayıcı ve kitaplıklarını yüklemek ve Web uygulamalarını bu yorumlayıcıya doğru şekilde başvuracak şekilde yapılandırmak.
ms.date: 01/07/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f96e9123f613cf50eebbedd393f5bce9cfa633d2
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830675"
---
# <a name="how-to-set-up-a-python-environment-on-azure-app-service-windows"></a>Azure App Service (Windows) üzerinde Python ortamı ayarlama

> [!Important]
> Microsoft, [Linux üzerinde App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)doğrudan dağıtımı için bu makalede açıklandığı gibi Windows üzerinde App Service için Python uzantılarını kullanımdan kaldırılmıştır.

[Azure App Service](https://azure.microsoft.com/services/app-service/) Web uygulamalarına yönelik bir hizmet olarak platform sunumudur, bir tarayıcı aracılığıyla erişilen sitelere, kendi istemcileriniz tarafından kullanılan REST API 'lerine veya olay tarafından tetiklenen bir işleme sahip olsun. App Service, uygulamaları uygulamak için Python kullanmayı tamamen destekler.

Azure App Service için özelleştirilebilir Python desteği, her biri Python çalışma zamanının belirli bir sürümünü içeren bir App Service *site uzantıları* kümesi olarak sağlanır. Daha sonra istediğiniz paketleri bu makalede açıklandığı gibi doğrudan bu ortama yükleyebilirsiniz. App Service ortamı özelleştirilerek, Web uygulaması projelerinizde paketleri korumanıza veya uygulama kodu ile karşıya yüklemeye gerek kalmaz.

> [!Tip]
> App Service, varsayılan olarak, sunucudaki kök klasörlerde bulunan Python 2,7 ve Python 3,4 ' nin yanı sıra, bu ortamlarda paketleri özelleştiremez veya yükleyemez, ya da kendi varlığına bağlı olmanız gerekir. Bunun yerine, bu makalede açıklandığı gibi, denetlediğiniz bir site uzantısına güvenmelisiniz.

## <a name="choose-a-python-version-through-the-azure-portal"></a>Azure portal bir Python sürümü seçin

1. Azure portal web uygulamanız için bir App Service oluşturun.
1. App Service sayfasında, **geliştirme araçları** bölümüne gidin, **Uzantılar**' ı seçin ve **+ Ekle**' yi seçin.
1. Listede, istediğiniz Python sürümünü içeren uzantıya gidin:

    ![Python uzantılarını gösteren Azure portal](media/python-on-azure-extensions.png)

    > [!Tip]
    > Python 'un daha eski bir sürümüne ihtiyacınız varsa ve site uzantılarında listede görmüyorsanız, sonraki bölümde açıklandığı gibi Azure Resource Manager aracılığıyla da yükleyebilirsiniz.

1. Uzantıyı seçin, yasal koşulları kabul edin ve **Tamam**' ı seçin.
1. Yükleme tamamlandığında portalda bir bildirim görüntülenir.

## <a name="choose-a-python-version-through-the-azure-resource-manager"></a>Azure Resource Manager bir Python sürümü seçin

Bir Azure Resource Manager şablonuyla App Service dağıtıyorsanız, site uzantısını kaynak olarak ekleyin. Özellikle uzantı, `resources` `resources` türü `siteextensions` ve [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22)'dan adı ile iç içe geçmiş kaynak (altında bir nesne) olarak görünür.

Örneğin, bir başvuru eklendikten sonra `python361x64` (Python 3.6.1 x64), şablonunuz aşağıdaki gibi görünebilir (bazı özellikler atlandı):

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

## <a name="set-webconfig-to-point-to-the-python-interpreter"></a>web.config Python yorumlayıcıya işaret etmek için ayarla

Site uzantısını yükledikten sonra (portal veya bir Azure Resource Manager şablonu aracılığıyla), uygulamanızın *web.config* dosyasını Python Yorumlayıcısına işaret edersiniz. *web.config* dosyası, IIS (7 +) Web sunucusuna, bir httpplatform (önerilen) veya FastCGI aracılığıyla Python isteklerini nasıl işleyeceğine ilişkin App Service çalışır.

Site uzantısının *python.exe*tam yolunu bularak başlayın, sonra uygun *web.config* dosyasını oluşturun ve değiştirin.

### <a name="find-the-path-to-pythonexe"></a>python.exe yolunu bulun

Python sürümüne ve mimarisine (daha eski sürümlerin olması dışında) uygun bir klasörde *d:\home* altındaki sunucuya bir Python site uzantısı yüklenir. Örneğin, Python 3.6.1 x64, *d:\home\python361x64*' de yüklüdür. Python Yorumlayıcısına tam yol daha sonra *d:\home\python361x64\python.exe*.

App Service özel yolu görmek için App Service sayfasında **Uzantılar** ' ı seçin ve ardından listeden uzantıyı seçin.

![Azure App Service uzantı listesi](media/python-on-azure-extension-list.png)

Bu eylem, uzantının yolunu içeren Açıklama sayfasını açar:

![Azure App Service uzantı ayrıntıları](media/python-on-azure-extension-detail.png)

Uzantının yolunu görmekte sorun yaşıyorsanız, konsolunu kullanarak el ile bulabilirsiniz:

1. App Service sayfanızda **geliştirme araçları**  >  **konsolunu**seçin.
1. `ls ../home` `dir ..\home` *Python361x64*gibi en üst düzey uzantıları klasörlerini görmek için veya komutunu girin.
1. `ls ../home/python361x64` `dir ..\home\python361x64` *python.exe* ve diğer yorumlayıcı dosyalarını içerdiğini doğrulamak için veya gibi bir komut girin.

### <a name="configure-the-httpplatform-handler"></a>HttpPlatform işleyicisini yapılandırma

HttpPlatform modülü, yuva bağlantılarını doğrudan bir tek başına Python işlemine geçirir. Bu geçiş, istediğiniz herhangi bir Web sunucusunu çalıştırmanıza izin verir, ancak yerel bir Web sunucusu çalıştıran bir başlatma betiği gerektirir. Komut dosyasını `<httpPlatform>` *web.config*öğesinde belirtirsiniz; burada `processPath` öznitelik, site uzantısının Python yorumlayıcısını ve `arguments` özniteliği, betiğinizi ve sağlamak istediğiniz bağımsız değişkeni gösterir:

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

`HTTP_PLATFORM_PORT`Burada gösterilen ortam değişkeni, yerel sunucunuzun localhost bağlantıları için dinlemesi gereken bağlantı noktasını içerir. Bu örnek ayrıca, isterseniz başka bir ortam değişkeninin nasıl oluşturulacağını gösterir `SERVER_PORT` .

### <a name="configure-the-fastcgi-handler"></a>FastCGI işleyicisini yapılandırma

FastCGI, istek düzeyinde çalışacak bir arabirimdir. IIS, gelen bağlantıları alır ve her isteği bir veya daha fazla kalıcı Python işlemde çalışan bir WSGI uygulamasına iletir. [Wfastcgı paketi](https://pypi.io/project/wfastcgi) , her Python site uzantısıyla önceden yüklenmiş ve yapılandırılmış olduğundan, bu kodu, şişe çerçevesini temel alan bir Web uygulaması için aşağıda gösterildiği gibi *web.config* dahil ederek kolayca etkinleştirebilirsiniz. *python.exe* ve *wfastcgi.py* için tam yolların anahtara yerleştirileceğini unutmayın `PythonHandler` :

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

`<appSettings>`Burada tanımlanan, uygulamanız için ortam değişkenleri olarak kullanılabilir:

- Değeri, `PYTHONPATH` ücretsiz olarak genişletilebilir, ancak uygulamanızın kökünü içermelidir.
- `WSGI_HANDLER` uygulamanızdan bir WSGI uygulaması Importable öğesine işaret etmelidir.
- `WSGI_LOG` isteğe bağlıdır, ancak uygulamanızda hata ayıklama için önerilir.

Şişe, Flask ve Docgo Web uygulamaları için *web.config* içeriğiyle ilgili ek ayrıntılar için bkz. [Azure 'da yayımlama](publishing-python-web-applications-to-azure-from-visual-studio.md) .

## <a name="install-packages"></a>Paketleri yükler

Bir site uzantısı aracılığıyla yüklenen Python yorumlayıcı, Python ortamınızın yalnızca bir parçasıdır. Muhtemelen bu ortama farklı paketler de yüklemeniz gerekir.

Paketleri doğrudan sunucu ortamına yüklemek için aşağıdaki yöntemlerden birini kullanın:

| Yöntemler | Kullanım |
| --- | --- |
| [Azure App Service kudu konsolu](#azure-app-service-kudu-console) | Paketleri etkileşimli olarak kurar. Paketler saf Python olmalıdır veya tekerlek yayımlamalıdır. |
| [Kudu REST API](#kudu-rest-api) | Paket yüklemesini otomatik hale getirmek için kullanılabilir.  Paketler saf Python olmalıdır veya tekerlek yayımlamalıdır. |
| Uygulama ile paket | Paketleri doğrudan projenize yükleyip uygulamanızın bir parçası gibi App Service dağıtın. Sahip olduğunuz bağımlılıklara ve bunları ne sıklıkta güncelleştirdiğinize bağlı olarak, bu yöntem, çalışan bir dağıtımı almanın en kolay yolu olabilir. Kitaplıkların, sunucudaki Python sürümüyle eşleşmesi gerekir, aksi takdirde dağıtımdan sonra hataları görmeniz önerilir. Bu, App Service site uzantılarında Python 'un sürümleri python.org ' de yayımlanan sürümlerle tamamen aynı olduğundan, yerel geliştirme için uyumlu bir sürümü kolayca edinebilirsiniz. |
| Sanal ortamlar | Desteklenmez. Bunun yerine, paketlemeyi kullanın ve `PYTHONPATH` ortam değişkenini paketlerin konumunu işaret etmek üzere ayarlayın. |

### <a name="azure-app-service-kudu-console"></a>Azure App Service kudu konsolu

[Kudu konsolu](https://github.com/projectkudu/kudu/wiki/Kudu-console) , App Service sunucusuna ve dosya sistemine doğrudan, yükseltilmiş komut satırı erişimi sağlar. Bu, her ikisi de değerli bir hata ayıklama aracıdır ve paketleri yükleme gibi CLı işlemlerine izin verir.

1. **Geliştirme araçları**  >  **Gelişmiş Araçlar**' ı seçip **Git**' i seçerek Azure Portal App Service sayfasından kudu 'yi açın. Bu eylem, eklenen ana App Service URL 'siyle aynı URL 'ye gider `.scm` . Örneğin, temel URL 'niz `https://vspython-test.azurewebsites.net/` daha sonra kudu açık ise `https://vspython-test.scm.azurewebsites.net/` (yer işareti yapabilirsiniz):

    ![Azure App Service için kudu konsolu](media/python-on-azure-console01.png)

1. Konsol cmd 'yi açmak için **hata ayıklama konsolu**  >  **cmd** ' yi seçin. buradan, Python yüklemenize gidebilir ve hangi kitaplıkların zaten orada olduğunu görebilirsiniz.

1. Tek bir paket yüklemek için:

    a. Paketi yüklemek istediğiniz *d:\home\python361x64*gibi Python yüklemesinin klasörüne gidin.

    b. `python.exe -m pip install <package_name>`Bir paket yüklemek için kullanın.

    ![Azure App Service için kudu konsolu aracılığıyla şişe yükleme örneği](media/python-on-azure-console02.png)

1. Uygulamanız için zaten sunucuya bir *requirements.txt* dağıttıysanız, bu gereksinimlerin tümünü aşağıdaki şekilde yükleyebilirsiniz:

    a. Paketi yüklemek istediğiniz *d:\home\python361x64*gibi Python yüklemesinin klasörüne gidin.

    b. `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt` komutunu çalıştırın.

    *requirements.txt* kullanmak önerilir, çünkü hem yerel olarak hem de sunucusunda tam paket kümesini yeniden oluşturmak kolaydır. *requirements.txt* değişiklik dağıttıktan sonra konsolu ziyaret etmeyi ve komutu yeniden çalıştırmayı unutmayın.

> [!Note]
> App Service hiç C derleyicisi yoktur, bu nedenle, yerel uzantı modülleriyle tüm paketler için tekerleği yüklemeniz gerekir. Birçok popüler paket kendi tekerlekleri sağlar. Olmayan paketler için, `pip wheel <package_name>` yerel geliştirme bilgisayarınızda öğesini kullanın ve ardından tekerleği sitenize yükleyin. Bir örnek için bkz. [requirements.txtgereken paketleri yönetme ](managing-required-packages-with-requirements-txt.md).

### <a name="kudu-rest-api"></a>Kudu REST API

Azure portal aracılığıyla kudu konsolunu kullanmak yerine, komutu ' e göndererek kudu REST API aracılığıyla komutları uzaktan çalıştırabilirsiniz `https://yoursite.scm.azurewebsites.net/api/command` . Örneğin, paketini yüklemek için `bottle` AŞAĞıDAKI JSON 'ı öğesine gönderin `/api/command` :

```json
{
    "command": 'python.exe -m pip install bottle',
    "dir": '\home\python361x64'
}
```

Komutlar ve kimlik doğrulama hakkında daha fazla bilgi için bkz. [kudu belgeleri](https://github.com/projectkudu/kudu/wiki/REST-API).

Ayrıca, `az webapp deployment list-publishing-profiles` Azure CLI aracılığıyla komutunu kullanarak kimlik bilgilerini görebilirsiniz (bkz. [az WebApp Deployment](/cli/azure/webapp/deployment?view=azure-cli-latest&preserve-view=true#az-webapp-deployment-list-publishing-profiles)). [GitHub](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42)'Da kudu komutlarının nakledilmesi için bir yardımcı kitaplık kullanılabilir.
