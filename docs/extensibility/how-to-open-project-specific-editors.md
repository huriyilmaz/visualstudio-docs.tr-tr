---
title: 'Nasıl yapılır: projeye özgü düzenleyiciler açma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 22106ea09f86e3d61fe7aaa6e86e6e99c002f32d
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905807"
---
# <a name="how-to-open-project-specific-editors"></a>Nasıl yapılır: projeye özgü düzenleyiciler açma
Bir proje tarafından açılan bir öğe, doğası gereği bu proje için belirli düzenleyiciye bağlıysa, projenin projeye özgü bir düzenleyici kullanarak dosyayı açması gerekir. Dosya, bir düzenleyici seçmek için IDE 'nin mekanizmasına devredilemez. Örneğin, standart bir bit eşlem Düzenleyicisi kullanmak yerine, projenize özgü olan dosyadaki bilgileri tanıyan belirli bir bit eşlem düzenleyicisini belirtmek için bu projeye özgü düzenleyici seçeneğini kullanabilirsiniz.

 IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> bir dosyanın belirli bir proje tarafından açılması gerektiğini belirlediğinde yöntemini çağırır. Daha fazla bilgi için bkz. [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Projenin `OpenItem` projeye özgü bir düzenleyici kullanarak bir dosya açmasını sağlamak üzere yöntemini uygulamak için aşağıdaki yönergeleri kullanın.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>OpenItem metodunu projeye özgü bir düzenleyici ile uygulamak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> `RDT_EditLock` Dosyanın (belge verileri nesnesi) zaten açık olup olmadığını anlamak için yöntemini () çağırın.

    > [!NOTE]
    > Belge verileri ve belge görünümü nesneleri hakkında daha fazla bilgi için bkz. [özel düzenleyicilerde belge verileri ve belge görünümü](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Dosya zaten açıksa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> yöntemini çağırarak ve parametresi için bir IDO_ActivateIfOpen değeri belirterek dosyayı yeniden açın `grfIDO` .

     Dosya açıksa ve belgenin çağıran proje dışında bir proje olması halinde, kullanıcının açılmakta olduğu düzenleyicinin başka bir projeden olduğu bir uyarı görüntülenir. Dosya penceresi daha sonra ortaya çıkmış.

3. Metin ara belleğine (belge verileri nesnesi) zaten açıksa ve başka bir görünüm eklemek istiyorsanız, bu görünümü bağlamak sizin sorumluluğunuzdadır. Projeden bir görünüm (belge görünümü nesnesi) örneği oluşturmak için önerilen yaklaşım aşağıdaki gibidir:

    1. `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> Arabirime bir işaretçi almak için hizmette çağrı yapın <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> .

    2. <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>Belge görünümü sınıfının bir örneğini oluşturmak için yöntemini çağırın.

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A>Belge görünümü nesneniz belirterek yöntemi çağırın.

     Bu yöntem belge görünümü nesnesini belge penceresinde siteler.

5. Ya da yöntemlerine uygun çağrıları gerçekleştirin <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> .

     Bu noktada, görünümün tamamen başlatılmış olması ve açılmaya hazırlanmalıdır.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>Görünümü göstermek ve açmak için yöntemini çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Proje öğelerini aç ve Kaydet](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl yapılır: standart düzenleyiciler açma](../extensibility/how-to-open-standard-editors.md)
- [Nasıl yapılır: açık belgeler için düzenleyiciler açma](../extensibility/how-to-open-editors-for-open-documents.md)
