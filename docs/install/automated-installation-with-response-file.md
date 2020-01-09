---
title: Yükleme yanıt dosyası ile otomatikleştirme
description: Visual Studio yüklemenizin otomatikleştirmenize yardımcı olur. bir JSON yanıt dosyası oluşturmayı öğrenin
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 43a4212a9faf0b7fef3395a847e8c614507e56df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588543"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Yanıt dosyasında ayarları tanımlama

Visual Studio dağıtma Yöneticiler, bir yanıt dosyası kullanarak belirleyebilir `--in` parametresi, aşağıdaki örnekte olduğu gibi:

```cmd
vs_enterprise.exe --in customInstall.json
```

Yanıt dosyaları [JSON](http://json-schema.org/) içerikleri komut satırı bağımsız değişkenleri yansıtan dosyaları.  Genel olarak bir komut satırı parametre bağımsız değişken olmadan alırsa, (örneğin, `--quiet`, `--passive`, vs.), yanıt dosyasındaki değeri true/false olmalıdır.  Bağımsız değişken aldığı durumlarda (örneğin, `--installPath <dir>`), yanıt dosyasındaki değeri bir dize olmalıdır.  Bir bağımsız değişkeni alır ve komut satırında birden fazla kez görünebilir (örneğin, `--add <id>`), dizelerden oluşan bir dizi olmalıdır.

Birden çok giriş parametre alır, üzerinde yanıt dosyasından komut satırı geçersiz kılma ayarları dışında belirtilen parametreler (örneğin, `--add`). Birden fazla giriş varsa, komut satırında sağlanan girişler yanıt dosyasındaki ayarları ile birleştirilir.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio için varsayılan yapılandırma ayarı

Bir ağ düzeni önbellekle oluşturduysanız `--layout`, bir ilk `response.json` düzende dosyası oluşturulur. Kısmi bir düzen oluşturursanız, bu yanıt dosyası düzende dahil edilen diller ve iş yüklerini içerir.  Kurulum bu düzeninden otomatik olarak çalışan iş yüklerinin ve bileşenlerin düzende seçer bu response.json dosyası kullanır.  Kullanıcılar yine de seçebilir veya Visual Studio'yu yüklemeden önce kurulum UI içinde herhangi bir iş yükünü seçimini kaldırın.

Bir düzen oluşturma yöneticileri değiştirebilirsiniz `response.json` düzenini, kullanıcıları, bunlar düzenden Visual Studio yüklediğinizde gördüğünüzü varsayılan ayarlarını denetlemek için dosyasında.  Örneğin, bir yönetici belirli iş yükleri ve bileşenlerin varsayılan olarak yüklü isterse, yapılandırabileceği `response.json` bunları eklemek için dosya.

Visual Studio kurulumunda bir düzen klasöründen çalıştırdığınızda, _otomatik olarak_ Düzen klasöründe yanıt dosyası kullanır.  Kullanmak zorunda değilsiniz `--in` seçeneği.

Güncelleştirebilirsiniz `response.json` bu düzeninden yükleyen kullanıcılar için varsayılan ayar tanımlamak için bir çevrimdışı Düzen klasöründe oluşturulan dosya.

> [!WARNING]
> Düzen oluşturulurken tanımlanan varolan özellikleri bırakın önemlidir.

Temel `response.json` ürün ve yüklemek istediğiniz kanalı için bir değer verilebilir dışında Düzen dosyasında aşağıdaki örneğe benzer görünmelidir:

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

Bir düzen güncelle response.template.json dosyası da oluşturulur.  Bu dosya, tüm iş yükü, bileşen ve dil kullanılabilir kimliklerini içerir.  Bu dosya, bir şablon için hangi tüm içinde özel bir yükleme içerdiğinden sağlanır.  Yöneticiler bu dosya, bir özel yanıt dosyası için bir başlangıç noktası olarak kullanabilir.  Yalnızca kimlikleri yükleyin ve kendi yanıt dosyasına kaydetmek istemediğiniz herhangi bir şeyi kaldırın.  Response.template.json dosya özelleştirmeyin veya Düzen güncelleştirildiğinde yaptığınız değişiklikler kaybolacak.

## <a name="example-layout-response-file-content"></a>Örnek Düzen yanıt dosyası içeriği

Aşağıdaki örnek, altı yaygın iş yüklerinin ve bileşenlerin ve hem İngilizce ve Fransızca kullanıcı Arabirimi dilleri ile Visual Studio Enterprise yükler. Bu örnekte, şablon olarak kullanabilirsiniz; yalnızca iş yüklerinin ve bileşenlerin, yüklemek istediğiniz değiştirin:

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
