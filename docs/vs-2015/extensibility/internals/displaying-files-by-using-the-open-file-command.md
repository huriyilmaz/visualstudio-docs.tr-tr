---
title: Dosya Aç komutunu kullanarak dosyaları görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd0018df4efb023357e10ab8050f6cf5e9eba1fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64826163"
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Dosya Aç Komutunu Kullanarak Dosyaları Görüntüleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki adımlarda IDE 'nin içindeki **Dosya** menüsünde bulunan **Açık dosya** komutunu nasıl işlediği açıklanır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bu adımlar, projelerin bu komuttan kaynaklanan çağrılara nasıl yanıt vereceğini de açıklamaktadır.  
  
 Bir Kullanıcı **Dosya** menüsündeki **Dosya Aç** komutuna tıkladığında ve **Dosya Aç** iletişim kutusundan bir dosya seçtiğinde aşağıdaki işlem gerçekleşir.  
  
1. Çalışan belge tablosunu kullanarak IDE, dosyanın zaten bir projede açık olup olmadığını belirler.  
  
    - Dosya açıksa, IDE pencereyi kapatır.  
  
    - Dosya açık değilse, IDE her bir projeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> sorgulamak için çağırır ve dosyayı hangi projenin açabilceğini tespit edebilir.  
  
        > [!NOTE]
        > Proje uygulamanızda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> , projenizin dosyayı açtığı düzeyi gösteren bir öncelik değeri sağlayın. Öncelik değerleri <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> numaralandırmada verilmiştir.  
  
2. Her proje, projenin dosyayı açmak için yaptığı önem derecesini gösteren bir öncelik düzeyiyle yanıt verir.  
  
3. IDE, dosyayı hangi projenin açtığını öğrenmek için aşağıdaki ölçütleri kullanır:  
  
    - En yüksek önceliğe (DP_Intrinsic) yanıt veren proje dosyayı açar. Bu önceliğe sahip birden fazla proje yanıt verirse, yanıt veren ilk proje dosyasını açar.  
  
    - En yüksek önceliğe (DP_Intrinsic) sahip hiçbir proje yanıt vermezse, ancak tüm projeler aynı ve daha düşük önceliğe sahip olursa, etkin proje dosyayı açar. Etkin bir proje yoksa, yanıt veren ilk proje dosyayı açar.  
  
    - Hiçbir proje dosyanın sahipliğini talep etmez (DP_Unsupported), Miscellaneous Files projesi dosyayı açar.  
  
         Çeşitli dosyalar projesinin bir örneği oluşturulursa, proje her zaman DP_CanAddAsExternal değer ile yanıt verir. Bu değer, projenin dosyayı açabildiğini gösterir. Bu proje, başka bir projede yer alan dosyaları açmak için kullanılır. Bu projedeki öğelerin listesi kalıcı değil; Bu proje yalnızca bir dosyayı açmak için kullanıldığında **Çözüm Gezgini** görünür.  
  
         Çeşitli dosyalar projesi dosyayı açabileceğini belirtmezse, projenin bir örneği oluşturulmamış demektir. Bu durumda, IDE çeşitli dosyalar projesinin bir örneğini oluşturur ve projeye dosyayı açmasını söyler.  
  
4. IDE, dosyayı hangi projenin açtığını belirler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Bu proje üzerinde yöntemi çağırır.  
  
5. Projenin ardından projeye özgü bir düzenleyici veya standart düzenleyici kullanarak dosyayı açma seçeneği vardır. Daha fazla bilgi için bkz. [nasıl yapılır: projeye özgü düzenleyicileri açma](../../extensibility/how-to-open-project-specific-editors.md) ve [nasıl yapılır: sırasıyla standart düzenleyiciler açma](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birlikte Aç komutunu kullanarak dosyaları görüntüleme](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Proje öğelerini açma ve kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Nasıl yapılır: projeye özgü düzenleyiciler açma](../../extensibility/how-to-open-project-specific-editors.md)   
 [Nasıl Yapılır: Standart Düzenleyicileri Açma](../../extensibility/how-to-open-standard-editors.md)
