---
title: Hata Ayıklama için SDK Yardımcıları | Microsoft Docs
description: C++ içinde hata ayıklama altyapılarını, ifade değerlendiricilerini ve sembol sağlayıcılarını uygulamaya ilişkin genel yardımcı işlevler olan işlevler ve bildirimleri öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fd85921256d8212a1d02d2d24277ff2ed71dde97
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103071"
---
# <a name="sdk-helpers-for-debugging"></a>Hata Ayıklama için SDK Yardımcıları
Bu işlevler ve bildirimler, C++ içinde hata ayıklama altyapılarını, ifade değerlendiricilerini ve sembol sağlayıcılarını uygulamaya ilişkin genel yardımcı işlevlerdir.

> [!NOTE]
> Şu anda bu işlevlerin ve bildirimlerin yönetilen sürümleri yoktur.

## <a name="overview"></a>Genel Bakış
 Hata ayıklama altyapılarının, ifade değerlendiricilerin ve sembol sağlayıcılarının Visual Studio için bunların kayıtlı olması gerekir. Bu, aksi takdirde "ölçümleri ayarlama" olarak bilinen kayıt defteri alt anahtarları ve girişleri ayarlandırarak yapılır. Aşağıdaki genel işlevler, bu ölçümleri güncelleştirme işlemini kolaylaştırmak için tasarlanmıştır. Bu işlevler tarafından güncelleştirilen her kayıt defteri alt anahtarının düzenini bulmak için Kayıt Defteri Konumları bölümüne bakın.

## <a name="general-metric-functions"></a>Genel Ölçüm İşlevleri
 Bunlar hata ayıklama altyapıları tarafından kullanılan genel işlevlerdir. İfade değerlendiricileri ve sembol sağlayıcıları için özel işlevler daha sonra ayrıntılı olarak açıklanacak.

### <a name="getmetric-method"></a>GetMetric Yöntemi
 Kayıt defterinden bir ölçüm değeri verir.

```cpp
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
|pszMachine|[in] Yazmaçları yazacak uzak bir makinenin adı `NULL` (yerel makine anlamına gelir).|
|pszType|[in] Ölçüm türlerinden biri.|
|guidSection|[in] Belirli bir altyapının, değerlendiricinin, özel durumun vb. GUID'si. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|
|pszMetric|[in] Elde edilen ölçüm. Bu, belirli bir değer adına karşılık gelen bir değerdir.|
|pdwValue|[in] Ölçümün değerinin depolama konumu. GetMetric'in DWORD (bu örnekte olduğu gibi), BSTR, GUID veya GUID dizisini getirerek çeşitli çeşitler vardır.|
|pszAltRoot|[in] Kullanmak için alternatif bir kayıt defteri kökü. varsayılanı `NULL` kullanmak için olarak ayarlayın.|

### <a name="setmetric-method"></a>SetMetric Yöntemi
 Kayıt defterinde belirtilen ölçüm değerini ayarlar.

```cpp
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
|pszType|[in] Ölçüm türlerinden biri.|
|guidSection|[in] Belirli bir altyapının, değerlendiricinin, özel durumun vb. GUID'si. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|
|pszMetric|[in] Elde edilen ölçüm. Bu, belirli bir değer adına karşılık gelen bir değerdir.|
|dwValue|[in] Ölçümde değerin depolama konumu. Bir DWORD (bu örnekte), BSTR, GUID veya GUID dizisini depolayabli birkaç SetMetric türü vardır.|
|fUserSpecific|[in] Ölçüm kullanıcıya özgü ise ve yerel makine kovanı yerine kullanıcının kovanlarına yazıldıysa TRUE.|
|pszAltRoot|[in] Kullanmak için alternatif bir kayıt defteri kökü. varsayılanı `NULL` kullanmak için olarak ayarlayın.|

### <a name="removemetric-method"></a>RemoveMetric Yöntemi
 Belirtilen ölçümü kayıt defterinden kaldırır.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|Parametre|Açıklama|
|---------------|-----------------|
|pszType|[in] Ölçüm türlerinden biri.|
|guidSection|[in] Belirli bir altyapının, değerlendiricinin, özel durumun vb. GUID'si. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|
|pszMetric|[in] Kaldırılacak ölçüm. Bu, belirli bir değer adına karşılık gelen bir değerdir.|
|pszAltRoot|[in] Kullanmak için alternatif bir kayıt defteri kökü. varsayılanı `NULL` kullanmak için olarak ayarlayın.|

