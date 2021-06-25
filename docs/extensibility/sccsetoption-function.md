---
description: Bu işlev, kaynak denetimi eklentisinin davranışını kontrol altına alan seçenekleri ayarlar.
title: SccSetOption İşlev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18e33cbb8dbee9b332456826ed33e46e4d2e76de
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904106"
---
# <a name="sccsetoption-function"></a>SccSetOption İşlevi
Bu işlev, kaynak denetimi eklentisinin davranışını kontrol altına alan seçenekleri ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Parametreler
 pvContext

[in] Kaynak denetimi eklentisi bağlam yapısı.

 nOption

[in] Ayar olan seçenek.

 dwVal

[in] Seçeneğin ayarları.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisinin aşağıdaki değerlerden birini dönmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Seçenek başarıyla ayarlanmıştır.|
|SCC_I_SHARESUBPROJOK|ise `nOption` döndürülür `SCC_OPT_SHARESUBPROJ` ve kaynak denetimi eklentisi, IDE'nin hedef klasörü ayarlamaya izin verir.|
|SCC_E_OPNOTSUPPORTED|seçeneği ayarlanmaz ve bu ayara bağlı değildir.|

## <a name="remarks"></a>Açıklamalar
 IDE, kaynak denetimi eklentisinin davranışını kontrol etmek için bu işlevi çağıran bir işlevdir. İlk parametresi, `nOption` ayarda olan değeri belirtirken, ikinci parametresi ise bu `dwVal` değerle ne yapacaklarını belirtir. Eklenti ile ilişkili bu bilgileri depolar, bu nedenle `pvContext``,` [IDE'nin SccInitialize](../extensibility/sccinitialize-function.md) çağrısında bulunduktan sonra bu işlevi çağırmış olması gerekir (ancak [SccOpenProject'e](../extensibility/sccopenproject-function.md)yapılan her çağrıdan sonra olması gerekmez).

 Seçeneklerin ve değerlerinin özeti:

