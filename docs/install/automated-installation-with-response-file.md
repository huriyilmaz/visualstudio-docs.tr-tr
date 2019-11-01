---
title: Yüklemeyi bir yanıt dosyasıyla otomatikleştirin
description: Visual Studio yüklemenizi otomatikleştirmenize yardımcı olan bir JSON yanıt dosyası oluşturmayı öğrenin
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d26211f566bb8f683f3b38deade4f13defe9cb01
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189508"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Yanıt dosyasındaki ayarları tanımlama

Visual Studio dağıtan Yöneticiler, aşağıdaki örnekte olduğu gibi `--in` parametresini kullanarak bir yanıt dosyası belirtebilir:

```cmd
vs_enterprise.exe --in customInstall.json
```

Yanıt dosyaları, içeriği komut satırı bağımsız değişkenlerini yansıtarak [JSON](http://json-schema.org/) dosyalarıdır.  Genel olarak, bir komut satırı parametresi bağımsız değişken alırsa (örneğin, `--quiet`, `--passive`, vb.), yanıt dosyasındaki değer true/false olmalıdır.  Bir bağımsız değişken alırsa (örneğin, `--installPath <dir>`), yanıt dosyasındaki değer bir dize olmalıdır.  Bir bağımsız değişken alırsa ve komut satırında birden çok kez görünebilen (örneğin, `--add <id>`), dize dizisi olmalıdır.

Parametrelerin birden çok giriş (örneğin, `--add`) olması dışında, yanıt dosyasındaki komut satırı geçersiz kılma ayarlarında belirtilen parametreler. Birden çok giriş olduğunda, komut satırında sağlanan girişler yanıt dosyasındaki ayarlarla birleştirilir.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio için varsayılan yapılandırmayı ayarlama

`--layout`bir ağ düzeni önbelleği oluşturduysanız, düzende bir ilk `response.json` dosyası oluşturulur. Kısmi bir düzen oluşturursanız, bu yanıt dosyası, düzende yer alan iş yüklerini ve dilleri içerir.  Bu düzenden kurulum 'u çalıştırmak, mizanpaja dahil olan iş yüklerini ve bileşenleri seçen bu Response. json dosyasını otomatik olarak kullanır.  Kullanıcılar, Visual Studio 'Yu yüklemeden önce kurulum Kullanıcı arabirimindeki iş yüklerini seçebilir veya seçimden kaldırır.

Düzen oluşturan Yöneticiler, mizanpajdaki `response.json` dosyasını, kullanıcıların Visual Studio 'Yu düzenden yüklediklerinde göreceği varsayılan ayarları denetlemek için değiştirebilir.  Örneğin, bir yönetici varsayılan olarak belirli iş yüklerini ve bileşenleri istiyorsa, `response.json` dosyayı onları eklemek üzere yapılandırabilirler.

Visual Studio Kurulumu bir düzen klasöründen çalıştırıldığında, _otomatik olarak_ düzen klasöründeki yanıt dosyasını kullanır.  `--in` seçeneğini kullanmak zorunda değilsiniz.

Bu düzenden yükleyen kullanıcılar için varsayılan ayarı tanımlamak üzere çevrimdışı bir düzen klasöründe oluşturulan `response.json` dosyasını güncelleştirebilirsiniz.

> [!WARNING]
> Düzen oluşturulduğunda tanımlanmış mevcut özellikleri bırakmanız önemlidir.

Bir düzendeki temel `response.json` dosyası aşağıdaki örneğe benzer görünmelidir, ancak yüklemek istediğiniz ürün ve kanal için değeri de içermelidir:

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

Bir düzen oluşturduğunuzda veya güncelleştirdiğinizde bir Response. Template. JSON dosyası da oluşturulur.  Bu dosya, kullanılabilecek tüm iş yükü, bileşen ve dil kimliklerini içerir.  Bu dosya, tümünün özel bir yüklemeye dahil edilip edildikleriniz için bir şablon olarak sağlanır.  Yöneticiler, bu dosyayı özel bir yanıt dosyası için bir başlangıç noktası olarak kullanabilir.  Yüklemek istemediğiniz nesnelerin kimliklerini kaldırmanız ve kendi yanıt dosyanıza kaydetmeniz yeterlidir.  Response. Template. json dosyasını özelleştirmeyin veya Düzen her güncelleştirildiğinde değişiklikleriniz kaybedilir.

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
