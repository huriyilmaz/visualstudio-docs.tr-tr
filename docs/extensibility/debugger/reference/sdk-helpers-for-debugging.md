---
title: Hata Ayıklama için SDK Yardımcıları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713643"
---
# <a name="sdk-helpers-for-debugging"></a>Hata Ayıklama için SDK Yardımcıları
Bu işlevler ve bildirimler, hata ayıklama altyapılarını, ifade değerlendiricilerini ve C++'daki sembol sağlayıcılarını uygulamak için genel yardımcı işlevlerdir.

> [!NOTE]
> Şu anda bu işlevlerin ve bildirimlerin yönetilen sürümü yok.

## <a name="overview"></a>Genel Bakış
 Hata ayıklama motorları, ifade değerlendiricilerve sembol sağlayıcılarının Visual Studio tarafından kullanılabilmesi için bunların kaydedilmesi gerekir. Bu, kayıt defteri alt anahtarlarını ve girişlerini ayarlayarak yapılır, aksi takdirde "ölçümleri ayarlama" olarak bilinir. Aşağıdaki genel işlevler, bu ölçümleri güncelleştirme işlemini kolaylaştırmak için tasarlanmıştır. Bu işlevler tarafından güncelleştirilen her kayıt defteri alt anahtarının düzenini öğrenmek için Kayıt Defteri Konumları'ndaki bölüme bakın.

## <a name="general-metric-functions"></a>Genel Metrik Fonksiyonlar
 Bunlar hata ayıklama motorları tarafından kullanılan genel işlevlerdir. İfade değerlendiriciler ve sembol sağlayıcıları için özel leştirilmiş işlevler daha sonra ayrıntılı olarak açıklanır.

### <a name="getmetric-method"></a>GetMetric Yöntemi
 Kayıt defterinden bir metrik değer alır.

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
|pszMachine|[içinde] Muhtemelen uzak bir makinenin adı olan`NULL` kayıt (yerel makine anlamına gelir) yazılacaktır.|
|pszType|[içinde] Metrik türlerden biri.|
|guidSection|[içinde] Belirli bir motorun, değerlendiricinin, istisnanın vb. GUID'i Bu, belirli bir öğe için metrik türü altında bir alt bölüm belirtir.|
|pszMetric|[içinde] Elde edilecek metrik. Bu, belirli bir değer adına karşılık gelir.|
|pdwDeğer|[içinde] Metrikteki değerin depolama konumu. GetMetric'in bir DWORD (bu örnekte olduğu gibi), bir BSTR, GUID veya bir dizi GUID döndürebilecek birkaç tadı vardır.|
|pszAltRoot|[içinde] Kullanılacak alternatif bir kayıt defteri kökü. Varsayılanı `NULL` kullanmak üzere ayarlayın.|

### <a name="setmetric-method"></a>SetMetric Yöntemi
 Kayıt defterinde belirtilen metrik değeri ayarlar.

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
|pszType|[içinde] Metrik türlerden biri.|
|guidSection|[içinde] Belirli bir motorun, değerlendiricinin, istisnanın vb. GUID'i Bu, belirli bir öğe için metrik türü altında bir alt bölüm belirtir.|
|pszMetric|[içinde] Elde edilecek metrik. Bu, belirli bir değer adına karşılık gelir.|
|dwDeğer|[içinde] Metrikteki değerin depolama konumu. SetMetric'in bir DWORD (bu örnekte), bir BSTR, GUID veya bir dizi GUID depolayabilen birkaç tadı vardır.|
|fUserSpecific|[içinde] Metrik kullanıcıya özelse ve yerel makine kovanı yerine kullanıcının kovanına yazılması gerekiyorsa DOĞRU.|
|pszAltRoot|[içinde] Kullanılacak alternatif bir kayıt defteri kökü. Varsayılanı `NULL` kullanmak üzere ayarlayın.|

### <a name="removemetric-method"></a>RemoveMetric Yöntemi
 Belirtilen ölçütleri kayıt defterinden kaldırır.

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
|pszType|[içinde] Metrik türlerden biri.|
|guidSection|[içinde] Belirli bir motorun, değerlendiricinin, istisnanın vb. GUID'i Bu, belirli bir öğe için metrik türü altında bir alt bölüm belirtir.|
|pszMetric|[içinde] Kaldırılacak metrik. Bu, belirli bir değer adına karşılık gelir.|
|pszAltRoot|[içinde] Kullanılacak alternatif bir kayıt defteri kökü. Varsayılanı `NULL` kullanmak üzere ayarlayın.|

