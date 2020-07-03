---
title: 'Nasıl yapılır: standart düzenleyiciler açma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c12e831654e7e138289d33b6e6f0409328e22c8c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905791"
---
# <a name="how-to-open-standard-editors"></a>Nasıl yapılır: standart düzenleyiciler açma
Standart bir düzenleyici açtığınızda, IDE 'nin dosya için projeye özgü bir düzenleyici belirtmek yerine, belirlenen dosya türü için standart bir düzenleyici belirlemesine izin verirolursunuz.

 Yöntemini uygulamak için aşağıdaki yordamı izleyin <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> . Bu, bir proje dosyasını standart düzenleyicide açar.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>OpenItem metodunu standart bir düzenleyici ile uygulamak için

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock` Belge verisi nesne dosyasının zaten açık olup olmadığını belirleme () çağrısı.

2. Dosya zaten açıksa, parametresini çağırarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> parametresi için değerini belirterek dosyayı yeniden açın `IDO_ActivateIfOpen` `grfIDO` .

     Dosya açıksa ve belge çağıran projeden farklı bir projeye aitse, projeniz açılan düzenleyicinin başka bir projeden olduğunu belirten bir uyarı alır. Dosya penceresi daha sonra ortaya çıkmış.

3. Belge açık veya çalışan belge tablosunda değilse, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> `OSE_ChooseBestStdEditor` dosya için standart bir düzenleyici açmak üzere yöntemini () çağırın.

     Yöntemini çağırdığınızda, IDE aşağıdaki görevleri gerçekleştirir:

    1. IDE, hangi düzenleyicinin dosyayı açabilme ve bunu yapmak için en yüksek önceliğe sahip olduğunu anlamak için kayıt defterindeki düzenleyiciler/{Editdıtortype}/Extensions alt anahtarını tarar.

    2. IDE, dosyayı hangi düzenleyicinin açduymayı belirledikten sonra, IDE çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> . Düzenleyicinin bu yöntemin uygulanması, IDE 'nin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Yeni açılan belgeyi çağırması ve site için gereken bilgileri döndürür.

    3. Son olarak, IDE,, gibi normal Kalıcılık arabirimini kullanarak belgeyi yükler <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .

    4. IDE daha önce hiyerarşinin veya hiyerarşi öğesinin kullanılabilir olduğunu belirleiyorsa, IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> yöntem çağrısıyla birlikte geri geçirilecek proje düzeyi bağlam işaretçisini almak için proje üzerinde yöntemi çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> .

4. <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> Düzenleyicinin projenizden bağlamı almasına izin vermek istiyorsanız IDE 'yi projeniz üzerinde çağırdığında IDE 'ye bir işaretçi döndürün.

     Bu adımın gerçekleştirilmesi, projenin düzenleyiciye ek hizmetler sunmasına olanak tanır.

     Belge görünümü veya belge görünümü nesnesi bir pencere çerçevesinde başarıyla oluşturulmuşsa, nesnesi çağırarak verileri ile başlatılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Proje öğelerini aç ve Kaydet](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıl yapılır: projeye özgü düzenleyiciler açma](../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl yapılır: açık belgeler için düzenleyiciler açma](../extensibility/how-to-open-editors-for-open-documents.md)
- [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
