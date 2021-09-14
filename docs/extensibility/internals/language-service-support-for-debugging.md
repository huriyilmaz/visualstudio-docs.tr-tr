---
title: Hata Ayıklama için Dil Hizmeti Desteği | Microsoft Docs
description: IVsLanguageDebugInfo arabiriminde, Visual Studio'da hata ayıklama desteği sağlayan dil hizmeti özellikleri hakkında Visual Studio.
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
ms.openlocfilehash: f3626b7d3f558e9adc7431c21567a74bfe7f0df5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626126"
---
# <a name="language-service-support-for-debugging"></a>Hata Ayıklama için Dil Hizmeti Desteği
Dil hizmeti, arabirim aracılığıyla hata ayıklayıcıyı destekleyen özellikler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> sağlar. Bu özellikler kesme noktaları doğrulamayı ve Otomatikler penceresine bir ifade **listesi sağlamaktır.**

 Ancak dilinizin hata ayıklaması için bir ifade değerlendiriciniz gerekir. İfade değerlendirici, hata ayıklama sırasında değer üretmek için ifadelerin değerlendirilmesinden sorumludur. CLR ifade değerlendiricilerini uygulama hakkında bilgi için lütfen bkz:

- [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Yönetilen İfade Değerlendirici Örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Derleyici Çıkışı
 Derleyici türü, diliniz için hata ayıklamayı uygulamak için ne ihtiyacınız olduğunu belirler. Derleyiciniz bir .pdb Windows işletim sistemini hedeflese ve bir .pdb dosyası yazarsa, programlarla tümleşik yerel kod hata ayıklama altyapısıyla programlarda hata Visual Studio. Derleyiciniz Microsoft ara dili (MSIL) üretirse, programlarda hata ayıklamayı yönetilen kod hata ayıklama altyapısıyla da Visual Studio. Derleyiciniz özel bir işletim sistemini veya farklı bir çalışma zamanı ortamını hedeflese kendi hata ayıklama altyapınızı yazmanız gerekir.

 Dilinize hata ayıklama uygulama hakkında daha fazla bilgi için hata [ayıklama SDK'Başlarken'Visual Studio](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) bakın.
