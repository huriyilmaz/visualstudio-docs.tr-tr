---
title: Eski API kullanarak metin görünümüne erişme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184945"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Metin Görünümüne Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin görünümü, metin arabelleğinde depolanan metnin sunumudur. Aşağıdaki bölümde gösterildiği gibi eski API 'YI kullanarak metin görünümüne erişebilirsiniz.  
  
## <a name="text-view-object"></a>Metin görünümü nesnesi  
 Her görünüm kendi metin arabelleğiyle ilişkilendirilir ve görünüm arabellekteki verilerin bir penceresidir. Aşağıdaki diyagramda, ile temsil edilen metin görünümü nesnesinin temel arabirimleri gösterilmektedir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Visual Studio metin görünümü nesnesi](../extensibility/media/vstextview.gif "VsTextView")  
Metin görünümü nesnesi  
  
 Görünüm, arabelleğe metin sunma yöntemidir. Bu, Word sarması ve anahat oluşturma gibi özellikler içerir, böylece görünümde gördükleriniz, arabellekteki metnin tam bir gösterimi değildir.  
  
 Bir görünüm, diğer hizmet veya işlemlerin gelen komutları ele almasını ve görünümün üzerinde işlem yapmadan önce üzerinde işlem yapmasını sağlar. Bunu yapmak için en yaygın hizmet bir dil hizmetidir. Bir dil hizmeti, örneğin, özel girintileme davranışı veya araç ipuçları sağlamak üzere ENTER tuşu için komutu kesmeye yönelik olması gerekebilir.  
  
## <a name="adding-functionality-to-the-text-view"></a>Metin görünümüne Işlevsellik ekleme  
 Belirli tuş vuruşlarını işleyerek metin görünümü davranışını özelleştirebilirsiniz. Tuş vuruşlarını kesme altına almak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> nesneniz üzerinde uygulama ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komutları izlemek ve ele almak için bir komut hedefi () sağlamanız gerekir.  
  
 Metin görünümü komut filtreleri için sıralı mimari kullanır. Yöntemi çağırarak yeni komut filtreleri ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> nesneler) diziye eklenir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  
  
 Metin görünümü için olay bildirimi, arabirimi kullanılarak sağlanır `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` . Metin görünümündeki değişiklikler hakkında bildirim almak için bu arabirimi istemci nesneniz üzerinde uygulayın. <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>Görünümdeki değişiklikler hakkında bildirim almak için metin görünümündeki arabirimini kullanarak bu arabirimi metin görünümünde kullanıma sunun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API 'YI kullanarak görünüm ayarlarını değiştirme](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Genel Ayarları İzlemek İçin Metin Yöneticisini Kullanma](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
