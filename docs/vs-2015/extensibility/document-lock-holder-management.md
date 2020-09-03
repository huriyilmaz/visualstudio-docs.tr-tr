---
title: Belge kilit tutucusu yönetimi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73c6151b5c02cb81a10c2725091c16457db70e33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204628"
---
# <a name="document-lock-holder-management"></a>Belge Kilit Tutucusu Yönetimi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalışan belge tablosu (RDT), açık belgelerin sayısını ve sahip oldukları tüm düzenleme kilitlerini saklar. Kullanıcı bir belge penceresinde açık bir belge görmeden, arka planda program aracılığıyla düzenlendiğinde bir belgeye düzenleme kilidi yerleştirebilirsiniz. Bu işlevsellik genellikle bir grafik kullanıcı arabirimi aracılığıyla birden çok dosyayı değiştiren tasarımcılar tarafından kullanılır.  
  
## <a name="document-lock-holder-scenarios"></a>Belge kilit tutucusu senaryoları  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>"A" dosyasında "b" dosyası üzerinde bir bağımlılık vardır  
 "A" dosya türü için standart bir "a" Düzenleyicisi uyguladığınız ve "a" türündeki her bir dosyanın "b" türünde bir dosyayı (veya bağımlılığı açık) içeren bir durum düşünün. "B" türündeki dosyalar için standart bir "B" Düzenleyicisi var. "A" Düzenleyici "a" dosyasını açtığında "b" karşılık gelen dosyanın başvurusunu alır. "B" dosyası görüntülenmiyor, ancak düzenleyici "A" değiştirebilir. "A" Düzenleyicisi, yönteminden "b" dosyasının belge verilerine bir başvuru edinir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> ve ayrıca "b" dosyasında bir düzenleme kilidi saklar. "A" Düzenleyicisi "b" dosyasını değiştirmeyi tamamladıktan sonra, yöntemini çağırarak "b" dosyasındaki kilit düzenleme sayısını azaledebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>Parametresi olarak ayarlanmış parametresini çağrılırsa, bu adımı atlayabilirsiniz `dwRDTLockType` <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> .  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>"B" dosyası farklı bir düzenleyici tarafından açıldı  
 "B" dosyasının "A" düzenleyici tarafından açılmaya çalışıldığında "B", "A" Düzenleyicisi tarafından zaten açılmıştı. iki ayrı senaryo vardır:  
  
- "B" dosyası uyumlu bir düzenleyicide açıksa, yöntemi kullanılarak "A" dosyası "b" dosyasında bir belge düzenleme kilidi kaydedin <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> . "A" düzenleyiciniz "b" dosyasını değiştirmeyi tamamladıktan sonra, yöntemini kullanarak belge düzenleme kilidini kaldırın <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> .  
  
- "B" dosyası uyumsuz bir şekilde açıksa, "A" Düzenleyicisi tarafından "b" dosyasını açmaya çalışmasına izin verebilir veya "A" Düzenleyicisi ile ilişkili görünümün "A" kısmen açık olmasına izin verebilir ve uygun bir hata iletisi görüntüleyebilirsiniz. Hata iletisi, kullanıcıdan uyumsuz düzenleyicide "b" dosyasını kapatmasını ve "A" düzenleyicisini kullanarak "a" dosyasını yeniden açmasını ister. Ayrıca, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> kullanıcının uyumsuz düzenleyicide açık olan "b" dosyasını kapatmasını istemek için yöntemini de uygulayabilirsiniz. Kullanıcı "b" dosyasını kapatırsa, "a" düzenleyicisinde "a" dosyasının açılması normal olarak devam eder.  
  
## <a name="additional-document-edit-lock-considerations"></a>Ek belge düzenleme kilidi konuları  
 "A" Düzenleyicisi "b" dosyası üzerinde belge düzenleme kilidine sahip tek düzenleyicidir ve "b" Düzenleyicisi "b" dosyasında bir belge düzenleme kilidi de bulunduracaksa farklı bir davranış alırsınız. ' De [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , **Sınıf Tasarımcısı** ilişkili kod dosyasında düzenleme kilidi olmayan bir görsel tasarımcı örneğidir. Diğer bir deyişle, kullanıcının Tasarım görünümünde açık bir sınıf diyagramı varsa ve ilişkili kod dosyası aynı anda açıksa ve Kullanıcı kod dosyasını değiştirirse ancak değişiklikleri KAYDETMEZSE, değişiklikler sınıf diyagramı (. CD) dosyasına da kaybedilir. **Sınıf Tasarımcısı** , kod dosyasında tek belge düzenleme kilidine sahipse, kod dosyasını kapatırken kullanıcının değişiklikleri kaydetmesi istenmez. IDE, kullanıcıdan değişiklikleri yalnızca Kullanıcı **Sınıf Tasarımcısı**kapatıldıktan sonra kaydetmesini ister. Kaydedilen değişiklikler her iki dosyada da yansıtılır. Kod dosyasında hem **Sınıf Tasarımcısı** hem de kod dosyası Düzenleyicisi belge düzenleme kilitlenmeleri tutuluyorsa, kod dosyasını veya formu kapatırken kullanıcıdan kaydetmesi istenir. Bu noktada, kaydedilen değişiklikler hem form hem de kod dosyasında yansıtılır. Sınıf diyagramları hakkında daha fazla bilgi için bkz. [sınıf diyagramları Ile çalışma (sınıf Tasarımcısı)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Düzenleyici olmayan bir belgeye düzenleme kilidi yerleştirmeniz gerekiyorsa, arayüzü uygulamanız gerektiğini unutmayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> .  
  
 Kod dosyalarını program aracılığıyla değiştiren bir UI Tasarımcısı, birden fazla dosyada değişiklik yapar. Bu gibi durumlarda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> yöntemi, bir veya daha fazla belgeyi, **değişiklikleri aşağıdaki öğelerde kaydetmek istiyor musunuz?** iletişim kutusunda bir veya daha fazla belgenin kaydedilmesini işler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalıştırılan belge tablosu](../extensibility/internals/running-document-table.md)   
 [Kalıcılık ve Çalıştırılan Belge Tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)
