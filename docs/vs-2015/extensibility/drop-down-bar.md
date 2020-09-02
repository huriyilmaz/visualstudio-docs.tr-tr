---
title: Açılan çubuk | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - drop-down bar
ms.assetid: 4bb621bd-72f5-43d5-916f-9f66617da049
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4296a8fa4146a52d167bce3d8b051aa3ca073
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204663"
---
# <a name="drop-down-bar"></a>Aşağı Açılan Çubuk
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Açılan çubuk, kod penceresinin en üstünde sağlanır ve iki açılan liste içerir.  
  
## <a name="drop-down-bar-interfaces"></a>Açılan çubuk arabirimleri  
 ' De, [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Örneğin, açılan çubuk [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Aşağıdaki resimde gösterildiği gibi öğeler ve öğeler üye işlevleri için listeler içerir.  
  
 ![&#45;aşağı çubukları bırak](../extensibility/media/vsdropdown-bar.gif "vsDropdown_bar")  
Açılan çubuk  
  
 Açılan bir çubuğu uygularken, birincil önemli dört arabirim vardır:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient>  
  
     Açılan çubuğun içeriğini eklemek için bu arabirimi uygulayın. Her açılan birleşim düz metin veya süslü metin (kalın, altı çizili veya italik) içerebilir, pencere metin yazı tipi renklendirmesi veya gri yazı tipi renklendirmesini sağlayabilir ve isteğe bağlı olarak aşağı açılan öğenin yanında küçük bir bit eşlem sağlayabilir. Arabirime benzer şekilde <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> , bit eşlem görüntüleri görüntü listelerinde sağlanır. Her açılan birleşim farklı bir görüntü listesine sahip olabilir; Ancak, her bir görüntü listesinin aynı yüksekliğin görüntülerini içermesi gerekir. Ayrıca, yöntemini kullanarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarClient.GetComboTipText%2A> her birleşim için bir araç ipucu sağlayabilirsiniz.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>  
  
     Bir kod penceresi için açılan çubuğun oluşturulması veya yok olması için bu arabirimi çağırın. Bu arabirim, bir açılan çubuğun, yöntemi çağırarak bir kod penceresine zaten eklenmiş olup olmadığını anlamak için de kullanılabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> . <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>Öğesinden için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager> çağrısı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>  
  
     Doğrudan açılan çubukla iletişim kurmak için bu arabirimi çağırın. Bu arabirimi, açılan çubuğun içeriğini yenilemeyi zorlamak veya liste kutularından birindeki seçimi değiştirmek için kullanabilirsiniz.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>  
  
     `ShowDropdownBarOption`Dil hizmeti kayıt defteri anahtarınıza kaydolduysanız, kod pencere yöneticinizin bu olayı, açılan çubuğun görüntülenip görüntülenmeyeceğini ilişkin kullanıcı tercihleriyle eşitlenmek üzere izlemesi gerekir. Dil hizmeti anahtarınıza bu seçeneği kaydetmeyin, **Seçenekler** menüsünde açılır çubuğun gösterilmesi veya gizlenmesi seçeneği devre dışı bırakılır.  
  
## <a name="attaching-a-drop-down-bar-to-a-code-window"></a>Bir kod penceresine açılan bir çubuk iliştirme  
 Kod penceresine bir açılan bir çubuk eklendiğinde, yöntem çağrıldığında bir dil hizmetinin açılan çubuğa eklemesi gerekir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . Yöntemine yapılan bir çağrı, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.GetDropdownBar%2A> bir açılan çubuğun zaten mevcut olmadığını gösteriyorsa, öğesini çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager.AddDropdownBar%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBarManager>Arayüze erişmek için, <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> uygulamanız eklendiği sırada size döndürülen işaretçiden çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API 'YI kullanarak kod pencerelerini özelleştirme](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)   
 [Eski Dil Hizmetinde Gezinti Çubuğu için Destek](../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)
