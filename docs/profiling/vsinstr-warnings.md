---
title: VSInstr uyarıları | Microsoft Docs
ms.date: 11/04/2016
description: VSInstr.exe aracı tarafından verilen uyarılar ve uyarının görünmesini engellemek için uyarı numaralarıyla birlikte NOWARN seçeneğini nasıl kullanabileceğinizi öğrenin.
ms.topic: reference
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bd8cd7516bf86bec039cd66aa183ac5a89108c63d2a69cd7c795e047ab42d4d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270009"
---
# <a name="vsinstr-warnings"></a>VSInstr uyarıları
Aşağıdaki tabloda *VSInstr.exe* aracı tarafından verilen uyarılar listelenmektedir. Uyarının görünmesini engellemek için uyarı numaralarıyla birlikte NOWARN seçeneğini kullanabilirsiniz.

|Uyarı numarası|Açıklama|
|--------------------|-----------------|
|**VSP1026**|MSCorLib 'e başvurmayan kitaplıklarda kapsam desteklenmez. Bu durum genellikle taşınabilir kitaplıklar için de kullanılır.<br /><br />.NET Core için [/Enablecodecoverage](../test/vstest-console-options.md) komut satırı seçeneği gereklidir.|
|**VSP2000**|İç Hata. Bu yürütülebilir dosya için modül dosyası adı alınamıyor.|
|**VSP2001**|\<assembly name> , kesin adlandırılmış bir derlemedir. Yürütülebilmesi için önce yeniden imzalanması gerekir.<br /><br /> Bu uyarı, imzalanmış bir derleme gösterildiğinde oluşur. *sn.exe* aracını kullanarak ikiliyi bir şekilde kapatabilir veya tanımlayıcı ad gereksinimini geçici olarak kapatabilirsiniz. Daha fazla bilgi için bkz. [Sn.exe (tanımlayıcı ad aracı)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|Dosyadaki işlev bulunamadı \<funcname>\<filename><br /><br /> Bu uyarı, bir işlev belirtilen dosyada bulunamıyorsa oluşur.|
|**VSP2003**|Dosyadaki işleve çapraz atlama bulunamadı \<funcname> \<filename> .<br /><br /> VSInstr çapraz atlamaları null olarak belirtmezseniz bu uyarı oluşur. Çapraz atlamaları kod iyileştirmesi için kullanılır.|
|**VSP2004**|İşlev \<funcname> dışlama komut satırı anahtarı kullanılarak dışlandı, ancak çapraz bir geçiş içerdiğinden gerekiyordu.<br /><br /> Bu uyarı, işlev DıŞLAMA seçeneği kullanılarak dışlandıysa ve izleme işlemi sırasında gerekliyse oluşur. Profil Oluşturucu, gerekli işlevi otomatik olarak ekler.|
|**VSP2005**|İç Izleme hatası \<error text><br /><br /> Bu uyarı, izleme gerçekleştirilemediği takdirde verilir. Hata metnini inceleyerek düzelmediğini tespit edin.|
|**VSP2006**|İçin PDB bulunamadı \<name><br /><br /> Bu uyarı PDB dosyası arama yolunda yoksa veya ikiliye eşleşmezse oluşur.|
|**VSP2007**|\<filename> hiç ınstrumentable kodu içermiyor.<br /><br /> Bu uyarı, ikili dosyadaki işlevlerin hepsi dışlanmışsa veya belirtilen dosya yalnızca kaynaklar içeriyorsa verilir.|
|**VSP2008**|İçindeki güvenlik öznitelikleri alınamıyor \<name> . Hata kodu \<code><br /><br /> Bu uyarı, kullanıcının READ_DAC izni yoksa oluşur. İzleme işlemi sırasında, profil oluşturucu ikili için özgün DACL 'yi korumaya çalışır. Özgün ikilinin yeni bir ikiliyle değiştirildiği için, özgün ikiliden DACL 'nin kopyalanması ve yeni ikiliye uygulanması gerekir. Bu, kullanıcının özgün ikilide READ_DAC erişimi yoksa başarısız olabilir.|
|**VSP2009**|Üzerinde güvenlik öznitelikleri ayarlanamıyor \<name> . Hata kodu \<error number><br /><br /> Bu uyarı, kullanıcının WRITE_DAC izni yoksa oluşur. İzleme işlemi sırasında, profil oluşturucu ikili için özgün DACL 'yi korumaya çalışır. Özgün ikilinin yeni bir ikiliyle değiştirildiği için, özgün ikiliden DACL 'nin kopyalanması ve yeni ikiliye uygulanması gerekir. Bu, kullanıcının yeni ikili üzerinde WRITE_DAC erişimi yoksa başarısız olabilir.|
|**VSP2010**|-INCLUDE/-EXCLUDE seçenekleri nedeniyle izleme için hiçbir işlev özel olarak seçilmedi|
|**VSP2011**|Include/exclude funcspec \<name> , hiçbir işlev ile eşleşmiyor|
|**VSP2012**|Görüntü, kod kapsamı için belgelenmiş bir kod içermez.<br /><br /> Profiler aşağıdaki kod türünü denetlemez:<br /><br /> -Static CRT işlevleri<br />-Kullanıcıdışı CodeAttribute öznitelikli yönetilen Yöntemler<br />-Hata Gerhiddenattribute özniteliğine sahip yönetilen Yöntemler<br />-MASı blokları<br /><br /> Bu uyarı, bu filtrelemeden sonra bir kod ayrıldıysa oluşturulur.|
|**VSP2013**|Bu görüntüyü işaretleme, bunun 32 bitlik bir işlem olarak çalışmasını gerektirir. CLR üstbilgi bayrakları bunu yansıtacak şekilde güncelleştirildi.<br /><br /> Profil Oluşturucu ikiliyi değiştirir, böylece 64 bit işletim sistemleri WOW64 öykünücüsü 'nde 32 bit işlemi açabilir. Kitaplıklar (dll 'Ler) için, var olan 64 bitlik bir işlemde yükleniyorsa bu durum başarısız olabilir. Bu uyarı kullanıcıya bağımlılığı bildirir.|
|**VSP2014**|Elde edilen belgelenmiş görüntü geçersiz görünüyor ve çalışmayabilir.<br /><br /> Bu ileti, son belgelenmiş derlemede geçersiz bir PE üstbilgisi olduğunda oluşur.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