|`nOption`|`dwValue`|Açıklama|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Arka plan olay kuyruğa alma özelliğini etkinleştirme/devre dışı bırakma.|
|`SCC_OPT_USERDATA`|Rastgele değer|OPTNAMECHANGEPFN geri çağırma [işlevine geçirilme bir kullanıcı](../extensibility/optnamechangepfn.md) değeri belirtir.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE'nin şu anda bir işlemi iptal etme desteği olup olmadığını gösterir.|
|`SCC_OPT_NAMECHANGEPFN`|[OPTNAMECHANGEPFN geri çağırma işlevinin](../extensibility/optnamechangepfn.md) işaretçisi|Bir ad değişikliği geri çağırma işlevinin işaretçisini ayarlar.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE'nin dosyaları el ile kullanıma alanın (kaynak denetimi kullanıcı arabirimi aracılığıyla) veya yalnızca kaynak denetim eklentisi aracılığıyla kullanıma alınmış olması gerekip gerek olmadığını gösterir.|
|`SCC_OPT_SHARESUBPROJ`|Yok|Kaynak denetimi eklentisi IDE'nin yerel proje klasörünü belirtmesini sağlarsa eklenti `SCC_I_SHARESUBPROJOK` döndürür.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 ise, `nOption` `SCC_OPT_EVENTQUEUE` IDE arka plan işlemeyi devre dışı bırakıyor (veya yeniden etkinleştirmektedir). Örneğin, derleme sırasında IDE, kaynak denetim eklentisine herhangi bir tür boşta işlemeyi durdurma talimatı ve olabilir. Derlemeden sonra, eklentinin olay kuyruğu güncel tutmak için arka plan işlemeyi yeniden etkinleştirir. değerine karşılık gelen , ve için iki olası `SCC_OPT_EVENTQUEUE` `nOption` değer `dwVal` `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE` vardır.

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 değeri `nOption` `SCC_OPT_HASCANCELMODE` ise, IDE kullanıcıların uzun işlemleri iptal etmelerini sağlar. olarak `dwVal` `SCC_OPT_HCM_NO` (varsayılan) ayarı, IDE'nin iptal moduna sahip olmadığını gösterir. Kaynak denetimi eklentisinin, kullanıcının iptal etmesini istiyorsa kendi İptal düğmesini sunmalıdır. `SCC_OPT_HCM_YES` IDE'nin bir işlemi iptal etme olanağı sağladığını gösterir, bu nedenle SCC eklentisinin kendi İptal düğmesini görüntülemesi gerekmeyebilirsiniz. IDE olarak ayarlarsa, yanıt vermeye ve geri çağırma işlevine gönderilen iletilere `dwVal` `SCC_OPT_HCM_YES` `SCC_MSG_STATUS` `DOCANCEL` `lpTextOutProc` hazırlanır (bkz. [LPTEXTOUTPROC).](../extensibility/lptextoutproc.md) IDE bu değişkeni ayarlamazsa eklenti bu iki iletileri göndermez.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 nOption olarak ayarlanırsa ve hem kaynak denetimi eklentisi hem de IDE buna izin verdiyse, eklenti bir kaynak denetimi işlemi sırasında bir dosyayı yeniden adlandırarak veya `SCC_OPT_NAMECHANGEPFN` hareket ettirebilirsiniz. , `dwVal` [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)türünde bir işlev işaretçisine ayarlanır. Bir kaynak denetimi işlemi sırasında eklenti bu işlevi çağırarak üç parametre iletir. Bunlar bir dosyanın eski adı (tam yol ile), bu dosyanın yeni adı (tam yol ile) ve IDE ile ilgisi olan bilgilerin işaretçisidir. IDE, veriye işaret ediyor olarak ayarlanmış `SccSetOption` çağrısıyla `nOption` bu son `SCC_OPT_USERDATA` `dwVal` işaretçiyi gönderir. Bu işlev için destek isteğe bağlıdır. Bu özelliği kullanan bir VSSCI eklentisinin işlev işaretçisini ve kullanıcı veri değişkenlerini 'de başlatması ve verilen bir yeniden adlandırma işlevini `NULL` çağırması gerekir. Ayrıca verilen değeri tutmak veya yeni bir çağrısına yanıt olarak değiştirmek için hazır olması `SccSetOption` gerekir. Bu, bir kaynak denetimi komut işlemi ortasında olmaz, ancak komutlar arasında olabilir.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 nOption olarak ayarlanırsa, IDE şu anda açık olan projede yer alan dosyaların hiçbir zaman kaynak denetim sisteminin kullanıcı arabirimi aracılığıyla el ile kullanıma `SCC_OPT_SCCCHECKOUTONLY` açılmaması gerektiğini belirtir. Bunun yerine, dosyalar yalnızca IDE denetimi altındaki kaynak denetimi eklentisi aracılığıyla kullanıma alınmış olması gerekir. olarak ayarlanırsa, dosyaların eklenti tarafından normal şekilde ele alınmalıdır ve kaynak denetimi kullanıcı arabirimi üzerinden `dwValue` `SCC_OPT_SCO_NO` kullanıma alınabilirsiniz. olarak ayarlanırsa, yalnızca eklentinin dosyaları denetlemesine izin verilir ve kaynak denetim sisteminin `dwValue` `SCC_OPT_SCO_YES` kullanıcı arabirimi çağrılmamalıdır. Bu, IDE'nin yalnızca IDE aracılığıyla göz atarak anlamlı olan "sözde dosyalar" olabileceği durumlar için kullanılır.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 olarak ayarlanırsa, IDE kaynak denetiminden dosya eklerken kaynak denetimi eklentisinin belirtilen bir yerel klasörü `nOption` `SCC_OPT_SHARESUBPROJ` kullanıp kullana olmadığını test ediyor. Bu durumda `dwVal` parametrenin değeri önemli değildir. Eklenti, IDE'nin [SccAddFromScc](../extensibility/sccaddfromscc-function.md) çağrıldığda dosyaların kaynak denetiminden eklenmiştir yerel hedef klasörü belirtmeye izin verirse, işlev çağrıldığnda eklentinin dönmesi `SCC_I_SHARESUBPROJOK` `SccSetOption` gerekir. Ardından IDE, `lplpFileNames` hedef klasörü `SccAddFromScc` geçmek için işlevinin parametresini kullanır. Eklenti, kaynak denetiminden eklenen dosyaları yerk için bu hedef klasörü kullanır. Seçenek ayarlanırken eklenti geri dönmezse, IDE eklentinin yalnızca geçerli yerel klasöre dosya `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` ekleye olduğunu varsayer.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
