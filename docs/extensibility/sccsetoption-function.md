---
title: SccSetOption Fonksiyonu | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700306"
---
# <a name="sccsetoption-function"></a>SccSetOption İşlevi
Bu işlev, kaynak denetim eklentisinin davranışını denetleyen seçenekler ayarlar.

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

[içinde] Kaynak denetimi eklentisi bağlam yapısı.

 nOption

[içinde] Ayarlanan seçenek.

 dwVal

[içinde] Seçenek için ayarlar.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetim eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Seçenek başarıyla ayarlandı.|
|SCC_I_SHARESUBPROJOK|`nOption` Döndürülürve `SCC_OPT_SHARESUBPROJ` kaynak denetim eklentisi IDE'nin hedef klasörü ayarlamasına olanak tanır.|
|SCC_E_OPNOTSUPPORTED|Seçenek ayarlı değildi ve güvenilen olmamalıdır.|

## <a name="remarks"></a>Açıklamalar
 IDE, kaynak denetim eklentisinin davranışını denetlemek için bu işlevi çağırır. İlk parametre, `nOption`ayarlanan değeri gösterirken, `dwVal`ikincisi, bu değerle ne yapacağını gösterir. Eklenti, bu bilgileri bir `pvContext``,` ile ilişkili olarak depolar, böylece IDE [SccInitialize'ı](../extensibility/sccinitialize-function.md) aradıktan sonra bu işlevi aramalıdır (ancak [SccOpenProject'e](../extensibility/sccopenproject-function.md)yapılan her çağrıdan sonra mutlaka gerekmez).

 Seçeneklerin ve değerlerinin özeti:

