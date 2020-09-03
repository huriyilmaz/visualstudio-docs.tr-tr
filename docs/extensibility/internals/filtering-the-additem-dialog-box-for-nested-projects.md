---
title: Iç Içe projeler için AddItem Iletişim kutusunu filtreleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708378"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>İç içe projeler için AddItem iletişim kutusunu filtrele
İç içe geçmiş bir proje için bir **ek iletişim kutusu** görüntülediğinizde, ana proje iletişim kutusunda hangi öğelerin görüntülendiğini denetleyebilir.

 Arabirim, ek <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> bir iletişim kutusunda olacak düğümleri filtrelemenizi sağlar. **AddItem** Alt proje **AddItem** iletişim kutusunu görüntülediğinde, üst öğe `IVsFilterAddProjectItemDlg` arabirimi uygulayabilir ve aksi takdirde alt öğe projesinde görüntülenecek öğeleri filtreleyebilirsiniz.

 Projeler belirli üst projeler altında işleve göre gruplandırılırken, `IVsFilterAddProjectItemDlg` kullanıcının iç içe geçmiş bir projedeki kısayol menüsünde **Proje öğesi Ekle** ' yi seçtiği zaman uygulayabilirsiniz. `IvsFilterAddProjectItemDlg displays`Yalnızca proje öğeleri veya bu gruba özgü dosyalar uygulama. Diğer gruplar için proje öğeleri, aynı dizinde depolansalar bile iletişim kutusunda filtrelenirler.

 Bir kullanıcı alt öğe için **AddItem** iletişim kutusunu açtığında, ana projenin `IVsFilterAddProjectItemDlg` arabirim uygulanması çağrılır.

 `IVsFilterAddProjectItemDlg`Arabirim filtreleme kategorisine göre de uygulanabilir. Daha fazla bilgi için bkz. [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Yeni öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Proje ve öğe şablonlarını Kaydet](../../extensibility/internals/registering-project-and-item-templates.md)
- [İç içe projeler](../../extensibility/internals/nesting-projects.md)
