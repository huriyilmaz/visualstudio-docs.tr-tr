---
title: VSInstr | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779928"
---
# <a name="vsinstr"></a>VSInstr
VSInstr aracı enstrüman ikilileri için kullanılır. Aşağıdaki sözdizimi kullanılarak çağrılır:

```cmd
VSInstr [/U] filename [/options]
```

 Aşağıdaki tabloDA VSInstr araç seçenekleri açıklanmaktadır:

|Seçenekler|Açıklama|
|-------------|-----------------|
|Yardım **mı,** yardım **mı?**|Yardım görüntüler.|
|**U**|Yönlendirilen konsol çıktısını Unicode olarak yazar. İlk seçenek belirtilmelidir.|
|`@filename`|Satır başına bir komut seçeneği içeren bir yanıt dosyasının adını belirtir.  Tırnak işaretleri kullanmayın.|
|**OutputPath**`:path`|Enstrümantif görüntü için bir hedef dizini belirtir. Bir çıktı yolu belirtilmemişse, özgün ikili aynı dizindeki dosya adına "Orig" eklenerek yeniden adlandırılır ve ikilinin bir kopyası işlenir.|
|**Exclude** `:funcspec`|Problar tarafından enstrümantasyon hariç tutmak için bir işlev belirtimi belirtir. Bir işleve sonda ekleme profilleme öngörülemeyen veya istenmeyen sonuçlara neden olduğunda yararlıdır.<br /><br /> Aynı ikili işlevlere başvuran **Dışla** ve **Ekle** seçeneklerini kullanmayın.<br /><br /> Ayrı **Dışlama** seçenekleriyle birden çok işlev belirtimi belirtebilirsiniz.<br /><br /> `funcspec`olarak tanımlanan bir:<br /><br /> [namespace\<ayırıcı1>] [sınıf\<ayırıcı2>]fonksiyonu<br /><br /> \<ayırıcı1> `::` yerel kod `.` ve yönetilen kod içindir.<br /><br /> \<separator2> her zaman`::`<br /><br /> **Dışlama** kod kapsamıyla desteklenir.<br /><br /> Joker karakter \* desteklenir. Örneğin, ad alanı kullanımındaki tüm işlevleri hariç tutmak için:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikili işlevlerin tam adlarını listelemek için **VSInstr /DumpFuncs'u** kullanabilirsiniz.|
|**Dahil Et**`:funcspec`|Probları olan bir ikili ile enstrüman için bir işlev belirtimi belirtir. İkilideki diğer tüm işlevler enstrümante değildir.<br /><br /> Ayrı **Dahil** seçenekleriyle birden çok işlev belirtimi belirtebilirsiniz.<br /><br /> Aynı ikili işlevlere başvuran **Ekle** ve **Dışla** seçeneklerini kullanmayın.<br /><br /> **Include** kod kapsamı ile desteklenmez.<br /><br /> `funcspec`olarak tanımlanan bir:<br /><br /> [namespace\<ayırıcı1>] [sınıf\<ayırıcı2>]fonksiyonu<br /><br /> \<ayırıcı1> `::` yerel kod `.` ve yönetilen kod içindir.<br /><br /> \<separator2> her zaman`::`<br /><br /> Joker karakter \* desteklenir. Örneğin, ad alanı kullanımına tüm işlevleri eklemek için:<br /><br /> MyNamespace::\*<br /><br /> Belirtilen ikili işlevlerin tam adlarını listelemek için **VSInstr /DumpFuncs'u** kullanabilirsiniz.|
|**DumpFuncs**|Belirtilen görüntüdeki işlevleri listeler. Enstrümantasyon yapılmaz.|
|**SmallFuncs hariç**|Herhangi bir işlev çağrısı yapmayan kısa işlevler olan küçük işlevleri enstrümantasyondan dışlar. **ExcludeSmallFuncs** seçeneği, böylece daha az enstrümantasyon hızı sağlar.<br /><br /> Küçük fonksiyonların dışlanması da azaltır. *vsp* dosya boyutu ve analiz için gerekli zaman.|
|**İşaretle:**{**Önce**`&#124;`**Üst**`&#124;`**Alt****}**`&#124;``,funcname,markid`|.vsp rapor dosyasındaki veri aralığının başlangıcını veya sonunu tanımlamak için kullanabileceğiniz bir profil işareti (raporlardaki verileri sınırlamak için kullanılan bir tanımlayıcı) ekler.<br /><br /> **Önce** - Hedef fonksiyon girişinden hemen önce.<br /><br /> **Sonra** - Hedef fonksiyon çıkışından hemen sonra.<br /><br /> **Üst** - Hedef fonksiyon girişinden hemen sonra.<br /><br /> **Alt** - Hedef işlevinde her dönüşten hemen önce.<br /><br /> `funcname`- Hedef fonksiyonun adı<br /><br /> `Markid`- Profil işaretinin tanımlayıcısı olarak kullanılacak pozitif tamsayı (uzun).|
|**Kapsam**|Kapsama enstrümantasyonu gerçekleştirir. Sadece aşağıdaki seçenekleri ile kullanılabilir: **Verbose**, **OutputPath**, **Dışlamak**, ve **Logfile**..|
|**Ayrıntılı**|**Verbose** seçeneği enstrümantasyon işlemi hakkında ayrıntılı bilgileri görüntülemek için kullanılır.|
|**NoWarn**`[:[Message Number[;Message Number]]]`|Tüm veya belirli uyarıları bastırın.<br /><br /> `Message Number`- uyarı numarası. `Message Number` Atlanırsa, tüm uyarılar bastırılır.<br /><br /> Daha fazla bilgi için [VSInstr Warnings'a](../profiling/vsinstr-warnings.md)bakın.|
|**Kontrol** `:{` **İş parçacığı** `&#124;` **işlemi** `&#124;` **global**`}`|Aşağıdaki VSInstr veri toplama denetimi Seçenekleri'nin profil oluşturma düzeyini belirtir:<br /><br /> **Başlangıç**<br /><br /> **Yalnızca Başlangıç**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **Askıya AlmaYalnızca**<br /><br /> **Yalnızca Özgeçmiş**<br /><br /> **İş parçacığı** - iş parçacığı düzeyinde veri toplama denetimi işlevlerini belirtir. Profil oluşturma başlatıldı veya yalnızca geçerli iş parçacığı için durduruldu. Diğer iş parçacıklarının profil oluşturma durumu etkilenmez. Varsayılan iş parçacığıdır.<br /><br /> **İşlem** - işlem düzeyinde profil oluşturma veri toplama denetim işlevlerini belirtir. Profil oluşturma, geçerli işlemdeki tüm iş parçacıkları için başlar veya durur. Diğer işlemlerin profil oluşturma durumu etkilenmez.<br /><br /> **Global** - küresel düzeyde (çapraz işlem) veri toplama denetim işlevlerini belirtir.<br /><br /> Profil oluşturma düzeyini belirtmezseniz bir hata oluşur.|
|**Start** `:{` **Inside'ı** `&#124;` **Outside** Başlat`},funcname`|Veri toplamayı hedef işlevle ve bu işlev tarafından çağrılan alt işlevlere sınırlar.<br /><br /> **İçinde** - Hedef işleve girişten hemen sonra StartProfile işlevini ekler. Hedef işlevdeki her dönüşten hemen önce StopProfile işlevini ekler.<br /><br /> **Dış** - Hedef fonksiyona yapılan her çağrıdan hemen önce StartProfile işlevini ekler. Hedef fonksiyona yapılan her çağrıdan hemen sonra StopProfile işlevini ekler.<br /><br /> `funcname`- hedef fonksiyonun adı.|
|**Dış** `&#124;` **İçeride** **Askıya Alma** `:{``},funcname`|Hedef işlev ve işlev tarafından çağrılan alt işlevler için veri toplamayı dışlar.<br /><br /> **İçinde** - Hedef işleve girişten hemen sonra Askıya Alma Profili işlevini ekler. Hedef işlevde her dönüşten hemen önce ResumeProfile işlevini ekler.<br /><br /> **Dış** - Hedef işleve girişten hemen önce Askıya Alma Profili işlevini ekler. Hedef işlevden çıktıktan hemen sonra ResumeProfile işlevini ekler.<br /><br /> `funcname`- hedef fonksiyonun adı.<br /><br /> Hedef işlev bir StartProfile işlevi içeriyorsa, Askıya Alma Profili işlevi önüne eklenir. Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi ondan sonra eklenir.|
|**Başlangıç:** `{` **Before** `&#124;` `&#124;` **Üst** **Alttan** **Önce** `&#124;``},funcname`|Profil oluşturma çalışması sırasında veri toplamaya başlar. Belirtilen konuma StartProfile API işlevini ekler.<br /><br /> **Önce** - hemen önce hedef fonksiyon girişi.<br /><br /> **Sonra** - hemen sonra hedef fonksiyonu çıkışı.<br /><br /> **Üst** - hedef işlev girişinden hemen sonra.<br /><br /> **Alt** - hedef işlevinde her dönüşhemen önce.<br /><br /> `funcname`- hedef fonksiyonun adı.|
|**StopOnly:**{**Önce**`&#124;`**Üst**`&#124;`**Alt**}**sonra**`&#124;``,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. Belirtilen konuma StopProfile işlevini ekler.<br /><br /> **Önce** - hemen önce hedef fonksiyon girişi.<br /><br /> **Sonra** - hemen sonra hedef fonksiyonu çıkışı.<br /><br /> **Üst** - hedef işlev girişinden hemen sonra.<br /><br /> **Alt** - hedef işlevinde her dönüşhemen önce.<br /><br /> `funcname`- hedef fonksiyonun adı.|
|**Yalnızca Askıya Alma:**{**Önce**`&#124;`**Üst**`&#124;`**Alt****} sonra**`&#124;``,funcname`|Profil oluşturma çalışması sırasında veri toplamayı durdurur. Askıya Alma Profil API'sini belirtilen konuma ekler.<br /><br /> **Önce** - hemen önce hedef fonksiyon girişi.<br /><br /> **Sonra** - hemen sonra hedef fonksiyonu çıkışı.<br /><br /> **Üst** - hedef işlev girişinden hemen sonra.<br /><br /> **Alt** - hedef işlevinde her dönüşhemen önce.<br /><br /> `funcname`- hedef fonksiyonun adı.<br /><br /> Hedef işlev bir StartProfile işlevi içeriyorsa, Askıya Alma Profili işlevi önüne eklenir.|
|**ResumeOnly:**{**Önce**`&#124;`**Üst**`&#124;`**Alt**}**sonra**`&#124;``,funcname`|Profil oluşturma çalışması sırasında veri toplamayı başlatVeya devam ettirer.<br /><br /> Genellikle **Bir AskOnly** seçeneği profil oluşturmayı durdurduktan sonra profil oluşturma başlatmak için kullanılır. Belirtilen konuma ResumeProfile API ekler.<br /><br /> **Önce** - hemen önce hedef fonksiyon girişi.<br /><br /> **Sonra** - hemen sonra hedef fonksiyonu çıkışı.<br /><br /> **Üst** - hedef işlev girişinden hemen sonra.<br /><br /> **Alt** - hedef işlevinde her dönüşhemen önce.<br /><br /> `funcname`- hedef fonksiyonun adı.<br /><br /> Hedef işlev bir StopProfile işlevi içeriyorsa, ResumeProfile işlevi ondan sonra eklenir.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [VSInstr uyarıları](../profiling/vsinstr-warnings.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
