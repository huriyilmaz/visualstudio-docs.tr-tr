---
title: Hata ayıklayıcıda döküm dosyalarını kullanma | Microsoft Docs
description: Döküm dosyası, yürütülen bir uygulamanın ve yüklü modüllerin anlık görüntüsüdür. Uygulamaya hata ayıklama erişiminizin olmadığı durumlar için bir döküm dosyası oluşturmayı düşünün.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f446b1d7e23245739a94b1b7c99fecefb0d00c85
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090258"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısındaki döküm dosyaları

<a name="BKMK_What_is_a_dump_file_"></a>*Döküm dosyası* , yürütülmekte olan işlemi ve zaman içinde bir uygulama için yüklenen modülleri gösteren bir anlık görüntüdür. Yığın bilgilerine sahip bir döküm, bu noktada uygulamanın belleğinin anlık görüntüsünü de içerir.

bir döküm dosyasını Visual Studio bir yığın ile açmak, bir hata ayıklama oturumunda kesme noktasında durmayla benzer bir şeydir. Yürütmeye devam edemeseniz de, döküm sırasında uygulamanın yığınlarını, iş parçacıklarını ve değişken değerlerini inceleyebilirsiniz.

Dökümler genellikle geliştiricilerin erişimi olmayan makinelerden gelen sorunları ayıklamak için kullanılır. Kendi makinenizde kilitlenme veya yanıt vermeyen bir programı yeniden oluşturamıyorsanız bir müşterinin makinesinden döküm dosyası kullanabilirsiniz. Test ediciler, daha fazla test için kullanılacak kilitlenme veya yanıt vermeyen program verilerini kaydetmek için de dökümler oluşturur.

Visual Studio hata ayıklayıcı, yönetilen veya yerel kod için döküm dosyaları kaydedebilir. Visual Studio veya dosyaları *mini döküm* biçiminde kaydettiğinizde diğer uygulamalar tarafından oluşturulan döküm dosyalarının hatalarını ayıklayabilirler.

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> Gereksinimler ve sınırlamalar

- 64 bitlik makinelerden alınan döküm dosyalarının hatalarını ayıklamak için Visual Studio 64 bit makinede çalışıyor olmalıdır.

::: moniker range=">= vs-2019"
- Visual Studio, Linux işletim sistemindeki yönetilen uygulamaların döküm dosyalarının hatalarını ayıklayabilir. 
::: moniker-end

- Visual Studio, ARM cihazlarından yerel uygulamaların döküm dosyalarının hatalarını ayıklayabilir. Ayrıca, yalnızca yerel hata ayıklayıcıda, ARM cihazlarından yönetilen uygulamaların dökümlerinde hata ayıklama yapabilir.

- [çekirdek modu](/windows-hardware/drivers/debugger/kernel-mode-dump-files) döküm dosyalarında hata ayıklamak veya Visual Studio [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) hata ayıklama uzantısını kullanmak için, [Windows sürücü setinde (WDK)](/windows-hardware/drivers/download-the-wdk)Windows için hata ayıklama araçlarını indirin.

- Visual Studio, daha eski, [tam kullanıcı modu döküm](/windows/desktop/wer/collecting-user-mode-dumps) biçiminde kaydedilen döküm dosyalarının hatalarını ayıklayamıyor. Tam Kullanıcı modu dökümü, yığın içeren bir dökümle aynı değildir.

- En iyi duruma getirilmiş kodun döküm dosyalarının hatalarının ayıklanması kafa karıştırıcı olabilir. Örneğin, işlevlerin derleyici girişi beklenmeyen çağrı yığınlarıyla sonuçlanabilir ve diğer iyileştirmeler değişkenlerin ömrünü değiştirebilir.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> Heap 'ler içeren veya içermeyen döküm dosyaları

Döküm dosyalarının yığın bilgisi olabilir veya olmayabilir.

- **Heap Içeren döküm dosyaları** , döküm sırasında değişkenlerin değerleri de dahil olmak üzere, uygulamanın belleğinin anlık görüntüsünü içerir. Visual Studio, yüklü yerel modüllerin ikili dosyalarını bir öbek ile bir döküm dosyasına kaydeder ve bu da hata ayıklamayı çok daha kolay hale getirir. Visual Studio, bir uygulama ikilisini bulmasa bile, bir döküm dosyasındaki sembolleri bir yığın ile yükleyebilir.

- **Heap Içermeyen döküm dosyaları** , Heap 'ler dökümlerinden çok daha küçüktür, ancak hata ayıklayıcının sembol bilgilerini bulmak için uygulama ikili dosyalarını yüklemesi gerekir. Yüklenen ikili dosyalar, döküm oluşturma sırasında çalışan olanlarla tam olarak eşleşmelidir. Boap içermeyen döküm dosyaları yalnızca yığın değişkenlerinin değerlerini kaydeder.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> Döküm dosyası oluşturma