### <a name="enummetricsections-method"></a>EnumMetricSections Yöntemi
 Kayıt defterindeki çeşitli metrik bölümleri oyalar.

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
|pszMachine|[içinde] Muhtemelen uzak bir makinenin adı olan`NULL` kayıt (yerel makine anlamına gelir) yazılacaktır.|
|pszType|[içinde] Metrik türlerden biri.|
|rgguidBölümler|[içinde, dışarı] Doldurulacak önceden tahsis edilmiş GUID dizisi.|
|pdwSize|[içinde] `rgguidSections` Dizide depolanabilecek maksimum GUID sayısı.|
|pszAltRoot|[içinde] Kullanılacak alternatif bir kayıt defteri kökü. Varsayılanı `NULL` kullanmak üzere ayarlayın.|

## <a name="expression-evaluator-functions"></a>İfade Değerlendirici Fonksiyonları

|İşlev|Açıklama|
|--------------|-----------------|
|Geteemetric|Kayıt defterinden bir metrik değer alır.|
|Seteemetric|Kayıt defterinde belirtilen metrik değeri ayarlar.|
|Removeeemetric|Belirtilen ölçütleri kayıt defterinden kaldırır.|
|GetEEMetricFile|Belirtilen ölçümden bir dosya adı alır ve dosya içeriğini dize olarak döndürerek yükler.|

## <a name="exception-functions"></a>Özel Durum Fonksiyonları

|İşlev|Açıklama|
|--------------|-----------------|
|GetExceptionMetric|Kayıt defterinden bir metrik değer alır.|
|SetExceptionMetric|Kayıt defterinde belirtilen metrik değeri ayarlar.|
|Özel DurumMetrik'i Kaldırma|Belirtilen ölçütleri kayıt defterinden kaldırır.|
|RemoveAllExceptionMetrics|Kayıt defterindeki tüm özel durum ölçümlerini kaldırır.|

## <a name="symbol-provider-functions"></a>Sembol Sağlayıcı Fonksiyonları

|İşlev|Açıklama|
|--------------|-----------------|
|Getspmetric|Kayıt defterinden bir metrik değer alır.|
|Setspmetric|Kayıt defterinde belirtilen metrik değeri ayarlar.|
|Spmetric'i kaldırır|Belirtilen ölçütleri kayıt defterinden kaldırır.|

## <a name="enumeration-functions"></a>Numaralandırma Fonksiyonları

|İşlev|Açıklama|
|--------------|-----------------|
|EnumMetricSections|Belirli bir metrik türü için tüm ölçümleri oyalar.|
|EnumDebugEngine|Kayıtlı hata ayıklama motorlarını oyalar.|
|EnumEEs|Kayıtlı ifade değerlendiricileri oyalar.|
|EnumExceptionMetrics|Tüm özel durum ölçümlerini doğrular.|

## <a name="metric-definitions"></a>Metrik Tanımlar
 Bu tanımlar önceden tanımlanmış metrik adlar için kullanılabilir. Adlar çeşitli kayıt defteri anahtarlarına ve değer adlarına karşılık gelir ve `extern LPCWSTR metrictypeEngine`tüm geniş karakter dizeleri olarak tanımlanır: örneğin.

|Önceden Tanımlanmış Metrik Türleri|Açıklama: Temel anahtar için ....|
|-----------------------------|---------------------------------------|
|metrictypeMotor|Tüm hata ayıklama motoru ölçümleri.|
|metrictypePortSupplier|Tüm liman tedarikçisi ölçümleri.|
|metrictypeException|Tüm özel durum ölçümleri.|
|metricttypeEEExtension|Tüm ifade değerlendirici uzantıları.|

