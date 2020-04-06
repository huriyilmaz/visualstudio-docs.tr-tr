---
title: İç içe geçmiş projeler için AddItem İletişim Kutusunu Filtreleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708378"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>İç içe geçmiş projeler için AddItem iletişim kutusunu filtreleme
İç içe bir proje için bir **AddItem** iletişim kutusu görüntülediğinizde, ana proje iletişim kutusunda hangi öğelerin görüntüleneceğini denetleyebilir.

 Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> **AddItem** iletişim kutusunda yer alacak düğümleri filtrelemenizi sağlar. Alt proje **AddItem** iletişim kutusunu görüntülediğinde, üst `IVsFilterAddProjectItemDlg` öğe arabirimi uygulayabilir ve aksi takdirde çocuğun projesinde görüntülenecek öğeleri filtreleyebilir.

 Projeler belirli ana projeler altında işleve göre `IVsFilterAddProjectItemDlg` gruplandırıldığında, kullanıcı iç içe bir projede kısayol menüsünde **Proje Öğesi Ekle'yi** seçtiğinde uygulayabilirsiniz. Yalnızca `IvsFilterAddProjectItemDlg displays` bu gruba özgü proje öğelerini veya dosyaları uygulama. Diğer gruplar için proje öğeleri, aynı dizinde depolansalar bile iletişim kutusundan filtrelenir.

 Bir kullanıcı çocuk için **AddItem** iletişim kutusunu açtığında, üst projenin `IVsFilterAddProjectItemDlg` arabiriminin uygulanması çağrılır.

 `IVsFilterAddProjectItemDlg` Arabirim, kategoriye göre filtreleme de uygulayabilir. Daha fazla bilgi için bkz. [Yeni Öğe Ekle iletişim kutusuna öğe ekle](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) ve proje ve öğe [şablonlarını kaydedin.](../../extensibility/internals/registering-project-and-item-templates.md)

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Proje ve madde şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Nest projeleri](../../extensibility/internals/nesting-projects.md)
