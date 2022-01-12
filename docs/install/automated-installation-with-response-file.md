---
title: Yüklemeyi bir yanıt dosyasıyla otomatikleştirin
description: Visual Studio yüklemenizi otomatikleştirmenize yardımcı olan bir JSON yanıt dosyası oluşturmayı öğrenin
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
ms.openlocfilehash: 43df6bc03167e1949ab8592719f374849f765d23
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534352"
---
# <a name="programmatically-configure-default-settings-using-a-response-file"></a>Yanıt dosyası kullanarak program aracılığıyla varsayılan ayarları yapılandırma

Visual Studio yanıt dosyası, içeriği komut satırı parametrelerini ve bağımsız değişkenlerini yansıtan bir [JSON](http://json-schema.org/) dosyasıdır. Yanıt dosyası, ürüne ilk yükleme sırasında istemci ayarlarını başlatmak için kullanılır. 

## <a name="automate-installation"></a>Yüklemeyi otomatikleştirin
Visual Studio dağıtan yöneticiler `--in` , aşağıdaki örnekte olduğu gibi parametresini kullanarak bir yanıt dosyası belirtebilir:

```shell
vs_enterprise.exe --in customInstall.json
```
## <a name="response-file-contents"></a>Yanıt dosyası içeriği
Yanıt dosyası komut satırı parametrelerini kapsüller ve şu genel kuralları izler:
 - Bir komut satırı parametresi bağımsız değişken alırsa (örneğin,, `--quiet` `--passive` vb.), yanıt dosyasındaki değer true/false olmalıdır. 
 - Parametresi bir bağımsız değişkeni (örneğin, `--installPath <dir>` ) alırsa, yanıt dosyasındaki değer bir dize olmalıdır. 
 - Parametresi bir bağımsız değişken alırsa ve komut satırında birden çok kez görünebilen (örneğin, `--add <id>` ), yanıt dosyasındaki değer bir dize dizisi olmalıdır.

Komut satırında belirtilen parametreler, parametrelerin birden çok giriş (örneğin,) olması dışında, yanıt dosyasına dahil edilen ayarları geçersiz kılar `--add` . Birden çok giriş olduğunda, komut satırında sağlanan girişler yanıt dosyasındaki ayarlarla birleştirilir.

## <a name="configure-the-response-file-used-with-network-layouts"></a>Ağ düzenleriyle kullanılan yanıt dosyasını yapılandırma
Komutunu kullanarak bir ağ düzeni oluşturduysanız `--layout` , düzen klasörünün kökünde bir başlangıç varsayılan Vanilla `response.json` dosyası oluşturulmuştur. yöneticiler daha sonra bu `response.json` dosyada, istemci üzerinde Visual Studio yüklemek veya güncelleştirmek üzere bu düzendeki önyükleyici çağırdıklarında kullanması gereken ayarları denetlemek için düzende bu dosyayı değiştirebilir.

Dosyadaki yapılandırma ayarlarına `response.json` yalnızca istemci düzende önyükleyici kullanılıyorsa başvurulur ve kullanılır. , `response.json` İstemci güncelleştirmeyi istemcide yerel  olarak çağırırsa mizanpajda kullanılamaz.  

Yönetici kısmi bir düzen oluşturmadıysa, varsayılan `response.json` dosya yalnızca kısmi düzende yer alan iş yüklerini ve dilleri belirtir. 

`--quiet`İstemci ilk yüklemeyi  gerçekleştirirken modunun kullanılmadığını varsayarsak, ilk yükleme çalıştıran kullanıcılar içinde belirtilen Varsayılanları geçersiz kılabilir `response.json` ve yükleme gerçekten gerçekleşmeden önce kurulum Kullanıcı arabirimindeki iş yüklerini daha da seçebilir veya seçimden kaldırabilirsiniz. kullanıcı, mizanpajda kullanılamayan bileşenleri veya iş yüklerini seçip, `response.json` Microsoft tarafından barındırılan sunucu noktalarında channeluri ise, Visual Studio kurulum paketleri ınternet 'ten edinmeye çalışacaktır.

Visual Studio kurulum bir düzen klasöründen çalıştırıldığında, kurulum dosyayı _otomatik olarak_ `response.json` düzen klasöründe kullanacaktır. Seçeneğini kullanmak zorunda değilsiniz `--in` .

> [!WARNING]
> Düzen oluşturulduğu sırada tanımlanmış olan ' de herhangi bir özelliği silmemenizi çok önemlidir `response.json` . Değerleri değiştirebilirsiniz, ancak herhangi bir öğeyi kaldıramazsınız.

`response.json`Bir düzendeki temel dosya, yüklemek istediğiniz ürün ve kanal için değeri içermesi dışında aşağıdaki örneğe benzer olmalıdır:

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

Bir düzen oluşturduğunuzda veya güncelleştirdiğinizde bir Response. Template. JSON dosyası da oluşturulur.  Bu dosya, kullanılabilecek tüm iş yükü, bileşen ve dil kimliklerini içerir.  Bu dosya, tümünün özel bir yüklemeye dahil edilip edildikleriniz için bir şablon olarak sağlanır. Yöneticiler, bu dosyayı özel bir yanıt dosyası için bir başlangıç noktası olarak kullanabilir. Yüklemek istemediğiniz nesnelerin kimliklerini kaldırmanız ve `response.json` dosyaya veya kendi yanıt dosyanıza kaydetmeniz yeterlidir. Response. Template. json dosyasını özelleştirmeyin veya Düzen her güncelleştirildiğinde değişiklikleriniz kaybedilir.

## <a name="example-customized-layout-response-file-content"></a>Örnek özelleştirilmiş düzen yanıt dosyası içeriği

::: moniker range="vs-2017"

aşağıdaki `response.json` dosya örneği, hem ingilizce hem de fransızca kullanıcı arabirimi dillerini dahil etmek ve güncelleştirme konumunun düzene geri dönmesi için yapılandırılmasını sağlamak üzere bir Visual Studio Enterprise istemci yüklemesini başlatacak. Visual Studio 2017 için, istemci üzerinde güncelleştirme konumu (channeluri) ayarlandığında, daha sonra değiştirilemez.

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

aşağıdaki `response.json` dosya örneği, birkaç ortak iş yükü ve bileşeni seçmek, hem ingilizce hem de fransızca kullanıcı arabirimi dillerini seçmek ve güncelleştirme konumunun düzene geri işaret edecek şekilde yapılandırılmasını sağlamak için Visual Studio Enterprise istemci yüklemesini başlatacak. Visual Studio 2019 ' de, güncelleştirme konumunun (channeluri) yalnızca ilk yükleme sırasında yapılandırılabileceğini ve en son yükleyicideki işlevselliği kullanmadığınız _durumlar dışında_ , bundan sonra değiştirilemeyeceğini unutmayın. [Visual Studio kurumsal dağıtımları için varsayılan ayarlar](set-defaults-for-enterprise-deployments.md#configuring-source-location-for-updates) ' a bakın ve düzeninizi yapılandırma hakkında bilgi için [en son yükleyiciyi her zaman içerecek şekilde yapılandırın](create-a-network-installation-of-visual-studio.md#configure-the-layout-to-always-include-and-provide-the-latest-installer) .

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

aşağıdaki `response.json` dosya örneği, birkaç ortak iş yükü ve bileşeni seçmek, hem ingilizce hem de fransızca kullanıcı arabirimi dillerini seçmek ve güncelleştirme konumunun düzene geri işaret edecek şekilde yapılandırılmasını sağlamak için Visual Studio Enterprise istemci yüklemesini başlatacak. 

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
Visual Studio önyükleyici ile bir dosyayla eşleştirmeniz sırasında hata oluşturan bir sorunla karşılaşırsanız `response.json` , daha fazla bilgi için [Visual Studio sayfasını yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) bölümüne bakın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.
* [Visual Studio yöneticileri kılavuzu](https://aka.ms/vs/admin/guide)
* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio yüklerken veya kullanırken ağla ilgili hatalarda sorun giderme](troubleshooting-network-related-errors-in-visual-studio.md)
