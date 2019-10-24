---
title: SccSetOption Işlevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f48cb84a64c036b373308dfe29bfaf5d2e028b91
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720551"
---
# <a name="sccsetoption-function"></a>SccSetOption İşlevi
Bu işlev, kaynak denetimi eklentisinin davranışını denetleyen seçenekleri ayarlar.

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

'ndaki Kaynak denetimi eklentisi bağlam yapısı.

 nOption

'ndaki Ayarlanmakta olan seçenek.

 dwVal

'ndaki Seçeneğinin ayarları.

## <a name="return-value"></a>Dönüş Değeri
 Bu işlevin kaynak denetimi eklentisi uygulamasının aşağıdaki değerlerden birini döndürmesi beklenir:

|Değer|Açıklama|
|-----------|-----------------|
|SCC_OK|Seçenek başarıyla ayarlandı.|
|SCC_I_SHARESUBPROJOK|`nOption` `SCC_OPT_SHARESUBPROJ` ve kaynak denetimi eklentisi IDE 'nin hedef klasörü ayarlamasına izin veriyorsa döndürülür.|
|SCC_E_OPNOTSUPPORTED|Seçenek ayarlanmadı ve üzerinde güvenilmemelidir.|

## <a name="remarks"></a>Açıklamalar
 IDE, kaynak denetimi eklentisinin davranışını denetlemek için bu işlevi çağırır. `nOption`ilk parametresi, ayarlanmakta olan değeri belirtir, ikincisi, `dwVal`, bu değerle ne yapılacağını gösterir. Eklenti, bu bilgileri bir `pvContext``,` ilişkili olarak depolar, böylece IDE, [SccInitialize](../extensibility/sccinitialize-function.md) çağrıldıktan sonra bu işlevi çağırmalıdır (ancak her bir [SccOpenProject](../extensibility/sccopenproject-function.md)çağrısından sonra olması gerekmez).

 Seçeneklerin Özeti ve değerleri:

