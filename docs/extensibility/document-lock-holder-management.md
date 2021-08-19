---
title: Belge Kilidi Tutucu Yönetim | Microsoft Docs
description: Kullanıcı belge penceresinde açık belgeyi görmeden, çalışan belge tablosunda bir belgeye düzenleme kilidi açmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: caed437da38206b351634e8f59d04463a221e267
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152516"
---
# <a name="document-lock-holder-management"></a>Belge kilidi tutucu yönetimi

Çalışan belge tablosu (RDT), açık belgelerin ve sahip olduğu düzenleme kilitlerinin sayısını sürdürür. Kullanıcı belge penceresinde açık belgeyi görmeden, arka planda program aracılığıyla düzenlenmiş bir belgeyi RDT'de düzenleme kilidi ekleyebilirsiniz. Bu işlevsellik genellikle grafik kullanıcı arabirimi aracılığıyla birden çok dosyada değişiklik yapan tasarımcılar tarafından kullanılır.

## <a name="document-lock-holder-scenarios"></a>Belge kilidi tutucu senaryoları

### <a name="file-a-has-a-dependence-on-file-b"></a>"a" dosyasının "b" dosyasına bağımlılığı vardır

"a" dosya türü için standart bir düzenleyici "A" uygulayan bir durum düşünün ve "a" türünde her dosyanın "b" türünde bir dosyaya başvurusu (veya bağımlılığı vardır) vardır. "b" türünde dosyalar için standart bir "B" düzenleyicisi vardır. "A" düzenleyicisi "a" dosyasını açtığında ilgili "b" dosyasına başvurur. "b" dosyası görüntülenmez, ancak "A" düzenleyicisi dosyayı değiştirebilir. "A" düzenleyicisi yöntemden "b" dosyasının belge verilerine bir başvuru edinir ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> ayrıca "b" dosyasında bir düzenleme kilidi bulundurrır. "A" düzenleyicisi "b" dosyasını değiştirdikten sonra yöntemini çağırarak "b" dosyasındaki düzenleme kilidi sayısını <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> esndirebilirsiniz. parametresiyle yöntemini çağırdıysanız bu adımı <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> atlarsanız bu adımı `dwRDTLockType` [_VSRDTFLAGS. RDT_NoLock.](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_NoLock>)

### <a name="file-b-is-opened-by-a-different-editor"></a>"b" dosyası farklı bir düzenleyici tarafından açılır

"A" düzenleyicisi dosyayı açmaya çalıştığında "b" dosyasının "B" düzenleyicisi tarafından zaten açılmış olduğu durumda, işlemesi gereken iki ayrı senaryo vardır:

- "b" dosyası uyumlu bir düzenleyicide açıksa, "A" düzenleyicisinin yöntemini kullanarak "b" dosyasına bir belge düzenleme kilidi kaydetmesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> gerekir. "A" düzenleyiciniz "b" dosyasını değiştirdikten sonra, yöntemini kullanarak belge düzenleme kilidinin kaydını <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> açın.

- "b" dosyası uyumsuz bir şekilde açıksa "b" dosyasının "A" düzenleyicisi tarafından açılma girişiminin başarısız olması veya "A" düzenleyicisiyle ilişkili görünümün kısmen açılmasına ve uygun bir hata iletisi görüntülemesine izin veebilirsiniz. Hata iletisi kullanıcıya uyumsuz düzenleyicide "b" dosyasını kapatmasını ve ardından "a" dosyasını "A" düzenleyicisini kullanarak yeniden açmasını talimatlatır. Ayrıca, kullanıcıdan [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] uyumsuz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> düzenleyicide açık olan "b" dosyasını kapatması için yöntemini de kullanabilirsiniz. Kullanıcı "b" dosyasını kapatırsa "a" dosyasının "A" düzenleyicisinde açılması normal şekilde devam eder.

## <a name="additional-document-edit-lock-considerations"></a>Ek belge düzenleme kilidi konuları

"A" düzenleyicisi "b" dosyasında belge düzenleme kilidi olan tek düzenleyici ise , "B" düzenleyicisinin de "b" dosyasında belge düzenleme kilidi tutarsa farklı bir davranışla karşınız olur. içinde Sınıf Tasarımcısı, ilişkili kod dosyasında düzenleme kilidi tutmayan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir görsel tasarımcı örneğidir.  Yani, kullanıcının tasarım görünümünde açık bir sınıf diyagramı varsa ve ilişkili kod dosyası aynı anda açıksa ve kullanıcı kod dosyasını değiştirirse ancak değişiklikleri kaydetmezse, değişiklikler sınıf diyagramı (.cd) dosyasında da kaybolur. Kod **Sınıf Tasarımcısı** belge düzenleme kilidi varsa, kullanıcıdan kod dosyasını kapatırken değişiklikleri kaydetmesi istenlanmaz. IDE, kullanıcıdan değişiklikleri kaydetmesi ancak kullanıcı tarafından **Sınıf Tasarımcısı.** Kaydedilen değişiklikler her iki dosyada da yansıtıldı. Hem **Sınıf Tasarımcısı** hem de kod dosyası düzenleyicisinde belge düzenleme kilitleri varsa, kullanıcıdan kod dosyasını veya formu kapatırken kaydetmesi istenir. Bu noktada kaydedilen değişiklikler hem forma hem de kod dosyasına yansıtıldı. Sınıf diyagramları hakkında daha fazla bilgi için [bkz. Sınıf diyagramları ile çalışma (Sınıf Tasarımcısı)](../ide/class-designer/designing-and-viewing-classes-and-types.md).

Düzenleyici olmayan bir belgeye düzenleme kilidi eklemeniz gerekirse arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> uygulamalısınız.

Kod dosyalarını program aracılığıyla değiştiren bir kullanıcı arabirimi tasarımcısı çoğu zaman birden fazla dosyada değişiklik yapar. Böyle durumlarda yöntemi, aşağıdaki öğelerde yapılan değişiklikleri kaydetmek istiyor musunuz? iletişim kutusuyla bir veya daha fazla <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> **belgeyi kaydetmeyi** ele almaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Belge tablosu çalıştırma](../extensibility/internals/running-document-table.md)
- [Kalıcılık ve çalışan belge tablosu](../extensibility/internals/persistence-and-the-running-document-table.md)
