---
title: Özellikler penceresi nesne listesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95ef509491e05daf575e211ae479c815994eb3d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148339"
---
# <a name="properties-window-object-list"></a>Özellikler Penceresi Nesne Listesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Özellikler** penceresindeki nesne listesi, seçimi bir veya daha fazla seçili pencerede bulunan diğer nesnelerle değiştirmenize olanak tanıyan bir açılan liste listesidir. Bu listenin içinden farklı bir nesne seçilmesi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> , ortama yeni bir nesnenin seçili olduğunu bildirmek için bir çağrısı tetikler. **Özellikler** penceresinde görünen bilgiler daha sonra yeni seçilen nesneyle ilişkili özellikleri gösterecek şekilde değiştirilir.  
  
## <a name="the-object-list"></a>Nesne listesi  
 Nesne listesi iki alandan oluşur: nesne adı (kalın olarak gösterilir) ve nesne türü.  
  
 Kalın yazı tipiyle nesne türünün solunda görünen nesne adı, `Name` arabirim tarafından sunulan özelliği kullanılarak nesnenin kendisinden alınır <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> . <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, üzerindeki tek yöntemi <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> Bu arabirimin coclass 'ı için döndürür. **Özellikler** penceresi, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> açılan listede nesne adı olarak görünen coclass 'ın adını almak için kullanır.  
  
 Nesnenin bir `Name` özelliği yoksa, nesne listesinin ad alanında bir ad görüntülenmez. Adı nesne listesinde görüntülenmesini istiyorsanız nesnesine bir ad özelliği ekleyebilirsiniz.  
  
 COM nesnesi uygulamadıysa <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> , **Özellikler** penceresi, listenin sol tarafındaki nesne adı yerine arabirim adını görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
