---
title: Hata ayıklayıcı genişletilebilirliği ile çalışmaya başlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152706"
---
# <a name="getting-started-with-debugger-extensibility"></a>Hata Ayıklayıcı Genişletilebilirliği ile Çalışmaya Başlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Ortamında programların hatalarını ayıklamak için kullanılan hata ayıklayıcı bileşenlerini oluşturmak ve özelleştirmek için sahip olmanız gereken bilgileri sağlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama, önceki hata ayıklayıcılarda gerçekleştirilen kapsamlı kullanılabilirlik testinizden türetilmiş iyileştirmeler ekledi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Çok dilli bir uygulamada ilerlemek için hata ayıklamayı kullanabilir veya uygulamalarda ve çok dilli çözümlerde hata ayıklama sırasında değişkenlerin anında düzenlenmesinden yararlanabilirsiniz.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama, hata ayıklamakta olan program ile işlem dışı yürütülür ve bu nedenle uygulamanın işlem alanında daha az zorlayıcıdır. Sonuç olarak, hata ayıklama programınızı etkilemeden hata ayıklayıcı ile etkileşime geçen bileşenleri yazmak daha kolay olur.  
  
 En iyi şekilde kullanmak için, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] aşağıdakiler hakkında bilgi sahibi olmanız gerekir:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Tümleşik geliştirme ortamı (IDE)  
  
- C++ programlama dili  
  
- ATL COM  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Hata Ayıklayıcıyı Genişletmek için Yol Haritası](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Derleyiciye ve çıktısına bağlı olarak, ürününüzün hata ayıklamayı uygulama sürecini özetler.  
  
 [Hata Ayıklayıcı Bileşenleri](../../extensibility/debugger/debugger-components.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Hata ayıklama altyapısını (de), ifade değerlendiricisi (ee) ve Sembol işleyicisini (sh) içeren hata ayıklama bileşenlerine genel bakış sağlar.  
  
 [Hata Ayıklayıcı Kavramları](../../extensibility/debugger/debugger-concepts.md)  
 Ana hata ayıklama mimarisi kavramlarını açıklar.  
  
 [Hata Ayıklayıcı Bağlamları](../../extensibility/debugger/debugger-contexts.md)  
 Hata ayıklama altyapısının (DE) kod, belge ve ifade değerlendirme bağlamlarının eşzamanlı olarak nasıl çalıştığını açıklar. Üç bağlamın her biri için bu konuyla ilgili konum, konum veya değerlendirmeyi açıklar.  
  
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)  
 Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
