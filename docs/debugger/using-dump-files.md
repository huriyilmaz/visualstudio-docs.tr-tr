---
title: Hata ayıklayıcısında döküm dosyalarını | Microsoft Docs
description: Döküm dosyası, yürütülen bir uygulamanın ve yüklenen modüllerin anlık görüntüsüdür. Uygulamaya hata ayıklama erişiminizin olduğu durumlar için döküm dosyası oluşturmayı göz önünde bulundurabilirsiniz.
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 97111878fc818addde3673336b02b928d90758f5
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970080"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Hata ayıklayıcısında Visual Studio döküm

<a name="BKMK_What_is_a_dump_file_"></a> Döküm *dosyası,* yürütülen işlemi ve uygulama için belirli bir noktada yüklenen modülleri gösteren anlık görüntüdür. Yığın bilgileri içeren bir döküm, uygulamanın o noktadaki belleğinin anlık görüntüsünü de içerir.

Döküm dosyasını yığın içinde açmak Visual Studio bir hata ayıklama oturumunda kesme noktası olarak durmaya benzer. Yürütmeye devam edesiniz ancak döküm sırasında uygulamanın yığınlarını, iş parçacıklarını ve değişken değerlerini inceebilirsiniz.

Dökümler çoğunlukla geliştiricilerin erişimine sahip olmadığını makinelerden hata ayıklamak için kullanılır. Kendi makineniz üzerinde kilitlenme veya yanıt vermemeye neden olan bir programı yeniden oluşturamıyorsanız müşterinin makinesine ait döküm dosyasını kullanabilirsiniz. Test ediciler ayrıca kilitlenmeyi veya yanıt vermemeyen program verilerini daha fazla test için kullanmak üzere kaydetmek için dökümler de oluşturabilir.

Visual Studio hata ayıklayıcı, yönetilen veya yerel kod için döküm dosyaları kaydedebilir. Uygulama tarafından veya dosyaları mini Visual Studio kaydeden diğer uygulamalar tarafından oluşturulan döküm dosyalarında *hata ayıklar.*

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Gereksinimler ve sınırlamalar

- 64 bit makinelerden döküm dosyalarında hata ayıklamak Visual Studio 64 bit makinede çalışıyor olması gerekir.

::: moniker range=">= vs-2019"
- Visual Studio Linux işletim sistemi tarafından yönetilen uygulamaların döküm dosyalarında hata ayıklaması olabilir. 
::: moniker-end

- Visual Studio, ARM cihazlarından yerel uygulamaların döküm dosyalarının hatalarını ayıklayabilir. Ayrıca arm cihazlarından yönetilen uygulamaların dökümlerinin hata ayıklamasını da yalnızca yerel hata ayıklayıcısında da ayıklar.

- Çekirdek modu [döküm dosyalarında](/windows-hardware/drivers/debugger/kernel-mode-dump-files) hata ayıklamak [veya](/dotnet/framework/tools/sos-dll-sos-debugging-extension)SOS.dllhata ayıklama uzantısını Visual Studio'da kullanmak için Windows için hata ayıklama araçlarını Windows [Sürücü Seti'ne (WDK) indirin.](/windows-hardware/drivers/download-the-wdk)

- Visual Studio, eski, tam kullanıcı modu döküm biçiminde kaydedilen döküm [dosyalarında hata ayıklaması kurup ayıklayamzın.](/windows/desktop/wer/collecting-user-mode-dumps) Tam kullanıcı modu döküm, yığınlı dökümle aynı değildir.

- En iyi duruma getirilmiş kodun döküm dosyalarının hatalarının ayıklanması kafa karıştırıcı olabilir. Örneğin, işlevlerin derleyicinin temel oluşturması beklenmeyen çağrı yığınlarına neden olabilir ve diğer iyileştirmeler değişkenlerin ömrünü değiştirebilir.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Yığınlar ile veya yığınlar olmadan döküm dosyaları

Döküm dosyaları yığın bilgilerine sahip olabilir veya sahip değildir.

- **Yığınlar içeren döküm** dosyaları, döküm zamanında değişkenlerin değerleri de dahil olmak üzere uygulama belleğinin anlık görüntüsünü içerir. Visual Studio, yüklenen yerel modüllerin ikili dosyalarını bir yığınla döküm dosyasına kaydeder ve bu da hata ayıklamayı çok daha kolay hale getirir. Visual Studio bir uygulama ikili dosyası bulsa bile yığın ile döküm dosyasından semboller yükleyebilirsiniz.

- **Yığınlar olmadan döküm dosyaları** yığınlar ile dökümlerden çok daha küçüktür, ancak hata ayıklayıcı sembol bilgilerini bulmak için uygulama ikili dosyalarını yüklemesi gerekir. Yüklenen ikili dosyalar, döküm oluşturma sırasında çalışan ikili dosyalar ile tam olarak eşleşmesi gerekir. Yığınlar olmadan döküm dosyaları yalnızca yığın değişkenlerinin değerlerini kaydedin.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Döküm dosyası oluşturma

