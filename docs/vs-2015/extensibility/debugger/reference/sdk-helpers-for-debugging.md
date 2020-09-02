---
title: Hata ayıklama için SDK yardımcıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3296613ffbe3148caa04989dfc9d609334b4c200
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64838111"
---
# <a name="sdk-helpers-for-debugging"></a>Hata Ayıklama için SDK Yardımcıları
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu işlevler ve bildirimler, C++ ' da hata ayıklama altyapılarını, Expression değerlendiricileri ve sembol sağlayıcılarını uygulamak için genel yardımcı işlevlerdir.  
  
> [!NOTE]
> Bu işlevlerin ve bildirimlerin yönetilen bir sürümü şu anda yok.  
  
## <a name="overview"></a>Genel Bakış  
 Hata ayıklama motorları, ifade değerlendiricileri ve sembol sağlayıcılarının Visual Studio tarafından kullanılabilmesi için, bunların kayıtlı olmaları gerekir. Bu, kayıt defteri alt anahtarları ve girişleri ayarlanarak yapılır, aksi takdirde "ölçüm ayarı" olarak bilinir. Aşağıdaki genel işlevler, bu ölçümleri güncelleştirme sürecini kolaylaştırmak için tasarlanmıştır. Bu işlevler tarafından güncellenen her bir kayıt defteri alt anahtarının yerleşimini öğrenmek için kayıt defteri konumlarının bölümüne bakın.  
  
## <a name="general-metric-functions"></a>Genel ölçüm Işlevleri  
 Bunlar, hata ayıklama motorları tarafından kullanılan genel işlevlerdir. Expression değerlendiricileri ve symbol sağlayıcıları için özelleştirilmiş işlevler daha sonra ayrıntılı olarak açıklanmıştır.  
  
### <a name="getmetric-method"></a>GetMetric yöntemi  
 Kayıt defterinden bir ölçüm değeri alır.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszMachine|'ndaki Kaydı yazılacak olan, büyük olasılıkla uzak makinenin adı ( `NULL` yerel makine anlamına gelir).|  
|pszType|'ndaki Ölçüm türlerinden biri.|  
|guidSection|'ndaki Belirli bir altyapının GUID 'SI, değerlendirici, özel durum, vb. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|  
|pszMetric|'ndaki Elde edilecek ölçüm. Bu, belirli bir değer adına karşılık gelir.|  
|pdwValue|'ndaki Ölçümdeki değerin depolama konumu. GetMetric 'in bir DWORD (Bu örnekte olduğu gibi), bir BSTR, GUID veya GUID dizisi döndüresağlayan çeşitli türleri vardır.|  
|pszAltRoot|'ndaki Kullanılacak alternatif bir kayıt defteri kökü. Varsayılan öğesini `NULL` kullanmak için olarak ayarlayın.|  
  
### <a name="setmetric-method"></a>SetMetric yöntemi  
 Kayıt defterindeki belirtilen ölçüm değerini ayarlar.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszType|'ndaki Ölçüm türlerinden biri.|  
|guidSection|'ndaki Belirli bir altyapının GUID 'SI, değerlendirici, özel durum, vb. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|  
|pszMetric|'ndaki Elde edilecek ölçüm. Bu, belirli bir değer adına karşılık gelir.|  
|dwValue|'ndaki Ölçümdeki değerin depolama konumu. SetMetric 'in bir DWORD (Bu örnekte), bir BSTR, GUID veya GUID dizisi depolayabilen çeşitli türleri vardır.|  
|fUserSpecific|'ndaki Ölçüm kullanıcıya özgü ise ve yerel makine Hive yerine kullanıcının yığınına yazılması gerekiyorsa doğru.|  
|pszAltRoot|'ndaki Kullanılacak alternatif bir kayıt defteri kökü. Varsayılan öğesini `NULL` kullanmak için olarak ayarlayın.|  
  
### <a name="removemetric-method"></a>RemoveMetric yöntemi  
 Belirtilen ölçümü kayıt defterinden kaldırır.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszType|'ndaki Ölçüm türlerinden biri.|  
|guidSection|'ndaki Belirli bir altyapının GUID 'SI, değerlendirici, özel durum, vb. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|  
|pszMetric|'ndaki Kaldırılacak ölçüm. Bu, belirli bir değer adına karşılık gelir.|  
|pszAltRoot|'ndaki Kullanılacak alternatif bir kayıt defteri kökü. Varsayılan öğesini `NULL` kullanmak için olarak ayarlayın.|  
  