|Hata Ayıklama Motoru Özellikleri|Açıklama|
|-----------------------------|-----------------|
|metricAddressBP|Adres kesme noktaları için destek belirtmek için sıfıra göre ayarlayın.|
|metricAlwaysLoadYerel|Hata ayıklama motorını her zaman yerel olarak yüklemek için sıfıra ayarlanın.|
|metricLoadInDebuggeeSession|KULLANıLMAZ|
|metricLoadedByDebuggee|Hata ayıklama altyapısının her zaman program tarafından yüklendiğini veya hata ayıklandığını belirtmek için sıfırsız olarak ayarlayın.|
|metricAttach|Varolan programlara ek desteğini belirtmek için sıfıra ayarlayın.|
|metricCallStackBP|Çağrı yığını kesme noktaları için destek belirtmek için sıfırolmayan olarak ayarlayın.|
|metricConditionalBP|Koşullu kesme noktalarının ayarını desteklemek için sıfıra ayarlayın.|
|metricDataBP|Verilerdeki değişikliklerde kesme noktalarının ayarlanması için destek belirtmek için sıfıra göre sıfıra ayarlayın.|
|metrikDisassembly|Bir sökme listesinin üretimi için destek göstermek için sıfıra göre ayarlayın.|
|metricDumpWriting|Döküm yazma desteği (bellek bir çıkış aygıtına dökümü) için destek göstermek için sıfır olmayan olarak ayarlayın.|
|metricENC|Edit ve Continue desteğini belirtmek için sıfıra ayarlayın. **Not:**  Özel hata ayıklama altyapısı bunu asla ayarlamamalı veya her zaman 0 olarak ayarlamamalıdır.|
|metricİst'ler|Özel durumlar için destek belirtmek için sıfıra ayarlayın.|
|metricFunctionBP|Adlandırılmış kesme noktaları (belirli bir işlev adı çağrıldığında kırığı kesme noktaları) için destek göstermek için sıfır olmayan olarak ayarlayın.|
|metricHitCountBP|"Isabet noktası" kesme noktalarının (yalnızca belirli bir sayıda vurulduktan sonra tetiklenen kesme noktaları) ayarını desteklemek için sıfıra göre ayarlayın.|
|metricJITDebug|Tam zamanında hata ayıklama desteğini belirtmek için sıfıra ayarlanır (çalışan bir işlemde bir özel durum oluştuğunda hata ayıklama başlatılır).|
|metricMemory|KULLANıLMAZ|
|metricPortSupplier|Uygulandığında bunu liman tedarikçisinin CLSID'sine ayarlayın.|
|metricRegisters|KULLANıLMAZ|
|metricSetNextStatement|Bir sonraki deyimin ayarlanması için destek belirtmek için sıfır ayarı (ara deyimlerin yürütülmesini atlar).|
|metricSuspendThread|İş parçacığı yürütmeaskıya destek belirtmek için sıfır olmayan olarak ayarlayın.|
|metricWarnIfNoSymbols|Sembol yoksa kullanıcıya bildirilmesi gerektiğini belirtmek için sıfırolmayan olarak ayarlayın.|
|metricProgramProvider|Bunu program sağlayıcısının CLSID'sine ayarlayın.|
|metricAlwaysLoadProgramProviderLocal|Program sağlayıcısının her zaman yerel olarak yüklenmesi gerektiğini belirtmek için bunu sıfıra ayarlayın.|
|metricEngineCanWatchProcess|Hata ayıklama altyapısının program sağlayıcısı yerine işlem olaylarını izleyeceğini belirtmek için bunu sıfıra ayarlayın.|
|metrikUzaktan Dinleme|Uzaktan hata ayıklama desteğini belirtmek için bunu sıfırolmayan olarak ayarlayın.|
|metricEncUseNativeBuilder|Edit ve Continue Manager'ın Hata Ayıklama altyapısının encbuild.dll'sini edit ve continue için oluşturması gerektiğini belirtmek için bunu sıfıra ayarlayın. **Not:**  Özel hata ayıklama altyapısı bunu asla ayarlamamalı veya her zaman 0 olarak ayarlamamalıdır.|
|metricLoadUnderWOW64|Hata ayıklama altyapısının 64 bit lik bir işlemi hata ayıklarken WOW altındaki hata ayıklama işlemine yüklenmesi gerektiğini belirtmek için bunu sıfıra ayarlayın; aksi takdirde hata ayıklama motoru Visual Studio işleminde yüklenir (WOW64 altında çalışır).|
|metricLoadProgramProviderUnderWOW64|Program sağlayıcısının WOW altında 64 bit işlemin hata ayıklama işleminde hata ayıklama işlemine yüklenmesi gerektiğini belirtmek için bunu sıfıra ayarlayın; aksi takdirde, Visual Studio işleminde yüklenir.|
|metricStopOnExceptionCrossingManagedBoundary|İşlenmemiş bir özel durum yönetilen/yönetilmeyen kod sınırları arasında atıldığında işlemin durmasını belirtmek için bunu sıfıra ayarlayın.|
|metricAutoSelectPriority|Hata ayıklama altyapısının otomatik seçimi için bunu bir önceliğe ayarlayın (daha yüksek değerler daha yüksek önceliğe eşittir).|
|metricAutoSelectUyumListe|Hata ayıklama motorları için GUID'leri belirten girişleri içeren kayıt defteri anahtarı, otomatik seçimde yoksayılması. Bu girişler, guid dize olarak ifade edilen bir sayı (0, 1, 2 vb.) dir.|
|metricUyumsuzListe|Bu hata ayıklama altyapısıyla uyumsuz hata ayıklama motorları için GUID'leri belirten girişler içeren kayıt defteri anahtarı.|
|metrikDisableJITOptimization|Hata ayıklama sırasında tam zamanında optimizasyonların (yönetilen kod için) devre dışı bırakılması gerektiğini belirtmek için bunu sıfıra ayarlayın.|

