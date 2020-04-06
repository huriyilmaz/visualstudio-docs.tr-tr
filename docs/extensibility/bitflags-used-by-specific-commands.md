---
title: Belirli Komutlar Tarafından Kullanılan Bit Bayrakları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740018"
---
# <a name="bitflags-used-by-specific-commands"></a>Belirli komutlar tarafından kullanılan Bit bayrakları
Kaynak Denetimi Eklentisi API'sindeki bir dizi işlevin davranışı, tek bir değerde bir veya daha fazla bit ayarlayarak değiştirilebilir. Bu değerler bit bayrakları olarak bilinir. Kaynak Denetimi Eklentisi API'si tarafından kullanılan çeşitli bit bayrakları burada ayrıntılı olarak açıklanır ve bunları kullanan işleve göre gruplanır.

## <a name="checked-out-flag"></a>Kullanıma alındı bayrağı
 Bu bayrak [SccAdd](../extensibility/sccadd-function.md) veya [SccCheckin](../extensibility/scccheckin-function.md)için ayarlanabilir.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Dosyayı kullanıma alanın.|

## <a name="add-flags"></a>Bayrak ekleme
 Bu bayraklar [SccAdd](../extensibility/sccadd-function.md)tarafından kullanılır.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Kaynak denetim eklentisinin dosyanın metin mi yoksa ikili mi olduğunu otomatik olarak algılaması beklenir.|
|`SCC_FILETYPE_TEXT`|0x01|Dosya türü metindir.|
|`SCC_FILETYPE_BINARY`|0x04|Dosya türü ikilidir. **Not:** `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` ve bayraklar birbirini dışlar.   Tam olarak bir veya ikisini ayarlayın.|
|`SCC_ADD_STORELATEST`|0x02|Yalnızca en son sürümü depolayın (delta yok).|

## <a name="diff-flags"></a>Diff bayrakları
 [SccDiff,](../extensibility/sccdiff-function.md) bir diff işleminin kapsamını tanımlamak için bu bayrakları kullanır. Bayraklar `SCC_DIFF_QD_xxx` birbirini dışlar. Bunlardan herhangi biri belirtilirse, o zaman hiçbir görsel geribildirim verilecektir. "Hızlı diff" (QD) olarak, eklenti dosyanın nasıl farklı olduğunu belirlemez, yalnızca farklıysa. Bu bayrakların hiçbiri belirtilmemişse, bir "görsel diff" yapılır; ayrıntılı dosya farklılıkları hesaplanır ve görüntülenir. İstenen QD desteklenmezse, eklenti bir sonraki en iyi sine geçer. Örneğin, IDE bir denetim um istiyorsa ve eklenti bunu desteklemiyorsa, eklenti tam içerik denetimi yapar (görsel ekrandan çok daha hızlı).

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Büyük/küçük harf farklılıklarını yoksay.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Beyaz boşluk farklılıklarını yoksay. **Not:**  Ve `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` bayraklar isteğe bağlı bit bayraklarıdır.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|Tüm dosya içeriğini karşılaştırarak QD.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD tarafından checksum.|
|`SCC_DIFF_QD_TIME`|0x0040|Dosya tarihi/saat damgası ile QD.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Bu, tüm QD bit bayraklarını kontrol etmek için kullanılan bir maskedir. Bir fonksiyona geçirilmemelidir; üç QD bit flags birbirini dışlar. QD her zaman Kullanıcı Aracı'nın görüntülenmesi anlamına gelir.|

## <a name="populatelist-flag"></a>PopulateList bayrağı
 Bu bayrak `fOptions` parametredeki [SccPopulateList](../extensibility/sccpopulatelist-function.md) tarafından kullanılır.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE dizinleri geçiyor, dosyaları değil.|

## <a name="populatedirlist-flags"></a>PopulateDirList bayrakları
 Bu bayraklar `fOptions` parametredeki [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) tarafından kullanılır.

|Opsiyon Değeri|Değer|Açıklama|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Dizinler için yalnızca bir dizin düzeyini inceleyin (bu varsayılandır).|
|SCC_PDL_RECURSIVE|0x0001|Verilen her dizin altındaki tüm dizinleri gözden geçirin.|
|SCC_PDL_INCLUDEFILES|0x0002|Sınav sürecine dosya adlarını ekleyin.|

## <a name="openproject-flags"></a>Project bayraklarını aç
 Bu bayraklar `dwFlags` parametrede [SccOpenProject](../extensibility/sccopenproject-function.md) tarafından kullanılır.

|Opsiyon Değeri|Değer|Açıklama|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Kaynak denetiminde proje yoksa, oluşturun. Bu bayrak ayarlanmamışsa, proje oluşturmasını `SCC_OP_SILENTOPEN` kullanıcıdan iste (bayrak belirtilmediği sürece).|
|SCC_OP_SILENTOPEN|0x0000002L|Kullanıcıdan proje oluşturmasını İsteme; sadece `SCC_E_UNKNOWNPROJECT`geri dön .|

## <a name="get-flags"></a>Bayrakları alın
 Bu bayraklar [SccGet](../extensibility/sccget-function.md) ve [SccCheckout](../extensibility/scccheckout-function.md)tarafından kullanılır.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE dizinleri değil, dosyaları geçiyor: Bu dizinlerde tüm dosyaları alın.|
|`SCC_GET_RECURSIVE`|0x0000002L|IDE dizinleri geçiyor: Bu dizinleri ve tüm alt dizinleri alın.|

## <a name="noption-values"></a>nOption değerleri
 Bu bayraklar `nOption` parametredeki [SccSetOption](../extensibility/sccsetoption-function.md) tarafından kullanılır.

|Bayrak|Değer|Açıklama|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Olay sırasının durumunu ayarlayın.|
|`SCC_OPT_USERDATA`|0x0000002L|Kullanıcı verilerini `SCC_OPT_NAMECHANGEPFN`belirtin.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE iptal işleyebilir.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Ad değişiklikleri için geri arama ayarlayın.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Kaynak denetimi eklentisi ui ödemedevre ve çalışma dizini ayarlamayın.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Çalışan bir dizini belirtmek için kaynak denetim sisteminden ekleyin. Doğrudan soyundan geliyorsa ilişkili projede paylaşmayı deneyin.|

## <a name="dwval-bitflags"></a>dwVal bit bayrakları
 Bu bayraklar `dwVal` parametredeki [SccSetOption](../extensibility/sccsetoption-function.md) tarafından kullanılır.

|Bayrak|Değer|Açıklama|Değere `nOption` göre kullanılır|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Olay sırası etkinliğini askıya alır.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Olay sırası günlüğe kaydetmeyi sağlar.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Varsayılan) İptal modu yoktur; istenirse eklenti temin etmelidir.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE iptal işlemlerini işler.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Varsayılan) Tamam plug-in UI kontrol etmek için; çalışma dizini ayarlanır.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Plug-in UI ödeme, çalışma dizini yok.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
