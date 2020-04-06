---
title: Hata Ayıklama genişletme yol haritası | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713141"
---
# <a name="roadmap-for-extending-the-debugger"></a>Hata ayıklamayı genişletmek için yol haritası
Bu dokümantasyon, hata ayıklamanın [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] .'la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]genişletilmesi için kılavuz ve başvuru bilgileri sağlar.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hata ayıklama belgeleri örnekleri, kapsamlı bir başvuru ve hata ayıklama özelleştirmek için tipik yollar gösteren çeşitli temsili senaryolar içerir.

 Derleyiciniz ve çıktısı, ürününde hata ayıklama ayarlamak için nelerin gerekli olduğunu belirler. Derleyiciniz:

- Windows yerel işletim sistemini hedefler ve bir *. PDB* dosyası, yerel kod hata ayıklama motoru (DE), entegre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]olan programları hata ayıklama olabilir. Bir DE veya ifade değerlendiricisi uygulamanız gerekmez. İfade değerlendiricisi C++ programlama dilinin sözdizimi için yazılmıştır.

- Microsoft ara dil (MSIL) çıktısı üretir, yönetilen kod hata ayıklama motoru DE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ile programları hata ayıklama, aynı zamanda entegre edebilirsiniz. Bu nedenle, yalnızca bir ifade değerlendirici uygulamak gerekir. Örnek bir ifade değerlendirici sizin için sağlanmaktadır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   [İfade değerlendirmesi](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [İfadeleri değerlendirme](../../extensibility/debugger/evaluating-expressions.md)

   [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)

   [Kesme modunda ifade değerlendirmesi](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Ortak bir dil çalışma zamanı ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Özel bir işletim sistemini veya başka bir çalışma zamanı ortamını hedeflerseniz, kendi DE'nizi yazmanız gerekir. ATL COM kullanarak basit bir DE oluşturan bir öğretici sağlanır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Öğretici: ATL COM kullanarak hata ayıklama motoru oluşturun](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Liman tedarikçisi uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Ayrıca bkz.
- [başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
