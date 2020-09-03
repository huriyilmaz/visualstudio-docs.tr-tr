---
title: Eski API kullanarak metin katmanlarına erişme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148017"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Metin Katmanlarına Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin katmanı genellikle metin düzeninin bazı yönlerini kapsar. Örneğin, "bir kez işlev" katmanı, giriş işaretini (metin ekleme noktası) içeren bir işlevden önce ve sonra metin gizler.  
  
 Bir metin katmanı, bir arabellek ile bir görünüm arasında bulunur ve görünümün arabelleğin içeriğini nasıl göreceğini değiştirir.  
  
## <a name="text-layer-information"></a>Metin katmanı bilgileri  
 Aşağıdaki listede, metin katmanlarının nasıl çalıştığı açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- Bir metin katmanındaki metin, Sözdizimi renklendirmesi ve işaretçileriyle donanıp eklenebilir.  
  
- Şu anda kendi Katmanlarınızı uygulayamamaktadır.  
  
- Bir katman ortaya çıkaran <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , öğesinden türetilmiş <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Metin arabelleğinin kendisi de bir katman olarak uygulanır ve bu da bir görünümün temeldeki katmanlarla polymorphically 'e anlaşma sağlar.  
  
- Herhangi bir sayıda katman, görünüm ve arabellek arasında olabilir. Her katman yalnızca altındaki katmanla ilgilidir ve görünüm büyük ölçüde en üst katman ile ilgilidir. (Görünüm arabellek hakkında bazı bilgiler de vardır.)  
  
- Bir katman, yalnızca altındaki katmanları etkileyebilir. Bu, kaynak standart olayları ötesinde yukarıdaki katmanları etkilemez.  
  
- Düzenleyicide gizli metin, yapay metin ve sözcük kaydırması Katmanlar olarak uygulanır. Doğrudan katmanlarla etkileşimde bulunmadan gizli ve yapay metinler uygulayabilirsiniz. Daha fazla bilgi için bkz. [bir eski dil hizmetinde anahat oluşturma](../extensibility/internals/outlining-in-a-legacy-language-service.md) ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Her metin katmanının, arabirimi aracılığıyla kullanıma sunulan kendi yerel koordinat sistemi vardır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> . Örneğin, satır kaydırması katmanı, temeldeki metin arabelleği yalnızca bir satır içerdiğinde iki satır içerebilir.  
  
- Görünüm, arabirim aracılığıyla katmanlarla iletişim kurar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> . Bu arabirimi, arabellek koordinatları ile görünüm koordinatlarını bağdaştırmak için kullanın.  
  
- Metin kaynaklı yapay metin katmanı gibi herhangi bir katmanın yerel bir uygulamasını sağlaması gerekir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Bunun yanı sıra, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> bir metin katmanının, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> arabirimindeki olayları uygulaması ve tetiklemesi gerekir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel düzenleyicilerde söz dizimi renklendirmesi](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Eski API ile metin Işaretleyicileri kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Eski API'yi Kullanarak Düzenleyici Denetimlerini ve Menüleri Özelleştirme](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
