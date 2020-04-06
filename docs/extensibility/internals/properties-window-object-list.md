---
title: Özellikler Penceresi Nesne Listesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706144"
---
# <a name="properties-window-object-list"></a>Özellikler Penceresi Nesne Listesi
**Özellikler** penceresindeki nesne listesi, seçimi bir veya daha fazla seçili pencerede bulunan diğer nesnelerle değiştirmenize olanak tanıyan açılır listedir. Bu liste içinden farklı bir nesne seçmek, ortama yeni bir nesnenin seçildiğini bildirmek için <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> bir çağrıyı tetikler. **Özellikler** penceresinde görüntülenen bilgiler daha sonra yeni seçilen nesneile ilişkili özellikleri göstermek için değiştirilir.

## <a name="the-object-list"></a>Nesne Listesi
 Nesne listesi iki alandan oluşur: nesne adı (kalın olarak görüntülenir) ve nesne türü.

 Kalın nesne türünün solunda görüntülenen nesne `Name` <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> adı, arabirim tarafından sağlanan özelliği kullanılarak nesnenin kendisinden alınır. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, tek yöntem <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> bu arabirimin coclass için döndürür. **Özellikler** penceresi, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> açılan listede nesne adı olarak görüntülenen coclass'ın adını almak için kullanır.

 Nesnenin bir `Name` özelliği yoksa, nesne listesinin Ad alanında bir ad görüntülenmez. Adın nesne listesinde görüntülenmesini istiyorsanız nesneye bir Ad özelliği ekleyebilirsiniz.

 COM nesnesi uygulamazsa, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> **Özellikler** penceresi listenin sol tarafındaki nesne adının yerine arabirim adını görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
