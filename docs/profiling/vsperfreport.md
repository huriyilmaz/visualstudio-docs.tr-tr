---
title: VSPerfReport | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 282bb801625429d639e625a0a5edb02a8fb4da25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777991"
---
# <a name="vsperfreport"></a>VSPerfReport
VSPerfReport komut satırı aracı, Profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Oluşturma Araçları profil oluşturma veri dosyalarını kullanarak raporlar oluşturmak için kullanılır. Varsayılan rapor biçimi bir . *csv* dosyası.

 VSPerfReport aşağıdaki sözdizimini kullanır:

```cmd
VSPerfReport [/U] vspfilename [/options]
```

 Geçerli `filename` olması gerektiğini unutmayın. *vsp* veya . *vsps* dosyası.

 VSPerfReport komut satırı aracı da karşılaştırmak için kullanılır. *vsp* veya . *vsps* dosyaları. Bir fark ("diff") raporu oluşturmak için aşağıdaki sözdizimini kullanın:

```cmd
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]
```

 `vspfilename1 and vspfilename2`geçerli olmalıdır. *vsp* veya . *vsps* dosyaları.

## <a name="symbol-files"></a>Sembol dosyaları
 Işlev adları ve satır numaraları gibi sembol bilgilerini görüntülemek için VSPerfReport sembolüne erişim gerektirir (. PDB) profilli bileşenlerin dosyaları ve Windows sembol dosyaları. Daha fazla bilgi için [bkz: Komut satırından sembol dosya konumlarını belirtin.](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)

## <a name="general-report-options"></a>Genel rapor seçenekleri
 Aşağıdaki tabloda genel rapor biçimlendirme seçenekleri ve bildirilecek verileri seçen seçenekler açıklanmaktadır.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**U**|Rapor çıktısı ve yeniden yönlendirilen konsol çıktısı Unicode olarak yazılır. Belirtilen ilk seçenek olmalıdır.|
|**Özet:**[*türleri*]|Bir veya daha fazla rapor türü oluşturur.<br /><br /> -   `All`- tüm rapor türleri oluşturulur.<br />-   `CallerCallee`- işlevler arasındaki ebeveyn-alt ilişkileri.<br />-   `Function`- fonksiyonlar denir.<br />-   `CallTree`- işlevlerihiyerarşisi denir.<br />-   `Counter`- Windows performans sayacı değerleri ile birlikte tüm işaretleri.<br />-   `Ip`- talimatlar profilli.<br />-   `Life`- ayrılan nesnelerin kullanım ömrü (ayırma verileri toplandığında kullanılabilir.)<br />-   `Line`kaynak kodu satırı profil verileri.<br />-   `Header`- rapor dosya üstbilgisi bilgilerini içerir.<br />-   `Mark`tüm işaretleri.<br />-   `Module`- modüller profilli.<br />-   `Process`- profilli işler.<br />-   `Thread`- konuları profilli.<br />-   `Type`- ayrılan türleri.<br />-   `Contention`- kaynak çekişmeleri.<br />-   `RuleWarnings`- performans kuralı sorunları<br />-   `ETW`- Profil oluşturma çalışmasında toplanan tüm Windows (ETW) olayları için Olay İzleme. .etl veri dosyası özgün konumunda veya .vsp veya .vsps dosyasını içeren dizinde olmalıdır.|
|**Xml**|XML formatında çıktı raporu.|
|**CallTrace**|Işlev giriş ve çıkışları, ETW olayları ve işaretleri nin bir listesini oluşturur.|
|**ClearPacked Semboller**|Profil oluşturucu veri dosyasından daha önce katışmık sembolleri kaldırır. PackSymbols'i ikinci kez çalıştırmadan önce bu komutu çalıştırın.|
|**SymbolPath:**`path`|Profil oluşturucu veri dosyası için semboller içeren bir veya daha fazla arama yolu veya sembol sunucusu belirtir.|
|**Hata AyıklamaSymPath**|Semboller için aranan konumları ve bulunup bulunmadıklarını listeler. Bu seçenek, simge çözümlemesi sorunlarını gidermek için yararlıdır.|
|**Paket Sembolleri**|Sembolleri profil oluşturma verileri (.vsp) dosyasına kaydeder, böylece simge (.* pdb*) dosyaları analiz için gerekli değildir.|
|**Çıktı:** *yol*&#124;*dosya adı*|Oluşturulan rapor dosyaları için alternatif bir konum belirtir. Varsayılan olarak, raporlar geçerli dizinde oluşturulur.|
|**SummaryFile**|Analiz edilen bilgileri .vsps özet dosyasında analiz edin ve kaydedin.|
|**Yazdırma İşaretleri**|Belirtilen rapor dosyasındaki tüm işaretlerin adlarını ve zaman damgalarını gösterin.|
|**?**|Kullanım bilgilerini görüntüler.|
|**NoLogo**|Rapor çalışırken sürüm bilgilerini gizler.|
|**UserRulesDirectory**|Kullanıcı tanımlı performans kuralları içeren dizin belirtir [Henüz uygulanmadı].|

