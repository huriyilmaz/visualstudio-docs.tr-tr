---
title: VSPerfReport | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7667aac348a6f7b208786191c35afe86542862d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148227"
---
# <a name="vsperfreport"></a>VSPerfReport
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfReport komut satırı aracı, Profil Oluşturma Araçları profil oluşturma veri dosyalarını kullanarak rapor oluşturmak için kullanılır  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Varsayılan rapor biçimi bir. CSV dosyasıdır.  
  
 VSPerfReport aşağıdaki sözdizimini kullanır:  
  
```  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 `filename`Bunun geçerli bir. vsp veya. vsps dosyası olması gerektiğini unutmayın.  
  
 VSPerfReport komut satırı aracı,. vsp veya. vsps dosyalarını karşılaştırmak için de kullanılır. Fark ("diff") raporu oluşturmak için aşağıdaki sözdizimini kullanın:  
  
```  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` geçerli. vsp veya. vsps dosyaları olmalıdır.  
  
## <a name="symbol-files"></a>Sembol dosyaları  
 İşlev adları ve satır numaraları gibi simge bilgilerini göstermek için, VSPerfReport simgesine erişim gerektirir (. PDB) dosyaları profili oluşturulmuş bileşenlerin ve Windows sembol dosyalarının dosyalarını. Daha fazla bilgi için bkz. [nasıl yapılır: sembol dosyası konumlarını komut satırından belirtme](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Genel rapor seçenekleri  
 Aşağıdaki tabloda, genel rapor biçimlendirme seçenekleri ve bildirilecek verileri seçme seçenekleri açıklanmaktadır.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**U**|Rapor çıkışı ve yeniden yönlendirilen konsol çıkışı Unicode olarak yazılır. Belirtilen ilk seçenek olmalıdır.|  
|**Özet:**[*türler*]|Bir veya daha fazla rapor türü oluşturur.<br /><br /> -   `All` -Tüm rapor türleri oluşturulur.<br />-   `CallerCallee` -İşlevler arasındaki üst/alt öğe ilişkileri.<br />-   `Function` -işlevleri çağırılır.<br />-   `CallTree` -çağrılan işlevlerin hiyerarşisi.<br />-   `Counter` -Hepsi Windows performans sayacı değerleriyle birlikte işaretler.<br />-   `Ip` -profil oluşturulan yönergeler.<br />-   `Life` -ayrılan nesnelerin ömrü (ayırma verileri toplandığında kullanılabilir.)<br />-   `Line` kaynak kodu satırı profil verileri.<br />-   `Header` -Rapor dosya üst bilgisi bilgilerini içerir.<br />-   `Mark` Tüm işaretler.<br />-   `Module` -modüller profili oluşturulmuş.<br />-   `Process` -profili oluşturulan işlem.<br />-   `Thread` -profili oluşturulan iş parçacıkları.<br />-   `Type` -ayrılmış türler.<br />-   `Contention` -Kaynak çekişmeleri.<br />-   `RuleWarnings` -performans kuralı sorunları<br />-   `ETW` -profil oluşturma çalıştırmasında toplanan Windows için olay Izleme (ETW) olayları. . Etl veri dosyası özgün konumunda veya. vsp veya. vsps dosyasını içeren dizinde olmalıdır.|  
|**'Sini**|XML biçiminde çıktı raporu.|  
|**CallTrace**|İşlev girdisi listesini oluşturur ve çıkar, ETW olayları ve işaretler.|  
|**ClearPackedSymbols**|Önceden eklenmiş sembolleri profil oluşturucu veri dosyasından kaldırır. PackSymbols komutunu ikinci kez çalıştırmadan önce bu komutu çalıştırın.|  
|**SymbolPath:**`path`|Profil Oluşturucu veri dosyası için semboller içeren bir veya daha fazla arama yolunu veya sembol sunucusunu belirtir.|  
|**DebugSymPath**|Semboller için aranan konumları ve bunların bulunup bulunamadığını listeler. Bu seçenek, sembol çözümleme sorunlarını gidermek için kullanışlıdır.|  
|**PackSymbols**|Sembolleri profil oluşturma verileri (. vsp) dosyasına kaydederek sembol (. pdb) dosyalarının analiz için gerekli olmaması gerekir.|  
|**Çıkış:** *yol*&#124;*dosya adı*|Oluşturulan rapor dosyaları için alternatif bir konum belirtir. Varsayılan olarak, raporlar geçerli dizinde oluşturulur.|  
|**SummaryFile**|Çözümlenen bilgileri bir. vsps özet dosyasında çözümleyin ve kaydedin.|  
|**Printiþaretleri**|Belirtilen rapor dosyasında tüm işaretlerin adlarını ve zaman damgalarını göster.|  
|**?**|Kullanım bilgilerini görüntüler.|  
|**NoLogo**|Rapor çalışırken sürüm bilgilerini gizler.|  
|**Kullanıcıkuralları dizini**|Kullanıcı tanımlı performans kurallarını içeren dizini belirtir [henüz uygulanmadı].|  
  
## <a name="filter-options"></a>Filtre seçenekleri  
 Aşağıdaki tabloda kullanılabilir verileri filtreleme seçenekleri açıklanmaktadır.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**Adatmycode**[**:**[ `caller` ] [, `callee` ]]|Yalnızca Kullanıcı uygulaması işlev çağrılarını göster; sistem çağrılarını gizleyin.<br /><br /> -Parametre yok-tüm sistem işlevlerini gizleyin.<br />-   `caller` -uygulama işlevleri çağıran sistem işlevlerinin bir düzeyini gösterir.<br />-   `callee` -Kullanıcı uygulama işlevleri tarafından çağrılan sistem işlevlerinin bir düzeyini gösterir.|  
|**StartTime:**[*değer*]|Yalnızca değerden sonra toplanan verileri göster (milisaniye cinsinden)|  
|**Bitişsaati:**[*değer*]|Yalnızca değerden önce toplanan verileri göster (milisaniye cinsinden)|  
|**Filtredosyası:**`VSPFFile`|Visual Studio performans raporu penceresinden oluşturulan bir filtre dosyasının konumunu belirtir.|  
|**Msfilter:**[*başlangıçsaati, süre*]|Yalnızca `starttime` uzunluğu `duration` (milisaniye cinsinden) kadar olan verileri göster|  
|**İşlem:**[*pid*]|Yalnızca belirtilen işlemden verileri göster.|  
|**Iş parçacığı:**[*ThreadID*]|Yalnızca belirtilen iş parçacığından verileri göster.|  
|**Iş parçacığı:**[*ThreadID, ProcessId*]|Belirtilen işlemle ilişkili iş parçacığından yalnızca verileri göster.|  
  
## <a name="difference-report-options"></a>Fark raporu seçenekleri  
 Aşağıdaki tabloda rapor dosyalarını karşılaştırma seçenekleri açıklanmaktadır.  
  
|Seçenekler|Açıklama|  
|-------------|-----------------|  
|**Farklı**  `vspfile1 vspfile2`|İki rapor dosyası (. vsp veya. vsps) dosyasını karşılaştırın. Özet seçenekleri fark seçeneği kullanılarak yok sayılacak.|  
|**Fark:**[*değer*]|Bu eşik değerinin altında iki değer arasındaki fark yok sayıardı edilir. Ayrıca, bu eşiğin altındaki değerlere sahip yeni veriler gösterilmeyecektir.|  
|**Difftable:**[*tabloadı*]|Dosyaları karşılaştırmak için bu belirli tabloyu kullanın. Varsayılan değer işlevler tablosudur.|  
|**Diffcolumn:**[*ColumnName*]|Bu özel sütun Compare değerlerini kullanın. Varsayılan değer, özel örnek yüzdesi sütunudur.|  
|**QueryDiffTables**|Belirtilen iki rapor dosyası için geçerli tabloları ve sütunları listeleyin.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Raporu Görünümleri](../profiling/performance-report-views.md)