### <a name="enummetricsections-method"></a>EnumMetricSections yöntemi  
 Kayıt defterindeki çeşitli ölçüm bölümlerini numaralandırır.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|pszMachine|'ndaki Kaydı yazılacak olan, büyük olasılıkla uzak makinenin adı ( `NULL` yerel makine anlamına gelir).|  
|pszType|'ndaki Ölçüm türlerinden biri.|  
|rgguidSections|[in, out] Doldurulacak GUID 'lerin önceden ayrılmış dizisi.|  
|pdwSize|'ndaki Dizide depolanabilecek en fazla GUID sayısı `rgguidSections` .|  
|pszAltRoot|'ndaki Kullanılacak alternatif bir kayıt defteri kökü. Varsayılan öğesini `NULL` kullanmak için olarak ayarlayın.|  
  
## <a name="expression-evaluator-functions"></a>İfade değerlendirici Işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|GetEEMetric|Kayıt defterinden bir ölçüm değeri alır.|  
|SetEEMetric|Kayıt defterindeki belirtilen ölçüm değerini ayarlar.|  
|RemoveEEMetric|Belirtilen ölçümü kayıt defterinden kaldırır.|  
|GetEEMetricFile|Belirtilen ölçüden bir dosya adı alır ve dosya içeriğini bir dize olarak döndürerek yükler.|  
  
## <a name="exception-functions"></a>Özel durum Işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|GetExceptionMetric|Kayıt defterinden bir ölçüm değeri alır.|  
|SetExceptionMetric|Kayıt defterindeki belirtilen ölçüm değerini ayarlar.|  
|RemoveExceptionMetric|Belirtilen ölçümü kayıt defterinden kaldırır.|  
|Removeallexceptionölçümlerini|Tüm özel durum ölçümlerini kayıt defterinden kaldırır.|  
  
## <a name="symbol-provider-functions"></a>Sembol sağlayıcısı Işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|GetSPMetric|Kayıt defterinden bir ölçüm değeri alır.|  
|SetSPMetric|Kayıt defterindeki belirtilen ölçüm değerini ayarlar.|  
|RemoveSPMetric|Belirtilen ölçümü kayıt defterinden kaldırır.|  
  
## <a name="enumeration-functions"></a>Sabit Listesi Işlevleri  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|EnumMetricSections|Belirtilen Ölçüm türü için tüm ölçümleri numaralandırır.|  
|EnumDebugEngine|Kayıtlı hata ayıklama altyapılarını numaralandırır.|  
|EnumEEs|Kayıtlı değerlendiricileri deyimini numaralandırır.|  
|Trımexceptionölçümlerini|Tüm özel durum ölçümlerini numaralandırır.|  
  
## <a name="metric-definitions"></a>Ölçüm Tanımları  
 Bu tanımlar, önceden tanımlanmış ölçüm adları için kullanılabilir. Adlar çeşitli kayıt defteri anahtarlarına ve değer adlarına karşılık gelir ve hepsi geniş karakter dizeleri olarak tanımlanır: Örneğin, `extern LPCWSTR metrictypeEngine` .  
  
|Önceden tanımlanmış ölçüm türleri|Açıklama: için temel anahtar....|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Tüm hata ayıklama altyapısı ölçümleri.|  
|Metrictypeporttedarikçi|Tüm bağlantı noktası sağlayıcısı ölçümleri.|  
|metrictypeException|Tüm özel durum ölçümleri.|  
|metricttypeEEExtension|Tüm ifade değerlendirici uzantıları.|  
  
