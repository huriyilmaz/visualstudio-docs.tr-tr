---
title: Hata ayıklama için SDK yardımcıları | Microsoft Docs
description: C++ ' da hata ayıklama altyapılarını, Expression değerlendiricileri ve sembol sağlayıcılarını uygulamak için genel yardımcı işlevler olan işlevler ve bildirimler hakkında bilgi edinin.
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
ms.openlocfilehash: d09b91f0cbe2db0755546932455326a4e78eb13c07c846d8dd55f8984bc0145d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388998"
---
# <a name="sdk-helpers-for-debugging"></a>Hata Ayıklama için SDK Yardımcıları
Bu işlevler ve bildirimler, C++ ' da hata ayıklama altyapılarını, Expression değerlendiricileri ve sembol sağlayıcılarını uygulamak için genel yardımcı işlevlerdir.

> [!NOTE]
> Bu işlevlerin ve bildirimlerin yönetilen bir sürümü şu anda yok.

## <a name="overview"></a>Genel Bakış
 hata ayıklama motorları, ifade değerlendiricileri ve sembol sağlayıcılarının Visual Studio tarafından kullanılabilmesi için, bunların kayıtlı olmaları gerekir. Bu, kayıt defteri alt anahtarları ve girişleri ayarlanarak yapılır, aksi takdirde "ölçüm ayarı" olarak bilinir. Aşağıdaki genel işlevler, bu ölçümleri güncelleştirme sürecini kolaylaştırmak için tasarlanmıştır. Bu işlevler tarafından güncellenen her bir kayıt defteri alt anahtarının yerleşimini öğrenmek için kayıt defteri konumlarının bölümüne bakın.

## <a name="general-metric-functions"></a>Genel ölçüm Işlevleri
 Bunlar, hata ayıklama motorları tarafından kullanılan genel işlevlerdir. Expression değerlendiricileri ve symbol sağlayıcıları için özelleştirilmiş işlevler daha sonra ayrıntılı olarak açıklanmıştır.

### <a name="getmetric-method"></a>GetMetric yöntemi
 Kayıt defterinden bir ölçüm değeri alır.

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
|pszMachine|'ndaki Kaydı yazılacak olan, büyük olasılıkla uzak makinenin adı ( `NULL` yerel makine anlamına gelir).|
|pszType|'ndaki Ölçüm türlerinden biri.|
|guidSection|'ndaki Belirli bir altyapının GUID 'SI, değerlendirici, özel durum, vb. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|
|pszMetric|'ndaki Elde edilecek ölçüm. Bu, belirli bir değer adına karşılık gelir.|
|pdwValue|'ndaki Ölçümdeki değerin depolama konumu. GetMetric 'in bir DWORD (Bu örnekte olduğu gibi), bir BSTR, GUID veya GUID dizisi döndüresağlayan çeşitli türleri vardır.|
|pszAltRoot|'ndaki Kullanılacak alternatif bir kayıt defteri kökü. Varsayılan öğesini `NULL` kullanmak için olarak ayarlayın.|

### <a name="setmetric-method"></a>SetMetric yöntemi
 Kayıt defterindeki belirtilen ölçüm değerini ayarlar.

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
|pszType|'ndaki Ölçüm türlerinden biri.|
|guidSection|'ndaki Belirli bir altyapının GUID 'SI, değerlendirici, özel durum, vb. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|
|pszMetric|'ndaki Elde edilecek ölçüm. Bu, belirli bir değer adına karşılık gelir.|
|dwValue|'ndaki Ölçümdeki değerin depolama konumu. SetMetric 'in bir DWORD (Bu örnekte), bir BSTR, GUID veya GUID dizisi depolayabilen çeşitli türleri vardır.|
|fUserSpecific|'ndaki Ölçüm kullanıcıya özgü ise ve yerel makine Hive yerine kullanıcının yığınına yazılması gerekiyorsa doğru.|
|pszAltRoot|'ndaki Kullanılacak alternatif bir kayıt defteri kökü. Varsayılan öğesini `NULL` kullanmak için olarak ayarlayın.|

### <a name="removemetric-method"></a>RemoveMetric yöntemi
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
|pszType|'ndaki Ölçüm türlerinden biri.|
|guidSection|'ndaki Belirli bir altyapının GUID 'SI, değerlendirici, özel durum, vb. Bu, belirli bir öğe için ölçüm türü altında bir alt bölüm belirtir.|
|pszMetric|'ndaki Kaldırılacak ölçüm. Bu, belirli bir değer adına karşılık gelir.|
|pszAltRoot|'ndaki Kullanılacak alternatif bir kayıt defteri kökü. Varsayılan öğesini `NULL` kullanmak için olarak ayarlayın.|

