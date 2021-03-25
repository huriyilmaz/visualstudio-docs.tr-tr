---
title: VSTextView nesnesi | Microsoft Docs
description: VSTextView nesnesi, kullanıcıların metin arabelleğinin Unicode metnini görüntülemesine ve düzenlemesine izin veren bir penceredir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a7ec65ed2beb866bfbb4e35fd5b290d3457ad3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062167"
---
# <a name="vstextview-object"></a>VSTextView nesnesi

Metin görünümü, kullanıcıların metin arabelleğinin Unicode metnini görüntülemesine ve düzenlemesine izin veren bir penceredir. Esas olarak görünüm, çoğu kullanıcının düzenleyici olarak başvurduğu şeydir. Görünüm, çeşitli metin katmanları (sözcük kaydırması, anahat metni vb.) tarafından arabelleğinden ayrıldığından, bu görünümün arabellekteki metnin tam bir gösterimi olması garanti edilmez. Metin görünümü hakkında daha fazla bilgi için, bkz. [eskı API kullanarak metin görünümüne erişme](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

Aşağıdaki tabloda, nesnesindeki arabirimler gösterilmektedir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .

|Arabirim|Description|
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