|Hata ayıklama altyapısı özellikleri|Description|  
|-----------------------------|-----------------|  
|metricAddressBP|Adres kesme noktaları desteğini göstermek için sıfır dışında olarak ayarlayın.|  
|metricAlwaysLoadLocal|Hata ayıklama altyapısını her zaman yerel olarak yüklemek için sıfır dışında olarak ayarlayın.|  
|Metricloadındebuggeesession|KULLANıLMıYOR|  
|Metricloadedbydebugayıklanan|Hata ayıklama altyapısının hata ayıklamakta olan program tarafından her zaman yüklenemeyeceğini belirtmek için sıfır dışında olarak ayarlayın.|  
|metricAttach|Mevcut programlara ek desteğini göstermek için sıfır dışında bir değere ayarlayın.|  
|metricCallStackBP|Çağrı yığını kesme noktaları desteğini göstermek için sıfır dışında olarak ayarlayın.|  
|Metricconditionalbümp|Koşullu kesme noktaları ayarı desteğini göstermek için sıfır dışında olarak ayarlayın.|  
|metricDataBP|Verilerdeki değişikliklerle ilgili kesme noktası ayarı desteğini göstermek için sıfır dışında olarak ayarlayın.|  
|metricDisassembly|Ayrıştırılmış bir listenin üretiminin desteğini göstermek için sıfır dışında olarak ayarlayın.|  
|metricDumpWriting|Döküm yazma desteğini (belleğin bir çıkış cihazına dökümünü alma) belirtmek için sıfır dışında olarak ayarlayın.|  
|metricENC|Düzenle ve devam et desteğini göstermek için sıfır dışında bir değere ayarlayın. **Note:**  Özel bir hata ayıklama altyapısı hiçbir zaman bunu ayarlanmamış veya her zaman 0 olarak ayarlanmalıdır.|  
|metricExceptions|Özel durumların desteğini göstermek için sıfır dışında bir değere ayarlayın.|  
|metricFunctionBP|Adlandırılmış kesme noktaları desteğini (belirli bir işlev adı çağrıldığında kesen kesme noktaları) belirtmek için sıfır dışında olarak ayarlayın.|  
|metricHitCountBP|"İsabet noktası" kesme noktaları (yalnızca belirli sayıda vurduktan sonra tetiklenen kesme noktaları) için destek belirtmek üzere sıfır dışında olarak ayarlayın.|  
|Metricjjdebug|Tam zamanında hata ayıklama desteğini göstermek için sıfır dışında bir değer ayarlayın (çalışan bir işlemde bir özel durum oluştuğunda hata ayıklayıcı başlatılır).|  
|metricMemory|KULLANıLMıYOR|  
|Metricporttedarikçi|Uygulanmışsa, bağlantı noktası tedarikçinin CLSID değerine ayarlayın.|  
|Metricyazmaçları|KULLANıLMıYOR|  
|Metricsetnextdeyimsi|Sonraki deyimi ayarlama desteğini (ara deyimlerin yürütülmesini atlar) belirtmek için sıfır dışında olarak ayarlayın.|  
|metricSuspendThread|İş parçacığı yürütmeyi askıya alma desteğini göstermek için sıfır dışında olarak ayarlayın.|  
|metricWarnIfNoSymbols|Sembol yoksa kullanıcının bildirilmesi gerektiğini belirtmek için sıfır dışında olarak ayarlayın.|  
|metricProgramProvider|Bunu program sağlayıcısının CLSID 'sine ayarlayın.|  
|metricAlwaysLoadProgramProviderLocal|Program sağlayıcısının her zaman yerel olarak yüklenmesi gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın.|  
|metricEngineCanWatchProcess|Hata ayıklama altyapısının program sağlayıcısı yerine işlem olaylarını izleyemeyeceğini belirtmek için bunu sıfır dışında olarak ayarlayın.|  
|metricRemoteDebugging|Uzaktan hata ayıklama desteğini göstermek için bunu sıfır dışında olarak ayarlayın.|  
|metricEncUseNativeBuilder|Düzenle ve devam et yöneticisinin Düzenle ve devam et için derlemek üzere hata ayıklama altyapısının encbuild.dll kullanması gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın. **Note:**  Özel bir hata ayıklama altyapısı hiçbir zaman bunu ayarlanmamış veya her zaman 0 olarak ayarlanmalıdır.|  
|metricLoadUnderWOW64|Hata ayıklama altyapısının 64 bitlik bir işlemde hata ayıklarken WOW altındaki hata ayıklanan işlemde yüklenmesi gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın; Aksi halde, hata ayıklama altyapısı Visual Studio işleminde yüklenir (WOW64 altında çalışır).|  
|metricLoadProgramProviderUnderWOW64|Program sağlayıcısının, WOW altında 64 bitlik bir işlemin hatalarını ayıklarken hata ayıklanan işlemde yüklenmesi gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın; Aksi takdirde, Visual Studio işleminde yüklenir.|  
|Metricstoponexceptioncrossınmanagedsınır|Yönetilen/yönetilmeyen kod sınırları genelinde işlenmeyen bir özel durum oluşursa işlemin durması gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın.|  
|Metricoto Selectpriority|Bunu hata ayıklama altyapısının otomatik seçimi için öncelik olarak ayarlayın (daha yüksek değerler daha yüksek önceliğe eşittir).|  
|Metricoto Selectıncompatiblelist|Otomatik seçimde yok sayılacak hata ayıklama altyapısının GUID 'Lerini belirten girişleri içeren kayıt defteri anahtarı. Bu girişler, bir dize olarak ifade edilen bir GUID ile (0, 1, 2, vb.) bir sayıdır.|  
|Metricıncompatiblelist|Bu hata ayıklama altyapısıyla uyumsuz olan hata ayıklama motorları için GUID 'Leri belirten girişleri içeren kayıt defteri anahtarı.|  
|Metricdisablejitoptılama|Tam zamanında iyileştirmelerin (yönetilen kod için) hata ayıklama sırasında devre dışı bırakılacağını belirtmek için bunu sıfır dışında olarak ayarlayın.|  
  
