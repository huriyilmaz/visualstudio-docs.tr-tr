---
title: Özel hata ayıklama altyapısı oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b2a73dfae7772d8edec076238704aa1b52c9b028
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64829307"
---
# <a name="creating-a-custom-debug-engine"></a>Özel Hata Ayıklama Altyapısı Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE), belirli çalışma zamanı mimarilerinin hata ayıklamasına izin veren bir bileşendir. Çalışma zamanı ortamı başına genellikle yalnızca bir DE uygulama vardır.  
  
> [!NOTE]
> Transact-SQL ve JScript için ayrı uygulamalar olsa da, VBScript ve JScript tek bir DE paylaşabilirsiniz.  
  
 Aynı hata ayıklama hizmetlerini yürütme denetimi, kesme noktaları ve ifade değerlendirmesi olarak sağlamak için yorumlayıcı veya işlem sistemiyle birlikte da kullanılır. Bu hizmetler DE aynı arabirimler aracılığıyla uygulanır ve hata ayıklayıcının farklı çalışma modları arasında geçişine neden olabilir. Daha fazla bilgi için bkz. [Işletimsel modlar](../../extensibility/debugger/operational-modes.md).  
  
 DE oluşturmak aşağıdaki adımlardan oluşur:  
  
1. Visual Studio ile DE kaydetme  
  
2. Bir programın ayıklanamayacağını etkinleştirme  
  
3. Yürütme denetimi ve durum değerlendirmesi  
  
4. Olayları gönderme  
  
5. Sonlandırma ve ayırma  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Özel Bir Hata Ayıklama Altyapısını Kaydetme](../../extensibility/debugger/registering-a-custom-debug-engine.md)  
 Kullanılabilmesi için, Visual Studio ile bir hata ayıklama altyapısını kaydetmek için gereken adımları açıklar.  
  
 [Bir Programı Hataları Ayıklanacak Şekilde Etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)  
 Aynı programda hata ayıklamanıza başlamadan önce, önce bunu başlatmanız veya mevcut bir programa iliştirmelisiniz.  
  
 [Yürütme Denetimi ve Durum Değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)  
 Uygulamanın hata ayıklamanın yürütme denetim özelliklerinin uygulanması gerektirdiğini açıklar.  
  
 [Olayları Gönderme](../../extensibility/debugger/sending-events.md)  
 DCOM tabanlı bir olay modeli olarak hata ayıklayıcı ile DE arasındaki iletişimi açıklar.  
  
 [Sonlandırma ve Ayırma](../../extensibility/debugger/termination-and-detaching.md)  
 Hata ayıklama için kesme noktası, özel durum, çalışma zamanı hataları veya hatalı döngüler olmadığı anlamına gelen normal sonlandırmanın nasıl yapılacağını açıklar.  
  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)  
 Hata ayıklama oturumunda gerçekleşen olayların arama sırasını belgeler.  
  
 [Nasıl Yapılır: Özel Hata Ayıklama Altyapısında Hata Ayıklama](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md)  
 Özel bir DE hata ayıklamanın nasıl yapılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
