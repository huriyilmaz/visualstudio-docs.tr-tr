---
title: VSCodeWindow nesnesi | Microsoft Docs
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
ms.openlocfilehash: e7d8587036c2b9ac4ea8de4b4422243e39e901bd
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583651"
---
# <a name="vscodewindow-object"></a>VSCodeWindow nesnesi
Kod penceresi, genellikle nesnesini içeren bir veya daha fazla metin görünümü içerebilen özelleşmiş bir belge penceresidir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .

 Mimari türsel olarak, kod penceresi pencere çerçevesinin içindeki bir belge penceresidir. İşlevsellik, kod penceresi ise yalnızca ek özelliklerle bir belge penceresidir. Çoklu belge arabirimi (MDI) modunda, kod penceresi MDI alt çerçevesidir. Daha fazla bilgi için bkz. [eskı API 'yi kullanarak kod pencerelerini özelleştirme](../vs-2015/extensibility/customizing-code-windows-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true).

 Aşağıdaki tablo, nesnesindeki arabirimleri içerir <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> .

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Genel olarak benzersiz tanımlayıcı (GUID) tarafından tanımlanan bir hizmeti bulmak için genel erişim mekanizması sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Bir veya daha fazla kod görünümü içeren birden çok belge arabirimi (MDI) alt öğesini temsil eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Pencere çerçevesini doldurur.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Şekil düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)