|İfade Değerlendirici Özellikleri|Açıklama|
|-------------------------------------|-----------------|
|metricEngine|Bu, belirtilen ifade değerlendiricisi destekleyen hata ayıklama motorlarının sayısını tutar.|
|metricPreloadModüller|Bir programa karşı bir ifade değerlendiricisi başlatıldığında modüllerin önceden yüklenmesi gerektiğini belirtmek için bunu sıfıra ayarlayın.|
|metricThisObjectName|Bunu "bu" nesne adı olarak ayarlayın.|

|İfade Değerlendirici Uzantı Özellikleri|Açıklama|
| - |-----------------|
|metricExtensionDll|Bu uzantıyı destekleyen dll adı.|
|metricExtensionRegistersDesteklenen|Desteklenen kayıtların listesi.|
|metricExtensionRegistersEntryPoint|Kayıtlara erişmek için giriş noktası.|
|metricExtensionTypesDestekli|Desteklenen türlerin listesi.|
|metricExtensionTypesEntryPoint|Türlere erişmek için giriş noktası.|

|Liman Tedarikçisi Özellikleri|Açıklama|
|------------------------------|-----------------|
|metricPortPickerCLSID|Bağlantı noktası seçicinin CLSID'si (kullanıcının bağlantı noktalarını seçmek ve hata ayıklamak için kullanılacak bağlantı noktaları eklemek için kullanabileceği bir iletişim kutusu).|
|metricDisallowUserEnteredPorts|Kullanıcı tarafından girilen bağlantı noktaları bağlantı noktası tedarikçisine eklenemezse sıfıra inmez (bu, bağlantı noktası seçici iletişim kutusunu temelde salt okunur hale getirir).|
|metricPidBase|İşlem kimliklerini ayırırken bağlantı noktası tedarikçisi tarafından kullanılan temel işlem kimliği.|

|Önceden Tanımlanmış SP Mağaza Türleri|Açıklama|
|-------------------------------|-----------------|
|storetypeFile|Semboller ayrı bir dosyada saklanır.|
|storetypeMetadata|Semboller bir derlemede meta veri olarak depolanır.|

|Çeşitli Özellikler|Açıklama|
|------------------------------|-----------------|
|metricShowNonUserCode|Kullanıcı olmayan kodu göstermek için bunu sıfırolmayan olarak ayarlayın.|
|metricJustMyCodeStepping|Adımatmanın yalnızca kullanıcı kodunda gerçekleşebileceğini belirtmek için bunu sıfıra ayarlayın.|
|metricCLSID|Belirli bir metrik türdeki bir nesne için CLSID.|
|metricName|Belirli bir metrik türdeki bir nesne için kullanıcı dostu ad.|
|metricLanguage|Dil adı.|

## <a name="registry-locations"></a>Kayıt Yerleri
 Ölçümler, özellikle `VisualStudio` alt anahtarda, kayıt defterinden okunur ve yazılır.