### <a name="enummetricsections-method"></a>EnumMetricSections yöntemi
 Kayıt defterindeki çeşitli ölçüm bölümlerini numaralandırır.

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
|RemoveAllExceptionMetrics|Tüm özel durum ölçümlerini kayıt defterinden kaldırır.|

## <a name="symbol-provider-functions"></a>Sembol Sağlayıcısı İşlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|GetSPMetric|Kayıt defterinden bir ölçüm değeri verir.|
|SetSPMetric|Kayıt defterinde belirtilen ölçüm değerini ayarlar.|
|RemoveSPMetric|Belirtilen ölçümü kayıt defterinden kaldırır.|

## <a name="enumeration-functions"></a>Numaralama İşlevleri

|İşlev|Açıklama|
|--------------|-----------------|
|EnumMetricSections|Belirtilen ölçüm türü için tüm ölçümleri numaralar.|
|EnumDebugEngine|Kayıtlı hata ayıklama altyapılarını numaralar.|
|EnumEEs|Kayıtlı ifade değerlendiricilerini numaralar.|
|EnumExceptionMetrics|Tüm özel durum ölçümlerini numaralar.|

## <a name="metric-definitions"></a>Ölçüm Tanımları
 Bu tanımlar önceden tanımlanmış ölçüm adları için kullanılabilir. Adlar çeşitli kayıt defteri anahtar ve değer adlarını ifade eder ve bunların hepsi geniş karakter dizeleri olarak tanımlanır: örneğin, `extern LPCWSTR metrictypeEngine` .

|Önceden Tanımlanmış Ölçüm Türleri|Açıklama: için temel anahtar...|
|-----------------------------|---------------------------------------|
|metrictypeEngine|Tüm hata ayıklama altyapısı ölçümleri.|
|metrictypePortSupplier|Tüm bağlantı noktası tedarikçi ölçümleri.|
|metrictypeException|Tüm özel durum ölçümleri.|
|metricttypeEEExtension|Tüm ifade değerlendirici uzantıları.|

