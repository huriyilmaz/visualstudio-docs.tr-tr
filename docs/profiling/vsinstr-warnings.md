---
title: VSInstr Uyarıları | Microsoft Docs
ms.date: 11/04/2016
description: VSInstr.exe aracı tarafından verilen uyarılar hakkında bilgi edinmek ve uyarının görünmesini engel olmak için NOWARN seçeneğini uyarı numaralarıyla birlikte nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: accc9ab98ede9c691b8f81d75f80fdeb07546159
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725652"
---
# <a name="vsinstr-warnings"></a>VSInstr uyarıları
Aşağıdaki tabloda,VSInstr.exearacı *tarafından verilen uyarılar* listeleyecektir. NowARN seçeneğini uyarı numaralarıyla birlikte kullanarak uyarının görünmesini engelebilirsiniz.

|Uyarı Numarası|Description|
|--------------------|-----------------|
|**VSP1026**|Kapsam, MSCorLib'e başvuru yapmayan kitaplıklarda desteklenmiyor. Taşınabilir Kitaplıklar için bu durum genellikle böyledir.<br /><br />.NET Core [için /EnableCodeCoverage](../test/vstest-console-options.md) komut satırı seçeneği gereklidir.|
|**VSP2000**|İç Hata. Bu yürütülebilir dosya için modül dosyası adı bulunamıyor.|
|**VSP2001**|\<assembly name> , kesin olarak adlandırılmış bir derlemedir. Yürütülmeden önce yeniden imzalanmış olması gerekir.<br /><br /> Bu uyarı, imzalı bir derlemenin takip edisi olduğunda oluşur. İkiliyi yeniden *sn.exe* veya güçlü ad gereksinimini geçici olarak kapatmak içinsn.exearacını kullanabilirsiniz. Daha fazla bilgi için [ bkz.Sn.exe (güçlü ad aracı)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|Dosyada işlev \<funcname> bulunamıyor \<filename><br /><br /> Bir işlev belirtilen dosyada bulunamazsa bu uyarı oluşur.|
|**VSP2003**|dosyasında işleve çapraz \<funcname> atlamalar \<filename> bulunamıyor.<br /><br /> VSInstr çapraz atlamaları null hale döndürene kadar bu uyarı oluşur. Çapraz atlamalar, kod iyileştirmesi için kullanılır.|
|**VSP2004**|İşlev EXCLUDE komut satırı anahtarı kullanılarak dışlandı, ancak çapraz atlama \<funcname> içerdiği için gerekli oldu.<br /><br /> İşlev EXCLUDE seçeneği kullanılarak dışlandı, ancak ölçüm ölçümleme işlemi sırasında gerekli olduğunda bu uyarı oluşur. Profil oluşturma, gerekli işlevi otomatik olarak içerir.|
|**VSP2005**|İç Ölçüm hatası \<error text><br /><br /> Bu uyarı, ölçümleme gerçekleştirilelemezse yapılır. Düzeltilmiş olup olmadığını belirlemek için hata metnini gözden geçirme.|
|**VSP2006**|için PDB bulunamadi \<name><br /><br /> Bu uyarı, PDB dosyası arama yolunda yoksa veya ikili dosyayla eşleşmezse oluşur.|
|**VSP2007**|\<filename> , hiçbir irdelenebilir kod içerir.<br /><br /> Bu uyarı, ikili dosyada yer alan işlevlerin hepsi hariç tutulsa veya belirtilen dosya yalnızca kaynaklar içeriyorsa verilen uyarıdır.|
|**VSP2008**|'den güvenlik öznitelikleri \<name> alamayamıyor. Hata kodu \<code><br /><br /> Bu uyarı, kullanıcının READ_DAC oluşur. Ölçümleme işlemi sırasında profil oluşturma işlemi, ikili dosya için özgün DACL'i korumaya çalışır. Özgün ikili yeni bir ikili ile değiştirilenenden, özgün ikiliden DACL kopyalanır ve yeni ikiliye uygulanmalıdır. Kullanıcının özgün ikili dosyada erişim izni READ_DAC bu başarısız olabilir.|
|**VSP2009**|üzerinde güvenlik öznitelikleri \<name> ayaryamıyor. Hata kodu \<error number><br /><br /> Bu uyarı, kullanıcının WRITE_DAC oluşur. Ölçümleme işlemi sırasında profil oluşturma işlemi, ikili dosya için özgün DACL'i korumaya çalışır. Özgün ikili yeni bir ikili ile değiştirilenenden, özgün ikiliden DACL kopyalanır ve yeni ikiliye uygulanmalıdır. Kullanıcının yeni ikili dosyada erişim izni WRITE_DAC bu başarısız olabilir.|
|**VSP2010**|-INCLUDE/-EXCLUDE seçenekleri nedeniyle özellikle ölçüm için hiçbir işlev seçilmez|
|**VSP2011**|Dahil/Dışla funcspec \<name> hiçbir işlevle eşle değil|
|**VSP2012**|Görüntüde kod kapsamı için takip ed yalnızca kod içermesi gerekir.<br /><br /> Profiler aşağıdaki kod türünü ölçümletir:<br /><br /> - Statik CRT işlevleri<br />- NonUserCodeAttribute ile öznitelikli yönetilen yöntemler<br />- DebuggerHiddenAttribute ile öznitelikli yönetilen yöntemler<br />- MASM blokları<br /><br /> Bu filtrelemeden sonra kod kalmadı ise bu uyarı oluşturulur.|
|**VSP2013**|Bu görüntüyü takip etmek için 32 bit işlem olarak çalışması gerekir. CLR üst bilgi bayrakları bunu yansıtacak şekilde güncelleştirildi.<br /><br /> Profilleyici, ikili dosyayı, 64 bit işletim sistemlerinin WOW64 öykünücüsünün 32 bit işlemini açtırmalarını sağlar. Mevcut bir 64 bit işlemde yüklenen kitaplıklar (DLL) için bu başarısız olabilir. Bu uyarı, kullanıcıya bağımlılık hakkında bilgi sağlar.|
|**VSP2014**|Sonuçta elde edilen görüntü geçersiz gibi görünüyor ve çalıştırılamayabilirsiniz.<br /><br /> Bu ileti, son araçlı derlemenin geçersiz PE üst bilgisi olduğunda oluşur.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
