---
title: SccSetOption Işlevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f2660ca99d8704f5dd8e7b9aa66c9c8fc5bdbb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143741"
---
# <a name="sccsetoption-function"></a>SccSetOption İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, kaynak denetimi eklentisinin davranışını denetleyen seçenekleri ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
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
|SCC_I_SHARESUBPROJOK|Was ise `nOption` `SCC_OPT_SHARESUBPROJ` ve kaynak denetımı eklentisi IDE 'nin hedef klasörü ayarlamasına izin veriyorsa döndürülür.|  
|SCC_E_OPNOTSUPPORTED|Seçenek ayarlanmadı ve üzerinde güvenilmemelidir.|  
  
## <a name="remarks"></a>Açıklamalar  
 IDE, kaynak denetimi eklentisinin davranışını denetlemek için bu işlevi çağırır. İlk parametresi, `nOption` ayarlanmakta olan değeri, ikincisi ise `dwVal` , bu değerle ne yapılacağını gösterir. Eklenti bu bilgileri bir ile ilişkili olarak depolar `pvContext``,` , böylece IDE, [SccInitialize](../extensibility/sccinitialize-function.md) çağrıldıktan sonra bu işlevi çağırmalıdır (ancak her bir [SccOpenProject](../extensibility/sccopenproject-function.md)çağrısından sonra olması gerekmez).  
  
 Seçeneklerin Özeti ve değerleri:  
  
|`nOption`|`dwValue`|Açıklama|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Arka plan olay Queuing 'i etkinleştirilir/devre dışı bırakır.|  
|`SCC_OPT_USERDATA`|Rastgele değer|[SeçenekAdı Changepfn](../extensibility/optnamechangepfn.md) callback işlevine geçirilecek bir kullanıcı değeri belirtir.|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|IDE 'nin şu anda bir işlemi iptal etmeyi destekleyip desteklemediğini gösterir.|  
|`SCC_OPT_NAMECHANGEPFN`|[Seçeneknamechangepfn](../extensibility/optnamechangepfn.md) callback işlevine yönelik işaretçi|Ad değiştirme geri arama işlevine yönelik bir işaretçi ayarlar.|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|IDE 'nin, dosyalarını el ile kullanıma almasına (kaynak denetimi kullanıcı arabirimi aracılığıyla) veya yalnızca kaynak denetimi eklentisi aracılığıyla kullanıma alınması gerekip gerekmediğini belirtir.|  
|`SCC_OPT_SHARESUBPROJ`|YOK|Kaynak denetimi eklentisi IDE 'nin yerel proje klasörünü belirtmesini sağlamasına izin veriyorsa eklenti döndürülür `SCC_I_SHARESUBPROJOK` .|  
  
## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE  
 `nOption`İse `SCC_OPT_EVENTQUEUE` , IDE arka planda işlemeyi devre dışı bırakır (veya yeniden etkinleştirir). Örneğin, bir derleme sırasında IDE, kaynak denetimi eklentisinin herhangi bir türdeki boş işlemeyi durdurmasına izin verebilir. Derlemeden sonra, eklentinin olay kuyruğunu güncel tutmak için arka plan işlemeyi yeniden etkinleştirir. Değerine karşılık gelen,, `SCC_OPT_EVENTQUEUE` `nOption` ve için iki olası değer vardır `dwVal` `SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE` .  
  
## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE  
 Değeri `nOption` ise `SCC_OPT_HASCANCELMODE` , IDE kullanıcıların uzun işlemleri iptal etmesine izin verir. `dwVal` `SCC_OPT_HCM_NO` (Varsayılan) AYARı, IDE 'nin iptal moduna sahip olmadığını gösterir. Kaynak denetimi eklentisinin, kullanıcının iptal edebilmesini istiyorsa kendi Iptal düğmesini sunmalıdır. `SCC_OPT_HCM_YES` IDE 'nin bir işlemi iptal etme özelliği sağladığını gösterir, bu nedenle SCC eklentisinin kendi Iptal düğmesini görüntülemesi gerekmez. IDE `dwVal` olarak ayarlandıysa `SCC_OPT_HCM_YES` , `SCC_MSG_STATUS` `DOCANCEL` geri çağırma işlevine gönderilen iletileri ve yanıt vermeye hazırlanır `lpTextOutProc` (bkz. [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)). IDE bu değişkeni ayarlanmamışsa, eklenti bu iki iletiyi göndermemelidir.  
  
## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 Eğer Eğer Eğer Eğer, Eğer Eğer `SCC_OPT_NAMECHANGEPFN` , ve her ikisi de kaynak denetimi eklentisi ve IDE buna izin veriyor ise, eklenti aslında kaynak denetimi işlemi sırasında bir dosyayı yeniden adlandırabilir veya taşıyabilir. , `dwVal` [SeçenekAdı](../extensibility/optnamechangepfn.md)' nın bir işlev işaretçisine ayarlanacak. Kaynak denetim işlemi sırasında eklenti, üç parametreye geçerek bu işlevi çağırabilir. Bunlar bir dosyanın eski adıdır (tam yol ile), bu dosyanın yeni adı (tam yolu ile) ve IDE ile ilgisi olan bilgiler için bir işaretçi. IDE, `SccSetOption` `nOption` `SCC_OPT_USERDATA` verileri işaret eden ile olarak ayarla ' yı çağırarak bu son işaretçiye gönderilir `dwVal` . Bu işlev için destek isteğe bağlıdır. Bu özelliği kullanan bir VSSCı eklentisi, işlev işaretçisini ve Kullanıcı veri değişkenlerini ' a başlatması gerekir `NULL` ve kendisine verilmediği takdirde yeniden adlandırma işlevini çağırmamalıdır. Ayrıca, verildiği değeri tutmaya veya yeni bir çağrısına yanıt olarak değiştirmek için hazırlanmalıdır `SccSetOption` . Bu, bir kaynak denetimi komut işleminin ortasında gerçekleşmeyecektir, ancak komutlar arasında gerçekleşmeyebilir.  
  
## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 Eğer Eğer, olarak ayarlandıysa `SCC_OPT_SCCCHECKOUTONLY` , IDE Şu anda açık olan projedeki dosyaların, kaynak denetim sisteminin kullanıcı arabiriminden hiçbir şekilde el ile denetlenmeyeceğini gösterir. Bunun yerine, dosyalar yalnızca IDE denetimi altındaki kaynak denetimi eklentisi aracılığıyla kullanıma alınmalıdır. , `dwValue` Olarak ayarlandıysa `SCC_OPT_SCO_NO` , dosyaların normalde eklenti tarafından değerlendirilmesi ve kaynak denetimi kullanıcı arabirimi aracılığıyla kullanıma alınabileceği anlamına gelir. , `dwValue` Olarak ayarlandıysa `SCC_OPT_SCO_YES` , yalnızca eklentiye dosya kullanıma izin verilir ve kaynak denetim sisteminin kullanıcı arabirimi çağrılmamalıdır. Bu, IDE 'nin yalnızca IDE aracılığıyla kullanıma hazır hale getirmek için anlamlı bir "sözde dosyalar" olabileceği durumlar içindir.  
  
## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 `nOption`Olarak ayarlanırsa `SCC_OPT_SHARESUBPROJ` , IDE kaynak denetiminden dosya eklerken kaynak denetimi eklentisinin belirtilen yerel klasörü kullanıp kullanamayacağını test ediyor. `dwVal`Parametrenin değeri bu durumda değildir. Eklenti, IDE 'nin [SccAddFromScc](../extensibility/sccaddfromscc-function.md) çağrıldığında kaynak denetiminden ekleneceği yerel hedef klasörü belirtmesini sağlamasına izin veriyorsa,, işlev çağrıldığında eklentinin dönmesi gerekir `SCC_I_SHARESUBPROJOK` `SccSetOption` . Daha sonra IDE, `lplpFileNames` `SccAddFromScc` hedef klasöre geçirilecek işlevin parametresini kullanır. Eklenti, kaynak denetiminden eklenen dosyaları yerleştirmek için bu hedef klasörü kullanır. Seçenek ayarlandığında eklenti döndürülmezse `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` , IDE, eklentinin yalnızca geçerli yerel klasöre dosya ekleyebildiğinizi varsayar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentisi API Işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
