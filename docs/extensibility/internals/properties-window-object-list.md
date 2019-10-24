---
title: Özellikler penceresi nesne listesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e50b3fe46edb8d14cad9a03a45bc8650cb9713ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725182"
---
# <a name="properties-window-object-list"></a>Özellikler Penceresi Nesne Listesi
**Özellikler** penceresindeki nesne listesi, seçimi bir veya daha fazla seçili pencerede bulunan diğer nesnelerle değiştirmenize olanak tanıyan bir açılan liste listesidir. Bu listenin içinden farklı bir nesne seçilmesi, ortama yeni bir nesnenin seçili olduğunu bildirmek için <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> bir çağrı tetikler. **Özellikler** penceresinde görünen bilgiler daha sonra yeni seçilen nesneyle ilişkili özellikleri gösterecek şekilde değiştirilir.

## <a name="the-object-list"></a>Nesne listesi
 Nesne listesi iki alandan oluşur: nesne adı (kalın olarak gösterilir) ve nesne türü.

 Kalın yazı tipiyle nesne türünün solunda görünen nesne adı, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> arabirimi tarafından sunulan `Name` özelliği kullanılarak nesnenin kendisinden alınır. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>tek yöntemi, bu arabirimin coclass 'ı için <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> döndürür. **Özellikler** penceresi, açılan listede nesne adı olarak görünen coclass 'ın adını almak için <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> kullanır.

 Nesnenin `Name` bir özelliği yoksa, nesne listesinin ad alanında bir ad görüntülenmez. Adı nesne listesinde görüntülenmesini istiyorsanız nesnesine bir ad özelliği ekleyebilirsiniz.

 COM nesnesi <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>uygulamadıysa, **Özellikler** penceresi, listenin sol tarafındaki nesne adı yerine arabirim adını görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)