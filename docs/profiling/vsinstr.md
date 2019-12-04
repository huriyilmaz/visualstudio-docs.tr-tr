---
title: VSInstr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 386d81d14996547670944ce1b4911233eb9c8955
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779928"
---
# <a name="vsinstr"></a>VSInstr
VSInstr aracı ikilileri işaretlemek için kullanılır. Aşağıdaki sözdizimi kullanılarak çağrılır:

```cmd
VSInstr [/U] filename [/options]
```

 Aşağıdaki tabloda VSInstr araç seçenekleri açıklanmaktadır:

|Seçenekler|Açıklama|
|-------------|-----------------|
|**Yardım** veya **?**|Yardımı görüntüler.|
|**Larınız**|Yeniden yönlendirilen konsol çıkışını Unicode olarak yazar. İlk seçenek belirtilmelidir.|
|`@filename`|Her satırda bir komut seçeneği içeren bir yanıt dosyasının adını belirtir.  Tırnak işaretleri kullanmayın.|
|**OutputPath** `:path`|Belgelenmiş görüntü için bir hedef dizin belirtir. Bir çıkış yolu belirtilmemişse, özgün ikili, "orig" adını aynı dizindeki dosya adına ekleyerek yeniden adlandırılır ve ikilinin bir kopyası işaretlenir.|
|`:funcspec` **Dışla**|Araştırmalara göre izleme dışında tutulacak bir işlev belirtimi belirtir. Bir işlevde araştırma ekleme işleminin profil oluşturma işlemi öngörülemeyen veya istenmeyen sonuçlara neden olduğunda yararlıdır.<br /><br /> **Exclude** ve **Include** seçeneklerini aynı ikilinin işlevlerine başvuruda bulunan seçenekleri kullanın.<br /><br /> Ayrı **dışlama** seçenekleriyle birden çok işlev belirtimi belirtebilirsiniz.<br /><br /> `funcspec` şöyle tanımlanır:<br /><br /> [ad alanı\<separator1 >] [Class\<separator2 >] işlevi<br /><br /> \<separator1 > yerel kod için `::` ve yönetilen kod için `.`.<br /><br /> \<separator2 > her zaman `::`<br /><br /> **Dışlama** kod kapsamı ile desteklenir.<br /><br /> Joker karakter \* desteklenir. Örneğin, bir ad alanındaki tüm işlevleri dışlamak için şunu kullanın:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikilide işlevlerin tüm adlarını listelemek için **vsinstr/DumpFuncs** kullanabilirsiniz.|
|`:funcspec` **dahil et**|Yoklamalarla işaretlemek için bir ikilide bir işlev belirtimini belirtir. İkililerin tüm diğer işlevleri görüntülenmez.<br /><br /> Ayrı **içerme** seçenekleriyle birden çok işlev belirtimi belirtebilirsiniz.<br /><br /> Aynı ikili içindeki işlevlere başvuran **Include** ve **exclude** seçeneklerini kullanmayın.<br /><br /> **Include** , kod kapsamında desteklenmez.<br /><br /> `funcspec` şöyle tanımlanır:<br /><br /> [ad alanı\<separator1 >] [Class\<separator2 >] işlevi<br /><br /> \<separator1 > yerel kod için `::` ve yönetilen kod için `.`.<br /><br /> \<separator2 > her zaman `::`<br /><br /> Joker karakter \* desteklenir. Örneğin, bir ad alanındaki tüm işlevleri eklemek için şunu kullanın:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikilide işlevlerin tüm adlarını listelemek için **vsinstr/DumpFuncs** kullanabilirsiniz.|
|**DumpFuncs**|Belirtilen görüntü içindeki işlevleri listeler. Hiçbir izleme yapılmaz.|
|**ExcludeSmallFuncs**|Bir işlev çağrısı yapmayan kısa işlevler olan küçük işlevleri, izleme 'den dışlar. **ExcludeSmallFuncs** seçeneği, daha az sayıda izleme yükü sağlar ve bu sayede gelişmiş bir izleme hızına sahiptir.<br /><br /> Küçük işlevlerin dışlamasıdır de azalır. analiz için gereken *VSP* dosya boyutu ve zamanı.|
|**Mark:** {`&#124;`**en üstteki**`&#124;`**Bottom**} **sonra** ,**önce**`&#124;``,funcname,markid`|. Vsp rapor dosyasında bir veri aralığının başlangıcını veya sonunu belirlemek için kullanabileceğiniz bir profil işareti (raporlardaki verileri sınırlandırmak için kullanılan bir tanımlayıcı) ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname`-hedef işlevin adı<br /><br /> `Markid`-profil işaretinin tanımlayıcısı olarak kullanılacak pozitif bir tamsayı (uzun).|
|**Kaplama**|Kapsam İzleme gerçekleştirir. Yalnızca şu seçeneklerle kullanılabilir: **verbose**, **OutputPath**, **exclude**ve **logfile**.|
|**Seçeneini**|**Ayrıntılı** seçeneği, izleme işlemiyle ilgili ayrıntılı bilgileri görüntülemek için kullanılır.|
|**Nowarn** `[:[Message Number[;Message Number]]]`|Tüm veya belirli uyarıları gizleyin.<br /><br /> `Message Number`-uyarı numarası. `Message Number` atlanırsa, tüm uyarılar bastırılır.<br /><br /> Daha fazla bilgi için bkz. [vsinstr uyarıları](../profiling/vsinstr-warnings.md).|
|**`:{`** **Iş parçacığı** `&#124;` **işlem** `&#124;` **genel** `}`|Aşağıdaki VSInstr veri toplama denetimi seçeneklerinin profil oluşturma düzeyini belirtir:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **Yalnızca stop**<br /><br /> **SuspendOnly**<br /><br /> **Yalnızca Resume**<br /><br /> **Thread** -iş parçacığı düzeyindeki veri toplama denetim işlevlerini belirtir. Profil oluşturma başlatılmış veya yalnızca geçerli iş parçacığı için durdurulmuş. Diğer iş parçacıklarının profil oluşturma durumu etkilenmez. Varsayılan iş parçacığıdır.<br /><br /> **Process** -işlem düzeyinde profil oluşturma veri toplama denetim işlevlerini belirtir. Profil oluşturma, geçerli işlemdeki tüm iş parçacıkları için başlar veya duraklar. Diğer işlemlerin profil oluşturma durumu etkilenmez.<br /><br /> **Genel** -genel düzey (çapraz işlem) veri toplama denetim işlevlerini belirtir.<br /><br /> Profil oluşturma düzeyini belirtmezseniz bir hata oluşur.|
|**`&#124;`** **dışında** `:{` **başlatın** `},funcname`|Veri toplamayı, bu işlev tarafından çağrılan hedef işlevle ve alt işlevlerle sınırlandırır.<br /><br /> **İçinde** , StartProfile işlevini, hedef işleve girdisinden hemen sonra ekler. Her bir hedef işlevde döndürmeden hemen önce StopProfile işlevini ekler.<br /><br /> **Dışından** , her bir Target işlevine çağrısından hemen önce StartProfile işlevini ekler. Hedef işleve yapılan her çağrıdan hemen sonra StopProfile işlevini ekler.<br /><br /> `funcname`-hedef işlevin adı.|
|**`&#124;`** **dışında** `:{` **askıya alma** `},funcname`|İşlev tarafından çağrılan hedef işlev ve alt işlevler için veri toplamayı dışlar.<br /><br /> **İç** -SuspendProfile işlevini, hedef işleve girdisinden hemen sonra ekler. Her bir hedef işlevde döndürmeden önce ResumeProfile işlevini hemen ekler.<br /><br /> **Dışı-SuspendProfile** işlevini, hedef işleve olan girdiden hemen önce ekler. Hedef işlevden çıkıldıktan hemen sonra ResumeProfile işlevini ekler.<br /><br /> `funcname`-hedef işlevin adı.<br /><br /> Target işlevi bir StartProfile işlevi içeriyorsa, SuspendProfile işlevi önüne eklenir. Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi bundan sonra eklenir.|
|**Startonly:** `&#124;` **üstteki** `&#124;` **Bottom** `},funcname` **sonra** `&#124;` **önce** `{`|Profil oluşturma çalıştırması sırasında veri toplamayı başlatır. Belirtilen konuma StartProfile API işlevini ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname`-hedef işlevin adı.|
|**Yalnızca Stop:** {`&#124;`üstten **sonra**`&#124;` **önce**`&#124;`**Bottom**}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. StopProfile işlevini belirtilen konuma ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname`-hedef işlevin adı.|
|**SuspendOnly:** { **`&#124;``&#124;`** **Before** **top**`&#124;`**Bottom**}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. SuspendProfile API 'sini belirtilen konuma ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname`-hedef işlevin adı.<br /><br /> Target işlevi bir StartProfile işlevi içeriyorsa, SuspendProfile işlevi önüne eklenir.|
|**Yalnızca Resume,** **en üstteki**`&#124;`**son**`&#124;`**sonra**`&#124;`**önce** : {0}`,funcname`|Profil oluşturma çalışması sırasında veri toplamayı başlatır veya sürdürür.<br /><br /> Bir **SuspendOnly** seçeneği profil oluşturmayı durdurduktan sonra profil oluşturmayı başlatmak için genellikle kullanılır. Belirtilen konuma bir ResumeProfile API 'SI ekler.<br /><br /> **Önce** , hedef işlev girdisinden hemen önce.<br /><br /> **After** -Target işlevinden hemen sonra çıkış.<br /><br /> Hedef işlev girişinden hemen sonra **gelen üst** .<br /><br /> Target işlevindeki dönüşden hemen önce, **alt** .<br /><br /> `funcname`-hedef işlevin adı.<br /><br /> Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi bundan sonra eklenir.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [VSInstr uyarıları](../profiling/vsinstr-warnings.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