## <a name="filter-options"></a>Filtre seçenekleri
 Aşağıdaki tabloda kullanılabilir verileri filtreleme seçenekleri açıklanmaktadır.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**JustMyCode****:**[`caller`[`callee`[ ][, ]]|Yalnızca kullanıcı uygulama işlevi çağrılarını göster; sistem aramalarını gizle.<br /><br /> - Parametre yok - tüm sistem fonksiyonlarını gizleyin.<br />-   `caller`- uygulama işlevlerini arayan bir sistem işlevi düzeyini gösterin.<br />-   `callee`- kullanıcı uygulama işlevleri tarafından çağrılan sistem işlevlerinin bir düzeyini gösterin.|
|**Başlangıç Zamanı:**[*değer*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden.)|
|**Bitiş Zamanı:**[*değer*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden.)|
|**FilterFile:**`VSPFFile`|Visual Studio Performans Raporu penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|
|**MsFilter:**[*başlangıç zamanı, süre*]|Yalnızca uzunluğa `starttime` kadar `duration` (milisaniye cinsinden) verileri gösterin.|
|**İşlem:**[*pid*]|Yalnızca belirtilen işlemdeki verileri gösterin.|
|**Konu:**[*threadid*]|Yalnızca belirtilen iş parçacığındaki verileri gösterin.|
|**Konu:**[*threadid,processid*]|Yalnızca belirtilen işlemle ilişkili belirtilen iş parçacığındaki verileri gösterin.|

## <a name="difference-report-options"></a>Fark raporu seçenekleri
 Aşağıdaki tabloda rapor dosyalarını karşılaştırma seçenekleri açıklanmaktadır.

|Seçenekler|Açıklama|
|-------------|-----------------|
|**Fark**  `vspfile1 vspfile2`|İki rapor dosyalarını karşılaştırın (.* vsp* veya . *vsps*) Dosyaları. Özet seçenekleri diff seçeneği kullanılarak yoksayılır.|
|**Diff:**[*değer*]|Bu eşik değerinin altında iki değer arasındaki fark göz ardı edilecektir. Ayrıca, bu eşiğin altındaki değerlere sahip yeni veriler gösterilmez.|
|**DiffTable:**[*tablo adı*]|Dosyaları karşılaştırmak için bu özel tabloyu kullanın. Varsayılan işlevler tablosudur.|
|**DiffColumn:**[*sütun adı*]|Bu özel sütun karşılaştırma değerlerini kullanın. Varsayılan, özel örnekler yüzdesi sütunudur.|
|**QueryDiffTables**|Sağlanan iki rapor dosyası için geçerli tabloları ve sütunları listeleyin.|

## <a name="see-also"></a>Ayrıca bkz.
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
