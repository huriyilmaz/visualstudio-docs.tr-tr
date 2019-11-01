---
title: VSTextView nesnesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 927bbee8bde62ff24396ea7b50e55e901b8cff06
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189012"
---
# <a name="vstextview-object"></a>VSTextView nesnesi

Metin görünümü, kullanıcıların metin arabelleğinin Unicode metnini görüntülemesine ve düzenlemesine izin veren bir penceredir. Esas olarak görünüm, çoğu kullanıcının düzenleyici olarak başvurduğu şeydir. Görünüm, çeşitli metin katmanları (sözcük kaydırması, anahat metni vb.) tarafından arabelleğinden ayrıldığından, bu görünümün arabellekteki metnin tam bir gösterimi olması garanti edilmez. Metin görünümü hakkında daha fazla bilgi için, bkz. [eskı API kullanarak metin görünümüne erişme](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

Aşağıdaki tabloda <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> nesnesindeki arabirimler gösterilmektedir.

|Arabirim|Açıklama|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Bileşik eylemlerin (yani, tek bir geri alma/yineleme biriminde gruplanmış eylemler) oluşturulmasına izin vermez.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|, Görünümü yönetmek ve bunlara erişmek için temel yöntemleri sağlar. `IVsTextView` iş parçacıklı güvenli değildir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Bir pencere bölmesi oluşturur ve yönetir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Metin katmanlarla etkileşime girer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Farklı bir iş parçacığından görünüm üzerinde işlemler gerçekleştirir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Şekil düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer nesnesi](../extensibility/vstextbuffer-object.md)