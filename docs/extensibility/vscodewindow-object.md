---
title: VSCodeWindow nesnesi | Microsoft Docs
description: Genellikle VsTextView nesnesi olan bir veya daha fazla metin görünümü içerebilen özelleşmiş belge pencereleri olan kod pencereleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77839bf80f30de3177f647795ffb89aa3e103d58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062427"
---
# <a name="vscodewindow-object"></a>VSCodeWindow nesnesi
Kod penceresi, genellikle nesnesini içeren bir veya daha fazla metin görünümü içerebilen özelleşmiş bir belge penceresidir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .

 Mimari türsel olarak, kod penceresi pencere çerçevesinin içindeki bir belge penceresidir. İşlevsellik, kod penceresi ise yalnızca ek özelliklerle bir belge penceresidir. Çoklu belge arabirimi (MDI) modunda, kod penceresi MDI alt çerçevesidir. Daha fazla bilgi için bkz. [eskı API 'yi kullanarak kod pencerelerini özelleştirme](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015).

 Aşağıdaki tablo, nesnesindeki arabirimleri içerir <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> .

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Genel olarak benzersiz tanımlayıcı (GUID) tarafından tanımlanan bir hizmeti bulmak için genel erişim mekanizması sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Bir veya daha fazla kod görünümü içeren birden çok belge arabirimi (MDI) alt öğesini temsil eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Pencere çerçevesini doldurur.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Şekil düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)