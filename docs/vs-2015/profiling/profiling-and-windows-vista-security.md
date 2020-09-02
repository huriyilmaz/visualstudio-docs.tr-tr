---
title: Profil oluşturma ve Windows Vista güvenliği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7e485bc6289634e1bb6d4b4106d54c8dc82096b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683697"
---
# <a name="profiling-and-windows-vista-security"></a>Profil Oluşturma Windows Vista Güvenliği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]Bir bilgisayar yöneticisinin kullanılabilir hale getirildiğine yönelik kullanıcı erişim izinleri ayarlarına bağlı olarak, bireysel bir kullanıcı o bilgisayardaki bir işlemi profil için güvenlik iznine sahip olabilir. Aşağıdaki örneklerde kullanıcılar arasındaki olası farklılıklar gösterilmektedir:  
  
- Yönetici, sürücüyü ve hizmeti başlatmaya ayarladıktan sonra bazı kullanıcılar Gelişmiş profil oluşturma özelliklerine erişebilir.  
  
- Etki alanı kullanıcıları yalnızca örnek profil oluşturma erişimi sağlayabilir.  
  
- Bazı kullanıcılar, diğer tüm kullanıcılar için profil oluşturmaya erişimi reddedebilir.  
  
  Daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md)içindeki yönetici seçenekleri.  
  
## <a name="cross-session-profiling"></a>Çapraz oturum profili oluşturma  
 *Çapraz oturum profili oluşturma* , farklı bir oturum oturumunda çalışan bir işlemi profil oluşturma olanağıdır. Örneğin, çoğu hizmet oturum 0 ' da çalışır ve kullanıcılar 0 oturumunda doğrudan çalıştırılamaz. Performans Gezgini araç çubuğundaki **Işleme İliştir** düğmesini veya VSPerfCmd komut satırı aracının/Attach seçeneğini kullanarak, farklı oturum açma oturumlarındaki çoğu işlemi de profilin profilini oluşturabilirsiniz.  
  
 İşlemler arası profil oluşturma görünürlüğü seçeneklerini ayarlayarak kullanılabilir işlemlerin bir listesini görebilirsiniz. Bu seçenekler, **işleme**Ekle ' ye tıkladığınızda görüntülenen **İşleme İliştir** penceresinde kullanılabilir:  
  
- **Tüm kullanıcılardan işlem göster**  
  
     Bu seçenek seçilmezse, listede yalnızca geçerli kullanıcıya ait olan süreçler görüntülenir. **Tüm kullanıcılardan Işlem göster** seçildiğinde, listede tüm kullanıcıların süreçler görüntülenir.  
  
- **Tüm oturumlarda işlem göster**  
  
     Bu seçenek seçilmezse, listede geçerli oturumdaki süreçler görüntülenir. Bu seçenek belirlendiğinde, listede tüm oturumlardaki süreçler görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tahmin](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Nasıl yapılır: çalışan bir Işleme Iliştirme](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)
