---
title: Başlarken Ayıklayıcı Genişletilebilirliği ile | Microsoft Docs
description: Kullanmaya başlayın ortamında programlarda hata ayıklamak için kullanılan hata ayıklayıcı bileşenlerini oluşturma ve Visual Studio gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f10ea604cf4e07dbeec96c4dbbc3eadd3b3aef379a0dbbd7f11eb7f943957611
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308213"
---
# <a name="get-started-with-debugger-extensibility"></a>Kullanmaya başlayın ayıklayıcı genişletilebilirliği ile ilgili sorun giderme
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], ortamdaki programlarda hata ayıklamak için kullanılan hata ayıklayıcı bileşenlerini oluşturmak ve özelleştirmek için ihtiyacınız olan bilgileri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağlar.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, önceki hata ayıklayıcılarda gerçekleştirilen kapsamlı kullanılabilirlik testlerinden türetilen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirmeler ekledi. Hata ayıklamayı kullanarak çok dilli bir uygulamada adım adım ilerler veya uygulamalarda ve çok dilli çözümlerde hata ayıklarken değişkenlerin çalışırken [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] düzenlenmesini de gerçekleştirebilirsiniz.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama, program hata ayıklarken işlem dışı yürütülür ve bu nedenle uygulamanın işlem alanı için daha az müdahaleci olur. Sonuç olarak, hata ayıklama programınızı etkilemeden hata ayıklayıcıyla etkileşimde bulunan bileşenleri yazmak daha kolaydır.

 'i en [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] iyi şekilde kullanmak için aşağıdaki öğelere aşina olmak gerekir:

- Tümleşik [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geliştirme ortamı (IDE)

- C++ programlama dili

- ATL COM

## <a name="in-this-section"></a>Bu bölümde
 [Hata ayıklayıcısını genişletmek için yol haritası](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Derleyicinize ve çıkışına bağlı olarak, üründe hata ayıklama uygulama sürecini özetler.

 [Hata ayıklayıcısı bileşenleri](../../extensibility/debugger/debugger-components.md) Hata ayıklama altyapısını (DE), ifade değerlendiricisini (EE) ve sembol işleyicisini (SH) içeren hata ayıklama bileşenlerine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] genel bir bakış sağlar.

 [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramlarını açıklar.

 [Hata ayıklayıcısı bağlamları](../../extensibility/debugger/debugger-contexts.md) Hata ayıklama altyapısının (DE) kod, belge ve ifade değerlendirme bağlamları içinde aynı anda nasıl çalışı olduğunu açıklar. Üç bağlamın her biri için ilgili konum, konum veya değerlendirmeyi açıklar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