|İfade değerlendirici özellikleri|Description|  
|-------------------------------------|-----------------|  
|metricEngine|Bu, belirtilen ifade değerlendiricisi 'ni destekleyen hata ayıklama altyapısının sayısını tutar.|  
|metricPreloadModules|Bir programa karşı bir ifade değerlendirici başlatıldığında modüllerin önceden yüklenmesi gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın.|  
|metricThisObjectName|Bunu "This" nesne adı olarak ayarlayın.|  
  
|İfade değerlendirici uzantı özellikleri|Description|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Bu uzantıyı destekleyen dll 'nin adı.|  
|metricExtensionRegistersSupported|Desteklenen kayıt listesi.|  
|metricExtensionRegistersEntryPoint|Yazmaçlara erişmek için giriş noktası.|  
|Metricextensiontypesdestekleniyor|Desteklenen türlerin listesi.|  
|metricExtensionTypesEntryPoint|Türlere erişmek için giriş noktası.|  
  
|Bağlantı noktası sağlayıcı özellikleri|Description|  
|------------------------------|-----------------|  
|Metricportpickerclsıd|Bağlantı noktası seçicisinin CLSID 'SI (kullanıcının bağlantı noktalarını seçmek ve hata ayıklama için kullanılacak bağlantı noktaları eklemek için kullanabileceği bir iletişim kutusu).|  
|metricDisallowUserEnteredPorts|Kullanıcı tarafından girilen bağlantı noktaları bağlantı noktası sağlayıcısına eklenemediğinde sıfır dışında (Bu, bağlantı noktası Seçici iletişim kutusunu temelde salt okunurdur).|  
|metricPidBase|İşlem kimlikleri ayrılırken bağlantı noktası sağlayıcısı tarafından kullanılan temel işlem KIMLIĞI.|  
  
|Önceden tanımlanmış SP deposu türleri|Description|  
|-------------------------------|-----------------|  
|storetypeFile|Semboller ayrı bir dosyada depolanır.|  
|storetypeMetadata|Semboller bir derlemede meta veri olarak depolanır.|  
  
|Çeşitli özellikler|Description|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Kullanıcı olmayan kodu göstermek için bunu sıfır dışında olarak ayarlayın.|  
|metricJustMyCodeStepping|Adımlamayı Yalnızca Kullanıcı kodunda gerçekleşebileceğini belirtmek için sıfır dışında olarak ayarlayın.|  
|metricCLSID|Belirli bir ölçüm türündeki nesne için CLSID.|  
|metricName|Belirli bir ölçüm türündeki bir nesnenin Kullanıcı dostu adı.|  
|metricLanguage|Dil adı.|  
  
## <a name="registry-locations"></a>Kayıt defteri konumları  
 Ölçümler, özellikle alt anahtarda bulunan ve kayıt defterine yazılır `VisualStudio` .  
  
> [!NOTE]
> Çoğu zaman ölçümler HKEY_LOCAL_MACHINE anahtara yazılır. Ancak, bazen HKEY_CURRENT_USER hedef anahtar olur. Dbgmetric. lib her iki anahtarı da işler. Ölçüm alırken öncelikle HKEY_CURRENT_USER arar ve ardından HKEY_LOCAL_MACHINE. Bir ölçüm ayarlarken, bir parametre hangi üst düzey anahtarın kullanılacağını belirtir.  
  
 *[kayıt defteri anahtarı]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[sürüm kökü]*\  
  
 *[ölçüm kökü]*\  
  
 *[ölçüm türü]*\  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
