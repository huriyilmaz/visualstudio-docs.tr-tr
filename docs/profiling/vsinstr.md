---
title: VSInstr | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fc68ad7da06a1710e3c34ddb601155fc3d0b1182
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330501"
---
# <a name="vsinstr"></a>VSInstr
VSInstr aracı ikilileri işaretlemek için kullanılır. Aşağıdaki sözdizimi kullanılarak çağrılır:

```cmd
VSInstr [/U] filename [/options]
```

 Aşağıdaki tabloda VSInstr araç seçenekleri açıklanmaktadır:

|Seçenekler|Description|
|-------------|-----------------|
|**Yardım** veya **?**|Yardımı görüntüler.|
|**U**|Yeniden yönlendirilen konsol çıkışını Unicode olarak yazar. İlk seçenek belirtilmelidir.|
|`@filename`|Her satırda bir komut seçeneği içeren bir yanıt dosyasının adını belirtir.  Tırnak işaretleri kullanmayın.|
|**OutputPath**`:path`|Belgelenmiş görüntü için bir hedef dizin belirtir. Bir çıkış yolu belirtilmemişse, özgün ikili, "orig" adını aynı dizindeki dosya adına ekleyerek yeniden adlandırılır ve ikilinin bir kopyası işaretlenir.|
|**Hariç tut:**`funcspec`|Araştırmalara göre izleme dışında tutulacak bir işlev belirtimi belirtir. Bir işlevde araştırma ekleme işleminin profil oluşturma işlemi öngörülemeyen veya istenmeyen sonuçlara neden olduğunda yararlıdır.<br /><br /> **Exclude** ve **Include** seçeneklerini aynı ikilinin işlevlerine başvuruda bulunan seçenekleri kullanın.<br /><br /> Ayrı **dışlama** seçenekleriyle birden çok işlev belirtimi belirtebilirsiniz.<br /><br /> `funcspec` şöyle tanımlanır:<br /><br /> [ad alanı \<separator1> ] [sınıf \<separator2> ] çalışmayacaktır<br /><br /> \<separator1>`::`yerel kod ve `.` yönetilen kod içindir.<br /><br /> \<separator2> her zaman `::` değerine sahiptir<br /><br /> **Dışlama** kod kapsamı ile desteklenir.<br /><br /> Joker karakter \* desteklenir. Örneğin, bir ad alanındaki tüm işlevleri dışlamak için şunu kullanın:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikilide işlevlerin tüm adlarını listelemek için **vsinstr/DumpFuncs** kullanabilirsiniz.|
|**Şunları içerir:**`funcspec`|Yoklamalarla işaretlemek için bir ikilide bir işlev belirtimini belirtir. İkililerin tüm diğer işlevleri görüntülenmez.<br /><br /> Ayrı **içerme** seçenekleriyle birden çok işlev belirtimi belirtebilirsiniz.<br /><br /> Aynı ikili içindeki işlevlere başvuran **Include** ve **exclude** seçeneklerini kullanmayın.<br /><br /> **Include** , kod kapsamında desteklenmez.<br /><br /> `funcspec` şöyle tanımlanır:<br /><br /> [ad alanı \<separator1> ] [sınıf \<separator2> ] çalışmayacaktır<br /><br /> \<separator1>`::`yerel kod ve `.` yönetilen kod içindir.<br /><br /> \<separator2> her zaman `::` değerine sahiptir<br /><br /> Joker karakter \* desteklenir. Örneğin, bir ad alanındaki tüm işlevleri eklemek için şunu kullanın:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikilide işlevlerin tüm adlarını listelemek için **vsinstr/DumpFuncs** kullanabilirsiniz.|
|**DumpFuncs**|Belirtilen görüntü içindeki işlevleri listeler. Hiçbir izleme yapılmaz.|
|**ExcludeSmallFuncs**|Bir işlev çağrısı yapmayan kısa işlevler olan küçük işlevleri, izleme 'den dışlar. **ExcludeSmallFuncs** seçeneği, daha az sayıda izleme yükü sağlar ve bu sayede gelişmiş bir izleme hızına sahiptir.<br /><br /> Küçük işlevlerin dışlamasıdır de azalır. analiz için gereken *VSP* dosya boyutu ve zamanı.|
|**Mark:**{**Before** \| **After** \| **üst** \| **alttan**önce}`,funcname,markid`|. Vsp rapor dosyasında bir veri aralığının başlangıcını veya sonunu belirlemek için kullanabileceğiniz bir profil işareti (raporlardaki verileri sınırlandırmak için kullanılan bir tanımlayıcı) ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Target işlevinin adı<br /><br /> `Markid` -Profil işaretinin tanımlayıcısı olarak kullanılacak pozitif bir tamsayı (uzun).|
|**Kapsam**|Kapsam İzleme gerçekleştirir. Yalnızca şu seçeneklerle kullanılabilir: **verbose**, **OutputPath**, **exclude**ve **logfile**.|
|**Seçeneini**|**Ayrıntılı** seçeneği, izleme işlemiyle ilgili ayrıntılı bilgileri görüntülemek için kullanılır.|
|**Nowarn**`[:[Message Number[;Message Number]]]`|Tüm veya belirli uyarıları gizleyin.<br /><br /> `Message Number` -uyarı numarası. `Message Number`Atlanırsa, tüm uyarılar bastırılır.<br /><br /> Daha fazla bilgi için bkz. [vsinstr uyarıları](../profiling/vsinstr-warnings.md).|
|**Denetim:** `{` **Iş parçacığı** \| **İşlem** \| **Küresel**`}`|Aşağıdaki VSInstr veri toplama denetimi seçeneklerinin profil oluşturma düzeyini belirtir:<br /><br /> **Başlangıç**<br /><br /> **StartOnly**<br /><br /> **Askıya Alma**<br /><br /> **Yalnızca stop**<br /><br /> **SuspendOnly**<br /><br /> **Yalnızca Resume**<br /><br /> **Thread** -iş parçacığı düzeyindeki veri toplama denetim işlevlerini belirtir. Profil oluşturma başlatılmış veya yalnızca geçerli iş parçacığı için durdurulmuş. Diğer iş parçacıklarının profil oluşturma durumu etkilenmez. Varsayılan iş parçacığıdır.<br /><br /> **Process** -işlem düzeyinde profil oluşturma veri toplama denetim işlevlerini belirtir. Profil oluşturma, geçerli işlemdeki tüm iş parçacıkları için başlar veya duraklar. Diğer işlemlerin profil oluşturma durumu etkilenmez.<br /><br /> **Genel** -genel düzey (çapraz işlem) veri toplama denetim işlevlerini belirtir.<br /><br /> Profil oluşturma düzeyini belirtmezseniz bir hata oluşur.|
|**Başlangıç:** `{` **İçinde** \| **Dış**`},funcname`|Veri toplamayı, bu işlev tarafından çağrılan hedef işlevle ve alt işlevlerle sınırlandırır.<br /><br /> **İçinde** , StartProfile işlevini, hedef işleve girdisinden hemen sonra ekler. Her bir hedef işlevde döndürmeden hemen önce StopProfile işlevini ekler.<br /><br /> **Dışından** , her bir Target işlevine çağrısından hemen önce StartProfile işlevini ekler. Hedef işleve yapılan her çağrıdan hemen sonra StopProfile işlevini ekler.<br /><br /> `funcname` -Hedef işlevin adı.|
|**Askıya al:** `{` **İçinde** \| **Dış**`},funcname`|İşlev tarafından çağrılan hedef işlev ve alt işlevler için veri toplamayı dışlar.<br /><br /> **İç** -SuspendProfile işlevini, hedef işleve girdisinden hemen sonra ekler. Her bir hedef işlevde döndürmeden önce ResumeProfile işlevini hemen ekler.<br /><br /> **Dışı-SuspendProfile** işlevini, hedef işleve olan girdiden hemen önce ekler. Hedef işlevden çıkıldıktan hemen sonra ResumeProfile işlevini ekler.<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Target işlevi bir StartProfile işlevi içeriyorsa, SuspendProfile işlevi önüne eklenir. Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi bundan sonra eklenir.|
|**Startonly:** `{` **Önce** \| **Sonra** \| **En üst** \| **Alt**`},funcname`|Profil oluşturma çalıştırması sırasında veri toplamayı başlatır. Belirtilen konuma StartProfile API işlevini ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.|
|**Yalnızca Stop:**{**Before** \| **After** \| **en üst** \| **alttan**önce}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. StopProfile işlevini belirtilen konuma ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.|
|**SuspendOnly:**{**Before** \| **After** \| **en üst** \| **alttan**önce}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. SuspendProfile API 'sini belirtilen konuma ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Target işlevi bir StartProfile işlevi içeriyorsa, SuspendProfile işlevi önüne eklenir.|
|**Yalnızca resumeto:**{**Before** \| **After** \| **üst** \| **alttan**önce}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı başlatır veya sürdürür.<br /><br /> Bir **SuspendOnly** seçeneği profil oluşturmayı durdurduktan sonra profil oluşturmayı başlatmak için genellikle kullanılır. Belirtilen konuma bir ResumeProfile API 'SI ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname` -Hedef işlevin adı.<br /><br /> Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi bundan sonra eklenir.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [VSInstr uyarıları](../profiling/vsinstr-warnings.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
