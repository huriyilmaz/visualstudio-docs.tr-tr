---
title: CodeIndex komutu
description: CodeIndex komutunu kullanarak Azure DevOps Server 'de (eski adıyla Team Foundation Server).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a16d1ec94ad958f7a93b061c23650148fe38398d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056335"
---
# <a name="codeindex-command"></a>CodeIndex komutu

Kod **dizinini yönetmek için CodeIndex** komutunu Team Foundation Server. Örneğin, CodeLens bilgilerini düzeltmek için dizini sıfırlamak veya sunucu performansı sorunlarını araştırmak için dizin oluşturmayı kapatmak istiyor olabilir.

## <a name="required-permissions"></a>Gerekli izinler

**CodeIndex komutunu** kullanmak için Team Foundation Administrators güvenlik **grubunun bir üyesisiniz.** Bkz. [Azure DevOps Services ve TFS için tanımlanan izinler ve gruplar.](/azure/devops/organizations/security/permissions?view=vsts&preserve-view=true)

> [!NOTE]
> Yönetici kimlik bilgileriyle oturum açsanız bile, bu komutu çalıştırmak için yükseltilmiş bir Komut İstemi penceresi açabilirsiniz. Bu komutu Team Foundation için uygulama katmanından da çalıştırabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametreler

|**Bağımsız değişken**|**Açıklama**|
|------------------| - |
|`CollectionName`|Proje koleksiyonunun adını belirtir. Ad boşluk içeriyorsa, adı tırnak işaretleriyle (örneğin, "Fabrikam Web Sitesi") içine alın.|
|`CollectionId`|Proje koleksiyonunun kimlik numarasını belirtir.|
|`ServerPath`|Bir kod dosyasının yolunu belirtir.|

|**Seçenek**|**Açıklama**|
|----------------| - |
|**/indexingStatus**|Kod dizini oluşturma hizmetinin durumunu ve yapılandırmasını gösterir.|
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **üzerinde:** Tüm değişiklik kümeleri için dizin oluşturmaya başlama.<br />-   **off:** Tüm değişiklik kümeleri için dizin oluşturmayı durdurun.<br />-   **keepupOnly:** Önceden oluşturulmuş değişiklik kümeleri için dizin oluşturmayı durdurun ve yalnızca yeni değişiklik kümeleri için dizin oluşturmaya başlayabilirsiniz.|
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> Sunucu yolunun başında, sonunda veya her iki ucunda (*) joker karakterini kullanabilirsiniz.|Kod dosyalarının listesini ve dizine almak istemeyebilirsiniz yollarını belirtir.<br /><br /> -   **add:** Dizine alınmak istediğiniz dosyayı yoksayılan dosya listesine ekleyin.<br />-   **remove:** Yoksayılan dosya listesinden dizine almak istediğiniz dosyayı kaldırın.<br />-   **removeAll:** Yoksayılan dosya listesini silin ve tüm dosyaların dizinini dizine eklemeye başlama.<br />-   **view:** Dizine olmayan tüm dosyaları görme.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize` ]|KB'de belirtilen boyutu aşan belirtilen dosya sayısını gösterir. Ardından bu dosyaları dizin oluşturmanın dışında tutmak için **/ignoreList** seçeneğini kullanabilirsiniz.|
|**/reindexAll**|Daha önce dizine alan verileri temizleme ve dizin oluşturmayı yeniden başlatma.|
|**/destroyCodeIndex [/noPrompt]**|Kod dizinini silin ve tüm dizine verileri kaldırın. **/noPrompt seçeneğini kullanırsanız onay gerektirmez.**|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|Değişiklik kümeleri işleme sırasında CodeLens'in oluşturduğu geçici verinin ne kadar olduğunu denetleme. Varsayılan sınır 2 GB'tır.<br /><br /> -   **view:** Geçerli boyut sınırını gösterir.<br />-   `SizeInGBs`: Boyut sınırını değiştirme.<br />-   **disable:** Boyut sınırını kaldırın.<br /><br /> CodeLens yeni bir değişiklik kümesi işlemeden önce bu sınır denetlenir. Geçici veriler bu sınırı aşarsa CodeLens yenileri değil, geçmiş değişiklik kümeleri işlemeyi duraklatacak. Veriler temizlendikten ve bu sınırın altına düştüğünde CodeLens işlemi yeniden başlatacak. Temizleme işlemi günde bir kez otomatik olarak çalışır. Bu, temizleme çalışmaya başlayana kadar geçici verilerin bu sınırı aş olabileceği anlamına gelir.|
|**/indexHistoryPeriod**:[ görünüm &#124; tüm &#124; <`NumberOfMonths`> ]|Değişiklik geçmişinizin ne kadar süreyle dizine alalı olduğunu denetleme. Bu, CodeLens'in size ne kadar geçmiş gösterir olduğunu etkiler. Varsayılan sınır 12 aydır. Bu, CodeLens'in yalnızca son 12 aya göre değişiklik geçmişinizi gösterir.<br /><br /> -   **view:** Geçerli ay sayısını gösterir.<br />-   **all:** Tüm değişiklik geçmişini dizinleme.<br />-   `NumberOfMonths`: Değişiklik geçmişinin dizinini oluşturmada kullanılan ay sayısını değiştirme.|
|**/collectionName:**`CollectionName`|**CodeIndex** komutunun çalıştırılamayacak proje koleksiyonunun adını belirtir. **/CollectionId** kullanıyorsanız gereklidir.|
|**/collectionId:**`CollectionId`|**CodeIndex** komutunun çalıştırılamayacak proje koleksiyonunun kimlik numarasını belirtir. **/CollectionName** kullanasanız gereklidir.|

## <a name="examples"></a>Örnekler

> [!NOTE]
> Burada adı geçen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve olaylar hayal ürünüdür.  Hiçbir gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olayla ilişki amaçlanan veya alınmalıdır.

Kod dizini oluşturma durumunu ve yapılandırmasını görmek için:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Tüm değişiklik kümeleri için dizin oluşturma başlatmak için:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Daha önce oluşturulan değişiklik kümeleri için dizin oluşturmayı durdurmak ve yalnızca yeni değişiklik kümeleri için dizin oluşturma başlatmak için:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

10 KB'den büyük 50'ye kadar dosya bulmak için:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Belirli bir dosyayı dizin oluşturmanın dışında tutmak ve yoksayılan dosya listesine eklemek için:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Dizine olmayan tüm dosyaları görmek için:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Daha önce dizine alan verileri temizlemek ve dizin oluşturmayı yeniden başlatmak için:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Tüm değişiklik kümesi geçmişini kaydetmek için:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

CodeLens geçici verilerinde boyut sınırını kaldırmak ve geçici veri boyutundan bağımsız olarak dizine eklemeye devam etmek için:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Onay ile kod dizinini silmek için:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Ayrıca bkz.

- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)
- [TFSConfig ile sunucu yapılandırmasını yönetme](/azure/devops/server/command-line/tfsconfig-cmd)