|`nOption`|`dwValue`|Açıklama|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Arka plan olay Queuing 'i etkinleştirilir/devre dışı bırakır.|
|`SCC_OPT_USERDATA`|Rastgele değer|[SeçenekAdı Changepfn](../extensibility/optnamechangepfn.md) callback işlevine geçirilecek bir kullanıcı değeri belirtir.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE 'nin şu anda bir işlemi iptal etmeyi destekleyip desteklemediğini gösterir.|
|`SCC_OPT_NAMECHANGEPFN`|[Seçeneknamechangepfn](../extensibility/optnamechangepfn.md) callback işlevine yönelik işaretçi|Ad değiştirme geri arama işlevine yönelik bir işaretçi ayarlar.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE 'nin, dosyalarını el ile kullanıma almasına (kaynak denetimi kullanıcı arabirimi aracılığıyla) veya yalnızca kaynak denetimi eklentisi aracılığıyla kullanıma alınması gerekip gerekmediğini belirtir.|
|`SCC_OPT_SHARESUBPROJ`|Yok|Kaynak denetimi eklentisi IDE 'nin yerel proje klasörünü belirtmesini sağlamasına izin veriyorsa, eklenti `SCC_I_SHARESUBPROJOK`döndürür.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 `nOption` `SCC_OPT_EVENTQUEUE`, IDE arka planda işlemeyi devre dışı bırakır (veya yeniden etkinleştirir). Örneğin, bir derleme sırasında IDE, kaynak denetimi eklentisinin herhangi bir türdeki boş işlemeyi durdurmasına izin verebilir. Derlemeden sonra, eklentinin olay kuyruğunu güncel tutmak için arka plan işlemeyi yeniden etkinleştirir. `nOption``SCC_OPT_EVENTQUEUE` değerine karşılık gelen `dwVal`, yani `SCC_OPT_EQ_ENABLE` ve `SCC_OPT_EQ_DISABLE`için iki olası değer vardır.

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 `nOption` değeri `SCC_OPT_HASCANCELMODE`, IDE kullanıcıların uzun işlemleri iptal etmesine olanak tanır. `dwVal` `SCC_OPT_HCM_NO` (varsayılan) olarak ayarlamak, IDE 'nin iptal moduna sahip olmadığını gösterir. Kaynak denetimi eklentisinin, kullanıcının iptal edebilmesini istiyorsa kendi Iptal düğmesini sunmalıdır. `SCC_OPT_HCM_YES`, IDE 'nin bir işlemi iptal etme özelliği sağladığını gösterir, bu nedenle SCC eklentisinin kendi Iptal düğmesini görüntülemesi gerekmez. IDE, `SCC_OPT_HCM_YES``dwVal` ayarlarsa, `lpTextOutProc` callback işlevine gönderilen `SCC_MSG_STATUS` ve `DOCANCEL` iletileri yanıtlamak üzere hazırlanmaktadır (bkz. [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). IDE bu değişkeni ayarlanmamışsa, eklenti bu iki iletiyi göndermemelidir.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Eğer nOption `SCC_OPT_NAMECHANGEPFN`olarak ayarlanmışsa ve hem kaynak denetimi eklentisi hem de IDE buna izin verirseniz, eklenti aslında kaynak denetimi işlemi sırasında bir dosyayı yeniden adlandırabilir veya taşıyabilir. `dwVal`, [Seçeneknamechangepfn](../extensibility/optnamechangepfn.md)türünde bir işlev işaretçisine ayarlanacak. Kaynak denetim işlemi sırasında eklenti, üç parametreye geçerek bu işlevi çağırabilir. Bunlar bir dosyanın eski adıdır (tam yol ile), bu dosyanın yeni adı (tam yolu ile) ve IDE ile ilgisi olan bilgiler için bir işaretçi. IDE, verileri işaret eden `dwVal` ile `SCC_OPT_USERDATA``nOption` ayarlanmış `SccSetOption` çağırarak bu son işaretçiye gönderilir. Bu işlev için destek isteğe bağlıdır. Bu özelliği kullanan bir VSSCı eklentisi, `NULL`için işlev işaretçisini ve Kullanıcı veri değişkenlerini başlatmalıdır ve kendisine verilmediği takdirde yeniden adlandırma işlevini çağırmamalıdır. Ayrıca, verildiği değeri tutmak veya `SccSetOption`yeni bir çağrıya yanıt olarak değiştirmek için hazırlanmalıdır. Bu, bir kaynak denetimi komut işleminin ortasında gerçekleşmeyecektir, ancak komutlar arasında gerçekleşmeyebilir.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Eğer nOption `SCC_OPT_SCCCHECKOUTONLY`olarak ayarlandıysa, IDE Şu anda açık olan projedeki dosyaların, kaynak denetim sisteminin kullanıcı arabiriminden hiçbir şekilde el ile denetlenmemesi gerektiğini gösterir. Bunun yerine, dosyalar yalnızca IDE denetimi altındaki kaynak denetimi eklentisi aracılığıyla kullanıma alınmalıdır. `dwValue` `SCC_OPT_SCO_NO`olarak ayarlanırsa, dosyaların normalde eklenti tarafından değerlendirilmesi ve kaynak denetimi kullanıcı arabirimi aracılığıyla kullanıma alınması gerektiği anlamına gelir. `dwValue` `SCC_OPT_SCO_YES`olarak ayarlandıysa, yalnızca eklentinin dosyaları kullanıma açmasına izin verilir ve kaynak denetim sisteminin kullanıcı arabirimi çağrılmamalıdır. Bu, IDE 'nin yalnızca IDE aracılığıyla kullanıma hazır hale getirmek için anlamlı bir "sözde dosyalar" olabileceği durumlar içindir.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 `nOption` `SCC_OPT_SHARESUBPROJ`olarak ayarlanırsa, IDE kaynak denetiminden dosya eklerken kaynak denetimi eklentisinin belirtilen yerel klasörü kullanıp kullanamayacağını test edebilir. `dwVal` parametresinin değeri bu durumda değildir. Eklenti, IDE 'nin [SccAddFromScc](../extensibility/sccaddfromscc-function.md) çağrıldığında kaynak denetiminden ekleneceği yerel hedef klasörü belirtmesini sağlamasına izin veriyorsa, `SccSetOption` işlevi çağrıldığında eklentinin `SCC_I_SHARESUBPROJOK` döndürmesi gerekir. Daha sonra IDE, hedef klasöre geçmek için `SccAddFromScc` işlevinin `lplpFileNames` parametresini kullanır. Eklenti, kaynak denetiminden eklenen dosyaları yerleştirmek için bu hedef klasörü kullanır. `SCC_OPT_SHARESUBPROJ` seçeneği ayarlandığında eklenti `SCC_I_SHARESUBPROJOK` dönmezse, IDE, eklentinin yalnızca geçerli yerel klasöre dosya ekleyebildiğinizi varsayar.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)