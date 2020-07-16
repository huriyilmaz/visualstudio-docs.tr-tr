---
title: Döküm dosyalarını kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a2d6215887512f2e0c1410688b2bc924dc1fe3a
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387063"
---
# <a name="using-dump-files"></a>Döküm Dosyalarını Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yığınlar içeren veya içermeyen döküm dosyaları; bir döküm dosyası oluşturun; bir döküm dosyasını açın; döküm dosyası için kaynak dosyasını, pdb'leri ve ikili dosyaları bulun. 
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Dekiler  
 [Döküm dosyası nedir?](#BKMK_What_is_a_dump_file_)  
  
 [Heap içeren veya içermeyen döküm dosyaları](#BKMK_Dump_files__with_or_without_heaps)  
  
 [Gereksinimler ve sınırlamalar](#BKMK_Requirements_and_limitations)  
  
 [Döküm dosyası oluşturma](#BKMK_Create_a_dump_file)  
  
 [Bir döküm dosyası açın](#BKMK_Open_a_dump_file)  
  
 [İkili dosyaları, sembol (. pdb) dosyalarını ve kaynak dosyaları bulma](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="what-is-a-dump-file"></a><a name="BKMK_What_is_a_dump_file_"></a>Döküm dosyası nedir?  
 *Döküm dosyası* , döküm alındığı zaman bir uygulamanın anlık görüntüsüdür. Hangi işlemin yürütülmüş, hangi modüllerin de yüklenmiş olduğunu gösterir. Döküm, yığın bilgileriyle kaydedildiyse, döküm dosyası, zaman içinde o anda uygulamanın belleğinde olanların bir anlık görüntüsünü içerir. Döküm dosyasını Visual Studio'da bir yığın ile açmak, bir hata ayıklama oturumunda kesme noktasında durdurmak gibidir. Yürütme devam edemiyor olsanız da, döküm oluştuğu anda uygulamanın yığınlarını, iş parçacıklarını ve değişken değerlerini inceleyebilirsiniz.  
  
 Dökümler öncelikle geliştiricinin erişiminin olmadığı makinelerde oluşan sorunların hatalarını ayıklamak için kullanılır. Örneğin, makinenizde, müşterinin kilitlenme veya yanıt vermeyen programını yeniden oluşturamadığınızda bir müşterinin makinesinden döküm dosyası kullanabilirsiniz. Test makinesinin daha fazla test için kullanılabilmesi için kilitlenme veya yanıt vermeyen program verilerini kaydetmek üzere sınayıcılar tarafından da dökümler oluşturulur. Visual Studio hata ayıklayıcı, yönetilen veya yerel kod için döküm dosyaları kaydedebilir. Hata ayıklayıcı, Visual Studio veya dosyaları *mini döküm* biçiminde kaydetmiş diğer programlar tarafından oluşturulmuş döküm dosyalarını yükleyebilir.  
  
 ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a>Heap içeren veya içermeyen döküm dosyaları  
 Yığın bilgileri içeren veya içermeyen döküm dosyaları oluşturabilirsiniz.  
  
- **Heap Içeren döküm dosyaları** , uygulama belleğinin bir anlık görüntüsünü içerir. Bu döküm oluşturulduğundaki değişkenlerin değerlerini içerir. Yığınla kaydedilmiş bir döküm dosyası yüklerseniz, uygulama ikili dosyası bulunamasa bile Visual Studio sembolleri yükleyebilir. Visual Studio ayrıca döküm dosyasında yüklenen yerel modüllerin ikili dosyalarını kaydederek hata ayıklamayı daha da kolaylaştırır.  
  
- **Sayfa@@ içermeyen döküm dosyaları** yığın bilgileri olan dökümlerden çok daha küçüktür. Ancak hata ayıklayıcısının sembol bilgilerini bulmak için uygulama ikili dosyalarını yüklemesi gerekir. İkili dosyalar, döküm oluşturulduğunda kullanılan ikili dosyalarla tam olarak eşleşen ikili dosyalar olmalıdır. Sadece yığın değişkenlerin değerleri öbek veri olmadan döküm dosyalarına kaydedilir.  
  
  ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a>Gereksinimler ve sınırlamalar  
  
- En iyi duruma getirilmiş kodun döküm dosyalarının hatalarının ayıklanması kafa karıştırıcı olabilir. Örneğin, işlevlerin derleyici içerilmesi, beklenmeyen çağrı yığınlarıyla sonuçlanabilir ve diğer iyileştirmeler, değişkenlerin ömrünü değiştirebilir.  
  
- 64 bit bilgisayarda çalışan bir Visual Studio örneğinde 64 bit makinelerdeki döküm dosyalarının hataları ayıklanmalıdır.  
  
- Visual Studio'nun VS 2013 öncesi sürümlerinde, 64 bit makinelerde çalıştırılan 32 bit uygulamaların bazı araçlar tarafından toplanan (Görev Yöneticisi ve 64-bit WinDbg) dökümleri Visual Studio'da açılamadı. Bu sınırlama, VS 2013 sürümünde kaldırılmıştır.  
  
- Visual Studio, ARM cihazlarından yerel uygulamaların döküm dosyalarının hatalarını ayıklayabilir. Visual Studio, ARM cihazlarındaki yönetilen uygulamaların uygulama döküm dosyalarının da hatalarını ayıklayabilir, ancak bunu yalnızca yerel hata ayıklayıcıda yapabilir.  
  
- Visual Studio 2013 'de [çekirdek modu](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) döküm dosyalarında hata ayıklamak Için, [Windows Için hata ayıklama araçlarının Windows 8.1 sürümünü](https://msdn.microsoft.com/windows/hardware/gg463009)indirin. Bkz. [Visual Studio 'Da çekirdek hata ayıklama](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx).  
  
- Visual Studio, [tam Kullanıcı modu dökümü](/windows-hardware/drivers/debugger/user-mode-dump-files#full)olarak bilinen eski döküm biçiminde kaydedilen döküm dosyalarının hatalarını ayıklayamıyor. Tam kullanıcı modu dökümünün yığını olan bir dökümle aynı olmadığına dikkat edin.  
  
- Visual Studio 'da [SOS.dll (sos hata ayıklama uzantısı)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) ile hata ayıklamak Için, Windows Sürücü Seti 'nın (WDK) parçası olan Windows Için hata ayıklama araçları ' nı yüklemelisiniz. Bkz. [Windows 8.1 Preview: takımları, bitleri ve araçları indirme](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx).  
  
  ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a>Döküm dosyası oluşturma  
 Visual Studio ile bir döküm dosyası oluşturmak için:  
  
- Visual Studio'daki bir işlemde hata ayıklarken, hata ayıklayıcı kesme noktası veya bir özel durumda durduğunda döküm dosyasını kaydedebilirsiniz. **Dökümü farklı kaydet**, **Hata Ayıkla**' yı seçin. **Dökümü farklı kaydet** iletişim kutusunda, **farklı kaydet türü** listesinde, yığın Ile **mini döküm** veya **mini döküm** (varsayılan) seçeneğini belirleyebilirsiniz.  
  
- [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) etkinken, hata ayıklayıcı dışında çalışan çöken bir işleme hata ayıklayıcıyı iliştirebilir ve ardından bir döküm dosyasını kaydedebilirsiniz. Bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
  
  Windows mini döküm biçimini destekleyen herhangi bir programla da döküm dosyaları oluşturabilirsiniz. Örneğin, [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) 'Daki **ProcDump** komut satırı yardımcı programı, tetikleyicilere veya isteğe bağlı olarak işlem kilitlenme döküm dosyaları oluşturabilir. Döküm dosyalarını oluşturmak için diğer araçları kullanma hakkında ek bilgi için bu konudaki [gereksinimlere ve sınırlamalara](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) bakın.  
  
  ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a>Bir döküm dosyası açın  
  
1. Visual Studio 'da **Dosya**, **Aç**, **Dosya**' yı seçin.  
  
2. **Dosya Aç** iletişim kutusunda döküm dosyasını bulup seçin. Çoğunlukla .dmp uzantısına sahip olacaktır. Ardından **Tamam**' ı seçin.  
  
3. **Döküm dosyası Özeti** penceresi görüntülenir. Bu pencerede, döküm dosyasının hata ayıklama özet bilgilerini görüntüleyebilir, sembol yolunu ayarlayabilir, hata ayıklamayı başlatabilir ve özet bilgilerini panoya kopyalayabilirsiniz.  
  
     ![Mini döküm Özet sayfası](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. Hata ayıklamayı başlatmak için, **Eylemler** bölümüne gidin ve **yalnızca yerel ile hata ayıkla** ya da **karma ile hata ayıkla**' yı seçin.  
  
## <a name="find-binaries-symbol-pdb-files-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a>İkili dosyaları, sembol (. pdb) dosyalarını ve kaynak dosyaları bulma  
 Bir döküm dosyasında hata ayıklamak üzere Visual Studio'nun tam özelliklerini kullanmak aşağıdakilere erişim gerekir:  
  
- Dökümün alındığı .Exe dosyası ve döküm işleminde kullanılan diğer ikili dosyalar (DLL'ler vb.).  
  
   Yığın veriler ile bir dökümün hatalarını ayıklıyorsanız, Visual Studio bazı modüller için eksik ikili dosyalarla başa çıkabilir, ancak geçerli çağrı yığınları oluşturmak için yeterli modüller için ikili dosyalara sahip olmalıdır. Visual Studio, yığın ile döküm dosyasında yerel modüller içerir.  
  
- .exe ve diğer ikili dosyalar için sembol (.pdb) dosyaları.  
  
- İlgilendiğiniz modüller için kaynak dosyaları.  
  
   Yürütülebilir ve .pdb dosyaları, döküm oluşturulduğunda kullanılan dosyaların sürüm ve yapısıyla tam olarak eşleşmelidir.  
  
   Kaynak dosyaları bulamazsanız, modüllerin ayrıştırılmasını kullanarak hata ayıklayabilirsiniz,  
  
  **Yürütülebilir dosyalar için varsayılan arama yolları**  
  
  Visual Studio, döküm dosyasında bulunmayan yürütülebilir dosyalar için bu konumları otomatik olarak arar:  
  
1. Döküm dosyasını içeren dizin.  
  
2. Döküm dosyasında belirtilen modül yolu. Bu, makinede dökümün toplandığı modül yoludur.  
  
3. Visual Studio **araçları**, **Seçenekler** iletişim kutusunun **hata ayıklama**, **Seçenekler**, **semboller** sayfasında belirtilen sembol yolları. Bu sayfada arama yapmak için daha fazla konum ekleyebilirsiniz.  
  
   **Ikili/sembol/kaynak sayfalarını kullanma**  
  
   Visual Studio, dökümdeki bir modülün hatalarını ayıklamak için gerekli dosyaları bulamazsa, uygun bir sayfayı (**Ikili bulunamadı**, **hiçbir sembol bulunamadı**veya hiçbir **kaynak bulunamadı**) görüntüler. Bu sayfalar, sorunun nedeni hakkında ayrıntılı bilgi sağlar ve dosyaların doğru konumunu belirlememenize yardımcı olabilecek eylem bağlantıları sağlar. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
   ![En üst](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [içeriğe](#BKMK_Contents) dön  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)