### <a name="enummetricsections-method"></a>EnumMetricSections Yöntemi
 Kayıt defterindeki çeşitli ölçüm bölümlerini numaralar.

```cpp
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
|pszMachine|[in] Yazmaçları yazacak uzak bir makinenin adı `NULL` (yerel makine anlamına gelir).|
|pszType|[in] Ölçüm türlerinden biri.|
|rgguidSections|[in, out] Doldurulması gereken önceden bir GUID dizisi.|
|pdwSize|[in] Dizide depolanmış guid sayısı üst `rgguidSections` sayısı.|
|pszAltRoot|[in] Kullanmak için alternatif bir kayıt defteri kökü. varsayılanı `NULL` kullanmak için olarak ayarlayın.|

## <a name="expression-evaluator-functions"></a>İfade Değerlendirici İşlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|GetEEMetric|Kayıt defterinden bir ölçüm değeri verir.|
|SetEEMetric|Kayıt defterinde belirtilen ölçüm değerini ayarlar.|
|RemoveEEMetric|Belirtilen ölçümü kayıt defterinden kaldırır.|
|GetEEMetricFile|Belirtilen ölçümden bir dosya adı alır ve dosya içeriğini dize olarak döndürerek yükler.|

## <a name="exception-functions"></a>Özel Durum İşlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|GetExceptionMetric|Kayıt defterinden bir ölçüm değeri verir.|
|SetExceptionMetric|Kayıt defterinde belirtilen ölçüm değerini ayarlar.|
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

|Hata ayıklama altyapısı özellikleri|Açıklama|
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
|metricLoadUnderWOW64|Hata ayıklama altyapısının 64 bitlik bir işlemde hata ayıklarken WOW altındaki hata ayıklanan işlemde yüklenmesi gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın; aksi halde, hata ayıklama altyapısı Visual Studio işleme yüklenir (WOW64 altında çalışır).|
|metricLoadProgramProviderUnderWOW64|Program sağlayıcısının, WOW altında 64 bitlik bir işlemin hatalarını ayıklarken hata ayıklanan işlemde yüklenmesi gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın; aksi takdirde, Visual Studio işlemine yüklenir.|
|Metricstoponexceptioncrossınmanagedsınır|Yönetilen/yönetilmeyen kod sınırları genelinde işlenmeyen bir özel durum oluşursa işlemin durması gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın.|
|Metricoto Selectpriority|Bunu hata ayıklama altyapısının otomatik seçimi için öncelik olarak ayarlayın (daha yüksek değerler daha yüksek önceliğe eşittir).|
|Metricoto Selectıncompatiblelist|Otomatik seçimde yok sayılacak hata ayıklama altyapısının GUID 'Lerini belirten girişleri içeren kayıt defteri anahtarı. Bu girişler, bir dize olarak ifade edilen bir GUID ile (0, 1, 2, vb.) bir sayıdır.|
|Metricıncompatiblelist|Bu hata ayıklama altyapısıyla uyumsuz olan hata ayıklama motorları için GUID 'Leri belirten girişleri içeren kayıt defteri anahtarı.|
|Metricdisablejitoptılama|Tam zamanında iyileştirmelerin (yönetilen kod için) hata ayıklama sırasında devre dışı bırakılacağını belirtmek için bunu sıfır dışında olarak ayarlayın.|

|İfade değerlendirici özellikleri|Açıklama|
|-------------------------------------|-----------------|
|metricEngine|Bu, belirtilen ifade değerlendiricisi 'ni destekleyen hata ayıklama altyapısının sayısını tutar.|
|metricPreloadModules|Bir programa karşı bir ifade değerlendirici başlatıldığında modüllerin önceden yüklenmesi gerektiğini belirtmek için bunu sıfır dışında olarak ayarlayın.|
|metricThisObjectName|Bunu "This" nesne adı olarak ayarlayın.|

|İfade değerlendirici uzantı özellikleri|Açıklama|
| - |-----------------|
|metricExtensionDll|Bu uzantıyı destekleyen dll 'nin adı.|
|metricExtensionRegistersSupported|Desteklenen kayıt listesi.|
|metricExtensionRegistersEntryPoint|Yazmaçlara erişmek için giriş noktası.|
|Metricextensiontypesdestekleniyor|Desteklenen türlerin listesi.|
|metricExtensionTypesEntryPoint|Türlere erişmek için giriş noktası.|

|Bağlantı noktası sağlayıcı özellikleri|Açıklama|
|------------------------------|-----------------|
|Metricportpickerclsıd|Bağlantı noktası seçicisinin CLSID 'SI (kullanıcının bağlantı noktalarını seçmek ve hata ayıklama için kullanılacak bağlantı noktaları eklemek için kullanabileceği bir iletişim kutusu).|
|metricDisallowUserEnteredPorts|Kullanıcı tarafından girilen bağlantı noktaları bağlantı noktası sağlayıcısına eklenemediğinde sıfır dışında (Bu, bağlantı noktası Seçici iletişim kutusunu temelde salt okunurdur).|
|metricPidBase|İşlem kimlikleri ayrılırken bağlantı noktası sağlayıcısı tarafından kullanılan temel işlem KIMLIĞI.|

|Önceden tanımlanmış SP deposu türleri|Açıklama|
|-------------------------------|-----------------|
|storetypeFile|Semboller ayrı bir dosyada depolanır.|
|storetypeMetadata|Semboller bir derlemede meta veri olarak depolanır.|

|Çeşitli özellikler|Açıklama|
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

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[kayıt defteri anahtarı]*|`HKEY_CURRENT_USER` veya `HKEY_LOCAL_MACHINE`.|
|*[sürüm kökü]*|Visual Studio sürümü (örneğin,, `7.0` `7.1` veya `8.0` ). Ancak, bu kök, **devenv.exe** için **/rootsuffix** anahtarı kullanılarak da değiştirilebilir. VSıP için bu değiştirici genellikle **Exp** olur, bu nedenle sürüm kökü, örneğin, 8.0 exp olur.|
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

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[motor GUID 'si]*|Hata ayıklama altyapısının GUID'si.|
|*[sınıf guid'si]*|Bu hata ayıklama altyapısını uygulayan sınıfın GUID'si.|
|*[bağlantı noktası sağlayıcı guid]*|Varsa, bağlantı noktası sağlayıcının GUID'si. Birçok hata ayıklama altyapısı varsayılan bağlantı noktası tedarikçisini kullanır ve bu nedenle kendi tedarikçilerini belirtmez. Bu durumda alt anahtar `PortSupplier` eksik olacaktır.|

### <a name="port-suppliers"></a>Bağlantı Noktası Sağlayıcıları
 Aşağıda, kayıt defterindeki bağlantı noktası sağlayıcı ölçümlerinin organizasyonu ve organizasyonu ve ardından yer almaktadır. `PortSupplier`, bir bağlantı noktası sağlayıcının ölçüm türü adıdır ve *[ölçüm türü] 'e karşılık gelen bir addır.*

 `PortSupplier`\

 *[bağlantı noktası sağlayıcı guid]*\

 `CLSID` = *[sınıf guid'si]*

 *[ölçüm] = [ölçüm değeri]*

 *[ölçüm] = [ölçüm değeri]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[bağlantı noktası sağlayıcı guid]*|Bağlantı noktası sağlayıcının GUID'si|
|*[sınıf guid'si]*|Bu bağlantı noktası sağlayıcıyı uygulayan sınıfın GUID'si|

### <a name="symbol-providers"></a>Sembol Sağlayıcıları
 Aşağıda, kayıt defterinde sembol sağlayıcı ölçümlerinin organizasyonu yer almaktadır. `SymbolProvider`, sembol sağlayıcısının ölçüm türü adıdır ve *[ölçüm türü] 'e karşılık gelen bir addır.*

 `SymbolProvider`\

 *[sembol sağlayıcısı guid]*\

 `file`\

 `CLSID` = *[sınıf guid'si]*

 *[ölçüm] = [ölçüm değeri]*

 *[ölçüm] = [ölçüm değeri]*

 `metadata`\

 `CLSID` = *[sınıf guid'si]*

 *[ölçüm] = [ölçüm değeri]*

 *[ölçüm] = [ölçüm değeri]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[sembol sağlayıcısı guid]*|Sembol sağlayıcısının GUID'si|
|*[sınıf guid'si]*|Bu sembol sağlayıcısını uygulayan sınıfın GUID'si|

### <a name="expression-evaluators"></a>İfade Değerlendiricileri
 Aşağıda, kayıt defterindeki ifade değerlendirici ölçümlerinin organizasyonu yer almaktadır. `ExpressionEvaluator`, ifade değerlendiricisi için ölçüm türü adıdır ve *[ölçüm türü] ifadesine karşılık gelen değerdir.*

> [!NOTE]
> için ölçüm türü dbgmetric.h içinde tanımlanmamıştır çünkü ifade değerlendiricileri için tüm ölçüm değişikliklerinin uygun ifade değerlendiricisi ölçüm işlevlerini kullandığı varsayılır (alt anahtarın düzeni biraz karmaşıktır, dolayısıyla ayrıntılar `ExpressionEvaluator` `ExpressionEvaluator` dbgmetric.lib içinde gizlidir).

 `ExpressionEvaluator`\

 *[dil guid'si]*\

 *[vendor guid]*\

 `CLSID` = *[sınıf guid'si]*

 *[ölçüm] = [ölçüm değeri]*

 *[ölçüm] = [ölçüm değeri]*

 `Engine`\

 `0` = *[hata ayıklama altyapısı guid]*

 `1` = *[hata ayıklama altyapısı guid]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[dil guid'si]*|Bir dilin GUID'si|
|*[vendor guid]*|Satıcının GUID'si|
|*[sınıf guid'si]*|Bu ifade değerlendiriciyi uygulayan sınıfın GUID'si|
|*[hata ayıklama altyapısı guid]*|Bu ifade değerlendiricinin birlikte çalıştır olduğu hata ayıklama altyapısının GUID'si|

### <a name="expression-evaluator-extensions"></a>İfade Değerlendirici Uzantıları
 Aşağıda, kayıt defterindeki ifade değerlendirici uzantısı ölçümlerinin organizasyonu yer almaktadır. `EEExtensions`, ifade değerlendirici uzantılarının ölçüm türü adıdır ve *[ölçüm türü] ifadesine karşılık gelen addır.*

 `EEExtensions`\

 *[extension guid]*\

 *[ölçüm] = [ölçüm değeri]*

 *[ölçüm] = [ölçüm değeri]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[extension guid]*|İfade değerlendirici uzantısının GUID'si|

### <a name="exceptions"></a>Özel durumlar
 Aşağıda, kayıt defterindeki özel durum ölçümlerinin organizasyonu ve ardından gelir. `Exception`, özel durumların ölçüm türü adıdır ve *[ölçüm türü] 'e karşılık gelir.*

 `Exception`\

 *[hata ayıklama altyapısı guid]*\

 *[özel durum türleri]*\

 *[özel durum]*\

 *[ölçüm] = [ölçüm değeri]*

 *[ölçüm] = [ölçüm değeri]*

 *[özel durum]*\

 *[ölçüm] = [ölçüm değeri]*

 *[ölçüm] = [ölçüm değeri]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[hata ayıklama altyapısı guid]*|Özel durumları destekleyen hata ayıklama altyapısının GUID'si.|
|*[özel durum türleri]*|Alt anahtar için, işnebilir özel durum sınıfını tanımlayan genel bir başlık. Tipik adlar **C++ Özel Durumları,** **Win32 Özel** Durumları, **Ortak Dil** Çalışma Zamanı Özel Durumları ve Yerel **Run-Time Denetimleridir.** Bu adlar, kullanıcı için belirli bir özel durum sınıfını tanımlamak için de kullanılır.|
|*[özel durum]*|Özel durum için bir ad: örneğin, **_com_error** veya **Control-Break**. Bu adlar, kullanıcıya belirli bir özel durumu tanımlamak için de kullanılır.|

## <a name="requirements"></a>Gereksinimler
 Bu dosyalar SDK yükleme dizininde [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] bulunur (varsayılan olarak, *[sürücü]* \Program Files\Microsoft Visual Studio 2010 \\ SDK).

 Üst bilgi: includes\dbgmetric.h

 Kitaplık: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
