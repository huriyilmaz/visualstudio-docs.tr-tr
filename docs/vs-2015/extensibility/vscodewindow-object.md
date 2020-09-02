---
title: VSCodeWindow nesnesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690768"
---
# <a name="vscodewindow-object"></a>VSCodeWindow Nesnesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod penceresi, genellikle nesnesini içeren bir veya daha fazla metin görünümü içerebilen özelleşmiş bir belge penceresidir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 Mimari türsel olarak, kod penceresi pencere çerçevesinin içindeki bir belge penceresidir. İşlevsellik, kod penceresi ise yalnızca ek özelliklerle bir belge penceresidir. Çoklu belge arabirimi (MDI) modunda, kod penceresi MDI alt çerçevesidir. Daha fazla bilgi için bkz. [eskı API 'Yi kullanarak kod pencerelerini özelleştirme](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 Aşağıdaki tablo, nesnesindeki arabirimleri içerir <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Genel olarak benzersiz tanımlayıcı (GUID) tarafından tanımlanan bir hizmeti bulmak için genel erişim mekanizması sağlar.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Bir veya daha fazla kod görünümü içeren birden çok belge arabirimi (MDI) alt öğesini temsil eder.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Pencere çerçevesini doldurur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Şekil düzenleme](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
