---
title: VSCodeWindow Nesne | Microsoft Docs
description: Genellikle VsTextView nesnesi olan bir veya daha fazla metin görünümü içeren özelleştirilmiş belge pencereleri olan kod pencerelerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d9ce7cdc11fe44f2148f2c268e1cab554da6bffd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049226"
---
# <a name="vscodewindow-object"></a>VSCodeWindow nesnesi
Kod penceresi, genellikle nesnesi olan bir veya daha fazla metin görünümlerini içeren özel bir belge <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> penceresidir.

 Mimari olarak, kod penceresi bir pencere çerçevesi içinde yer alan bir belge penceresidir. İşlevsel olarak, kod penceresi yalnızca ek özelliklere sahip bir belge penceresidir. Çok belgeli arabirim (MDI) modunda kod penceresi MDI alt çerçevesidir. Daha fazla bilgi için [bkz. Eski API'yi kullanarak kod pencerelerini özelleştirme.](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

 Aşağıdaki tablo nesnesinde arabirimleri <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> içerir.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Genel olarak benzersiz bir tanımlayıcının (GUID) tanım sağladığı bir hizmeti bulmak için genel bir erişim mekanizması sağlar.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Bir veya daha fazla kod görünümleri içeren birden çok belge arabirimi (MDI) alt sınıflarını temsil eder.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Bir pencere çerçevesini doldurur.|

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Şekiller düzenleme](https://www.microsoft.com/download/details.aspx?id=55984)