> [!NOTE]
> Çoğu zaman, ölçümler HKEY_LOCAL_MACHINE tuşuna yazılır. Ancak, bazen HKEY_CURRENT_USER hedef anahtarı olacaktır. Dbgmetric.lib her iki anahtarı da işler. Bir metrik alırken, önce HKEY_CURRENT_USER arar, sonra HKEY_LOCAL_MACHINE. Bir metrik ayarlanırken, bir parametre hangi üst düzey anahtarın kullanılacağını belirtir.

 *[kayıt defteri anahtarı]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[sürüm kökü]*\

 *[metrik kök]*\

 *[metrik türü]*\

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[kayıt defteri anahtarı]*|`HKEY_CURRENT_USER` veya `HKEY_LOCAL_MACHINE`.|
|*[sürüm kökü]*|Visual Studio sürümü (örneğin, `7.0` `7.1`, `8.0`, veya ). Ancak, bu kök **devenv.exe** **/rootsuffix** anahtarı kullanılarak da değiştirilebilir. VSIP için, bu değiştirici genellikle **Exp**, bu nedenle sürüm kökü, örneğin, 8.0Exp olacaktır.|
|*[metrik kök]*|Bu ya `AD7Metrics` `AD7Metrics(Debug)`da, dbgmetric.lib hata ayıklama sürümü kullanılıp kullanılmadığına bağlı olarak. **Not:**  Dbgmetric.lib kullanılsa da kullanılmasa da, hata ayıklama ve sürüm sürümleri arasında kayıt defterine yansıtılması gereken farklar varsa bu adlandırma kuralına uyulmalıdır.|
|*[metrik türü]*|Yazılacak metrik türü: `Engine`, `ExpressionEvaluator` `SymbolProvider`, , vb. Bunların hepsi dbgmetric.h olarak `metricTypeXXXX`tanımlanır `XXXX` , nerede belirli tür adıdır.|
|*[metrik]*|Ölçümü ayarlamak için bir değer atanacak bir girişin adı. Ölçümlerin gerçek organizasyonu metrik türüne bağlıdır.|
|*[metrik değer]*|Metrmeye atanan değer. Değerin olması gereken tür (dize, sayı, vb.) metrik bağlıdır.|

> [!NOTE]
> Tüm GUID'ler `{GUID}`. Örneğin, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.

### <a name="debug-engines"></a>Hata Ayıklama Motorları
 Aşağıda, hata ayıklama motorları ölçümlerinin kayıt defterinde düzenlenmesi yer alan dır. `Engine`hata ayıklama altyapısının metrik türü adıdır ve yukarıdaki kayıt defteri alt ağacındaki *[metrik türü]* ile karşılık gelir.

 `Engine`\

 *[motor kılavuz]*\

 `CLSID` = *[sınıf rehberlik]*

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

 `PortSupplier`\

 `0` = *[liman tedarikçisi kılavuz]*

 `1` = *[liman tedarikçisi kılavuz]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[motor kılavuz]*|Hata ayıklama motorunun GUID'i.|
|*[sınıf rehberlik]*|Bu hata ayıklama altyapısını uygulayan sınıfın GUID'i.|
|*[liman tedarikçisi kılavuz]*|Varsa liman tedarikçisinin GUID'i. Birçok hata ayıklama motoru varsayılan bağlantı noktası tedarikçisini kullanır ve bu nedenle kendi tedarikçilerini belirtmez. Bu durumda, alt `PortSupplier` anahtar yok olacaktır.|

### <a name="port-suppliers"></a>Bağlantı Noktası Sağlayıcıları
 Aşağıda, kayıt defterindeki liman tedarikçisi ölçümlerinin organizasyonu vereme yer adatır. `PortSupplier`bir bağlantı noktası tedarikçisinin metrik türü adıdır ve *[metrik tür]* ile karşılık gelir.

 `PortSupplier`\

 *[liman tedarikçisi kılavuz]*\

 `CLSID` = *[sınıf rehberlik]*

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[liman tedarikçisi kılavuz]*|Liman tedarikçisinin GUID'i|
|*[sınıf rehberlik]*|Bu bağlantı noktası tedarikçisini uygulayan sınıfın GUID'i|

