---
title: Yanıt dosyasıyla yüklemeyi otomatikleştir
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115238"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Yanıt dosyasındaki ayarlar nasıl tanımlanır?

Visual Studio'yu dağıtan yöneticiler, aşağıdaki `--in` örnekte olduğu gibi parametreyi kullanarak bir yanıt dosyası belirtebilir:

```cmd
vs_enterprise.exe --in customInstall.json
```

Yanıt dosyaları, içeriği komut satırı bağımsız değişkenlerini yansıtan [JSON](http://json-schema.org/) dosyalarıdır.  Genel olarak, bir komut satırı parametresi hiçbir `--quiet`bağımsız `--passive`değişken (örneğin, , , vb) alıyorsa, yanıt dosyasındaki değer doğru/yanlış olmalıdır.  Bir bağımsız değişken alıyorsa `--installPath <dir>`(örneğin,), yanıt dosyasındaki değer bir dize olmalıdır.  Bir bağımsız değişken alıyorsa ve komut satırında birden `--add <id>`fazla kez görüntülenebiliyorsa (örneğin,), bir dizi dize olmalıdır.

Parametreler birden çok giriş aldığında (örneğin), `--add`yanıt dosyasındaki komut satırı geçersiz kılma ayarlarında belirtilen parametreler. Birden çok girdiniz olduğunda, komut satırında sağlanan girişler yanıt dosyasındaki ayarlarla birleştirilir.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio için varsayılan yapılandırma ayarlama

Düzende `--layout`bir ilk `response.json` dosya oluşturuldu. Kısmi bir düzen oluşturursanız, bu yanıt dosyası düzene dahil edilen iş yüklerini ve dilleri içerir.  Kurulumu bu düzenden çalıştırmak, düzene dahil edilen iş yüklerini ve bileşenleri seçen bu yanıt.json dosyasını otomatik olarak kullanır.  Kullanıcılar Visual Studio'yu yüklemeden önce kurulum kullanıcı arama b'sinde iş yüklerini seçmeye veya seçmeye devam edebilir.

Düzen oluşturan yöneticiler, kullanıcılarının `response.json` visual studio'yu düzenden yüklediklerinde gördükleri varsayılan ayarları denetlemek için dosyayı düzende değiştirebilir.  Örneğin, bir yönetici varsayılan olarak belirli iş yüklerinin ve bileşenlerinin `response.json` yüklenmesini istiyorsa, dosyayı bunları ekleyecek şekilde yapılandırabilir.

Visual Studio kurulumu bir düzen klasöründen çalıştırıldığında, düzen klasöründeki yanıt dosyasını _otomatik olarak_ kullanır.  Bu `--in` seçeneği kullanmak zorunda değilsiniz.

Bu düzenden `response.json` yüklenen kullanıcılar için varsayılan ayarı tanımlamak için çevrimdışı düzen klasöründe oluşturulan dosyayı güncelleştirebilirsiniz.

> [!WARNING]
> Düzen oluşturulduğunda tanımlanan varolan özellikleri bırakmanız çok önemlidir.

Bir `response.json` düzendeki temel dosya, yüklemek istediğiniz ürün ve kanal değerini içermesi dışında aşağıdaki örneğe benzer olmalıdır:

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

Bir düzen oluşturduğunuzda veya güncelleştirdiğinizde, bir yanıt.template.json dosyası da oluşturulur.  Bu dosya, kullanılabilecek tüm iş yükünü, bileşeni ve dil tamını içerir.  Bu dosya, özel bir yüklemeye nelerin ekleyebileceğini şablon olarak sağlar.  Yöneticiler bu dosyayı özel yanıt dosyası için başlangıç noktası olarak kullanabilir.  Yüklemek istemediğiniz şeyler için tadilleri kaldırın ve kendi yanıt dosyanıza kaydedin.  response.template.json dosyasını özelleştirmeyin yoksa düzen güncelleştirildiğinde değişiklikleriniz kaybolur.

## <a name="example-layout-response-file-content"></a>Örnek düzen yanıt dosyası içeriği

Aşağıdaki örnek, Visual Studio Enterprise'ı altı yaygın iş yükü ve bileşeni yle ve hem İngilizce hem de Fransızca UI dilleriyle yükler. Bu örneği şablon olarak kullanabilirsiniz; iş yüklerini ve bileşenleri yüklemek istediğiniz iş lerle değiştirmeniz gerekir:

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
* [Visual Studio'yu yüklediğinizde veya kullandığınızda ağla ilgili hataları giderme](troubleshooting-network-related-errors-in-visual-studio.md)