Hata ayıklayıcıda bir işlemde hata Visual Studio, hata ayıklayıcı bir özel durum veya kesme noktası durdurulurken döküm kaydedebilirsiniz.

Tam [Zamanında Hata Ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) etkinleştirildiğinde, Visual Studio hata ayıklayıcısını Visual Studio dışında bir kilitlenmeye neden olan işleme iliştirdikten sonra hata ayıklayıcıdan bir döküm dosyası kaydedebilirsiniz. Bkz. [Çalışan işlemlere ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

**Döküm dosyasını kaydetmek için:**

1. Hata ayıklama sırasında bir hata veya kesme noktası durdurulurken Hata Ayıkla Döküm Dökümlerini **Farklı**  >  **Kaydet'i seçin.**

1. Dökümü **Farklı Kaydet iletişim** kutusundaki Farklı **Kaydet'in altında** tür olarak, Yığın ile **Minidump** veya **Minidump (varsayılan)** öğesini seçin.

1. Bir yola göz atarak döküm dosyası için bir ad seçin ve ardından Kaydet'i **seçin.**

>[!NOTE]
>Döküm dosyalarını, otomatik mini döküm biçimini destekleyen herhangi bir Windows oluşturabilirsiniz. Örneğin, [Sysinternals](/sysinternals/) tarafından Windows **Procdump** komut satırı yardımcı programı tetikleyicilere veya isteğe bağlı olarak işlem kilitlenme bilgi dökümü dosyaları oluşturabilir. Döküm [dosyaları oluşturmak için diğer](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) araçları kullanma hakkında bilgi için bkz. Gereksinimler ve sınırlamalar.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Döküm dosyasını açma

1. Dosya Visual Studio Dosya **Aç'ı**  >    >  **seçin.**

1. Dosya **Aç iletişim** kutusunda döküm dosyasını bulun ve seçin. Genellikle bir *.dmp uzantısına sahip* olur. **Tamam**’ı seçin.

   Mini **döküm Dosyası Özeti penceresi döküm** dosyasıyla ilgili özet ve modül bilgilerini ve gerçekleştirebilirsiniz eylemleri gösterir.

   ![Minidump özet sayfası](../debugger/media/dbg_dump_summarypage.png "Minidump özet sayfası")

1. Eylemler **altında:**
   - Sembol yükleme konumlarını ayarlamak için Sembol **yollarını ayarla'ya tıklayın.**
   - Hata ayıklamayı başlatmak için Yönetilen Yalnızca **Hata** Ayıkla, Yalnızca Yerel Hata Ayıkla, Karma ile Hata Ayıkla veya Yönetilen Bellekle Hata **Ayıkla'yi seçin.**

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> .exe, .pdb ve kaynak dosyalarını bulma

Döküm dosyasında tam hata ayıklama özelliklerini kullanmak için Visual Studio gerekir:

- Döküm *.exe* oluşturulan dosya ve döküm işleminin kullandığı diğer ikili dosyalar (DLL'ler vb.) .
- Dosya ve diğer ikili dosyalar için Sembol (*.pdb* *).exe* dosyaları.
- Dosya *.exe* ve *.pdb* dosyaları döküm oluşturma sırasında dosyaların sürümü ve derlemesi ile tam olarak eştir.
- İlgili modüller için kaynak dosyalar. Kaynak dosyaları bulamıyorsanız modüllerin ayrımlarını kullanabilirsiniz.

Dökümde yığın verileri varsa, Visual Studio modüller için eksik ikili dosyalar ile başa çıkabilir, ancak geçerli çağrı yığınları oluşturmak için yeterli modül ikilileri olmalıdır.

### <a name="search-paths-for-exe-files"></a>Veri dosyaları için .exe arama

Visual Studio döküm dosyasına dahil olmayan *.exe* için bu konumları otomatik olarak arar:

1. Döküm dosyasını içeren klasör.
2. Döküm dosyasının, dökümünü topladığı makinede modül yolu olan modül yolunu belirtir.
3. Araçlar (veya Hata Ayıklama) **içinde belirtilen** sembol **yolları,**> **Hata Ayıklama**  >  **Seçenekleri'ne**  >  **sahiptir.** Döküm Dosyası Özeti **penceresinin** Eylemler **bölmesinden** Semboller **sayfasını da açabilirsiniz.** Bu sayfada, arama yapmak için daha fazla konum ekleyebilirsiniz.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>İkili Dosya Yok, Sembol Yok veya Kaynak Bulunamadı sayfalarını kullanın

Bu Visual Studio dökümde bir modülde hata ayıklamak için gereken dosyaları bulamazsa, İkili Dosya **Bulunamadı,** Sembol Bulunamadı **veya** Kaynak Bulunamadı **sayfası** gösterir. Bu sayfalar sorunun nedeni hakkında ayrıntılı bilgi sağlar ve dosyaları bu konuda size yardımcı olacak eylem bağlantıları sağlar. Bkz. [Sembol belirtme (.pdb) ve kaynak dosyaları.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Tanılama Çözümleyicileri ile yönetilen bellek dökümünde hata ayıklama](../debugger/how-to-debug-managed-memory-dump.md)
- [Tam Zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Sembol (.pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)