|Hata Ayıklama Altyapısı Özellikleri|Açıklama|
|-----------------------------|-----------------|
|metricAddressBP|Adres kesme noktaları desteğini belirtmek için sıfır olmayan olarak ayarlayın.|
|metricAlwaysLoadLocal|Hata ayıklama altyapısını her zaman yerel olarak yüklemek için sıfır olmayan olarak ayarlayın.|
|metricLoadInDebuggeeSession|KULLANILMADI|
|metricLoadedByDebuggee|Hata ayıklama altyapısının her zaman hata ayıklama yapılan program tarafından veya ile yük olacağını belirtmek için sıfır olmayan olarak ayarlayın.|
|metricAttach|Mevcut programlara ek desteğini göstermek için sıfır olmayan olarak ayarlayın.|
|metricCallStackBP|Çağrı yığını kesme noktaları desteğini belirtmek için sıfır olmayan olarak ayarlayın.|
|metricConditionalBP|Koşullu kesme noktaları ayarının desteğini belirtmek için sıfır olmayan olarak ayarlayın.|
|metricDataBP|Verilerde yapılan değişikliklerde kesme noktası ayarının desteğini belirtmek için sıfır olmayan olarak ayarlayın.|
|metricDisassembly|Bir disassembly listesinin üretimine yönelik desteği belirtmek için sıfır olmayan olarak ayarlayın.|
|metricDumpWriting|Döküm yazma desteğini belirtmek için sıfır olmayan olarak ayarlayın (bellek dökümleri bir çıkış cihazına boşaltıldı).|
|metricENC|Düzenle ve Devam'a destek olduğunu belirtmek için sıfır olmayan olarak ayarlayın. **Not:**  Özel hata ayıklama altyapısı bunu hiçbir zaman ayarlamalı veya her zaman 0 olarak ayarlamalı.|
|metricExceptions|Özel durumlar için desteği belirtmek için sıfır olmayan olarak ayarlayın.|
|metricFunctionBP|Adlandırılmış kesme noktaları (belirli bir işlev adı çağrıldı olduğunda kesme noktaları) için desteği belirtmek için sıfır olmayan olarak ayarlayın.|
|metricHitCountBP|"Isabet noktası" kesme noktaları (yalnızca belirli bir sayıya isabet edildikten sonra tetiklenen kesme noktaları) ayarını desteklemek için sıfır olmayan olarak ayarlayın.|
|metricJITDebug|Tam zamanında hata ayıklama desteğini belirtmek için sıfır dışında olarak ayarlayın (çalışan bir işlemde özel durum oluştuğunda hata ayıklayıcı başlatıldı).|
|metricMemory|KULLANILMADI|
|metricPortSupplier|Uygulanırsa, bunu bağlantı noktası sağlayıcının CLSID'siD'si olarak ayarlayın.|
|metricRegisters|KULLANILMADI|
|metricSetNextStatement|Sonraki deyimi ayarlama desteğini belirtmek için sıfır olmayan olarak ayarlayın (bu, ara deyimlerin yürütülmesini atlar).|
|metricSuspendThread|İş parçacığı yürütmeyi askıya alma desteğini belirtmek için sıfır olmayan olarak ayarlayın.|
|metricWarnIfNoSymbols|Simge yoksa kullanıcıya bildirilecekleri belirtmek için sıfır olmayan olarak ayarlayın.|
|metricProgramProvider|Bunu program sağlayıcısının CLSID'siD'si olarak ayarlayın.|
|metricAlwaysLoadProgramProviderLocal|Program sağlayıcısının her zaman yerel olarak yüklenmiş olması gerektiğini belirtmek için bunu sıfır olmayan olarak ayarlayın.|
|metricEngineCanWatchProcess|Hata ayıklama altyapısının program sağlayıcısı yerine işlem olaylarını izleyeceğini belirtmek için bunu sıfır olmayan olarak ayarlayın.|
|metricRemoteDebugging|Uzaktan hata ayıklama desteğini belirtmek için bunu sıfır olmayan olarak ayarlayın.|
|metricEncUseNativeBuilder|Düzenle ve Devam'a göre derlemek üzere Düzenle ve Devam Etmek için Düzenle ve Devam encbuild.dll hata ayıklama altyapısının altyapısını kullanması gerektiğini belirtmek için bunu sıfır dışı olarak ayarlayın. **Not:**  Özel hata ayıklama altyapısı bunu hiçbir zaman ayarlamalı veya her zaman 0 olarak ayarlamalı.|
|metricLoadUnderWOW64|Hata ayıklama altyapısının 64 bit işlemde hata ayıklama sırasında WOW altında hata ayıklama işlemi içinde yüklü olması gerektiğini belirtmek için bunu sıfır dışı olarak ayarlayın; aksi takdirde, hata ayıklama altyapısı Visual Studio (WOW64 altında çalışıyor) yüklenir.|
|metricLoadProgramProviderUnderWOW64|WOW altında 64 bit işlemde hata ayıklarken hata ayıklama sürecinde program sağlayıcısının yüklü olması gerektiğini belirtmek için bunu sıfır dışı olarak ayarlayın; aksi takdirde, bu işlem Visual Studio yüklenir.|
|metricStopOnExceptionCrossingManagedBoundary|Yönetilen/yönetilmeyen kod sınırları arasında işilmeyen bir özel durum olursa, sürecin durdurması gerektiğini belirtmek için bunu sıfır dışı olarak ayarlayın.|
|metricAutoSelectPriority|Hata ayıklama altyapısının otomatik seçimi için bunu bir öncelik olarak ayarlayın (daha yüksek değerler daha yüksek önceliğe eşittir).|
|metricAutoSelectIncompatibleList|Otomatik seçimde yok sayılacak hata ayıklama altyapısının GUID 'Lerini belirten girişleri içeren kayıt defteri anahtarı. Bu girişler, bir dize olarak ifade edilen bir GUID ile (0, 1, 2, vb.) bir sayıdır.|
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

|Yer tutucu|Açıklama|
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

|Yer tutucu|Açıklama|
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

|Yer tutucu|Açıklama|
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

|Yer tutucu|Açıklama|
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

|Yer tutucu|Açıklama|
|-----------------|-----------------|
|*[hata ayıklama altyapısı GUID]*|Özel durumları destekleyen bir hata ayıklama altyapısının GUID 'ı.|
|*[özel durum türleri]*|Ele alınan özel durumların sınıfını tanımlayan alt anahtar için genel bir başlık. Genellikle **C++ özel durumları**, **Win32 özel durumları**, **ortak dil çalışma zamanı özel durumları** ve **Yerel Run-Time denetimleri** bulunur. Bu adlar, kullanıcıya belirli bir özel durum sınıfını tanımlamak için de kullanılır.|
|*duruma*|Özel durum için bir ad: Örneğin, **_com_error** veya **Denetim kesme**. Bu adlar, kullanıcıya özel bir özel durumu tanımlamak için de kullanılır.|

## <a name="requirements"></a>Gereksinimler
 bu dosyalar [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK yükleme dizininde bulunur (varsayılan olarak, *[sürücü]* \program files \ Microsoft Visual Studio 2010 SDK \\ ).

 Üstbilgi: includes\dbgmetric.h

 Kitaplık: libs\ad2de.exe, libs\dbgmetric.exe

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
