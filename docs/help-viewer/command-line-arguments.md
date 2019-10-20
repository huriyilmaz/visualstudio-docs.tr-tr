---
title: Yardım Içeriği Yöneticisi için komut satırı bağımsız değişkenleri
ms.date: 11/01/2017
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9bead01c6440d5232a91a5e8fe2007b3e30340c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631972"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Yardım Içeriği Yöneticisi için komut satırı bağımsız değişkenleri

Yardım Içerik Yöneticisi (*HlpCtntMgr. exe*) için komut satırı bağımsız değişkenlerini kullanarak yerel yardım içeriğini dağıtmayı ve yönetmeyi belirtebilirsiniz. Bu komut satırı aracı için komut dosyalarını yönetici izinleriyle çalıştırmanız gerekir ve bu komut dosyalarını bir hizmet olarak çalıştıramazsınız. Bu aracı kullanarak aşağıdaki görevleri gerçekleştirebilirsiniz:

- Bir diskten veya buluttan yerel yardım içeriği ekleyin veya güncelleştirin.

- Yerel Yardım içeriğini kaldırın.

- Yerel yardım içerik deposunu taşıyın.

- Yerel Yardım içeriğini sessizce ekleyin, güncelleştirin, kaldırın veya taşıyın.

Sözdizimi:

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

Örneğin:

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

>[!NOTE]
> Katalog adı hem Visual Studio 2017 hem de Visual Studio 2019 için VisualStudio15. Bu beklenmeyen bir durum olabilir, ancak Visual Studio sürümleri için aynı Yardım görüntüleyicisinin kullanılması buna yöneliktir.

## <a name="switches-and-arguments"></a>Anahtarlar ve bağımsız değişkenler

Aşağıdaki tabloda yardım Içerik Yöneticisi için komut satırı aracı için kullanabileceğiniz anahtarlar ve bağımsız değişkenler tanımlanmaktadır:

