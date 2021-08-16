---
title: Yardım İçerik Yöneticisi için komut satırı bağımsız değişkenleri
description: Yerel Yardım içeriğini dağıtmayı ve yönetmeyi belirtmek için Yardım İçerik Yöneticisi (HlpCtntMgr.exe) için komut satırı bağımsız değişkenlerini kullanın.
ms.date: 11/01/2017
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 879ea5283ad429678a91b159691d3fed5d353e732dddd7119e20c214637cff1b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358681"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Yardım İçerik Yöneticisi için komut satırı bağımsız değişkenleri

Yardım İçerik Yöneticisi (HlpCtntMgr.exe) için komut satırı bağımsız değişkenlerini kullanarak yerel Yardım içeriğini *dağıtmayı ve yönetmeyi belirtebilirsiniz.* Bu komut satırı aracı için betikleri yönetici izinleriyle çalıştırmanız gerekir ve bu betikleri hizmet olarak çalıştıramazsınız. Bu aracı kullanarak aşağıdaki görevleri gerçekleştirebilirsiniz:

- Bir diskten veya buluttan yerel Yardım içeriği ekleyin veya güncelleştirin.

- Yerel Yardım içeriğini kaldırın.

- Yerel Yardım içerik depolarını taşıma.

- Yerel Yardım içeriğini sessizce ekleyin, güncelleştirin, kaldırın veya taşıyın.

Söz dizimi:

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

Örnek:

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

>[!NOTE]
> Katalog adı hem Visual Studio 2017 hem de 2019 için VisualStudio15 Visual Studio adıdır. Bu beklenmeyen bir durum olabilir, ancak bunun nedeni her iki sürümde de aynı Yardım Görüntüleyicisi'nin Visual Studio olmasıdır.

## <a name="switches-and-arguments"></a>Anahtarlar ve bağımsız değişkenler

Aşağıdaki tabloda, Yardım İçerik Yöneticisi için komut satırı aracı için kullanabileceğiniz anahtarlar ve bağımsız değişkenler tanımlanır:

