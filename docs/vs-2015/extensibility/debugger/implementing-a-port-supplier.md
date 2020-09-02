---
title: Bağlantı noktası sağlayıcısı uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152683"
---
# <a name="implementing-a-port-supplier"></a>Bağlantı Noktası Sağlayıcısı Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir bağlantı noktası sağlayıcısı, oturum hata ayıklama Yöneticisi 'ne (SDM) istek üzerine bağlantı noktaları sağlar. DCOM olmayan bir makinede hata ayıklanırken veya yeni bir cihazın desteklenmesi gerektiğinde bir bağlantı noktası tedarikçinin uygulanması gerekir. Örneğin, bir hücre telefonunda hata ayıklama sağlamak için, hücre telefonuna (Belki IR veya bir hücre bağlantısı aracılığıyla) bağlanan bağlantı noktaları sağlayan bir bağlantı noktası sağlayıcısı uygulayabilir ve telefonda çalışan işlem ve programları numaralandırır.  
  
 Windows tabanlı makinelerde (uzaktan hata ayıklama dahil) programlarda hata ayıklama için, Visual Studio yerel ve ortak dil çalışma zamanı (CLR) işlemlerine yönelik bağlantı noktası sağlayıcıları sağlar. bu nedenle, bu durumlarda kendi bağlantı noktası tedarikçinizi uygulamanız gerekmez.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Noktası Sağlayıcısı Uygulama ve Kaydetme](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 SDM 'nin bağlantı noktası tedarikçisiyle ve bağlantı noktalarıyla nasıl etkileşime gireceğini açıklar.  
  
 [Gerekli Bağlantı Noktası Sağlayıcısı Arabirimleri](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Bir bağlantı noktası sağlayıcısı edinmek için uygulanması gereken arabirimleri belgeler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklayıcı Kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Ana hata ayıklama mimarisi kavramlarını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
