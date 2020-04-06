---
title: VSTextView Nesne | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697707"
---
# <a name="vstextview-object"></a>VSTextView nesnesi

Metin görünümü, kullanıcıların metin arabelleği Tek kodu metnini görüntülemesini ve yönetmesini sağlayan bir penceredir. Esasen, görünüm çoğu kullanıcı nın editör olarak adlandırdığı şeydir. Görünüm çeşitli metin katmanları (sözcük kaydırma, metnin anahat vb.) tarafından arabellekten ayrıldığından, görünümün arabellekteki metnin tam bir temsili olacağı garanti edilmez. Metin görünümü hakkında daha fazla bilgi için, [eski API'yi kullanarak Metin görünümüne erişim ebakına](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015)bakın.

Aşağıdaki tabloda <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> nesnedeki arabirimler gösterilmektedir.

|Arabirim|Açıklama|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standart OLE arabirimi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Bileşik eylemlerin (diğer bir deyişle, tek bir geri/yeniden oluşturma biriminde gruplanan eylemler) oluşturulmasını sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Görünümü yönetmek ve erişim için temel yöntemleri sağlar. `IVsTextView`güvenli dişli değildir.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Pencere bölmesi oluşturur ve yönetir.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Metin katmanlarıyla etkileşime girsin.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Görünümde farklı bir iş parçacığından işlemler gerçekleştirir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Şekiller edit](https://www.microsoft.com/download/details.aspx?id=55984)
- [VSTextBuffer nesnesi](../extensibility/vstextbuffer-object.md)
