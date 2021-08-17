---
title: İç İçe Projeler için AddItem İletişim Kutusunu Filtreleme | Microsoft Docs
description: Üst projenin IVsFilterAddProjectItemDlg arabirimini kullanarak Visual Studio bir iç içe proje için AddItem iletişim kutusunu filtrelemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: aa65af14d05b60e78643f03c1f74719fb1c25eadf246451287ed04d58723e4f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338013"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>İç içe projeler için AddItem iletişim kutusunu filtreleme
İç içe bir proje **için AddItem** iletişim kutusu görüntülendiğinde, üst proje iletişim kutusunda hangi öğelerin görüntülendiğinden emin olabilir.

 Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> **AddItem** iletişim kutusunda olacak düğümleri filtrelemenize olanak sağlar. Alt proje **AddItem** iletişim kutusunu görüntülendiğinde üst öğe, alt projenin başka bir şekilde görüntülenebilir arabirimini ve `IVsFilterAddProjectItemDlg` filtre öğelerini uygulamaya ekleyebilir.

 Projeler belirli üst projelerin altında işleve göre gruplanmışsa, kullanıcı iç içe bir proje içindeki kısayol menüsünden Project Öğe Ekle'yi seçerek `IVsFilterAddProjectItemDlg` bunu gerçekleştirebilirsiniz.  Yalnızca bu `IvsFilterAddProjectItemDlg displays` gruba özgü proje öğelerini veya dosyaları uygulama. Project grupların tüm öğeleri, aynı dizinde depolanmış olsalar bile iletişim kutusunun dışında filtrelenmiş olur.

 Kullanıcı alt öğe için **AddItem** iletişim kutusunu açtığında, üst projenin arabirim `IVsFilterAddProjectItemDlg` uygulaması çağrılır.

 Arabirim `IVsFilterAddProjectItemDlg` ayrıca kategoriye göre filtreleme de gerçekleştirebilirsiniz. Daha fazla bilgi için [Bkz. Yeni Öğe Ekle iletişim kutusuna öğe ekleme ve](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) Proje ve öğe [şablonlarını kaydetme.](../../extensibility/internals/registering-project-and-item-templates.md)

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Yeni Öğe Ekle iletişim kutusuna öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)
- [Projeleri iç içe yerleştirme](../../extensibility/internals/nesting-projects.md)
