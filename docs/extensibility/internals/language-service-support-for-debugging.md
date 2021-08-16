---
title: Hata ayıklama için dil hizmeti desteği | Microsoft Docs
description: Visual Studio 'de hata ayıklama desteği sağlayan IVsLanguageDebugInfo arabirimindeki dil hizmeti özellikleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 72cac3ff7768d49f66c87b569312253669d735fa2e64fdb895b51ff29aae2ca4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375903"
---
# <a name="language-service-support-for-debugging"></a>Hata Ayıklama için Dil Hizmeti Desteği
Bir dil hizmeti, arabirim aracılığıyla bir hata ayıklayıcıyı destekleyen özellikler sağlayabilir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> . Bu özellikler, kesme noktalarını doğrulamayı ve **oto** penceresine ifadelerin bir listesini sağlamayı içerir.

 Ancak, dilinizdeki hata ayıklaması için bir ifade değerlendiricisi olması gerekir. İfade değerlendirici, hata ayıklama sırasında değerlerin üretilmesi için ifadelerin hesaplanmasından sorumludur. CLR ifadesi değerlendiricileri uygulama hakkında daha fazla bilgi için lütfen bkz:

- [CLR Ifadesi değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Yönetilen Ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Derleyici çıkışı
 Derleyicinin türü, dilinize yönelik hata ayıklamayı uygulamak için ne yapmanız gerektiğini belirler. derleyici Windows işletim sistemini hedefliyorsa ve bir. pdb dosyası yazıyorsa, Visual Studio tümleştirilmiş yerel kod hata ayıklama altyapısı ile programlarda hata ayıklaması yapabilirsiniz. Derleyici Microsoft ara dili (MSIL) üretirse, Visual Studio ile tümleştirilmiş, yönetilen kod hata ayıklama altyapısı ile programlarda hata ayıklaması yapabilirsiniz. Derleyicisinde özel bir işletim sistemi veya farklı bir çalışma zamanı ortamı hedeflerse, kendi hata ayıklama motorunuzu yazmanız gerekir.

 diliniz için hata ayıklamayı uygulama hakkında daha fazla bilgi için, bkz. Visual Studio hata ayıklama SDK 'sını [kullanmaya](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) başlama.
