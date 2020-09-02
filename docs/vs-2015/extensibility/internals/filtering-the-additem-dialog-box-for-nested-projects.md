---
title: Iç Içe projeler için AddItem Iletişim kutusunu filtreleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538102"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>İç içe Projeler için AddItem İletişim Kutusunu Filtreleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İç içe geçmiş bir proje için bir **ek iletişim kutusu** görüntülediğinizde, ana proje iletişim kutusunda hangi öğelerin görüntülendiğini denetleyebilir.  
  
 Arabirim, ek <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> bir iletişim kutusunda olacak düğümleri filtrelemenizi sağlar. **AddItem** Alt proje **AddItem** iletişim kutusunu görüntülediğinde, üst öğe `IVsFilterAddProjectItemDlg` arabirimi uygulayabilir ve aksi takdirde alt öğe projesinde görüntülenecek öğeleri filtreleyebilirsiniz.  
  
 Projeler belirli üst projeler altında işleve göre gruplandırılırken, `IVsFilterAddProjectItemDlg` kullanıcının iç içe geçmiş bir projedeki kısayol menüsünde **Proje öğesi Ekle** ' yi seçtiği zaman uygulayabilirsiniz. `IvsFilterAddProjectItemDlg displays`Yalnızca proje öğeleri veya bu gruba özgü dosyalar uygulama. Diğer gruplar için proje öğeleri, aynı dizinde depolansalar bile iletişim kutusunda filtrelenirler.  
  
 Bir kullanıcı alt öğe için **AddItem** iletişim kutusunu açtığında, ana projenin `IVsFilterAddProjectItemDlg` arabirim uygulanması çağrılır.  
  
 `IVsFilterAddProjectItemDlg`Arabirim filtreleme kategorisine göre de uygulanabilir. Daha fazla bilgi için, [Yeni öğe Ekle Iletişim kutularına öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) ve [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Yeni öğe Ekle Iletişim kutularına öğe ekleme](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
