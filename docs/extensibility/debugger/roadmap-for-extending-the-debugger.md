---
title: Hata AyıklayıcıSını Genişletme yol | Microsoft Docs
description: Visual Studio ayıklama belgelerinde örnek, başvuru ve hata ayıklayıcıyı özelleştirmenin tipik yollarını gösteren çeşitli senaryolar yer almaktadır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 00da6cede11993e0b498978bc9a18ec0e21781b4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634657"
---
# <a name="roadmap-for-extending-the-debugger"></a>Hata ayıklayıcısını genişletmek için yol haritası
Bu belge, ile hata ayıklayıcısını genişletmek için kılavuz [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] ve başvuru bilgileri [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] sağlar.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama belgeleri örnekler, kapsamlı bir başvuru ve hata ayıklayıcıyı özelleştirmenin tipik yollarını gösteren çeşitli temsili senaryolar içerir.

 Derleyiciniz ve çıkışı, üründe hata ayıklamayı ayarlamak için gerekenleri belirler. Derleyiciniz:

- Yerel işletim Windows hedeflemektedir ve bir *yazar. PDB* dosyası; ile tümleştirilmiş yerel kod hata ayıklama altyapısı (DE) ile programlarda hata ayıklaması [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sabilirsiniz. DE veya ifade değerlendiricisi uygulama gerekli değil. İfade değerlendirici, C++ programlama dilinin söz dizimi için yazılır.

- Microsoft ara dili (MSIL) çıkışı üretir, programlarda hata ayıklaması da ile tümleşik olan yönetilen kod hata ayıklama altyapısı DE ile birlikte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanabilirsiniz. Bu nedenle, yalnızca bir ifade değerlendiricisi uygulama gerekir. Sizin için bir örnek ifade değerlendirici sağlanır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   [İfade değerlendirmesi](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [İfadeleri değerlendirme](../../extensibility/debugger/evaluating-expressions.md)

   [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)

   [Kesme modunda ifade değerlendirmesi](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Ortak dil çalışma zamanı ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Özel bir işletim sistemini veya başka bir çalışma zamanı ortamını hedefler, kendi DE'nizi yazmanız gerekir. ATL COM kullanarak basit bir DE oluşturan öğretici sağlanır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Öğretici: ATL COM kullanarak hata ayıklama altyapısı oluşturma](/previous-versions/bb147024(v=vs.90))

   [Bağlantı noktası sağlayıcı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)