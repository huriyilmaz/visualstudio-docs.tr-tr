---
title: Hata Ayıklama için Dil Hizmeti Desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707431"
---
# <a name="language-service-support-for-debugging"></a>Hata Ayıklama için Dil Hizmeti Desteği
Dil hizmeti, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> arabirim üzerinden hata ayıklama yı destekleyen özellikler sağlayabilir. Bu özellikler, kesme noktalarını doğrulamayı ve Otomatik **Ler** penceresine ifadelerin listesini sağlamayı içerir.

 Ancak, dilinizi hata ayıklamak için bir ifade değerlendiriciniz olması gerekir. İfade değerlendiricisi hata ayıklama sırasında değer üretmek için ifadeleri değerlendirmekten sorumludur. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen bkz:

- [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Yönetilen İfade Değerlendirici Örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Derleyici Çıktısı
 Derleyici türü, diliniz için hata ayıklama uygulamak için ne yapmanız gerektiğini belirler. Derleyiciniz Windows işletim sistemini hedef alıyor sa ve bir .pdb dosyası yazıyorsa, Visual Studio'ya entegre edilmiş yerel kod hata ayıklama motoruyla programları hata ayıklayabilirsiniz. Derleyiciniz Microsoft ara dili (MSIL) üretiyorsa, Visual Studio'ya da entegre edilmiş yönetilen kod hata ayıklama motoruyla programları hata ayıklayabilirsiniz. Derleyiciniz özel bir işletim sistemini veya farklı bir çalışma zamanı ortamını hedefliyorsa, kendi hata ayıklama motorunuzu yazmanız gerekir.

 Diliniz için hata ayıklama uygulaması hakkında daha fazla bilgi için Visual Studio Hata Ayıklama SDK'da [Başlarken](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) bölümüne bakın.
