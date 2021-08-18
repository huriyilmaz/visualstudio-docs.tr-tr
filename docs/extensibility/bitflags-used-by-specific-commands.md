---
title: Belirli komutlar tarafından kullanılan bitflags | Microsoft Docs
description: Kaynak denetimi eklentisi API 'SI tarafından kullanılan ve bunları kullanan işlev tarafından düzenlenen bitflags hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 12adec8bbaad32d801de2dabdfb792bc1cc196ecce47a0cbfb35cb84052def21
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452673"
---
# <a name="bitflags-used-by-specific-commands"></a>Belirli komutlar tarafından kullanılan bitflags
Kaynak denetimi eklentisi API 'sindeki bir dizi işlevin davranışı tek bir değerde bir veya daha fazla bit ayarlanarak değiştirilebilir. Bu değerler bitflags olarak bilinir. Kaynak denetimi eklentisi API 'SI tarafından kullanılan çeşitli bitflags burada, bunları kullanan işleve göre gruplanmış olarak ayrıntılıdır.

## <a name="checked-out-flag"></a>Kullanıma alınan bayrak
 Bu bayrak, [SccAdd](../extensibility/sccadd-function.md) veya [SccCheckin](../extensibility/scccheckin-function.md)için ayarlanabilir.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Dosyayı kullanıma alınmış olarak tutun.|

## <a name="add-flags"></a>Bayrak Ekle
 Bu bayraklar [SccAdd](../extensibility/sccadd-function.md)tarafından kullanılır.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|-|Kaynak denetimi eklentisinin, dosyanın metin mi yoksa ikili mi olduğunu otomatik olarak algılaması beklenmektedir.|
|`SCC_FILETYPE_TEXT`|0x01|Dosya türü metindir.|
|`SCC_FILETYPE_BINARY`|0x04|Dosya türü binary. **Note:** `SCC_FILETYPE_TEXT` ve `SCC_FILETYPE_BINARY` bayrakları birbirini dışlıyor.   Tam olarak bir veya hiçbiri olarak ayarlayın.|
|`SCC_ADD_STORELATEST`|0x02|Yalnızca en son sürümü depola (deltas olmadan).|

## <a name="diff-flags"></a>Fark bayrakları
 [SccDiff](../extensibility/sccdiff-function.md) , bir fark işleminin kapsamını tanımlamak için bu bayrakları kullanır. `SCC_DIFF_QD_xxx`Bayraklar birbirini dışlıyor. Bunlardan herhangi biri belirtilmişse, hiçbir görsel geri bildirim verilsağlanmaz. Bir "hızlı fark" (QD) içinde eklenti, dosyanın farklı olduğunu, ancak farklı olduğunu belirlemez. Bu bayraklardan Hiçbiri belirtilmediyse, "görsel fark" yapılır; ayrıntılı dosya farklılıkları hesaplanır ve görüntülenir. İstenen QTıD desteklenmiyorsa, eklenti bir sonraki en iyi ifadeye gider. Örneğin, IDE bir sağlama toplamı isterse ve eklenti bunu desteklemiyorsa, eklenti tam içerik denetimi yapar (bir görsel ekranda hala çok daha hızlıdır).

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Büyük/küçük harf farklılıklarını yoksayın.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Boşluk farklarını yoksayın. **Note:**  `SCC_DIFF_IGNORECASE` Ve `SCC_DIFF_IGNORESPACE` bayrakları isteğe bağlı bitflags.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|Tüm dosya içeriklerini karşılaştırarak QD.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|Sağlama toplamı ile QD.|
|`SCC_DIFF_QD_TIME`|0x0040|Dosya tarih/saat damgasına göre QD.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Bu, tüm QD bit bayraklarını denetlemek için kullanılan bir maskedir. Bir işleve geçirilmemelidir; Üç QD bitflags birbirini dışlıyor. QD her zaman UI gösterimi anlamına gelir.|

## <a name="populatelist-flag"></a>PopulateList bayrağı
 Bu bayrak, parametresindeki [SccPopulateList](../extensibility/sccpopulatelist-function.md) tarafından kullanılır `fOptions` .

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE, dosyaları değil dizinleri geçiyor.|

## <a name="populatedirlist-flags"></a>PopulateDirList bayrakları
 Bu bayraklar, parametresindeki [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) tarafından kullanılır `fOptions` .

|Seçenek değeri|Değer|Açıklama|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Dizinler için yalnızca bir dizin düzeyini inceleyin (bu varsayılandır).|
|SCC_PDL_RECURSIVE|0x0001|Belirli her bir dizin altındaki tüm dizinleri yinelemeli olarak inceleyin.|
|SCC_PDL_INCLUDEFILES|0x0002|İnceleme işlemine dosya adlarını ekleyin.|

## <a name="openproject-flags"></a>OpenProject bayrakları
 Bu bayraklar, parametresindeki [SccOpenProject](../extensibility/sccopenproject-function.md) tarafından kullanılır `dwFlags` .

|Seçenek değeri|Değer|Açıklama|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Proje kaynak denetiminde yoksa, oluşturun. Bu bayrak ayarlanmamışsa, projenin Kullanıcı tarafından oluşturulmasını sor ( `SCC_OP_SILENTOPEN` bayrak belirtilmediyse).|
|SCC_OP_SILENTOPEN|0x00000002L|Kullanıcının bir proje oluşturmasını isteme; yalnızca geri dönün `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Bayrakları al
 Bu bayraklar [SccGet](../extensibility/sccget-function.md) ve [SccCheckout](../extensibility/scccheckout-function.md)tarafından kullanılır.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE, dosyaları değil, dizinleri geçiyor: bu dizinlerdeki tüm dosyaları al.|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE, dizinleri geçiyor: Bu dizinleri ve tüm alt dizinlerini al.|

## <a name="noption-values"></a>Önemli değerler
 Bu bayraklar, parametresindeki [SccSetOption](../extensibility/sccsetoption-function.md) tarafından kullanılır `nOption` .

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Olay kuyruğu durumunu ayarlayın.|
|`SCC_OPT_USERDATA`|0x00000002L|için kullanıcı verilerini `SCC_OPT_NAMECHANGEPFN` belirtin.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE iptal işlemini işebilir.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ad değişiklikleri için bir geri çağırma ayarlayın.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Kaynak denetimi eklentisi kullanıcı arabirimini devre dışı bırakma ve çalışma dizini ayarlama.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Çalışma dizini belirtmek için kaynak denetim sisteminden ekleyin. Doğrudan alt kullanıcı ise ilişkili projeyle paylaşmayı deneyin.|

## <a name="dwval-bitflags"></a>dwVal bitflags
 Bu bayraklar parametresinde [SccSetOption](../extensibility/sccsetoption-function.md) tarafından `dwVal` kullanılır.

|Bayrak|Değer|Açıklama|Değere göre `nOption` kullanılır|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Olay kuyruğu etkinliğini askıya alır.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Olay kuyruğu günlüğünü sağlar.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Varsayılan) İptal modu yoktur; eklentinin istenirse temini gerekir.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE iptal işlemini işler.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Varsayılan) Eklenti kullanıcı arabiriminden kontrol etmek için tamam; çalışma dizini ayarlanmıştır.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Eklenti kullanıcı arabirimini alma yok, çalışma dizini yok.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
