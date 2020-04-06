---
title: Visual Studio Debugger Genişletilebilirlik | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712509"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio hata ayıklama genişletilebilirlik
Visual Studio, programınızdaki hataları izlemek için güçlü ve kullanımı kolay bir araç sağlayan tamamen etkileşimli bir kaynak kod ayıklayıcı içerir. Hata ayıklama, Visual Basic, C#, C/C++ve JavaScript için tam destek vardır. Ancak, Microsoft [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [Download Center'dan](https://www.microsoft.com/download/details.aspx?id=21835)edinilebilen , diğer programlama dilleri aynı zengin özelliklere sahip hata ayıklamada desteklenebilir.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Hata ayıklama, hata ayıklama nın sırayla debugged olan dile özgü hata ayıklama bileşenleriiçin ortak ön uç (yani, kullanıcı arabirimi) olduğunu. Yeni diller için hata ayıklamanın [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desteği için gereken tek şey hata ayıklama altyapısı (DE) gibi gerekli arka uç bileşenlerini oluşturmaktır. Bu noktada [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] devreye girer.

 Yeni [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] bir DE oluşturmak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için gereken tüm öğelere tam bir başvuru içerir. Buna ek olarak, başlamak yardımcı olacak örnekler ve öğreticiler vardır.

 Hata ayıklama desteğine sahip bir dil proje sisteminin tam bir örneği için [IronPython örneğine](https://www.microsoft.com/download/details.aspx?id=55984)bakın.

 Aşağıdaki bölümlerde hata ayıklamanın [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]nasıl genişletilen .

## <a name="in-this-section"></a>Bu bölümde
 [Başlayın](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ayıklama'nın neler sunduğunu ve SDK'nın nasıl yüklenirolduğunu açıklar.

 [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md) Programınızı DE'ye hazırlamaktan DE'yi ayırmaya kadar özel DE işlemini belgeler.

 [CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Bir ifade değerlendiricisi yazmanız gerekip gerekmediğini açıklar.

 [Hata ayıklama motoru uygulama stratejisi ni seçin](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) DE'nizi nasıl uygulayacağınızı tartışır.

 [Referans](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ayıklama API'sini belgeler.

 [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md) Ortak bir dil çalışma zamanı ifade değerlendirici örneği ve hata ayıklama motoru örneği bağlantıları içerir.
