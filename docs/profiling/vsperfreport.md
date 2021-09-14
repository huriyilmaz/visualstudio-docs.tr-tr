---
title: VSPerfReport | Microsoft Docs
description: VsPerfReport komut satırı aracının, veri dosyalarının profilini oluşturmak için Visual Studio Profil Oluşturma Araçları olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ef7d9f356cd0babe78e1364aacb3657f762f31ef
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725647"
---
# <a name="vsperfreport"></a>VSPerfReport
VSPerfReport komut satırı aracı, veri dosyalarının profilini oluşturmak  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları oluşturmak için kullanılır. Varsayılan rapor biçimi bir 'dır. *csv* dosyası.

 VSPerfReport aşağıdaki sözdizimini kullanır:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 'nin `filename` geçerli bir olması gerektiğini unutmayın.*vsp* veya . *vsps* dosyası.

 karşılaştırması için VSPerfReport komut satırı aracı da kullanılır. *vsp* veya . *vsps* dosyaları. Fark ("fark") raporu oluşturmak için aşağıdaki söz dizimlerini kullanın:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2` geçerli olmalıdır. *vsp* veya . *vsps* dosyaları.

## <a name="symbol-files"></a>Sembol dosyaları
 İşlev adları ve satır numaraları gibi sembol bilgilerini görüntülemek için VSPerfReport simgesine () erişim gerektirir. PDB) dosyalarını ve sembol dosyalarını Windows dosyaları. Daha fazla bilgi [için, bkz. How to: Specify symbol file locations from the command line](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).

## <a name="general-report-options"></a>Genel rapor seçenekleri
 Aşağıdaki tabloda, genel rapor biçimlendirme seçenekleri ve rapor için verileri seçen seçenekler açıklandı.

|Seçenekler|Description|
|-------------|-----------------|
|**U**|Rapor çıkışı ve yeniden yönlendirilen konsol çıkışı Unicode olarak yazılır. Belirtilen ilk seçenek olması gerekir.|
|**Özet:**[*types*]|Bir veya daha fazla rapor türü oluşturur.<br /><br /> -   `All` - tüm rapor türleri oluşturulur.<br />-   `CallerCallee` - işlevler arasındaki üst/alt ilişki.<br />-   `Function` - çağrılır işlevler.<br />-   `CallTree` - adlı işlevlerin hiyerarşisi.<br />-   `Counter`- tüm işaretleri Windows sayaç değerleriyle birlikte işaretler.<br />-   `Ip` - yönergelerin profili.<br />-   `Life` - ayrılan nesnelerin yaşam süresi (ayırma verileri toplanmış olduğunda kullanılabilir.)<br />-   `Line` kaynak kod satırı profili verileri.<br />-   `Header` - rapor dosya üst bilgisi bilgilerini içerir.<br />-   `Mark` tüm işaretler.<br />-   `Module` - modüllerin profili.<br />-   `Process` - profili yapılan işlemler.<br />-   `Thread` - profili yapılan iş parçacıkları.<br />-   `Type` - ayrılmış türler.<br />-   `Contention` - kaynak içeriği.<br />-   `RuleWarnings` - performans kuralı sorunları<br />-   `ETW`- Profil oluşturma çalıştırması Windows (ETW) olayları için tüm Olay İzleme. .etl veri dosyası özgün konumda veya .vsp veya .vsps dosyasını içeren dizinde olmalıdır.|
|**Xml**|XML biçiminde çıktı raporu.|
|**CallTrace**|İşlev girişinin ve çıkışlarının, ETW olaylarının ve işaretlerinin listesini oluşturur.|
|**ClearPackedSymbols**|Daha önce eklenmiş olan sembolleri profil oluşturma veri dosyasından kaldırır. PackSymbols'ı ikinci kez çalıştırmadan önce bu komutu çalıştırın.|
|**SymbolPath:**`path`|Profil oluşturma veri dosyası için semboller içeren bir veya daha fazla arama yolu veya sembol sunucusu belirtir.|
|**DebugSymPath**|Sembollerin arandığı konumları ve bulunıp bulun bulduklarını listeler. Bu seçenek sembol çözümleme sorunlarını çözmek için kullanışlıdır.|
|**PackSymbols**|Sembolleri profil oluşturma verileri (.vsp) dosyasına kaydeder, böylece sembol () .*pdb*) dosyaları analiz için gerekli değildir.|
|**Çıkış:** *dosya*&#124;*yolu*|Oluşturulan rapor dosyaları için alternatif bir konum belirtir. Varsayılan olarak, raporlar geçerli dizinde oluşturulur.|
|**SummaryFile**|Analiz ve analiz bilgilerini bir .vsps özet dosyasına kaydedin.|
|**PrintMarks**|Belirtilen rapor dosyasındaki tüm işaretlerin adlarını ve zaman damgalarını gösterir.|
|**?**|Kullanım bilgilerini görüntüler.|
|**NoLogo**|Rapor çalışıyorken sürüm bilgilerini gizler.|
|**UserRulesDirectory**|Kullanıcı tanımlı performans kurallarını içeren dizini belirtir [Henüz uygulanmadı].|

## <a name="filter-options"></a>Filtre seçenekleri
 Aşağıdaki tabloda kullanılabilir verileri filtreleme seçenekleri açık almaktadır.

|Seçenekler|Description|
|-------------|-----------------|
|**JustMyCode**[**:**[ `caller` ][, `callee` ]]|Yalnızca kullanıcı uygulaması işlev çağrılarını göster; sistem çağrılarını gizler.<br /><br /> - Parametre yok - tüm sistem işlevlerini gizler.<br />-   `caller` - uygulama işlevlerini çağıran bir sistem işlevi düzeyi gösterir.<br />-   `callee` - kullanıcı uygulama işlevleri tarafından çağrılan bir sistem işlevi düzeyi gösterir.|
|**StartTime:**[*value*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden).)|
|**EndTime:**[*value*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden).)|
|**FilterFile:**`VSPFFile`|Performans Raporu penceresinden oluşturulan filtre dosyasının Visual Studio belirtir.|
|**MsFilter:**[*starttime,duration*]|Yalnızca uzunluğuna `starttime` kadar olan verileri göster `duration` (milisaniye cinsinden).)|
|**İşlem:**[*pid*]|Yalnızca belirtilen işlemden gelen verileri göster.|
|**İş Parçacığı:**[*threadid*]|Yalnızca belirtilen iş parçacığından verileri gösterir.|
|**İş parçacığı:**[*threadid,processid*]|Yalnızca belirtilen işlemle ilişkili belirtilen iş parçacığından verileri gösterir.|

## <a name="difference-report-options"></a>Fark raporu seçenekleri
 Aşağıdaki tabloda rapor dosyalarını karşılaştırmak için seçenekler açık almaktadır.

|Seçenekler|Description|
|-------------|-----------------|
|**Fark**  `vspfile1 vspfile2`|İki rapor dosyası karşılaştırması ( .*vsp* veya . *vsps*) Dosyaları. Fark seçeneği kullanılarak özet seçenekleri yoksayılır.|
|**Fark:**[*değer*]|Bu eşik değerinin altında iki değer arasındaki fark göz ardı edilir. Ayrıca, bu eşiğin altındaki değerlere sahip yeni veriler gösterilmez.|
|**DiffTable:**[*tabloadı*]|Dosyaları karşılaştırmak için bu belirli tabloyu kullanın. Varsayılan değer işlevler tablosudur.|
|**Diffcolumn:**[*ColumnName*]|Bu özel sütun Compare değerlerini kullanın. Varsayılan değer, özel örnek yüzdesi sütunudur.|
|**QueryDiffTables**|Belirtilen iki rapor dosyası için geçerli tabloları ve sütunları listeleyin.|

## <a name="see-also"></a>Ayrıca bkz.
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