|Anahtar|Gerekli mi?|Arguments|
|------------|---------------|---------------|
|/işlem|Evet|**yükleme**-   --belirtilen yükleme kaynağından yerel içerik deposuna kitap ekler.<br />     Bu anahtar,/booklist bağımsız değişkeni,/sourceURI bağımsız değişkeni veya her ikisini de gerektirir. /SourceURI bağımsız değişkenini belirtmezseniz, yükleme kaynağı olarak varsayılan Visual Studio URI 'SI kullanılır. /Booklist bağımsız değişkenini belirtmezseniz,/sourceUri üzerindeki tüm kitaplar yüklenir.<br />-   **Kaldır**--yerel içerik deposundan belirttiğiniz kitapları kaldırır.<br />     Bu anahtar,/booklist bağımsız değişkeni veya/sourceURI bağımsız değişkenini gerektirir.  /SourceURI bağımsız değişkenini belirtirseniz, tüm kitaplar kaldırılır ve/booklist bağımsız değişkeni yok sayılır.<br />-   **Move**--yerel depoyu belirttiğiniz yola taşır. Varsayılan yerel depo yolu, *% ProgramData%* altında bir dizin olarak ayarlanır.<br />     Bu anahtar,/locationPath ve/katalogadı bağımsız değişkenlerini gerektirir. Geçerli olmayan bir yol belirtirseniz veya sürücüde içeriği tutmak için yeterli boş alan yoksa hata iletileri olay günlüğüne yazılır.<br />**yenileme**-   --yüklendikleri veya en son güncelleştirildiği zamandan beri değiştirilen konuları güncelleştirir.<br />     Bu anahtar,/sourceURI bağımsız değişkenini gerektirir.|
|/catalogName|Evet|İçerik kataloğunun adını belirtir. Visual Studio 2017 ve Visual Studio 2019 için bu VisualStudio15.|
|/locale|Hayır|Yardım Görüntüleyicisi 'nin geçerli örneğinin içeriğini görüntülemek ve yönetmek için kullanılan ürün yerel ayarını belirtir. Örneğin, Ingilizce Birleşik Devletler için `EN-US` belirtirsiniz.<br /><br /> Bir yerel ayar belirtmezseniz, işletim sisteminin yerel ayarı kullanılır. Bu yerel ayar belirlenemiyorsa, `EN-US` kullanılır.<br /><br /> Geçerli olmayan bir yerel ayar belirtirseniz, olay günlüğüne bir hata iletisi kaydedilir.|
|/e|Hayır|Geçerli kullanıcının yönetici kimlik bilgileri varsa yardım Içerik yöneticisini yönetim ayrıcalıklarına yükseltir.|
|/sourceURI|Hayır|İçeriğin yüklendiği URL 'YI (hizmet API 'SI) veya içerik yükleme dosyasının ( *. msha*) yolunu belirtir. URL, Visual Studio 2010 Style uç noktasındaki ürün grubunu (üst düzey düğüm) veya ürün defterlerini (yaprak düzeyindeki düğüm) işaret edebilir. URL 'nin sonuna eğik çizgi (/) eklemeniz gerekmez. Eğik çizgi eklerseniz, uygun şekilde işlenir.<br /><br /> Bulunmayan, geçerli olmayan veya erişilemeyen bir dosya belirtirseniz ya da içerik yönetilirken internet bağlantısı yoksa veya kesintiye uğrarsa bir hata iletisi olay günlüğüne kaydedilir.|
|/Vendor|Hayır|Kaldırılacak ürün içeriği için satıcıyı belirtir (örneğin, `Microsoft`). Bu anahtar için varsayılan bağımsız değişken Microsoft.|
|/productName|Hayır|Kaldırılacak olan kitapların ürün adını belirtir. Ürün adı, içerikle birlikte gelen *HelpContentSetup. msha* veya *Books. html* dosyalarında tanımlanır. Kitapları tek seferde yalnızca bir üründen kaldırabilirsiniz. Birden çok üründen kitap kaldırmak için birden çok yükleme gerçekleştirmeniz gerekir.|
|/Booklist|Hayır|Yönetilecek kitapların adlarını boşluklarla ayırarak belirtir. Değerler, yükleme medyasında listelenen defterleriyle aynı olmalıdır.<br /><br /> Bu bağımsız değişkeni belirtmezseniz,/sourceURI içinde belirtilen ürün için önerilen tüm kitaplar yüklenir.<br /><br /> Bir kitabın adı bir veya daha fazla boşluk içeriyorsa, listenin uygun şekilde sınırlandırıldığından, çift tırnak (") ile çevreleyin.<br /><br /> Geçerli olmayan veya ulaşılabilir olmayan bir/sourceURI belirtirseniz, hata iletileri günlüğe kaydedilir.|
|/skuId|Hayır|Yükleme kaynağından ürünün stok tutma birimini (SKU) belirtir ve/SourceURI anahtarının tanımladığı kitapçıkları filtreler.|
|/Membership|Hayır|**minimum**-   --/skuId anahtarını kullanarak belirttiğiniz SKU 'ya bağlı olarak en az bir yardım içeriği kümesi yükleme. SKU ve içerik kümesi arasındaki eşleme, hizmet API 'sinde kullanıma sunulur.<br />**önerilen**-   :/skuId bağımsız değişkenini kullanarak belirttiğiniz SKU için önerilen bir kitaplar kümesi yüklenir. Yükleme kaynağı, hizmet API 'sidir veya *. MSHA*.<br />-   **Full**--/skuId bağımsız değişkenini kullanarak belirttiğiniz SKU için tüm kitap kümesini yükleme. Yükleme kaynağı, hizmet API 'sidir veya *. MSHA*.|
|/locationPath|Hayır|Yerel Yardım içeriği için varsayılan klasörü belirtir. Bu anahtarı yalnızca içerik yüklemek veya taşımak için kullanmalısınız. Bu anahtarı belirtirseniz,/Silent anahtarını da belirtmeniz gerekir.|
|/silent|Hayır|Durum bildirim alanındaki simge dahil olmak üzere kullanıcıya sormadan veya herhangi bir kullanıcı arabirimini görüntülemeden Yardım içeriğini kaldırır veya kaldırır. Çıkış, *% Temp%* dizinindeki bir dosyaya kaydedilir. **Önemli:**  İçeriği sessizce yüklemek için *. mshc* dosyalarını değil, dijital olarak imzalanmış *. cab* dosyalarını kullanmanız gerekir.|
|/launchingApp|Hayır|Yardım Görüntüleyicisi ana uygulama olmadan başlatıldığında uygulama ve Katalog bağlamını tanımlar. Bu anahtarın bağımsız değişkenleri *ŞirketAdı*, *ProductName*ve *versionNumber* (örneğin, `/launchingApp Microsoft,VisualStudio,16.0`).<br /><br /> Bu,/Silent parametresiyle içerik yüklemek için gereklidir.|
|/wait *saniye*|Hayır|Yükleme, kaldırma ve yenileme işlemlerini duraklatır. Katalog için bir işlem zaten devam ediyorsa, işlem devam etmek için verilen saniye sayısına kadar bekler. Süresiz olarak beklemek için 0 kullanın.|
|/?|Hayır|Yardım Içeriği Yöneticisi için komut satırı aracının anahtarlarını ve açıklamalarını listeler.|

### <a name="exit-codes"></a>Çıkış kodları

Yardım Içeriği Yöneticisi için komut satırı aracını sessiz modda çalıştırdığınızda, şu çıkış kodlarını döndürür:

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yardım Görüntüleyicisi Yönetici Kılavuzu](../help-viewer/administrator-guide.md)
- [Yardım Içerik Yöneticisi geçersiz kılmaları](../help-viewer/behavior-overrides.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)