|Yer tutucu|Description|  
|-----------------|-----------------|  
|*[kayıt defteri anahtarı]*|`HKEY_CURRENT_USER` veya `HKEY_LOCAL_MACHINE`.|  
|*[sürüm kökü]*|Visual Studio sürümü (örneğin,, `7.0` `7.1` veya `8.0` ). Ancak, bu kök, **devenv.exe**için **/rootsuffix** anahtarı kullanılarak da değiştirilebilir. VSıP için bu değiştirici genellikle **Exp**olur, bu nedenle sürüm kökü, örneğin, 8.0 exp olur.|  
|*[ölçüm kökü]*|Bu ya da `AD7Metrics` `AD7Metrics(Debug)` , dbgmetric. lib hata ayıklama sürümünün kullanılıp kullanılmadığını bağlı olarak. **Note:**  Dbgmetric. lib kullanılıp kullanılmayacağı, kayıt defterine yansıtılması gereken hata ayıklama ve sürüm sürümleri arasında farklılıklar varsa, bu adlandırma kuralının ' a bağlı olması gerekir.|  
|*[ölçüm türü]*|Yazılacak ölçüm türü: `Engine` , `ExpressionEvaluator` , `SymbolProvider` vb. Bunlar `metricTypeXXXX` , özel tür adı olduğu gibi dbgmetric. h olarak tanımlanmıştır `XXXX` .|  
|*Ölçüt*|Ölçümü ayarlamak için bir değere atanacak bir girdinin adı. Ölçümlerin gerçek organizasyonu, ölçüm türüne bağlıdır.|  
|*[ölçüm değeri]*|Ölçüme atanan değer. Değerin (dize, sayı, vb.) olması, ölçüme bağlıdır.|  
  
