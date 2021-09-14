---
title: VSInstr | Microsoft Docs
description: VSInstr aracının ikilileri ve diğer çeşitli VSInstr araç seçeneklerini nasıl takip etmek için kullan olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dfa8e4fda1200a9e364ef689c8eef32d2771baf7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725651"
---
# <a name="vsinstr"></a>VSInstr
VSInstr aracı ikilileri takip etmek için kullanılır. Aşağıdaki söz dizimi kullanılarak çağrılır:

```cmd
VSInstr [/U] filename [/options]
```

 Aşağıdaki tabloda VSInstr araç seçenekleri açık almaktadır:

|Seçenekler|Description|
|-------------|-----------------|
|**Yardım veya** **?**|Yardımı görüntüler.|
|**U**|Yeniden yönlendirilen konsol çıkışını Unicode olarak yazar. İlk seçenek belirtilmelidir.|
|`@filename`|Her satırda bir komut seçeneği içeren bir yanıt dosyasının adını belirtir.  Tırnak işareti kullanmayın.|
|**OutputPath**`:path`|Araçlı görüntü için bir hedef dizin belirtir. Çıkış yolu belirtilmezse, aynı dizinde dosya adına "Orig" ekli olarak özgün ikili dosya yeniden adlandırılır ve ikilinin bir kopyası kullanılır.|
|**Dışla:**`funcspec`|Yoklamalar tarafından ölçümlemenin dışında tutulacak bir işlev belirtimi belirtir. Bir işleve araştırma ekleme profili oluşturmanın öngörülemeyen veya istenmeyen sonuçlara neden olması yararlı olur.<br /><br /> Aynı ikili **dosyada** **yer alan** işlevlere başvuran Dışla ve Dahil Bırak seçeneklerini kullanma.<br /><br /> Ayrı Dışlama seçenekleriyle birden çok işlev **belirtimi belirtebilirsiniz.**<br /><br /> `funcspec` şu şekilde tanımlanır:<br /><br /> [ad alanı \<separator1> ] [class \<separator2> ] Işlev<br /><br /> \<separator1> , `::` yerel koda ve yönetilen `.` koda göredir.<br /><br /> \<separator2> her zaman `::` değerine sahiptir<br /><br /> **Dışlama** kod kapsamıyla birlikte de desteklene.<br /><br /> Joker karakter \* de desteklene. Örneğin, bir ad alanı içinde tüm işlevleri dışlamak için şunları kullanın:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikili **dosyada işlevlerin tam adlarını** listeleyebilirsiniz.|
|**Şunları içerir:**`funcspec`|Yoklamalarla ölçüm yapmak için ikili dosyada bir işlev belirtimi belirtir. Ikililer'de diğer tüm işlevlere yer velanmaz.<br /><br /> Ayrı Dahil Etmek seçenekleriyle birden çok işlev **belirtimi belirtebilirsiniz.**<br /><br /> Aynı ikili **dosyada** **işlevlere** başvuran Dahil Ve Dışla seçeneklerini kullanma.<br /><br /> **Dahil** etmek kod kapsamıyla birlikte desteklenmiyor.<br /><br /> `funcspec` şu şekilde tanımlanır:<br /><br /> [ad alanı \<separator1> ] [class \<separator2> ] Işlev<br /><br /> \<separator1> , `::` yerel koda ve yönetilen `.` koda göredir.<br /><br /> \<separator2> her zaman `::` değerine sahiptir<br /><br /> Joker karakter \* de desteklene. Örneğin, bir ad alanına tüm işlevleri eklemek için şunları kullanın:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikili **dosyada işlevlerin tam adlarını** listeleyebilirsiniz.|
|**DumpFuncs**|Belirtilen görüntü içindeki işlevleri listeler. Herhangi bir ölçümleme gerçekleştirilemez.|
|**ExcludeSmallFuncs**|Herhangi bir işlev çağrısı yapmayan kısa işlevler olan küçük işlevleri ölçümden dışlar. **ExcludeSmallFuncs seçeneği,** daha az ölçüm ek yükü sağlar ve bu nedenle gelişmiş bir ölçüm hızı sağlar.<br /><br /> Küçük işlevlerin dışlanması, 'i de azaltır. *vsp* dosya boyutu ve analiz için gereken süre.|
|**mark:**{ \| **before after** \| **top** \| **bottom**}`,funcname,markid`|.vsp rapor dosyasındaki bir veri aralığının başlangıcını veya sonunu tanımlamak için kullanabileceğiniz bir profil işareti (raporlara verileri sınırlandırma için kullanılan tanımlayıcı) ekler.<br /><br /> **Önce** - Hedef işlev girdiden hemen önce.<br /><br /> **Sonra** - Hedef işlev çıkışından hemen sonra.<br /><br /> **Top:** Hedef işlev girdiden hemen sonra.<br /><br /> **Alt** - Hedef işlevde her dönüşten hemen önce.<br /><br /> `funcname` - Hedef işlevin adı<br /><br /> `Markid` - Profil işaretinin tanımlayıcısı olarak kullanmak üzere pozitif bir tamsayı (uzun).|
|**Kapsam**|Kapsam ölçümlerini gerçekleştirir. Yalnızca şu seçeneklerle kullanılabilir: **Ayrıntılı**, **OutputPath**, **Exclude** ve **Logfile**..|
|**Ayrıntılı**|Ayrıntılı **seçeneği,** ölçümleme işlemiyle ilgili ayrıntılı bilgileri görüntülemek için kullanılır.|
|**NoWarn**`[:[Message Number[;Message Number]]]`|Tüm uyarıları veya belirli uyarıları gizleme.<br /><br /> `Message Number` - uyarı numarası. `Message Number`Atlanırsa, tüm uyarılar gizlenecektir.<br /><br /> Daha fazla bilgi için bkz. [VSInstr Uyarıları.](../profiling/vsinstr-warnings.md)|
|**Denetim:** `{` **İş Parçacığı** \| **İşlem** \| **Genel**`}`|Aşağıdaki VSInstr veri toplama denetimi Seçeneklerinin profil oluşturma düzeyini belirtir:<br /><br /> **Başlangıç**<br /><br /> **StartOnly**<br /><br /> **Askıya Alma**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **İş** parçacığı - İş parçacığı düzeyinde veri toplama denetim işlevlerini belirtir. Profil oluşturma yalnızca geçerli iş parçacığı için başlatıldı veya durduruldu. Diğer iş parçacıklarının profil oluşturma durumu etkilenmez. Varsayılan iş parçacığıdır.<br /><br /> **İşlem** - işlem düzeyinde profil oluşturma veri toplama denetim işlevlerini belirtir. Profil oluşturma geçerli işlemde tüm iş parçacıkları için başlatılır veya durur. Diğer işlemlerin profil oluşturma durumu etkilenmez.<br /><br /> **Genel** - Genel düzey (işlemler arası) veri toplama denetim işlevlerini belirtir.<br /><br /> Profil oluşturma düzeyini belirtmezseniz bir hata oluşur.|
|**Başlat:** `{` **İç** \| **Dış**`},funcname`|Veri toplamayı hedef işlevle ve bu işlev tarafından çağrılır alt işlevlerle sınırlar.<br /><br /> **içinde** - StartProfile işlevini hedef işleve girdiden hemen sonra ekler. Hedef işlevde her dönüşten hemen önce StopProfile işlevini ekler.<br /><br /> **Dışında** - StartProfile işlevini hedef işleve yapılan her çağrıdan hemen önce ekler. Hedef işleve yapılan her çağrıdan hemen sonra StopProfile işlevini ekler.<br /><br /> `funcname` - hedef işlevin adı.|
|**Askıya al:** `{` **İç** \| **Dış**`},funcname`|Hedef işlev ve işlev tarafından çağrılan alt işlevler için veri toplamayı dışlar.<br /><br /> **içinde** - SuspendProfile işlevini hedef işleve girdikten hemen sonra ekler. Hedef işlevde her dönüş öncesinde ResumeProfile işlevini hemen ekler.<br /><br /> **Dışında** - SuspendProfile işlevini hedef işleve girdiden hemen önce ekler. Hedef işlevden çıkıldıktan hemen sonra ResumeProfile işlevini ekler.<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Target işlevi bir StartProfile işlevi içeriyorsa, SuspendProfile işlevi önüne eklenir. Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi bundan sonra eklenir.|
|**Startonly:** `{` **Önce** \| **Sonra** \| **En üst** \| **Alt**`},funcname`|Profil oluşturma çalıştırması sırasında veri toplamayı başlatır. Belirtilen konuma StartProfile API işlevini ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.|
|**Yalnızca Stop:**{ \|  \| **en üst** \| **alttan** önce}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. StopProfile işlevini belirtilen konuma ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.|
|**SuspendOnly:**{ \|  \| **en üst** \| **alttan** önce}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. SuspendProfile API 'sini belirtilen konuma ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Target işlevi bir StartProfile işlevi içeriyorsa, SuspendProfile işlevi önüne eklenir.|
|**Yalnızca resumeto:**{ \|  \| **üst** \| **alttan** önce}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı başlatır veya sürdürür.<br /><br /> Bir **SuspendOnly** seçeneği profil oluşturmayı durdurduktan sonra profil oluşturmayı başlatmak için genellikle kullanılır. Belirtilen konuma bir ResumeProfile API 'SI ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi bundan sonra eklenir.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [VSInstr uyarıları](../profiling/vsinstr-warnings.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
