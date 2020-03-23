---
title: CodeIndex komutu
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bd2a6cc947c5f52212029bebe590d59906f5aee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591170"
---
# <a name="codeindex-command"></a>CodeIndex komutu

Team Foundation Server'da kod dizini oluşturmayı yönetmek için **CodeIndex** komutunu kullanın. Örneğin, CodeLens bilgilerini düzeltmek için dizini sıfırlamak veya sunucu performansı sorunlarını araştırmak için dizin oluşturmayı kapatmak isteyebilirsiniz.

## <a name="required-permissions"></a>Gerekli izinler

**CodeIndex** komutunu kullanmak için Takım Vakfı **Yöneticileri** güvenlik grubunun bir üyesi olmalısınız. [Bkz. Azure DevOps Hizmetleri ve TFS için tanımlanan İzinler ve gruplar.](/azure/devops/organizations/security/permissions?view=vsts)

> [!NOTE]
> Yönetim kimlik bilgileriyle oturum açsanız bile, bu komutu çalıştırmak için yükseltilmiş bir Komut İstem penceresi açmanız gerekir. Bu komutu Ekip Vakfı uygulama katmanından da çalıştırmalısınız.

## <a name="syntax"></a>Sözdizimi

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametreler

|**Bağımsız değişken**|**Açıklama**|
|------------------| - |
|`CollectionName`|Proje koleksiyonunun adını belirtir. Adın boşlukları varsa, adı tırnak işaretleriyle( örneğin Fabrikam Web Sitesi" ile kapa.|
|`CollectionId`|Proje koleksiyonunun kimlik numarasını belirtir.|
|`ServerPath`|Kod dosyasına giden yolu belirtir.|

|**Seçeneği**|**Açıklama**|
|----------------| - |
|**/indexingDurum**|Kod dizinioluşturma hizmetinin durumunu ve yapılandırmasını gösterin.|
|**/setIndexing:**[ &#124; kapalı &#124; keepupOnly ]|-   **on**: Tüm değişiklik kümelerini dizine almaya başlayın.<br />-   **off**: Tüm değişiklik kümelerini dizine almayı durdurun.<br />-   **keepupOnly**: Daha önce oluşturulmuş değişiklik kümelerini dizine almayı durdurun ve yalnızca yeni değişiklik kümelerini dizine almaya başlayın.|
|**/ignoreList:**[ ekle &#124; kaldır &#124; kaldırTüm &#124; görünümü ]`ServerPath`<br /><br /> Sunucu yolunun başında, sonunda veya her iki ucunda joker karakter (*) kullanabilirsiniz.|Dizine eklenmenizi istemediğiniz kod dosyalarının ve yollarının listesini belirtir.<br /><br /> -   **add**: Gözardı edilen dosya listesine dizine eklenmesini istemediğiniz dosyayı ekleyin.<br />-   **remove**: Gözardı edilen dosya listesinden dizine ekstre olmasını istediğiniz dosyayı kaldırın.<br />-   **removeAll**: Gözardı edilen dosya listesini temizleyin ve tüm dosyaları dizine eklemeye başlayın.<br />-   **view**: Dizine ekitolmayan tüm dosyaları görün.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|KB'de belirtilen boyutu aşan belirtilen dosya sayısını gösterir. Daha sonra bu dosyaları dizin oluşturmayı hariç tutmak için **/ignoreList** seçeneğini kullanabilirsiniz.|
|**/reindexTümü**|Daha önce dizine alınan verileri temizleyin ve dizin oluşturmayı yeniden başlatın.|
|**/destroyCodeIndex [/noPrompt]**|Kod dizini silin ve tüm dizinlenmiş verileri kaldırın. **/noPrompt** seçeneğini kullanıyorsanız onay gerektirmez.|
|**/temporaryDataSizeLimit**:[ `SizeInGBs` &#124; <> &#124; devre dışı ]|Değişiklik kümelerini işlerken CodeLens'in ne kadar geçici veri oluşturduğunu denetleyin. Varsayılan sınır 2 GB'dır.<br /><br /> -   **görünüm**: Geçerli boyut sınırını göster.<br />-   `SizeInGBs`: Boyut sınırını değiştirin.<br />-   **disable**: Boyut sınırını kaldırın.<br /><br /> Bu sınır, CodeLens yeni bir değişiklik kümesini işletmeden önce denetlenir. Geçici veriler bu sınırı aşarsa, CodeLens yenilerini değil, geçmiş değişiklik kümelerini işlemeyi duraklatır. CodeLens, veriler temizlendikten ve bu sınırın altına düştükten sonra işlemeye yeniden başlayacaktır. Temizleme günde bir kez otomatik olarak çalışır. Bu, temizleme çalışmaya başlayana kadar geçici verilerin bu sınırı aşabileceği anlamına gelir.|
|**/indexHistoryPeriod**:[ tüm `NumberOfMonths` &#124; <> &#124; görüntüle ]|Değişiklik geçmişinizi ne kadar süreyle dizine ekeceğinikontrol edin. Bu, CodeLens'in size ne kadar tarih gösterdiğini etkiler. Varsayılan sınır 12 aydır. Bu, CodeLens'in yalnızca son 12 aylık değişim geçmişinizi gösterdiği anlamına gelir.<br /><br /> -   **görünüm**: Geçerli ay sayısını göster.<br />-   **all**: Tüm değişim geçmişini dizine dizine dizin.<br />-   `NumberOfMonths`: Dizin değişikliği geçmişini dizine almak için kullanılan ay sayısını değiştirin.|
|**/collectionName:**`CollectionName`|**CodeIndex** komutunu çalıştıracak proje koleksiyonunun adını belirtir. **/CollectionId**kullanmıyorsanız gereklidir.|
|**/collectionId:**`CollectionId`|**CodeIndex** komutunu çalıştıracak proje koleksiyonunun kimlik numarasını belirtir. **/CollectionName**kullanmıyorsanız gereklidir.|

## <a name="examples"></a>Örnekler

> [!NOTE]
> Burada adı geçen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve olaylar hayal ürünüdür.  Herhangi bir gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yerler veya olaylar ile hiçbir ilişki amaçlanmamıştır veya çıkarılmalıdır.

Kod dizini oluşturma durumunu ve yapılandırmasını görmek için:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Tüm değişiklik kümelerini dizine ekinlemeye başlamak için:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Daha önce oluşturulmuş değişiklik kümelerini dizine almayı durdurmak ve yalnızca yeni değişiklik kümelerini dizine almaya başlamak için:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

10 KB'den büyük 50 dosyayı bulmak için:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Belirli bir dosyayı dizin oluşturmayı hariç tutmak ve göz ardı edilen dosya listesine eklemek için:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Dizine eklenmemiş tüm dosyaları görmek için:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Daha önce dizine eklenmiş verileri temizlemek ve dizin oluşturmayı yeniden başlatmak için:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Tüm değişiklik kümesi geçmişini kaydetmek için:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

CodeLens geçici verilerinin boyut sınırını kaldırmak ve geçici veri boyutundan bağımsız olarak dizine devam etmek için:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Onay ile kod dizini silmek için:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Ayrıca bkz.

- [CodeLens ile kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)
- [TFSConfig ile sunucu yapılandırmalarını yönetme](/azure/devops/server/command-line/tfsconfig-cmd)
