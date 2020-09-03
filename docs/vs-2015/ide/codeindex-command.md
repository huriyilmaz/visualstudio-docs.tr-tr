---
title: CodeIndex komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 070106dc4db0f5200c1346bbbf8c0b653aa104e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619673"
---
# <a name="codeindex-command"></a>CodeIndex Komutu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Team Foundation Server kod dizinlemeyi yönetmek için **CodeIndex** komutunu kullanın. Örneğin, CodeLens bilgilerini onarmak için dizini sıfırlamak veya sunucu performans sorunlarını araştırmak için dizin oluşturmayı devre dışı bırakmak isteyebilirsiniz.

 **Gerekli Izinler**

 **CodeIndex** komutunu kullanmak Için, **Team Foundation yöneticileri** güvenlik grubunun bir üyesi olmanız gerekir. [Team Foundation Server Için izin başvurusu](https://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6)' na bakın.

> [!NOTE]
> Yönetici kimlik bilgileriyle oturum açmış olsanız bile, bu komutu çalıştırmak için yükseltilmiş bir komut Istemi penceresi açmalısınız. Ayrıca, bu komutu Team Foundation uygulama katmanından çalıştırmanız gerekir.

## <a name="syntax"></a>Söz dizimi

```
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

#### <a name="parameters"></a>Parametreler

|**Değişkendir**|**Açıklama**|
|------------------|---------------------|
|`CollectionName`|Takım projesi koleksiyonunun adını belirtir. Adda boşluk varsa, adı tırnak işaretleri (örneğin, "Fabrikam Web sitesi") arasına alın.|
|`CollectionId`|Takım projesi koleksiyonunun kimlik numarasını belirtir.|
|`ServerPath`|Bir kod dosyasının yolunu belirtir.|

|**Seçenek**|**Açıklama**|
|----------------|---------------------|
|**/IndexingStatus**|Kod dizin oluşturma hizmetinin durumunu ve yapılandırmasını görüntüleyin.|
|**/setIndexing:**[&#124; kapalı &#124; yalnızca keepupOnly]|-   **Açık**: tüm değişiklik kümelerini dizine almayı Başlat.<br />-   **kapalı**: tüm değişiklik kümelerini dizinlemeyi durdur.<br />-   **keepupOnly**: önceden oluşturulmuş değişiklik kümelerinin dizinini oluşturmayı Durdur ve yalnızca yeni değişiklik kümelerini dizine almayı Başlat.|
|**/IgnoreList:**[Ekle &#124; kaldır &#124; removeall &#124; görünümü] `ServerPath`<br /><br /> Sunucu yolunun başlangıcında, sonunda veya her iki ucunda joker karakteri (*) kullanabilirsiniz.|Dizinlenmesini istemediğiniz kod dosyalarının ve yollarının listesini belirtir.<br /><br /> -   **Ekle**: dizinlenmesini istemediğiniz dosyayı, yoksayılan dosya listesine ekleyin.<br />-   **Kaldır**: dizine alınmasını istediğiniz dosyayı yoksayılan dosya listesinden kaldırın.<br />-   **RemoveAll**: yoksayılan dosya listesini temizleyin ve tüm dosyaları dizine almayı başlatın.<br />-   **görüntüle**: dizinlenmemiş tüm dosyaları görüntüleyin.|
|**/listlargefiles [/FileCount:** `FileCount` **/MinSize:** `MinSize` ]|KB cinsinden belirtilen boyutu aşan belirtilen dosya sayısını gösterir. Daha sonra bu dosyaları dizin oluşturma işleminden dışlamak için **/IgnoreList** seçeneğini kullanabilirsiniz.|
|**/Reındexall**|Önceden dizinli verileri temizleyin ve Dizin oluşturmayı yeniden başlatın.|
|**/Destroyıcodeındex [/noPrompt]**|Kod dizinini silin ve tüm dizinli verileri kaldırın. **/Noprompt** seçeneğini kullanırsanız onay gerektirmez.|
|**/temporaryDataSizeLimit**: [görünüm &#124; <`SizeInGBs`> &#124; devre dışı]|Değişiklik kümelerini işlerken CodeLens 'in ne kadar geçici veri oluşturduğunu denetleyin. Varsayılan sınır 2 GB 'dir.<br /><br /> -   **görüntüle**: geçerli boyut sınırını göster.<br />-   `SizeInGBs`: Boyut sınırını değiştirin.<br />-   **devre dışı bırak**: boyut sınırını kaldır.<br /><br /> Bu sınır, CodeLens yeni bir değişiklik kümesini işleyerek denetlenir. Geçici veriler bu sınırı aşarsa, CodeLens, yenilerini değil, geçmiş değişiklik kümelerini işlemeyi duraklatacaktır. CodeLens, veriler temizlendikten ve bu sınırın altına düştüğünde işlemeyi yeniden başlatacak. Temizleme, günde bir kez otomatik olarak çalıştırılır. Bu, temizleme çalışmaya başlamadan geçici verilerin bu sınırı aşabileceği anlamına gelir.|
|**/ındexgeçmişini**: [&#124; tüm &#124; <> görüntüleme `NumberOfMonths` ]|Değişiklik geçmişinizin ne kadar süreyle dizine alınacağını denetleyin. Bu, ne kadar geçmiş CodeLens 'in size gösterdiği geçmişi etkiler. Varsayılan sınır 12 aydır. Bu, CodeLens 'in yalnızca son 12 aydan değişiklik geçmişinizi gösterdiği anlamına gelir.<br /><br /> -   **görüntüle**: geçerli ay sayısını göster.<br />-   **All**: tüm değişiklik geçmişinin dizinini oluştur.<br />-   `NumberOfMonths`: Değişiklik geçmişine dizin eklemek için kullanılan ayların sayısını değiştirin.|
|**/CollectionName:**`CollectionName`|**CodeIndex** komutunun çalıştırılacağı takım projesi koleksiyonunun adını belirtir. **/CollectionId**kullanmıyorsanız gereklidir.|
|**/CollectionId:**`CollectionId`|**CodeIndex** komutunun çalıştırılacağı takım projesi koleksiyonunun kimlik numarasını belirtir. **/CollectionName**kullanmıyorsanız gereklidir.|

## <a name="examples"></a>Örnekler

> [!NOTE]
> Burada adı geçen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve olaylar hayal ürünüdür.  Herhangi bir gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olay ile ilişki amaçlanmamıştır.

 Kod dizini oluşturma durumunu ve yapılandırmasını görmek için:

```
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"
```

 Tüm değişiklik kümelerini dizine almayı başlatmak için:

```
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"
```

 Önceden oluşturulmuş değişiklik kümelerinin dizinini oluşturmayı durdurmak ve yalnızca yeni değişiklik kümelerini dizine almayı başlatmak için:

```
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"
```

 10 KB 'den büyük 50 dosya bulmak için:

```
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"
```

 Dizin oluşturma işleminden belirli bir dosyayı dışlamak ve yoksayılan dosya listesine eklemek için:

```
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"
```

 Dizini oluşturulmamış tüm dosyaları görmek için:

```
TFSConfig CodeIndex /ignoreList:view
```

 Önceden dizinli verileri temizlemek ve Dizin oluşturmayı yeniden başlatmak için:

```
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"
```

 Tüm değişiklik kümesi geçmişini kaydetmek için:

```
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"
```

 CodeLens geçici verilerinde boyut sınırını kaldırmak ve geçici veri boyutundan bağımsız olarak dizin oluşturmaya devam etmek için:

```
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"
```

 Kod dizinini onaylama ile silmek için:

```
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [TFS Için TFSConfig komut satırı araçlarıyla](https://msdn.microsoft.com/be8c997a-b97b-4e59-97f5-04db0a601a6c) [sunucu yapılandırmasını yönetme](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)
