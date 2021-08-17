---
title: Özellikler Penceresi Nesne Listesi | Microsoft Docs
description: Özellikler penceresi IDE'de nesne listesiyle etkileşim kurmak için Özellikler penceresi arabirimler hakkında Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4ed4b3fc37d4110d6cd6dfd02c2dea503cbee194
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042133"
---
# <a name="properties-window-object-list"></a>Özellikler Penceresi Nesne Listesi
Özellikler penceresindeki nesne **listesi,** seçimi bir veya daha fazla seçili pencerede bulunan diğer nesnelerle değiştirmenizi sağlayan bir açılan listedir. Bu listenin içinde farklı bir nesne seçmek, ortamı yeni bir nesnenin seç olduğunu <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> bildirmek için çağrısı tetikler. Ardından Özellikler penceresinde **görüntülenen bilgiler,** yeni seçilen nesneyle ilişkili özellikleri gösterecek şekilde değiştirilir.

## <a name="the-object-list"></a>Nesne Listesi
 Nesne listesi iki alandan oluşur: nesne adı (kalın olarak görüntülenir) ve nesne türü.

 Nesne türünün sol tarafından kalın olarak görüntülenen nesne adı, arabirimi tarafından sağlanan özelliği `Name` kullanılarak nesnenin kendisinden <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> alınır. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>üzerinde tek yöntemi <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> olan , bu <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> arabirimin ortak sınıfı için döndürür. Özellikler  penceresi, <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> açılır listede nesne adı olarak görüntülenen coclass'ın adını almak için kullanır.

 Nesnenin bir özelliği `Name` yoksa, nesne listesinin Ad alanında bir ad görüntülenmez. Adın nesne listesinde görüntülenebilir istemesi için nesneye bir Name özelliği ekleyebilirsiniz.

 COM nesnesi uygulamazsa, Özellikler penceresi listenin sol tarafındaki <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> nesne adının yerine arabirim adını görüntüler. 

## <a name="see-also"></a>Ayrıca bkz.
- [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)
