---
title: Yanıt dosyası ile yükleme işlemini otomatikleştirme
description: Uygulama yüklemenizi otomatikleştirmenize yardımcı olacak bir JSON yanıt dosyası Visual Studio öğrenin
ms.date: 03/30/2019
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
ms.openlocfilehash: 37b81b957c708f18d896d436a0687298b8bc7bee
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453691"
---
# <a name="automate-installs-by-using-settings-in-a-response-file"></a>Yanıt dosyasındaki ayarları kullanarak yüklemeleri otomatikleştirme

Aşağıdaki örnekte Visual Studio dağıtan yöneticiler parametresini kullanarak bir yanıt `--in` dosyası belirtebilirsiniz:

```shell
vs_enterprise.exe --in customInstall.json
```

Yanıt dosyaları, içeriği komut satırı bağımsız değişkenlerini yansıtan [JSON](http://json-schema.org/) dosyalarıdır.  Genel olarak, bir komut satırı parametresi bağımsız değişken (örneğin, , vb.) kabul yoksa, yanıt dosyasındaki değer `--quiet` `--passive` true/false olmalıdır.  Bir bağımsız değişken (örneğin, ) alıyorsa, yanıt `--installPath <dir>` dosyasındaki değer bir dize olmalıdır.  Bir bağımsız değişken alır ve komut satırı üzerinde birden çok kez görünebilirse (örneğin, `--add <id>` ), bir dize dizisi olması gerekir.

Parametrelerin birden çok giriş almaları (örneğin, ) dışında, yanıt dosyasından komut satırı geçersiz kılma ayarlarında belirtilen `--add` parametreler. Birden çok girişiniz olduğunda, komut satırına sağlanan girişler yanıt dosyasındaki ayarlarla birleştirilir.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio için varsayılan yapılandırma ayarlama

ile bir ağ düzeni önbelleği `--layout` oluşturduysanız, `response.json` düzende bir başlangıç dosyası oluşturulur. Kısmi bir düzen oluşturmanız, bu yanıt dosyası düzenin içinde yer alan iş yüklerini ve dilleri içerir.  Kurulumu bu düzenden çalıştırarak bu response.json dosyası otomatik olarak kullanılır ve bu dosya düzende yer alan iş yüklerini ve bileşenleri seçer.  Kullanıcılar, yüklemeden önce kurulum kullanıcı arabiriminde iş yüklerini seçmeye veya Visual Studio.

Düzen oluşturan yöneticiler, kullanıcıların düzenden yükleme yaptıklarında göreceği varsayılan ayarları kontrol etmek için Visual Studio `response.json` değiştirebilir.  Örneğin, bir yönetici varsayılan olarak belirli iş yüklerinin ve bileşenlerin yüklü olması istiyorsa, bunları eklemek `response.json` için dosyayı yapılandırabilirsiniz.

Kurulum Visual Studio bir düzen klasöründen çalıştırılırsa, otomatik _olarak_ düzen klasöründeki yanıt dosyasını kullanır.  seçeneğini kullanmak zorunda `--in` değildir.

Bu düzenden yükleme yapan kullanıcılar için varsayılan ayarı tanımlamak üzere çevrimdışı düzen `response.json` klasöründe oluşturulan dosyayı güncelleştirebilirsiniz.

> [!WARNING]
> Düzen oluşturulduğunda tanımlanan mevcut özellikleri bırakmanız kritik öneme sahiptir.

Bir düzende yer alan temel dosya, yüklemek istediğiniz ürün ve kanalın değerini içermesi dışında `response.json` aşağıdaki örnekteki gibi görünüyor olabilir:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range=">=vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

Bir düzen oluşturulduğunda veya güncelleştiren bir response.template.json dosyası da oluşturulur.  Bu dosya, kullanılmaktadır tüm iş yükünü, bileşeni ve dil kimliklerini içerir.  Bu dosya, özel bir yüklemeye dahil edilecek her şey için bir şablon olarak sağlanır.  Yöneticiler bu dosyayı özel yanıt dosyası için başlangıç noktası olarak kullanabilir.  Yüklemek istemediklerinizi için kimlikleri kaldırmanız ve kendi yanıt dosyanıza kaydetmeniz gerekir.  response.template.json dosyasını özelleştirin, yoksa düzen her güncelleştirildiğinde değişiklikleriniz kaybolur.

## <a name="example-layout-response-file-content"></a>Örnek düzen yanıt dosyası içeriği

Aşağıdaki örnek, Visual Studio Enterprise iş yükü ve bileşeni olan ve hem İngilizce hem de Fransızca kullanıcı arabirimi dilleriyle birlikte yüklemeleri gerçekleştirmektedir. Bu örneği şablon olarak kullanabilirsiniz; yalnızca iş yüklerini ve bileşenleri yüklemek istediğiniz bileşenlerle değiştirmenizi sağlar:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
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

::: moniker range=">=vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio'i yükleme veya kullanma sırasında ağ ile ilgili Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
