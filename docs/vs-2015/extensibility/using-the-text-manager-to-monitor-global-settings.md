---
title: Genel ayarları Izlemek için metin Yöneticisi 'ni kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695462"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Genel Ayarları İzlemek İçin Metin Yöneticisini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çekirdek Düzenleyici uygularsanız, bu değişiklikler düzenleyicinin örneğinizi etkileyebileceğinden, genel ayarlarda yapılan değişiklikleri izlemeniz gerekir. Metin Yöneticisi tarafından oluşturulan olayları dinleyerek değişiklikleri izleyebilirsiniz. Örneğin, bir bileşenin, belge verileri nesnesi gibi çekirdek düzenleyicide görünümü veya davranışı için genel bir tercih belirttiğinizde, metin Yöneticisi bu bilgileri depolar ve etkilenen tüm istemcilerle iletişim kurar.  
  
## <a name="text-manager-functions"></a>Metin Yöneticisi Işlevleri  
 Metin Yöneticisi, aşağıdakiler de dahil olmak üzere çeşitli ayarlar için olaylar oluşturur:  
  
- Bir arabelleğin kaynak kodu denetimi altında olup olmadığı  
  
- Dosya değişikliği bildirimlerine kaydolma  
  
- Belirli arabelleklerle hangi görünümlerin ilişkilendirildiğini takip etme  
  
- Metin renklendirme tercihleri  
  
- Sekme ve boşluk tercihleri  
  
  Belirli bir dile özgü olan Tercihler metin Yöneticisi tarafından yönetilmez. Bu ayarların her dil hizmeti tarafından yönetilmesi gerekir.  
  
  Metin Yöneticisi için olay bildirimi, arabirimi tarafından sağlanır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> . Bu arabirimi, metin Yöneticisi tarafından oluşturulan olayları işlemek için istemci nesneniz üzerinde uygulayın. Bu olaylara, <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> metin Yöneticisi üzerindeki arabirimini kullanarak kaydolabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek düzenleyicinin içinde](../extensibility/inside-the-core-editor.md)   
 [Düzenleyici Özellikleri](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
