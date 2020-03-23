---
title: VSInstr Uyarılar | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779954"
---
# <a name="vsinstr-warnings"></a>VSInstr uyarıları
Aşağıdaki *tabloda VSInstr.exe* aracı tarafından verilen uyarılar listeleneb.) Uyarının görünmesini engellemek için uyarı numaralarıyla birlikte NOWARN seçeneğini kullanabilirsiniz.

|Uyarı Numarası|Açıklama|
|--------------------|-----------------|
|**VSP1026**|KAPSAMA, MSCorLib'e başvurmayan kütüphanelerde desteklenmez. Bu genellikle Taşınabilir Kitaplıklar için durumdur.<br /><br />.NET Core için [/EnableCodeCoverage](../test/vstest-console-options.md) komut satırı seçeneği gereklidir.|
|**VSP2000**|İç Hata. Bu yürütülebilir için modül dosya adı alamıyorum.|
|**VSP2001**|\<derleme adı> güçlü adlandırılmış bir derlemedir. Yürütülmeden önce yeniden imzalanması gerekiyor.<br /><br /> Bu uyarı, imzalı bir derleme çalgılandığında oluşur. *Sn.exe* aracını ikiliyi istifa etmek veya güçlü ad gereksinimini geçici olarak kapatmak için kullanabilirsiniz. Daha fazla bilgi için [Bkz. Sn.exe (güçlü ad aracı)](/dotnet/framework/tools/sn-exe-strong-name-tool).|
|**VSP2002**|Dosya \<dosyasında \<funcname> bulamadım><br /><br /> Belirtilen dosyada bir işlev bulunamıyorsa bu uyarı oluşur.|
|**VSP2003**|Dosya \< \<dosyası nda> funcname işlevine çapraz atlayış lar>.<br /><br /> VSInstr çapraz atlamaları geçersiz kılamıyorsa bu uyarı oluşur. Çapraz atlamalar kod optimizasyonu için kullanılır.|
|**VSP2004**|Fonksiyon \<funcname> EXCLUDE komut satırı anahtarı kullanılarak dışlandı, ancak çapraz atlama içerdiğinden gerekliydi.<br /><br /> Bu uyarı, işlev DıŞla seçeneği kullanılarak dışlanmışsa, ancak enstrümantasyon işlemi sırasında gerekliyse oluşur. Profil oluşturucu otomatik olarak gerekli işlevi içerir.|
|**VSP2005**|İç Enstrümantasyon Hatası \<><br /><br /> Enstrümantasyon yapılamıyorsa bu uyarı verilir. Düzeltilip düzeltilemeyeceğini belirlemek için hata metnini gözden geçirin.|
|**VSP2006**|Ad> için \<PDB bulunamadı<br /><br /> Bu uyarı, PDB dosyası arama yolunda yoksa veya ikili dosyayla eşleşmiyorsa oluşur.|
|**VSP2007**|\<dosya adı> herhangi bir enstrümantable kod içerir.<br /><br /> Bu uyarı, ikili dosyadaki işlevlerin tümü dışlanmışsa veya belirtilen dosya yalnızca kaynak içeriyorsa verilir.|
|**VSP2008**|Ad> güvenlik \<öznitelikleri alınamıyor. Hata \<kodu kodu><br /><br /> Bu uyarı, kullanıcının READ_DAC izni yoksa oluşur. Enstrümantasyon işlemi sırasında, profil oluşturucu orijinal DACL'yi ikili için korumaya çalışır. Özgün ikili yeni bir ikili ile değiştirilmedığından, orijinal ikilideki DACL kopyalanmalıdır ve yeni ikiliye uygulanmalıdır. Kullanıcı nın orijinal ikili üzerinde READ_DAC erişimi yoksa bu durum başarısız olabilir.|
|**VSP2009**|Ad> güvenlik \<öznitelikleri ayarlayamıyor. Hata \<kodu hata numarası><br /><br /> Bu uyarı, kullanıcının WRITE_DAC izni yoksa oluşur. Enstrümantasyon işlemi sırasında, profil oluşturucu orijinal DACL'yi ikili için korumaya çalışır. Özgün ikili yeni bir ikili ile değiştirilmedığından, orijinal ikilideki DACL kopyalanmalıdır ve yeni ikiliye uygulanmalıdır. Kullanıcı yeni ikili üzerinde WRITE_DAC erişimi yoksa bu başarısız olabilir.|
|**VSP2010**|-INCLUDE/-EXCLUDE seçenekleri nedeniyle enstrümantasyon için özel olarak hiçbir işlev seçilmez|
|**VSP2011**|Funcspec \<adını ekleme/hariç tutma> işlevleriyle eşleşmez|
|**VSP2012**|Görüntü, kod kapsamı için işletilebilen herhangi bir kod içermez.<br /><br /> Profiler aşağıdaki kod türünü içermez:<br /><br /> - Statik CRT fonksiyonları<br />- NonUserCodeAttribute ile atfedilen yönetilen yöntemler<br />- DebuggerHiddenAttribute ile atfedilen yönetilen yöntemler<br />- MASM blokları<br /><br /> Bu filtrelemeden sonra hiç kod kalmamışsa, bu uyarı oluşturulur.|
|**VSP2013**|Bu görüntüyü enstrümanting 32-bit işlem olarak çalışmasını gerektirir. CLR üstbilgi bayrakları bunu yansıtacak şekilde güncelleştirildi.<br /><br /> Profil oluşturucu, 64 bit işletim sistemlerinin WOW64 emülatöründeki 32 bit işlemi açabilmesi için ikiliyi değiştirir. Kitaplıklar (DLs) için, varolan 64 bit işlemde yüklenirlerse bu durum başarısız olabilir. Bu uyarı, kullanıcıya bağımlılığı uyarır.|
|**VSP2014**|Ortaya çıkan enstrümanting görüntü geçersiz görünüyor ve çalışmayabilir.<br /><br /> Bu ileti, son enstrümantine derlemegeçersiz bir PE üstbilgi olduğunda oluşur.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
