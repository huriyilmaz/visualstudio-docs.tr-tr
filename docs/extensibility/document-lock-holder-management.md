---
title: Belge Kilidi Tutucu Yönetimi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9dd520f8ad5cab1f0cfee890c4bcc388c204bb1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712130"
---
# <a name="document-lock-holder-management"></a>Belge kilidi tutucu yönetimi

Çalışan belge tablosu (RDT), açık belge sayısını ve sahip oldukları tüm edit kilitlerini korur. Kullanıcı belge penceresinde açık bir belge görmeden arka planda programlı olarak düzenlendiğinde RDT'deki bir belgeye düzenleme kilidi yerleştirebilirsiniz. Bu işlevsellik genellikle bir grafik kullanıcı arabirimi aracılığıyla birden çok dosyayı değiştirmek tasarımcılar tarafından kullanılır.

## <a name="document-lock-holder-scenarios"></a>Belge kilidi tutucu senaryoları

### <a name="file-a-has-a-dependence-on-file-b"></a>Dosya "a" dosyası "b" bir bağımlılık vardır

Dosya türü "a" için standart bir düzenleyici "A" uyguladığınız ve "a" türündeki her dosyanın "b" türünden bir dosyaya başvuruda bulunduğu (veya bu dosyaya bağımlı olduğu) bir durum düşünün. "B" türü dosyalar için standart bir düzenleyici "B" vardır. Düzenleyici "A" dosyasını "a" açtığında ilgili dosya "b" için başvuru alır. "b" dosyası görüntülenmez, ancak "A" düzenleyicisi bunu değiştirebilir. Düzenleyici "A" <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> yöntemden "b" dosyasının belge verilerine bir başvuru alır ve "b" dosyasında bir edit kilidi tutar. Düzenleyici "A" dosya "b" değiştirerek yapıldıktan sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> yöntemi arayarak dosya "b" dosyaüzerinde düzenleme kilidi sayısı atlayabilirsiniz. _VSRDTFLAGS için parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> `dwRDTLockType` ayarlanmış yöntemi arasaydıysanız bu adımı atlayabilirsiniz. [ RDT_NoLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>).

### <a name="file-b-is-opened-by-a-different-editor"></a>Dosya "b" farklı bir düzenleyici tarafından açılır

"B" dosyasının düzenleyici "A" düzenleyicisi açmaya çalıştığında "B" düzenleyicisi tarafından zaten açılması durumunda, işlenen iki ayrı senaryo vardır:

- "b" dosyası uyumlu bir düzenleyicide açıksa, "A" düzenleyicisinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> "b" dosyasını kullanarak bir belge edit kilidi kaydettirmesi gerekir. Düzenleyiciniz "A" dosya "b" değiştirerek yapıldıktan sonra, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> yöntemi kullanarak belge edit kilidi ni açın.

- "b" dosyası uyumsuz bir şekilde açıksa, "A" düzenleyicisi tarafından "b" dosyasının açılma denemesinin başarısız olması na izin verebilir veya "A" düzenleyicisi ile ilişkili görünümün kısmen açılıp uygun bir hata iletisi görüntülemesine izin verebilirsiniz. Hata iletisi, kullanıcıya uyumsuz düzenleyicideki "b" dosyasını kapatmasını ve ardından "A" düzenleyicisini kullanarak "a" dosyasını yeniden açması nı bildirmelidir. Kullanıcıyı uyumsuz [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] düzenleyicide açık olan "b" dosyasını kapatmaya teşvik etmek için de yöntem <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> uygulayabilirsiniz. Kullanıcı "b" dosyasını kapatırsa, "A" düzenleyicisindeki "a" dosyasının açılması normal olarak devam eder.

## <a name="additional-document-edit-lock-considerations"></a>Ek belge edit kilit hususlar

Düzenleyici "B" düzenleyicisi "b" dosyasında belge edit kilidi olan tek düzenleyici ise, "B" düzenleyicisi de "b" dosyasında bir belge edit kilidi barındırıyorsa, farklı davranışlar elde elabilirsiniz. Sınıf [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Tasarımcısı,** ilişkili kod dosyasında düzenleme kilidi tutmayan görsel bir tasarımcı örneğidir. Diğer bir deyişle, kullanıcının tasarım görünümünde açık bir sınıf diyagramı varsa ve ilişkili kod dosyası aynı anda açılıyorsa ve kullanıcı kod dosyasını değiştirirancak değişiklikleri kaydetmezse, değişiklikler sınıf diyagramı (.cd) dosyasına da kaybolur. Sınıf **Tasarımcısı** kod dosyasındaki tek belge edit kilidine sahipse, kod dosyasını kapatırken kullanıcıdan değişiklikleri kaydetmesi istenmez. IDE, kullanıcıdan değişiklikleri yalnızca **Sınıf Tasarımcısı'nı**kapattıktan sonra kaydetmesini ister. Kaydedilen değişiklikler her iki dosyaya da yansıtılır. **Hem Sınıf Tasarımcısı** hem de kod dosyası düzenleyicisi kod dosyasında belge düzenle kilitleri tuttuysa, kullanıcıdan kod dosyasını veya formu kapatırken kaydetmesi istenir. Bu noktada kaydedilen değişiklikler hem formhem de kod dosyasına yansıtılır. Sınıf diyagramları hakkında daha fazla bilgi için [bkz.](../ide/class-designer/designing-and-viewing-classes-and-types.md)

Düzenleyici olmayan biri için bir belgeye bir edit kilidi yerleştirmeniz gerekiyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> arabirimi uygulamanız gerektiğini unutmayın.

Çoğu zaman kod dosyalarını programlı olarak değiştiren bir UI tasarımcısı birden fazla dosyada değişiklik yapar. Bu gibi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> durumlarda yöntem, **aşağıdaki öğelerdeki değişiklikleri kaydetmek istiyor musunuz?**

## <a name="see-also"></a>Ayrıca bkz.

- [Belge tablosunu çalıştırma](../extensibility/internals/running-document-table.md)
- [Kalıcılık ve çalışan belge tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)