> [!NOTE]
> Tüm GUID 'Ler biçiminde depolanır `{GUID}` . Örneğin, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Hata ayıklama motorları  
 Kayıt defterindeki hata ayıklama altyapısının ölçümlerinin organizasyonu aşağıda verilmiştir. `Engine` , hata ayıklama altyapısının ölçüm türü adıdır ve yukarıdaki kayıt defteri alt ağacındaki *[ölçüm türü]* öğesine karşılık gelir.  
  
 `Engine`\  
  
 *[motor GUID 'si]*\  
  
 `CLSID` = *[sınıf GUID 'si]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 `PortSupplier`\  
  
 `0` = *[bağlantı noktası sağlayıcı GUID]*  
  
 `1` = *[bağlantı noktası sağlayıcı GUID]*  
  
|Yer tutucu|Description|  
|-----------------|-----------------|  
|*[motor GUID 'si]*|Hata ayıklama altyapısının GUID 'SI.|  
|*[sınıf GUID 'si]*|Bu hata ayıklama altyapısını uygulayan sınıfın GUID 'ı.|  
|*[bağlantı noktası sağlayıcı GUID]*|Varsa, bağlantı noktası tedarikçinin GUID 'SI. Birçok hata ayıklama altyapısı varsayılan bağlantı noktası tedarikçiyi kullanır ve bu nedenle kendi tedarikçiyi belirtmez. Bu durumda, alt anahtar `PortSupplier` yok olur.|  
  
### <a name="port-suppliers"></a>Bağlantı Noktası Sağlayıcıları  
 Kayıt defterindeki bağlantı noktası sağlayıcısı ölçümlerinin organizasyonu aşağıda verilmiştir. `PortSupplier` , bir bağlantı noktası sağlayıcısı için ölçüm türü adıdır ve *[ölçüm türü]* öğesine karşılık gelir.  
  
 `PortSupplier`\  
  
 *[bağlantı noktası sağlayıcı GUID]*\  
  
 `CLSID` = *[sınıf GUID 'si]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
|Yer tutucu|Description|  
|-----------------|-----------------|  
|*[bağlantı noktası sağlayıcı GUID]*|Bağlantı noktası tedarikçinin GUID 'SI|  
|*[sınıf GUID 'si]*|Bu bağlantı noktası tedarikçiyi uygulayan sınıfın GUID 'ı|  
  
### <a name="symbol-providers"></a>Sembol sağlayıcıları  
 Kayıt defterindeki sembol sağlayıcısı ölçümlerinin organizasyonu aşağıda verilmiştir. `SymbolProvider` , sembol sağlayıcısının ölçüm türü adıdır ve *[ölçüm türü]* öğesine karşılık gelir.  
  
 `SymbolProvider`\  
  
 *[sembol sağlayıcısı GUID]*\  
  
 `file`\  
  
 `CLSID` = *[sınıf GUID 'si]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 `metadata`\  
  
 `CLSID` = *[sınıf GUID 'si]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
|Yer tutucu|Description|  
|-----------------|-----------------|  
|*[sembol sağlayıcısı GUID]*|Sembol sağlayıcısının GUID 'SI|  
|*[sınıf GUID 'si]*|Bu sembol sağlayıcısını uygulayan sınıfın GUID 'ı|  
  
### <a name="expression-evaluators"></a>İfade değerlendiricileri  
 Kayıt defterindeki ifade değerlendirici ölçümlerinin organizasyonu aşağıda verilmiştir. `ExpressionEvaluator` , ifade değerlendirici için ölçüm türü adıdır ve *[ölçüm türü]* öğesine karşılık gelir.  
  
> [!NOTE]
> İçin ölçüm türü `ExpressionEvaluator` dbgmetric. h içinde tanımlı değildir, çünkü Expression değerlendiricileri için tüm ölçüm değişikliklerinin uygun ifade değerlendirici ölçüm işlevleri üzerinden gitmesini varsayacaktır ( `ExpressionEvaluator` alt anahtarın düzeni biraz karmaşıktır, bu nedenle Ayrıntılar dbgmetric. lib içinde gizlenir).  
  
 `ExpressionEvaluator`\  
  
 *[dil GUID 'si]*\  
  
 *[satıcı GUID]*\  
  
 `CLSID` = *[sınıf GUID 'si]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 `Engine`\  
  
 `0` = *[hata ayıklama altyapısı GUID]*  
  
 `1` = *[hata ayıklama altyapısı GUID]*  
  
|Yer tutucu|Description|  
|-----------------|-----------------|  
|*[dil GUID 'si]*|Bir dilin GUID 'SI|  
|*[satıcı GUID]*|Satıcının GUID 'SI|  
|*[sınıf GUID 'si]*|Bu ifade değerlendirici uygulayan sınıfın GUID 'ı|  
|*[hata ayıklama altyapısı GUID]*|Bu ifade değerlendiricisi ile birlikte çalışarak hata ayıklama altyapısının GUID 'SI|  
  
### <a name="expression-evaluator-extensions"></a>İfade değerlendirici uzantıları  
 Aşağıda, kayıt defterindeki ifade değerlendirici uzantı ölçümlerinin organizasyonu verilmiştir. `EEExtensions` , ifade değerlendirici uzantılarının ölçüm türü adıdır ve *[ölçüm türü]* öğesine karşılık gelir.  
  
 `EEExtensions`\  
  
 *[uzantı GUID]*\  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
|Yer tutucu|Description|  
|-----------------|-----------------|  
|*[uzantı GUID]*|Bir ifade değerlendirici uzantısının GUID 'SI|  
  
### <a name="exceptions"></a>Özel durumlar  
 Aşağıda, kayıt defterindeki özel durum ölçümlerinin organizasyonu verilmiştir. `Exception` , özel durumların ölçüm türü adıdır ve *[ölçüm türü]* öğesine karşılık gelir.  
  
 `Exception`\  
  
 *[hata ayıklama altyapısı GUID]*\  
  
 *[özel durum türleri]*\  
  
 *duruma*\  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *duruma*\  
  
 *[ölçüm] = [ölçüm değeri]*  
  
 *[ölçüm] = [ölçüm değeri]*  
  
|Yer tutucu|Description|  
|-----------------|-----------------|  
|*[hata ayıklama altyapısı GUID]*|Özel durumları destekleyen bir hata ayıklama altyapısının GUID 'ı.|  
|*[özel durum türleri]*|Ele alınan özel durumların sınıfını tanımlayan alt anahtar için genel bir başlık. Genellikle **C++ özel durumları**, **Win32 özel durumları**, **ortak dil çalışma zamanı özel durumları**ve **yerel çalışma zamanı denetimleri**bulunur. Bu adlar, kullanıcıya belirli bir özel durum sınıfını tanımlamak için de kullanılır.|  
|*duruma*|Özel durum için bir ad: Örneğin, **_com_error** veya **Denetim kesme**. Bu adlar, kullanıcıya özel bir özel durumu tanımlamak için de kullanılır.|  
  
## <a name="requirements"></a>Gereksinimler  
 Bu dosyalar [!INCLUDE[vs_dev10_ext](../../../includes/vs-dev10-ext-md.md)] SDK yükleme dizininde bulunur (varsayılan olarak, *[sürücü]* \Program Files\Microsoft VISUAL Studio 2010 SDK \\ ).  
  
 Üstbilgi: includes\dbgmetric.h  
  
 Kitaplık: libs\ad2de.exe, libs\dbgmetric.exe  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
