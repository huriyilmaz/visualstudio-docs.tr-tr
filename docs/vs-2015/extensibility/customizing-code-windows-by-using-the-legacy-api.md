---
title: Eski API 'YI kullanarak kod pencerelerini özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556141"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Kod Penceresini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kod penceresi, bir veya daha fazla metin görünümünü destekleyen bir belge pencere nesnesidir. Bir kod penceresinin tam özellikleri, ilişkili dil hizmetine bağlıdır. Birden çok belgeli arabirim (MDI) modunda, kod penceresi MDI alt çerçevesidir.  
  
 Kod pencereleri dil Hizmetleri tarafından denetlenir ve her dil hizmeti kendi kod pencere yöneticisini sağlayabilir. Bu, dil hizmetinin dalgalı çizgiler, renklendirme ve daha fazlasını kod penceresine eklemesini sağlar. Çekirdek pencere oluşturma hakkında daha fazla bilgi için, bkz. [eskı API 'Yi kullanarak çekirdek düzenleyiciyi örnekleme](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Kod penceresi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> metin görünümü ve nesnede bulunan donatılanlar içeren bir nesnedir. Temel düzenleyiciyi örnekleriniz sırasında kod penceresini oluşturduğunuzda, dil hizmetiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Aşağıdaki çizimde gösterildiği gibi kod penceresine eklenebilir.  
  
 ![CodeWindow grafiği](../extensibility/media/vscodewindow.gif "VsCodeWindow")  
Kod penceresi  
  
 Dil hizmeti, kod penceresi yöneticisini uygular ve açılan bir çubuk gibi donbeslerinizi yönetmekten sorumludur. Kod penceresi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> kod penceresi başlatma sırasında yöntemini çağırır. Bu çağrı yapıldığında, dil hizmeti kod penceresine bir açılan çubuk veya düğme çubuğu ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> ) ekleyebilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 `Customizing Code Windows by Using the Legacy API`  
 Eski API kullanılarak kod pencerelerinin nasıl özelleştirileceğini açıklar.  
  
 [Nasıl Yapılır: Bir Düzenleyiciyi Başka Bir Düzenleyicide Barındırma](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Bir düzenleyici penceresi içinde ikinci bir düzenleyicinin nasıl barındırılacağını açıklar.  
  
 [Nasıl Yapılır: Düzenleyici Odağı Kaybettiğinde Olayları Başlatma](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Belge görünümünün bir belge veri nesnesine nasıl ekleneceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Eski API 'YI kullanarak çekirdek düzenleyiciyi örnekleme](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Eski API'yi Kullanarak Metin Görünümüne Erişme](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
