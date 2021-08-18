---
title: "Nasıl: Standart Düzenleyiciler'i | Microsoft Docs"
description: OpenItem yöntemini standart bir düzenleyiciyle nasıl uygulayacaklarını öğrenin. IDE, belirlenen dosya türü için standart bir düzenleyici belirler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fa3da3de94f28fd0cc02320471e76f63ecf1694b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124912"
---
# <a name="how-to-open-standard-editors"></a>Nasıl: Standart düzenleyicileri açma
Standart bir düzenleyiciyi açıp IDE'nin, dosya için projeye özgü bir düzenleyici belirtmek yerine belirlenmiş bir dosya türü için standart bir düzenleyici belirlemesine izin verirsiniz.

 yöntemini uygulamak için aşağıdaki yordamı <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> izleyin. Bu, proje dosyasını standart bir düzenleyicide açar.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>OpenItem yöntemini standart bir düzenleyiciyle uygulamak için

1. Belge <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> veri nesnesi dosyasının zaten açık olup olmadığını belirlemek için () `RDT_EditLock` çağrısı.

2. Dosya zaten açıksa, parametresi için değerini belirterek yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> çağırarak dosyayı `IDO_ActivateIfOpen` yeniden `grfIDO` açın.

     Dosya açıksa ve belge, çağıran projeden farklı bir projeye aitse, projeniz açılan düzenleyicinin başka bir projeden geldiğine bir uyarı alır. Ardından dosya penceresi açılır.

3. Belge açık veya çalışan belge tablosunda yoksa, dosya için standart bir düzenleyici açmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> yöntemini () `OSE_ChooseBestStdEditor` çağırabilirsiniz.

     yöntemini çağırarak IDE aşağıdaki görevleri gerçekleştirir:

    1. IDE, dosyayı hangi düzenleyicinin açıp en yüksek önceliğe sahip olduğunu belirlemek için kayıt defterinde editors/{guidEditorType}/Extensions alt anahtarını tarar.

    2. IDE, dosyayı hangi düzenleyicinin aça olduğunu belirledikten sonra, IDE çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> lar. Düzenleyicinin bu yöntemi uygulaması, IDE'nin yeni açılan belgeyi çağırarak site oluşturması <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> için gereken bilgileri döndürür.

    3. Son olarak, IDE gibi normal kalıcılık arabirimini kullanarak belgeyi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> yükler.

    4. IDE daha önce hiyerarşi veya hiyerarşi öğesinin kullanılabilir olduğunu belirlediyse IDE, yöntem çağrısıyla geri geçiş yapmak için proje düzeyinde bir bağlam işaretçisi almak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> proje üzerinde yöntemini <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> arar.

4. Düzenleyicinin projenizin bağlamını aldırarak IDE'nin projenizi çağırarak <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> IDE'ye bir işaretçisi dönmesini sebilirsiniz.

     Bu adımın gerçekleştirerek projenin düzenleyiciye ek hizmetler sunabilirsiniz.

     Belge görünümü veya belge görünümü nesnesi bir pencere çerçevesinde başarıyla sitelenmişse, nesnesi çağrılarak verileriyle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A> başlatılır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md)
- [Nasıllı: Projeye özgü düzenleyicileri açma](../extensibility/how-to-open-project-specific-editors.md)
- [Nasıl kullanılır: Açık belgeler için düzenleyicileri açma](../extensibility/how-to-open-editors-for-open-documents.md)
- [Dosya Aç komutunu kullanarak dosyaları görüntüleme](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
