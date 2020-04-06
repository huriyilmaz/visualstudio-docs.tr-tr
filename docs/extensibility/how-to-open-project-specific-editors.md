---
title: 'Nasıl Yapılsın: Projeye Özel Editörleri Aç | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710835"
---
# <a name="how-to-open-project-specific-editors"></a>Nasıl açılır: Projeye özel düzenleyicileri açın
Bir proje tarafından açılan bir öğe dosyası, bu proje için belirli bir düzenleyiciye özünde bağlıysa, projenin projeye özgü bir düzenleyici kullanarak dosyayı açması gerekir. Dosya, bir düzenleyici seçmek için IDE mekanizmasına devredilemez. Örneğin, standart bir bitmap düzenleyicisi kullanmak yerine, dosyadaki projenize özgü bilgileri tanıyan belirli bir biteşyardımcı düzenleyicisi belirtmek için bu projeye özgü düzenleyici seçeneğini kullanabilirsiniz.

 Bir dosyanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> belirli bir proje tarafından açılması gerektiğini belirlediğinde IDE yöntemi çağırır. Daha fazla bilgi için [Dosya aç komutunu kullanarak dosyaları görüntüle'ye](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)bakın. Projeye özel bir düzenleyici `OpenItem` kullanarak projenizin bir dosyayı açması için yöntemi uygulamak için aşağıdaki yönergeleri kullanın.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Projeye özel bir düzenleyiciyle OpenItem yöntemini uygulamak için

1. Dosyanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> (belge veri nesnesi) zaten açık olup olmadığını belirlemek için metodu (`RDT_EditLock`) çağırın.

    > [!NOTE]
    > Belge verileri ve belge görünümü nesneleri hakkında daha fazla bilgi için, [özel düzenleyicilerde Belge verileri ve belge görünümüne](../extensibility/document-data-and-document-view-in-custom-editors.md)bakın.

2. Dosya zaten açıksa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> yöntemi arayarak ve parametre için IDO_ActivateIfOpen değerini `grfIDO` belirterek dosyayı yeniden ortaya çıkar.

     Dosya açıksa ve belge arama projesi dışındaki bir projeye aitse, kullanıcıya açılan düzenleyicinin başka bir projeden geldiğine dair bir uyarı görüntülenir. Dosya penceresi daha sonra yüzeye çıkar.

3. Metin arabelleğiniz (belge veri nesnesi) zaten açıksa ve bu görünüme başka bir görünüm eklemek istiyorsanız, bu görünümü bağlamak sizin sorumluluğunuzdadır. Projeden bir görünümü (belge görünümü nesnesi) anlık olarak almak için önerilen yaklaşım aşağıdaki gibidir:

    1. `QueryService` Arabirimine <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> bir işaretçi almak <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> için hizmeti çağırın.

    2. Belge <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> görünümü sınıfının bir örneğini oluşturmak için yöntemi çağırın.

4. Belge <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> görünümü nesnenizi belirterek yöntemi arayın.

     Bu yöntem, belge görünümü nesnesini belge penceresinde siteler.

5. Yöntemlere veya yöntemlere <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> uygun <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> çağrıları gerçekleştirin.

     Bu noktada, görünüm tamamen başharfe getirilmeli ve açılmaya hazır olmalıdır.

6. Görünümü <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> göstermek ve açmak için yöntemi arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl yapılsın: Standart düzenleyicileri açın](../extensibility/how-to-open-standard-editors.md)
- [Nasıl yapilir: Açık belgeler için editörleri açın](../extensibility/how-to-open-editors-for-open-documents.md)