### <a name="symbol-providers"></a>Sembol Sağlayıcıları
 Aşağıda, kayıt defterindeki sembol tedarikçi ölçümlerinin organizasyonu vereme yer adatır. `SymbolProvider`sembol sağlayıcısının metrik türü adıdır ve *[metrik tür]* ile karşılık gelir.

 `SymbolProvider`\

 *[sembol sağlayıcı guid]*\

 `file`\

 `CLSID` = *[sınıf rehberlik]*

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

 `metadata`\

 `CLSID` = *[sınıf rehberlik]*

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[sembol sağlayıcı guid]*|Sembol sağlayıcısının GUID'i|
|*[sınıf rehberlik]*|Bu sembol sağlayıcısını uygulayan sınıfın GUID'i|

### <a name="expression-evaluators"></a>İfade Değerlendiriciler
 Aşağıda, kayıt defterindeki ifade değerlendirici ölçümlerinin organizasyonu verememektedir. `ExpressionEvaluator`ifade değerlendiricinin metrik türü adıdır ve *[metrik tür]* ile karşılık gelir.

> [!NOTE]
> İfade değerlendiriciler için tüm metrik değişikliklerin uygun ifade değerlendirici metrik işlevlerinden geçeceği varsayıldığı için metrik türü `ExpressionEvaluator` dbgmetric.h'de tanımlanmamıştır `ExpressionEvaluator` (alt anahtarın düzeni biraz karmaşıktır, bu nedenle ayrıntılar dbgmetric.lib'in içine gizlenir).

 `ExpressionEvaluator`\

 *[dil rehberliği]*\

 *[satıcı kılavuz]*\

 `CLSID` = *[sınıf rehberlik]*

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

 `Engine`\

 `0` = *[hata ayıklama motoru kılavuz]*

 `1` = *[hata ayıklama motoru kılavuz]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[dil rehberliği]*|Bir dilin GUID|
|*[satıcı kılavuz]*|Bir satıcının GUID|
|*[sınıf rehberlik]*|Bu ifade değerlendiricisini uygulayan sınıfın GUID'i|
|*[hata ayıklama motoru kılavuz]*|Bu ifade değerlendiricinin birlikte çalıştığı hata ayıklama altyapısının GUID'i|

### <a name="expression-evaluator-extensions"></a>İfade Değerlendirici Uzantıları
 Aşağıda, kayıt defterindeki ifade değerlendirici uzantı ölçümlerinin organizasyonu vereme mektedir. `EEExtensions`ifade değerlendirici uzantıları için metrik tür adıdır ve *[metrik türü]* karşılık gelir.

 `EEExtensions`\

 *[uzantı kılavuz]*\

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[uzantı kılavuz]*|Bir ifade değerlendirici uzantısı NıN GUID'i|

### <a name="exceptions"></a>Özel durumlar
 Aşağıda, kayıt defterindeki özel durum ölçümlerinin organizasyonu vereme yer adatır. `Exception`özel durumlar için metrik tür adıdır ve *[metrik türü]* karşılık gelir.

 `Exception`\

 *[hata ayıklama motoru kılavuz]*\

 *[özel durum türleri]*\

 *[özel durum]*\

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

 *[özel durum]*\

 *[metrik] = [metrik değer]*

 *[metrik] = [metrik değer]*

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[hata ayıklama motoru kılavuz]*|Özel durumları destekleyen hata ayıklama altyapısının GUID'i.|
|*[özel durum türleri]*|İşlenebilir özel durumlar sınıfını tanımlayan alt anahtar için genel bir başlık. Tipik adlar **C++ Özel Durumlar,** **Win32 Özel Durumlar,** Ortak Dil Çalışma Zamanı Özel Durumları ve Yerel Çalışma **Zamanı Denetimleridir.** **Native Run-Time Checks** Bu adlar, kullanıcıiçin özel bir sınıf tanımlamak için de kullanılır.|
|*[özel durum]*|Bir özel durum için bir ad: örneğin, **_com_error** veya **Denetim-Break**. Bu adlar, kullanıcıya özel bir özel durumu tanımlamak için de kullanılır.|

## <a name="requirements"></a>Gereksinimler
 Bu dosyalar [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK yükleme dizininde bulunur (varsayılan olarak, *[sürücü]* \Program Files\Microsoft Visual\\Studio 2010 SDK).

 Üstbilgi: içerir\dbgmetric.h

 Kitaplık: libs\ad2de.lib, libs\dbgmetric.lib

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
