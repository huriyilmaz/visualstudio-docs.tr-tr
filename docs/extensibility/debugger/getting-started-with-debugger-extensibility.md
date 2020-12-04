---
title: Hata ayıklayıcı genişletilebilirliği ile çalışmaya başlama | Microsoft Docs
description: Visual Studio ortamının içinden programlarda hata ayıklamak için kullanılan hata ayıklayıcı bileşenlerini oluşturmaya ve özelleştirmeye başlayın.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6949b9b8a9168915c64bc6183f6b1391a1c79220
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560041"
---
# <a name="get-started-with-debugger-extensibility"></a>Hata ayıklayıcı genişletilebilirliği ile çalışmaya başlama
, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Ortamında programların hatalarını ayıklamak için kullanılan hata ayıklayıcı bileşenlerini oluşturmak ve özelleştirmek için ihtiyacınız olan bilgileri sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, önceki hata ayıklayıcılarda gerçekleştirilen kapsamlı kullanılabilirlik testinizden türetilmiş iyileştirmeler ekledi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Çok dilli bir uygulamada ilerlemek için hata ayıklamayı kullanabilir veya uygulamalarda ve çok dilli çözümlerde hata ayıklama sırasında değişkenlerin anında düzenlenmesinden yararlanabilirsiniz.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, hata ayıklamakta olan program ile işlem dışı yürütülür ve bu nedenle uygulamanın işlem alanında daha az zorlayıcıdır. Sonuç olarak, hata ayıklama programınızı etkilemeden hata ayıklayıcı ile etkileşime geçen bileşenleri yazmak daha kolay olur.

 ' Yi en iyi şekilde kullanmak için [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] aşağıdaki öğeler hakkında bilgi sahibi olmanız gerekir:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tümleşik geliştirme ortamı (IDE)

- C++ programlama dili

- ATL COM

## <a name="in-this-section"></a>Bu bölümde
 [Hata ayıklayıcıyı genişletmek Için yol haritası](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Derleyiciye ve çıktısına bağlı olarak, ürününüzün hata ayıklamayı uygulama sürecini özetler.

 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama altyapısını (de), ifade değerlendiricisi (ee) ve Sembol işleyicisini (sh) içeren hata ayıklama bileşenlerine genel bakış sağlar.

 [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimarisi kavramlarını açıklar.

 [Hata ayıklayıcı bağlamları](../../extensibility/debugger/debugger-contexts.md) Hata ayıklama altyapısının (DE) kod, belge ve ifade değerlendirme bağlamlarının eşzamanlı olarak nasıl çalıştığını açıklar. Üç bağlamın her biri için, bu konuyla ilgili konum, konum veya değerlendirmeyi açıklar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
