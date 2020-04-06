---
title: 'Nasıl: Standart Editörler Aç | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710784"
---
# <a name="how-to-open-standard-editors"></a>Nasıl yapılsın: Standart düzenleyicileri açın
Standart bir düzenleyici açtığınızda, dosya için projeye özgü bir düzenleyici belirtmek yerine, IDE'nin atanmış bir dosya türü için standart bir düzenleyici belirlemesine izin esiniz.

 Yöntemi uygulamak için aşağıdaki <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> yordamı tamamlayın. Bu, standart bir düzenleyicide bir proje dosyası açar.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>OpenItem yöntemini standart bir düzenleyiciyle uygulamak için

1. Belge <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock`veri nesnesi dosyasının zaten açık olup olmadığını belirlemek için ( ) arayın.

2. Dosya zaten açıksa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> parametre `IDO_ActivateIfOpen` için bir değer belirterek yöntemi `grfIDO` çağırarak dosyayı yeniden ortaya çıkar.

     Dosya açıksa ve belge arama projesinden farklı bir projeye sahipse, projeniz açılan düzenleyicinin başka bir projeden geldiğine dair bir uyarı alır. Dosya penceresi daha sonra yüzeye çıkar.

3. Belge açık değilse veya çalışan belge tablosunda değilse, dosya için standart bir düzenleyici açmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntemi (`OSE_ChooseBestStdEditor`) arayın.

     Yöntemi aradiğinizde, IDE aşağıdaki görevleri gerçekleştirir:

    1. IDE, hangi düzenleyicinin dosyayı açabileceğini ve bunu yapmak için en yüksek önceliğe sahip olduğunu belirlemek için kayıt defterindeki Editörler/{guidEditorType}/Extensions alt anahtarını tarar.

    2. IDE dosyayı hangi düzenleyicinin açabileceğini belirledikten sonra, IDE çağırır. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Editörün bu yöntemi uygulaması, IDE'nin yeni açılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> belgeyi araması ve siteyi araması için gereken bilgileri döndürür.

    3. Son olarak, IDE gibi olağan kalıcılık arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>kullanarak belge yükler.

    4. IDE daha önce hiyerarşi veya hiyerarşi öğesinin kullanılabilir olduğunu belirlemişse, proje düzeyindebir bağlam <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> işaretçisinin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> yöntem çağrısıyla geri geçirilmesini sağlamak için IDE metodu çağırır.

4. Düzenleyicinin <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> projenizden bağlam almasına izin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> vermek istiyorsanız, IDE projenizi aradığında IDE'ye bir işaretçi döndürün.

     Bu adımı gerçekleştirmek, projenin düzenleyiciye ek hizmetler sunmasını sağlar.

     Belge görünümü veya belge görünümü nesnesi bir pencere çerçevesiiçinde başarıyla sitelendirilmişse, nesne ' yi arayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>verileriyle birlikte baş harfe çevrilir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl açılır: Projeye özel düzenleyicileri açın](../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl yapilir: Açık belgeler için editörleri açın](../extensibility/how-to-open-editors-for-open-documents.md)
- [Dosya aç komutunu kullanarak dosyaları görüntüleme](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
