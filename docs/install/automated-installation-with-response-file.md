---
title: Yanıt dosyası ile yükleme işlemini otomatikleştirme
description: Uygulama yüklemenizi otomatikleştirmenize yardımcı olacak bir JSON yanıt Visual Studio öğrenin
ms.date: 12/7/2021
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8e24cd459c90da4b3ccd7c8e481071dad2268c88
ms.sourcegitcommit: 0f2af2f1a8cf0a481fd8f673accf3aebf2e262c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "134713674"
---
# <a name="programmatically-configure-default-settings-using-a-response-file"></a>Program aracılığıyla yanıt dosyası kullanarak varsayılan ayarları yapılandırma

Bu Visual Studio dosyası, içeriği komut satırı parametrelerini ve bağımsız değişkenlerini yansıtan bir [JSON](http://json-schema.org/) dosyasıdır. Yanıt dosyası, ürünün istemciye ilk yüklenmesi sırasında istemci ayarlarını başlatmak için kullanılır. 

## <a name="automate-installation"></a>Yüklemeyi otomatikleştirme
Aşağıdaki örnekte Visual Studio dağıtan yöneticiler parametresini kullanarak `--in` bir yanıt dosyası belirtebilirsiniz:

```shell
vs_enterprise.exe --in customInstall.json
```
## <a name="response-file-contents"></a>Yanıt dosyası içeriği
Yanıt dosyası komut satırı parametrelerini kapsüller ve şu genel kuralları izler:
 - Bir komut satırı parametresi bağımsız değişken (örneğin, , vb.) yer alıyorsa, yanıt dosyasındaki değer `--quiet` `--passive` true/false olmalıdır. 
 - Parametre bir bağımsız değişken (örneğin, ) alıyorsa, yanıt `--installPath <dir>` dosyasındaki değer bir dize olmalıdır. 
 - parametresi bir bağımsız değişken alır ve komut satırı üzerinde birden çok kez (örneğin, ) görünebilirse, yanıt dosyasındaki değer `--add <id>` bir dize dizisi olmalıdır.

Komut satırı üzerinde belirtilen parametreler, parametrelerin birden çok giriş almaları (örneğin, ) dışında yanıt dosyasına dahil edilen ayarları geçersiz `--add` kılar. Birden çok girişiniz olduğunda, komut satırına sağlanan girişler yanıt dosyasındaki ayarlarla birleştirilir.

## <a name="configure-the-response-file-used-with-network-layouts"></a>Ağ düzenleriyle kullanılan yanıt dosyasını yapılandırma
komutunu kullanarak bir ağ düzeni oluşturduysanız, düzen klasörünün kökünde ilk varsayılan `--layout` vanilla dosyası `response.json` oluşturulmuştu. Yöneticiler daha sonra bu dosyayı düzende değiştirerek istemcilerin bu düzende önyükleyiciyi çağırarak istemciye yükleme veya güncelleştirme Visual Studio `response.json` ayarlarını kontrol eder.

Dosyanın yapılandırma `response.json` ayarlarına yalnızca istemci düzende önyükleyiciyi kullandığında başvurulur ve kullanılır. `response.json`düzende, _istemci_ güncelleştirmeyi istemcide yerel olarak faturalamak için kullanılmaz.  

Yönetici kısmi bir düzen oluşturdu ise, varsayılan dosya yalnızca kısmi düzende yer `response.json` alan iş yüklerini ve dilleri belirtir. 

İstemci ilk yüklemeyi yaparken modun kullanılmamış olduğunu varsayıldığında, ilk yüklemeyi çalıştıran kullanıcılar içinde belirtilen varsayılanları geçersiz kabilir ve yükleme gerçekleştirmeden önce kurulum kullanıcı arabiriminde herhangi bir iş yükünü daha fazla seçerek veya seçimini `--quiet`  `response.json` kaldırabilir. Kullanıcı düzende mevcut olmayan bileşenleri veya iş yüklerini seçerse ve kanalURI'si Microsoft tarafından barındırılan sunucuların üzerine geliyorsa, Visual Studio kurulumu paketleri internetten elde etmeye `response.json` dener.

Bu Visual Studio düzen klasöründen çalıştırılırsa, _kurulum_ düzen `response.json` klasöründeki dosyayı otomatik olarak kullanır. seçeneğini kullanmak zorunda `--in` değildir.

> [!WARNING]
> Düzeni oluşturulduğunda tanımlanan içinde herhangi bir `response.json` özelliği silmeniz kritik öneme sahiptir. Değerleri değiştirebilirsiniz, ancak öğeleri kaldırasınız.

Bir düzende yer alan temel dosya, yüklemek istediğiniz ürün ve kanalın değerini içermesi dışında `response.json` aşağıdaki örnekteki gibi görünüyor olabilir:

::: moniker range="vs-2017"

```Default response.json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range="=vs-2019"

```Default response.json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range="=vs-2022"

```Default response.json for Current channel layout
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/17/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.17.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

```Default response.json for LTSC 17.0 channel layout
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/17/release.ltsc.17.0/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.17.Release.LTSC.17.0",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

Bir düzen oluşturulduğunda veya güncelleştiren bir response.template.json dosyası da oluşturulur.  Bu dosya, kullanılmaktadır tüm iş yükünü, bileşeni ve dil kimliklerini içerir.  Bu dosya, özel bir yüklemeye dahil edilecek her şey için bir şablon olarak sağlanır. Yöneticiler bu dosyayı özel yanıt dosyası için başlangıç noktası olarak kullanabilir. Yüklemek istemeyebilirsiniz şeyler için kimlikleri kaldırmanız ve dosyaya veya kendi yanıt `response.json` dosyanıza kaydetmeniz gerekir. response.template.json dosyasını özelleştirin, yoksa düzen her güncelleştirildiğinde değişiklikleriniz kaybolur.

## <a name="example-customized-layout-response-file-content"></a>Örnek özelleştirilmiş düzen yanıt dosyası içeriği

::: moniker range="vs-2017"

Aşağıdaki dosya örneği, hem İngilizce hem de Fransızca kullanıcı arabirimi dillerini dahil etmek ve güncelleştirme konumunun düzeni geri işaret etmek üzere yapılandırılması için birkaç ortak iş yükü ve bileşeni içerecek şekilde bir Visual Studio Enterprise istemci yüklemesi `response.json` başlatacak. Visual Studio 2017 için, istemcide güncelleştirme konumu (channelURI) ayarlanacaksa daha sonra değiştirilemez.

```Example response.json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "\\\\server\\share\\layoutdirectory\\ChannelManifest.json",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range="=vs-2019"

Aşağıdaki dosya örneği, birkaç ortak iş yükü ve bileşeni seçmek, hem İngilizce hem de Fransızca kullanıcı arabirimi dillerini seçmek ve güncelleştirme konumunun düzeni geri işaret etmek üzere yapılandırılması için bir Visual Studio Enterprise istemcisi yüklemesi `response.json` başlatacak. Visual Studio 2019 için güncelleştirme konumunun (channelURI) yalnızca ilk yükleme sırasında yapılandırılanana ve  en son yükleyicide işlevselliği kullanmadıkça gerçek sonrasında değiştirilemez. Bu yapılandırma [hakkında bilgi için Visual Studio'nin](/visualstudio/install/set-defaults-for-enterprise-deployments#configuring-source-location-for-updates) kurumsal dağıtımları için varsayılanları ayarla ve Düzeninizi her zaman içerecek şekilde yapılandırma ve en son yükleyiciyi sağlama'ya bakın. [](/visualstudio/install/create-a-network-installation-of-visual-studio#configure-the-layout-to-always-include-and-provide-the-latest-installer)

```Example response.json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "\\\\server\\share\\layoutdirectory\\ChannelManifest.json",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2019",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range="=vs-2022"

Aşağıdaki dosya örneği, birkaç ortak iş yükü ve bileşeni seçmek, hem İngilizce hem de Fransızca kullanıcı arabirimi dillerini seçmek ve güncelleştirme konumunun düzeni geri işaret etmek üzere yapılandırılması için bir Visual Studio Enterprise istemcisi yüklemesi `response.json` başlatacak. 

```Example response.json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "\\\\server\\share\\layoutdirectory\\ChannelManifest.json",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.17.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2022",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal"
    ]
}
```

::: moniker-end

## <a name="troubleshooting"></a>Sorun giderme
Visual Studio önyükleyicisi bir dosyayla eşleştirilirken hata verirken bir sorunla karşılaştınız, daha fazla bilgi için bkz. Visual Studio'i yükleme veya kullanma sırasında ağ ile `response.json` [ilgili](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) hataları giderme.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.
* [Visual Studio Yöneticileri Kılavuzu](https://aka.ms/vs/admin/guide)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio'i yükleme veya kullanma sırasında ağ ile ilgili Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
