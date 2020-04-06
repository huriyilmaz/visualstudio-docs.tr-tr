---
title: VSCodeWindow Nesne | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697951"
---
# <a name="vscodewindow-object"></a>VSCodeWindow nesnesi
Kod penceresi, genellikle nesne olan bir veya daha fazla metin <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> görünümü içerebilen özel leştirilmiş bir belge penceresidir.

 Mimari olarak, kod penceresi pencere çerçevesi içinde bir belge penceresidir. İşlevsel olarak, kod penceresi yalnızca ek özelliklere sahip bir belge penceresidir. Çoklu belge arabirimi (MDI) modunda, kod penceresi MDI alt çerçevesidir. Daha fazla bilgi için, [eski API'yi kullanarak kod pencerelerini özelleştirme'ye](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)bakın.

 Aşağıdaki <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> tabloda nesnedeki arabirimler yer almaktadır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Genel olarak benzersiz bir tanımlayıcının (GUID) tanımladığı bir hizmeti bulmak için genel bir erişim mekanizması sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Bir veya daha fazla kod görünümü içeren birden çok belge arabirimini (MDI) alt birimi temsil eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Pencere çerçevelerini doldurur.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Şekiller edit](https://www.microsoft.com/download/details.aspx?id=55984)
