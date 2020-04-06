---
title: Debugger Extensibility ile başlarken | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738599"
---
# <a name="get-started-with-debugger-extensibility"></a>Hata ayıklama genişletilebilirliği ile başlayın
Bu, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ortam içinden gelen ayıklama programları için kullanılan hata ayıklama bileşenleri oluşturmak ve özelleştirmek için gereken bilgileri sağlar.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hata ayıklama, önceki hata ayıklayıcılar üzerinde gerçekleştirilen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kapsamlı kullanılabilirlik testinden kaynaklanan iyileştirmeler ilerlemiştir. Çok dilli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir uygulama üzerinden adım atmak için hata ayıklama yı kullanabilirsiniz veya uygulamaları ve çok dilli çözümleri hata ayıklarken değişkenlerin anında düzenlemesini uygulayabilirsiniz.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hata ayıklama, program debugged ve bu nedenle uygulamanın işlem alanında daha az müdahaleci olan işlem dışı yürütülür. Sonuç olarak, hata ayıklama programınızı etkilemeden hata ayıklama yla etkileşime girerek bileşenler yazmak daha kolaydır.

 En iyi [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]şekilde kullanmak için, aşağıdaki öğeleri aşina olmalıdır:

- Entegre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE)

- C++ programlama dili

- ATL COM

## <a name="in-this-section"></a>Bu bölümde
 [Hata ayıklamayı genişletmek için yol haritası](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Derleyicinize ve çıktısına bağlı olarak, ürününzde hata ayıklama işlemini özetler.

 [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md) Hata ayıklama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] altyapısı (DE), ifade değerlendiricisi (EE) ve sembol işleyicisini (SH) içeren hata ayıklama bileşenlerine genel bir bakış sağlar.

 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramları açıklar.

 [Hata ayıklama bağlamları](../../extensibility/debugger/debugger-contexts.md) Hata ayıklama altyapısının (DE) kod, belge ve ifade değerlendirme bağlamlarında aynı anda nasıl çalıştığını açıklar. Üç bağlamın her biri için, bununla ilgili konumu, konumu veya değerlendirmeyi açıklar.

 [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerine bağlantılar içerir.