Visual Studio bir işlemde hata ayıklaması yaparken, hata ayıklayıcı bir özel durumla veya kesme noktasında durdurulduğunda bir döküm kaydedebilirsiniz.

[tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) etkinken, Visual Studio hata ayıklayıcıyı Visual Studio dışında kilitlenen bir işleme ekleyebilirsiniz ve ardından hata ayıklayıcıdan bir döküm dosyası kaydedebilirsiniz. Bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Bir döküm dosyasını kaydetmek için:**

1. Hata ayıklama sırasında bir hata veya kesme noktasında durdurulduğunda,   >  **döküm kaydet**' i farklı Ayıkla ' yı seçin.

1. **Dökümü farklı kaydet** iletişim kutusunda, **farklı kaydet**' in altında, yığın Ile **mini döküm** veya **mini döküm** ' i seçin (varsayılan).

1. Bir yola gidin ve döküm dosyası için bir ad seçin ve ardından **Kaydet**' i seçin.

>[!NOTE]
>Windows mini döküm biçimini destekleyen herhangi bir programla döküm dosyaları oluşturabilirsiniz. örneğin, [Windows Sysinternals](/sysinternals/) 'ın **procdump** komut satırı yardımcı programı, tetikleyicilere veya isteğe bağlı olarak işlem kilitlenme döküm dosyaları oluşturabilir. Döküm dosyalarını oluşturmak için diğer araçları kullanma hakkında bilgi için bkz. [gereksinimler ve sınırlamalar](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) .

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> Bir döküm dosyası açın

1. Visual Studio **dosya**  >  **aç**  >  **dosya**' yı seçin.

1. **Dosya Aç** iletişim kutusunda döküm dosyasını bulup seçin. Genellikle *. dmp* uzantısına sahip olur. **Tamam**’ı seçin.

   **Mini döküm dosyası Özet** penceresi, döküm dosyası için Özet ve modül bilgilerini ve gerçekleştirebileceğiniz eylemleri gösterir.

   ![Mini döküm Özet sayfası](../debugger/media/dbg_dump_summarypage.png "Mini döküm Özet sayfası")

1. **Eylemler** altında:
   - Sembol yükleme konumlarını ayarlamak için **sembol yollarını ayarla**' yı seçin.
   - Hata ayıklamayı başlatmak için, **yalnızca yönetilen Ile hata** Ayıkla, **yalnızca yerel ile** Hata Ayıkla, **karma Ile** hata ayıklama veya **yönetilen bellekle hata ayıklama** seçeneğini belirleyin.

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> .exe,. pdb ve kaynak dosyalarını bul

bir döküm dosyasında tam hata ayıklama özelliklerini kullanmak için Visual Studio gereklidir:

- Döküm işleminin kullanıldığı *.exe* dosya ve diğer ikili dosyalar (dll 'ler vb.).
- *.exe* ve diğer ikili dosyalar için sembol (*. pdb*) dosyaları.
- Döküm oluşturma sırasında dosyaların sürümü ve derlemesi ile tam olarak eşleşen *.exe* ve *. pdb* dosyaları.
- İlgili modüller için kaynak dosyaları. Kaynak dosyaları bulamazsanız, modüllerin ayrıştırılmış derlemesini kullanabilirsiniz.

döküm, yığın verileri içeriyorsa, bazı modüller için eksik ikili dosyalarla Visual Studio olabilir, ancak geçerli çağrı yığınları oluşturmak için yeterli modüller için ikili dosyalara sahip olmalıdır.

### <a name="search-paths-for-exe-files"></a>.exe dosyaları için arama yolları

Visual Studio, döküm dosyasına dahil olmayan *.exe* dosyalar için bu konumları otomatik olarak arar:

1. Döküm dosyasını içeren klasör.
2. Döküm dosyasının belirttiği modül yolu, dökümü toplayan makinedeki modül yoludur.
3. **Araç** (veya **hata ayıklama**) seçeneklerinde belirtilen sembol yolları >   >  **hata ayıklama**  >  **sembolleri**. Ayrıca, **döküm dosyası Özeti** penceresinin **Eylemler** bölmesindeki **semboller** sayfasını açabilirsiniz. Bu sayfada, aramaya daha fazla konum ekleyebilirsiniz.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>Hiçbir binary, simge yok veya hiçbir kaynak bulunamadı sayfası kullanın

Visual Studio, dökümdeki bir modülün hatalarını ayıklamak için gereken dosyaları bulamazsa, **hiçbir ikili bulunamadı**, **hiçbir sembol bulunamadı** veya hiçbir **kaynak bulunamadı** sayfası görüntülenir. Bu sayfalar, sorunun nedeni hakkında ayrıntılı bilgi sağlar ve dosyaları bulmanıza yardımcı olabilecek eylem bağlantıları sağlar. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET tanılama Çözümleyicileri ile yönetilen bellek dökümünde hata ayıklama](../debugger/how-to-debug-managed-memory-dump.md)
- [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)