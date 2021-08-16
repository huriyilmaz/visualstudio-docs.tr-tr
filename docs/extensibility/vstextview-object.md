---
title: VSTextView Nesne | Microsoft Docs
description: VSTextView nesnesi, kullanıcıların metin arabelleğinin Unicode metnini görüntülemesini ve düzenlemesini sağlayan bir penceredir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8bfce06cdb6e98b6090933b83f53d43bed3f9b44317c60658d8d1eba4997ddec
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413524"
---
# <a name="vstextview-object"></a>VSTextView nesnesi

Metin görünümü, kullanıcıların metin arabelleğinin Unicode metnini görüntülemesini ve düzenlemesini sağlayan bir penceredir. Temelde çoğu kullanıcının düzenleyici olarak ifade edilen görünümdür. Görünüm, arabellekten çeşitli metin katmanlarıyla (sözcük kaydırma, açıklama metni gibi) ayrıldığından, görünümün arabellekte metnin tam bir gösterimi olması garanti edilemez. Metin görünümü hakkında daha fazla bilgi için [bkz. Eski API'yi kullanarakText görünümüne erişme.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

Aşağıdaki tabloda nesnesinde arabirimler <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> yer almaktadır.

|Arabirim|Açıklama|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Bileşik eylemlerin (başka bir ifadeyle, tek bir geri alma/yenidendo biriminde gruplandı) oluşturulmasını sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Görünümü yönetmek ve görünüme erişmek için temel yöntemleri sağlar. `IVsTextView` güvenli iş parçacıklı değildir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Bir pencere bölmesi oluşturur ve yönetir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Metin katmanlarıyla etkileşime geçme.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Görünümde farklı bir iş parçacığından işlemler gerçekleştirir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Şekiller düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer nesnesi](../extensibility/vstextbuffer-object.md)