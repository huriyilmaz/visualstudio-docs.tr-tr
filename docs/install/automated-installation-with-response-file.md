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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ecdda55bbe4e79af01f8fb9a9a2b77f775548b10
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115238"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Yanıt dosyasındaki ayarları tanımlama

Visual Studio dağıtan Yöneticiler `--in` , aşağıdaki örnekte olduğu gibi parametresini kullanarak bir yanıt dosyası belirtebilir:

```cmd
vs_enterprise.exe --in customInstall.json
```

Yanıt dosyaları, içeriği komut satırı bağımsız değişkenlerini yansıtarak [JSON](http://json-schema.org/) dosyalarıdır.  Genel olarak, bir komut satırı parametresi bağımsız değişken alırsa (örneğin,, `--quiet` `--passive` vb.), yanıt dosyasındaki değer true/false olmalıdır.  Bir bağımsız değişken alırsa (örneğin, `--installPath <dir>` ), yanıt dosyasındaki değer bir dize olmalıdır.  Bir bağımsız değişken alırsa ve komut satırında birden çok kez görünebilen (örneğin, `--add <id>` ), dize dizisi olmalıdır.

Parametrelerin birden çok giriş (örneğin,) olması dışında, yanıt dosyasındaki komut satırı geçersiz kılma ayarlarında belirtilen parametreler `--add` . Birden çok giriş olduğunda, komut satırında sağlanan girişler yanıt dosyasındaki ayarlarla birleştirilir.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio için varsayılan yapılandırmayı ayarlama

İle bir ağ düzeni önbelleği oluşturduysanız `--layout` , düzende bir başlangıç `response.json` dosyası oluşturulur. Kısmi bir düzen oluşturursanız, bu yanıt dosyası, düzende yer alan iş yüklerini ve dilleri içerir.  Bu düzenden kurulum 'u çalıştırmak, bu response.js, mizanpaja dahil olan iş yüklerini ve bileşenleri seçen dosya üzerinde otomatik olarak kullanır.  Kullanıcılar, Visual Studio 'Yu yüklemeden önce kurulum Kullanıcı arabirimindeki iş yüklerini seçebilir veya seçimden kaldırır.

Düzen oluşturan Yöneticiler, `response.json` mizanpajdaki dosyayı, kullanıcıların Visual Studio 'nun düzeninden yüklediklerinde göreceği varsayılan ayarları denetlemek için düzenleyebilir.  Örneğin, bir yönetici varsayılan olarak belirli iş yüklerini ve bileşenleri istiyorsa, `response.json` dosyayı eklemek için bu dosyaları yapılandırabilirler.

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