|Anahtar|Gerekli mi?|Bağımsız değişkenler|
|------------|---------------|---------------|
|/operation|Yes|-   **Install**--Adds books from the specified installation source to the local content store.<br />     Bu anahtar için /booklist bağımsız değişkeni, /sourceURI bağımsız değişkeni veya her ikisi de gerekir. /sourceURI bağımsız değişkenlerini belirtmezseniz, yükleme kaynağı Visual Studio URI'sini kullanırsınız. /booklist bağımsız değişkenlerini belirtmezseniz,/sourceUri'si üzerinde yer alan tüm kitaplar yüklenir.<br />-   **kaldır**--Belirttiğiniz kitapları yerel içerik mağazasından kaldırır.<br />     Bu anahtar için /booklist bağımsız değişkeni veya /sourceURI bağımsız değişkeni gerekir.  /sourceURI bağımsız değişkenlerini belirtirsiniz, tüm kitaplar kaldırılır ve /booklist bağımsız değişkeni yoksayılır.<br />-   **Move**--Yerel depo, belirttiğiniz yola taşınır. Varsayılan yerel depo yolu *%ProgramData%* altında bir dizin olarak ayarlanır<br />     Bu anahtar , /locationPath ve /catalogName bağımsız değişkenlerini gerektirir. Geçerli olmayan bir yol belirtirsiniz veya sürücüde içeriği tutmak için yeterli boş alan yoksa hata iletileri olay günlüğüne kaydedilir.<br />-   **Yenile**--Yüklendikten veya en son güncelleştirildiğinde değişen güncelleştirmeler konuları.<br />     Bu anahtar / sourceURI bağımsız değişken gerektirir.|
|/catalogName|Yes|İçerik kataloğu adını belirtir. 2017 Visual Studio 2019 Visual Studio için bu VisualStudio15'tir.|
|/locale|Hayır|Yardım görüntüleyicinin geçerli örneğinin içeriğini görüntülemek ve yönetmek için kullanılan ürün yerel ayarı belirtir. Örneğin, Eyaletler `EN-US` için English-United belirtirsiniz.<br /><br /> Yerel bir yerellik belirtmezseniz, işletim sisteminin yereli kullanılır. Bu yerel seçim belirlene belirlenene kadar `EN-US` kullanılır.<br /><br /> Geçerli olmayan bir yerel değer belirtirsiniz, olay günlüğüne bir hata iletisi kaydedilir.|
|/e|Hayır|Geçerli kullanıcının yönetici kimlik bilgileri varsa Yardım İçeriği Yöneticisi'ni Yönetim ayrıcalıklarına yükselter.|
|/sourceURI|Hayır|İçeriğin yük olduğu URL'yi (Hizmet API'si) veya içerik yükleme dosyasının yolunu (*.msha*) belirtir. URL, 2010 stilinde bir uç noktada Ürün Grubuna (üst düzey düğüm) veya Ürün Kitapları'Visual Studio işaret ediyor olabilir. URL'nin sonuna eğik çizgi (/) eklemek zorunda değilsiniz. Sonda bir eğik çizgi dahil ediyorsanız, bu uygun şekilde iş olur.<br /><br /> Bulunamıyor, geçerli olmayan veya erişilebilir olmayan bir dosya belirtirsiniz ya da İnternet bağlantısı kullanılamıyorsa veya içerik yönetilirken kesintiye uğrarsa olay günlüğüne bir hata iletisi kaydedilir.|
|/vendor|Hayır|Kaldırılacak ürün içeriği için satıcıyı belirtir (örneğin, `Microsoft` ). Bu anahtar için varsayılan bağımsız değişken Microsoft'tır.|
|/productName|Hayır|Kaldırılacak kitapların ürün adını belirtir. Ürün adı *helpcontentsetup.msha* veya *books.html* dosyalarında tanımlanır. Aynı anda yalnızca bir üründen kitapları kaldırabilirsiniz. Birden çok üründen kitapları kaldırmak için birden çok yükleme gerçekleştirmeniz gerekir.|
|/booklist|Hayır|Yönetilecek kitapların adlarını boşluklarla ayırarak belirtir. Değerler, yükleme medyasında listelenen kitap adlarından eşleşmeli.<br /><br /> Bu bağımsız değişkeni belirtmezseniz, /sourceURI'de belirtilen ürün için önerilen tüm kitaplar yüklenir.<br /><br /> Bir kitabın adı bir veya daha fazla boşluk içeriyorsa, listenin uygun şekilde sınırlandırılmış olması için çift tırnak içine alın (") .<br /><br /> Geçerli olmayan veya ulaşılamaz bir /sourceURI belirtirsiniz hata iletileri günlüğe kaydedilir.|
|/skuId|Hayır|Ürünün yükleme kaynağından stok tutma birimini (SKU) belirtir ve /SourceURI anahtarının tanımları olan kitapları filtreler.|
|/membership|Hayır|-   **Minimum**-- /skuId anahtarını kullanarak belirttiğiniz SKU'ya göre en düşük Yardım içeriği kümesi yüklenir. SKU ile içerik kümesi arasındaki eşleme, Hizmet API'sinde ortaya çıkar.<br />-   **Önerilen**—/skuId bağımsız değişkenlerini kullanarak belirttiğiniz SKU için bir dizi önerilen kitap yüklenir. Yükleme kaynağı hizmet API'si veya *'tir. MSHA*.<br />-   **Tam**-- /skuId bağımsız değişkenlerini kullanarak belirttiğiniz SKU için tüm kitap kümelerini yüklenir. Yükleme kaynağı hizmet API'si veya *'tir. MSHA*.|
|/locationpath|Hayır|Yerel Yardım içeriği için varsayılan klasörü belirtir. Bu anahtarı yalnızca içeriği yüklemek veya taşımak için kullanabilirsiniz. Bu anahtarı belirtirsiniz, /silent anahtarını da belirtmeniz gerekir.|
|/silent|Hayır|Kullanıcıya sorulmadan veya durum bildirim alanında simge de dahil olmak üzere herhangi bir kullanıcı arabirimini görüntülemeden Yardım içeriğini yükleyerek veya kaldırır. Çıkış *%Temp%* dizininde bir dosyaya kaydedilir. **Önemli:**  İçeriği sessiz bir şekilde yüklemek için *.mshc* dosyalarını *değil.cab* olarak imzalanan dosya dosyalarını kullanabilirsiniz.|
|/launchingApp|Hayır|Yardım görüntüleyicisi üst uygulama olmadan başlatıldıkları zaman uygulama ve katalog bağlamını tanımlar. Bu anahtarın bağımsız değişkenleri *CompanyName,* *ProductName* ve *VersionNumber 'dır* (örneğin, `/launchingApp Microsoft,VisualStudio,16.0` ).<br /><br /> Bu, /silent parametresiyle içerik yüklemek için gereklidir.|
|/wait *Saniye*|Hayır|Yükleme, kaldırma ve yenileme işlemlerini duraklatıyor. Katalog için devam eden bir işlem varsa, işlem devam etmek için verilen saniye sayısına kadar bekler. Süresiz olarak beklemek için 0 kullanın.|
|/?|Hayır|Yardım İçeriği Yöneticisi için komut satırı aracına ilişkin anahtarları ve açıklamalarını listeler.|

### <a name="exit-codes"></a>Çıkış kodları

Yardım İçeriği Yöneticisi için komut satırı aracını sessiz modda çalıştırarak aşağıdaki çıkış kodlarını döndürür:

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

- [Yardım Görüntüleyicisi yönetici kılavuzu](../help-viewer/administrator-guide.md)
- [Help Content Manager geçersiz kılmaları](../help-viewer/behavior-overrides.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)