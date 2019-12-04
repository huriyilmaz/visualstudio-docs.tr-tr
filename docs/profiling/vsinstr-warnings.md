---
title: VSInstr uyarıları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1a0cba29caeda01de1154430af7a0d94bcfc2a5
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779954"
---
# <a name="vsinstr-warnings"></a>VSInstr uyarıları
Aşağıdaki tabloda, *vsinstr. exe* aracı tarafından verilen uyarılar listelenmektedir. Uyarının görünmesini engellemek için uyarı numaralarıyla birlikte NOWARN seçeneğini kullanabilirsiniz.

|Uyarı numarası|Açıklama|
|--------------------|-----------------|
|**VSP1026**|MSCorLib 'e başvurmayan kitaplıklarda kapsam desteklenmez. Bu durum genellikle taşınabilir kitaplıklar için de kullanılır.<br /><br />.NET Core için [/Enablecodecoverage](../test/vstest-console-options.md) komut satırı seçeneği gereklidir.|
|**VSP2000**|İç Hata. Bu yürütülebilir dosya için modül dosyası adı alınamıyor.|
|**VSP2001**|\<bütünleştirilmiş kod adı > kesin adlandırılmış bir derlemedir. Yürütülebilmesi için önce yeniden imzalanması gerekir.<br /><br /> Bu uyarı, imzalanmış bir derleme gösterildiğinde oluşur. İkiliyi bırakmak veya tanımlayıcı ad gereksinimini geçici olarak kapatmak için *sn. exe* aracını kullanabilirsiniz. Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|Dosya \<dosya adı içinde \<funcname > işlevi bulunamadı ><br /><br /> Bu uyarı, bir işlev belirtilen dosyada bulunamıyorsa oluşur.|
|**VSP2003**|Dosya \<dosya adı > \<funcname > işlevine herhangi bir çapraz atlama bulunamadı.<br /><br /> VSInstr çapraz atlamaları null olarak belirtmezseniz bu uyarı oluşur. Çapraz atlamaları kod iyileştirmesi için kullanılır.|
|**VSP2004**|\<funcname > işlevi, harıç tutma komut satırı anahtarı kullanılarak dışlandı, ancak çapraz bir geçiş içerdiğinden gerekiyordu.<br /><br /> Bu uyarı, işlev DıŞLAMA seçeneği kullanılarak dışlandıysa ve izleme işlemi sırasında gerekliyse oluşur. Profil Oluşturucu, gerekli işlevi otomatik olarak ekler.|
|**VSP2005**|İç Izleme hatası \<hata metni ><br /><br /> Bu uyarı, izleme gerçekleştirilemediği takdirde verilir. Hata metnini inceleyerek düzelmediğini tespit edin.|
|**VSP2006**|\<adı için PDB bulunamadı ><br /><br /> Bu uyarı PDB dosyası arama yolunda yoksa veya ikiliye eşleşmezse oluşur.|
|**VSP2007**|\<filename > hiçbir ınstrumentable kodu içermiyor.<br /><br /> Bu uyarı, ikili dosyadaki işlevlerin hepsi dışlanmışsa veya belirtilen dosya yalnızca kaynaklar içeriyorsa verilir.|
|**VSP2008**|\<ad > Güvenlik öznitelikleri alınamıyor. Kod \<hata kodu ><br /><br /> Bu uyarı, kullanıcının READ_DAC izni yoksa oluşur. İzleme işlemi sırasında, profil oluşturucu ikili için özgün DACL 'yi korumaya çalışır. Özgün ikilinin yeni bir ikiliyle değiştirildiği için, özgün ikiliden DACL 'nin kopyalanması ve yeni ikiliye uygulanması gerekir. Bu, kullanıcının özgün ikilide READ_DAC erişimi yoksa başarısız olabilir.|
|**VSP2009**|\<ad > Güvenlik öznitelikleri ayarlanamıyor. Hata kodu \<hata numarası ><br /><br /> Bu uyarı, kullanıcının WRITE_DAC izni yoksa oluşur. İzleme işlemi sırasında, profil oluşturucu ikili için özgün DACL 'yi korumaya çalışır. Özgün ikilinin yeni bir ikiliyle değiştirildiği için, özgün ikiliden DACL 'nin kopyalanması ve yeni ikiliye uygulanması gerekir. Bu, kullanıcının yeni ikili üzerinde WRITE_DAC erişimi yoksa başarısız olabilir.|
|**VSP2010**|-INCLUDE/-EXCLUDE seçenekleri nedeniyle izleme için hiçbir işlev özel olarak seçilmedi|
|**VSP2011**|\<> adı ekleme/dışlama funcspec, hiçbir işlev ile eşleşmiyor|
|**VSP2012**|Görüntü, kod kapsamı için belgelenmiş bir kod içermez.<br /><br /> Profiler aşağıdaki kod türünü denetlemez:<br /><br /> -Static CRT işlevleri<br />-Kullanıcıdışı CodeAttribute öznitelikli yönetilen Yöntemler<br />-Hata Gerhiddenattribute özniteliğine sahip yönetilen Yöntemler<br />-MASı blokları<br /><br /> Bu uyarı, bu filtrelemeden sonra bir kod ayrıldıysa oluşturulur.|
|**VSP2013**|Bu görüntüyü işaretleme, bunun 32 bitlik bir işlem olarak çalışmasını gerektirir. CLR üstbilgi bayrakları bunu yansıtacak şekilde güncelleştirildi.<br /><br /> Profil Oluşturucu ikiliyi değiştirir, böylece 64 bit işletim sistemleri WOW64 öykünücüsü 'nde 32 bit işlemi açabilir. Kitaplıklar (dll 'Ler) için, var olan 64 bitlik bir işlemde yükleniyorsa bu durum başarısız olabilir. Bu uyarı kullanıcıya bağımlılığı bildirir.|
|**VSP2014**|Elde edilen belgelenmiş görüntü geçersiz görünüyor ve çalışmayabilir.<br /><br /> Bu ileti, son belgelenmiş derlemede geçersiz bir PE üstbilgisi olduğunda oluşur.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
