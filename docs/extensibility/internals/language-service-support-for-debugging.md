---
title: Hata ayıklama için dil hizmeti desteği | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707431"
---
# <a name="language-service-support-for-debugging"></a>Hata Ayıklama için Dil Hizmeti Desteği
Bir dil hizmeti, arabirim aracılığıyla bir hata ayıklayıcıyı destekleyen özellikler sağlayabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> . Bu özellikler, kesme noktalarını doğrulamayı ve **oto** penceresine ifadelerin bir listesini sağlamayı içerir.

 Ancak, dilinizdeki hata ayıklaması için bir ifade değerlendiricisi olması gerekir. İfade değerlendirici, hata ayıklama sırasında değerlerin üretilmesi için ifadelerin hesaplanmasından sorumludur. CLR ifadesi değerlendiricileri uygulama hakkında daha fazla bilgi için lütfen bkz:

- [CLR Ifadesi değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Yönetilen Ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Derleyici çıkışı
 Derleyicinin türü, dilinize yönelik hata ayıklamayı uygulamak için ne yapmanız gerektiğini belirler. Derleyici Windows işletim sistemini hedefliyorsa ve bir. pdb dosyası yazıyorsa, Visual Studio ile tümleştirilmiş yerel kod hata ayıklama altyapısı ile programlarda hata ayıklaması yapabilirsiniz. Derleyici Microsoft ara dili (MSIL) üretirse, Visual Studio ile tümleştirilmiş olan yönetilen kod hata ayıklama altyapısı ile programlarda hata ayıklaması yapabilirsiniz. Derleyicisinde özel bir işletim sistemi veya farklı bir çalışma zamanı ortamı hedeflerse, kendi hata ayıklama motorunuzu yazmanız gerekir.

 Diliniz için hata ayıklamayı uygulama hakkında daha fazla bilgi için bkz. Visual Studio hata ayıklama SDK 'sında [çalışmaya](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) başlama.