|`nOption`|`dwValue`|Açıklama|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Arka plan olayı nın sıraya lanmasını etkinleştiriyor/devre dışı kılabilir.|
|`SCC_OPT_USERDATA`|Rasgele değer|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) geri çağırma işlevine geçirilecek bir kullanıcı değerini belirtir.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE'nin bir işlemi iptal etmek için şu anda destekleyip desteklemediğini gösterir.|
|`SCC_OPT_NAMECHANGEPFN`|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) geri çağırma işleviniişaretçi|Ad değiştirme geri arama işleviiçin bir işaretçi ayarlar.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE'nin dosyalarının el ile (kaynak denetimi kullanıcı arabirimi üzerinden) kullanıma alınmasına izin verip vermediğini veya yalnızca kaynak denetimi eklentisi aracılığıyla kullanıma alınması gerekip gerekmediğini gösterir.|
|`SCC_OPT_SHARESUBPROJ`|Yok|Kaynak denetim eklentisi IDE'nin yerel proje klasörünü belirtmesine `SCC_I_SHARESUBPROJOK`izin veriyorsa, eklenti döndürür.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 `nOption` Varsa, `SCC_OPT_EVENTQUEUE`IDE arka plan işlemini devre dışı bırakıyor (veya yeniden etkinleştiriyor). Örneğin, bir derleme sırasında, IDE kaynak denetim eklentisine herhangi bir türde boşta işlemeyi durdurmatalimatı verebilir. Derlemeden sonra, eklentinin olay kuyruğunu güncel tutmak için arka plan işlemlerini yeniden etkinleştirilir. `SCC_OPT_EVENTQUEUE` Değerine karşılık `nOption`gelen , iki olası `dwVal`değer `SCC_OPT_EQ_ENABLE` vardır `SCC_OPT_EQ_DISABLE`, yani, ve .

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Değeri `nOption` ise, `SCC_OPT_HASCANCELMODE`IDE kullanıcıların uzun işlemleri iptal etmesine olanak sağlar. Ayar `dwVal` `SCC_OPT_HCM_NO` (varsayılan) IDE hiçbir iptal modu olduğunu gösterir. Kaynak denetimi eklentisi, kullanıcının iptal edebilmesi için kendi İptal düğmesini sunmalıdır. `SCC_OPT_HCM_YES`IDE'nin bir işlemi iptal etme olanağı sağladığını, bu nedenle SCC eklentisinin kendi İptal düğmesini görüntülemesi gerekmediğini gösterir. IDE `dwVal` ayarlarsa `SCC_OPT_HCM_YES`, yanıt `SCC_MSG_STATUS` vermeye ve `DOCANCEL` `lpTextOutProc` geri arama işlevine gönderilen iletilere hazırdır (bkz. [LPTEXTOUTPROC).](../extensibility/lptextoutproc.md) IDE bu değişkeni ayarlamazsa, eklenti bu iki ileti göndermemelidir.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 nOption ayarlanmışsa `SCC_OPT_NAMECHANGEPFN`ve hem kaynak denetim eklentisi hem de IDE buna izin verirse, eklenti bir kaynak denetim işlemi sırasında bir dosyayı yeniden adlandırabilir veya taşıyabilir. `dwVal` [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)türünde bir işlev işaretçisi olarak ayarlanır. Kaynak denetim işlemi sırasında, eklenti bu işlevi çağırabilir ve üç parametreyi geçirebilirsiniz. Bunlar, bir dosyanın eski adı (tam nitelikli yol ile) ve bu dosyanın yeni adı (tam nitelikli yol ile) ve IDE ile ilgili bilgilere bir işaretçi. IDE, verileri `SccSetOption` işaret ederek `nOption` `SCC_OPT_USERDATA` `dwVal` set ile arayarak bu son işaretçiyi gönderir. Bu işlev için destek isteğe bağlıdır. Bu yeteneği kullanan bir VSSCI eklentisi, işlev işaretçisini `NULL`ve kullanıcı veri değişkenlerini initialize etmelidir ve bir işlev verilmedikçe yeniden adlandırma işlevini çağırmamalıdır. Ayrıca, kendisine verilen değeri tutmak veya yeni bir çağrıya yanıt olarak `SccSetOption`değiştirmek için hazır olmalıdır. Bu, bir kaynak denetimi komut uyruğu işleminin ortasında olmaz, ancak komutlar arasında gerçekleşebilir.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 nOption `SCC_OPT_SCCCHECKOUTONLY`ayarlanmışsa, IDE, şu anda açık olan projedeki dosyaların kaynak denetim sisteminin kullanıcı arabirimi üzerinden el ile kullanıma almaması gerektiğini belirtir. Bunun yerine, dosyalar yalnızca IDE denetimi altındaki kaynak denetim eklentisi üzerinden kullanıma alınmalıdır. `dwValue` Ayarlanmışsa, dosyaların eklenti tarafından normal olarak işlenmeli ve kaynak denetimi UI üzerinden kullanıma `SCC_OPT_SCO_NO`alınabilir. `dwValue` Ayarlanırsa, yalnızca eklentinin dosyaları kullanıma almasına izin verilir ve kaynak denetim sisteminin UI'si çağrılmamalıdır. `SCC_OPT_SCO_YES` Bu, IDE'nin yalnızca IDE üzerinden kullanıma almanın anlamlı olduğu "sözde dosyalar" olabileceği durumlar içindir.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 `nOption` Ayarlanırsa, IDE kaynak denetimi eklentisinin kaynak denetiminden dosya eklerken belirli bir yerel klasörü kullanıp kullanamayacağını sınar. `SCC_OPT_SHARESUBPROJ` Bu durumda `dwVal` parametrenin değeri önemli değildir. Eklenti, [SccAddFromScc](../extensibility/sccaddfromscc-function.md) çağrıldığında dosyaların kaynak denetiminden eklenecek yerel hedef klasörünü iDE'nin belirtmesine izin veriyorsa, `SccSetOption` işlev çağrıldığında eklentinin dönmesi `SCC_I_SHARESUBPROJOK` gerekir. IDE daha sonra `lplpFileNames` hedef klasöründe geçmek için `SccAddFromScc` işlevin parametresini kullanır. Eklenti, kaynak denetiminden eklenen dosyaları yerleştirmek için bu hedef klasörü kullanır. Seçenek ayarlandığında eklenti geri `SCC_I_SHARESUBPROJOK` dönmezse, IDE eklentinin yalnızca geçerli yerel klasöre dosya ekleyebileceğini varsayar. `SCC_OPT_SHARESUBPROJ`

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
