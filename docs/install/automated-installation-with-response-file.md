---
title: Yanıt dosyası ile yükleme işlemini otomatikleştirme
description: Uygulama yüklemenizi otomatikleştirmenize yardımcı olacak bir JSON yanıt dosyası Visual Studio öğrenin
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7554ac46d7c4171cfb71166c51689ff4ae95c0d5
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724557"
---
# <a name="automate-installs-by-using-settings-in-a-response-file"></a>Yanıt dosyasındaki ayarları kullanarak yüklemeleri otomatikleştirme

Dağıtım yapan Visual Studio, aşağıdaki örnekte olduğu gibi `--in` parametresini kullanarak bir yanıt dosyası belirtebilirsiniz:

```cmd
vs_enterprise.exe --in customInstall.json
```

Yanıt dosyaları, içeriği komut satırı bağımsız değişkenlerini yansıtan [JSON](http://json-schema.org/) dosyalarıdır.  Genel olarak, bir komut satırı parametresi bağımsız değişken (örneğin, , vb.) kabul yoksa, yanıt dosyasındaki değer `--quiet` `--passive` true/false olmalıdır.  Bir bağımsız değişken (örneğin, ) alıyorsa, yanıt `--installPath <dir>` dosyasındaki değer bir dize olmalıdır.  Bir bağımsız değişken alır ve komut satırı üzerinde birden çok kez görünebilirse (örneğin, `--add <id>` ), bir dize dizisi olması gerekir.

Parametrelerin birden çok giriş almaları (örneğin, ) dışında, yanıt dosyasından komut satırı geçersiz kılma ayarlarında belirtilen `--add` parametreler. Birden çok girişiniz olduğunda, komut satırına sağlanan girişler yanıt dosyasındaki ayarlarla birleştirilir.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio için varsayılan yapılandırma ayarlama

ile bir ağ düzeni önbelleği `--layout` oluşturduysanız, `response.json` düzende bir başlangıç dosyası oluşturulur. Kısmi bir düzen oluşturmanız, bu yanıt dosyası düzenin içinde yer alan iş yüklerini ve dilleri içerir.  Kurulumu bu düzenden çalıştırarak, response.jsiş yüklerini ve bileşenleri seçen bu dosyada otomatik olarak kullanılır.  Kullanıcılar, yüklemeden önce kurulum kullanıcı arabiriminde iş yüklerini seçmeye veya Visual Studio.

Düzen oluşturan yöneticiler, kullanıcıların düzenden yükleme yaptıklarında göreceği varsayılan ayarları kontrol etmek için Visual Studio `response.json` değiştirebilir.  Örneğin, bir yönetici varsayılan olarak belirli iş yüklerinin ve bileşenlerin yüklü olması istiyorsa, bunları eklemek `response.json` için dosyayı yapılandırabilirsiniz.

Visual Studio Kurulumu bir düzen klasöründen çalıştırıldığında, _otomatik olarak_ düzen klasöründeki yanıt dosyasını kullanır.  Seçeneğini kullanmak zorunda değilsiniz `--in` .

`response.json`Bu düzenden yükleyen kullanıcılar için varsayılan ayarı tanımlamak üzere çevrimdışı bir düzen klasöründe oluşturulan dosyayı güncelleştirebilirsiniz.

> [!WARNING]
> Düzen oluşturulduğunda tanımlanmış mevcut özellikleri bırakmanız önemlidir.

`response.json`Bir düzendeki temel dosya, yüklemek istediğiniz ürün ve kanal için değeri içermesi dışında aşağıdaki örneğe benzer olmalıdır:

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

::: moniker range="vs-2019"

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

Bir düzen oluşturduğunuzda veya güncelleştirdiğinizde bir response.template.jsdosyası da oluşturulur.  Bu dosya, kullanılabilecek tüm iş yükü, bileşen ve dil kimliklerini içerir.  Bu dosya, tümünün özel bir yüklemeye dahil edilip edildikleriniz için bir şablon olarak sağlanır.  Yöneticiler, bu dosyayı özel bir yanıt dosyası için bir başlangıç noktası olarak kullanabilir.  Yüklemek istemediğiniz nesnelerin kimliklerini kaldırmanız ve kendi yanıt dosyanıza kaydetmeniz yeterlidir.  Dosya response.template.jsözelleştirmeyin veya Düzen her güncelleştirildiğinde değişiklikleriniz kaybedilir.

## <a name="example-layout-response-file-content"></a>Örnek düzen yanıt dosyası içeriği

Aşağıdaki örnek, Visual Studio Enterprise altı ortak iş yükü ve bileşeni ve hem Ingilizce hem de Fransızca Kullanıcı arabirimi dilleri ile yüklenmektedir. Bu örneği şablon olarak kullanabilirsiniz; yalnızca iş yüklerini ve bileşenleri yüklemek istediğiniz olanlarla değiştirin:

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

::: moniker range="vs-2019"

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
* [Visual Studio 'Yu yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md)
