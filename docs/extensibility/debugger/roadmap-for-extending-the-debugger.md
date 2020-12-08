---
title: Hata ayıklayıcıyı genişletmek için yol haritası | Microsoft Docs
description: Visual Studio hata ayıklama belgeleri örnek, bir başvuru ve hata ayıklayıcıyı özelleştirmenin tipik yollarını gösteren çeşitli senaryolar içerir.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 2574fe76faadf4284088c0d47592d0c5ba0d38f9
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848345"
---
# <a name="roadmap-for-extending-the-debugger"></a>Hata ayıklayıcıyı genişletmek için yol haritası
Bu belge [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] , hata ayıklayıcıyı ile genişletmek için kılavuz ve başvuru bilgileri sağlar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hata ayıklama belgelerinin örnekleri, kapsamlı bir başvuru ve hata ayıklayıcıyı özelleştirmenin tipik yollarını gösteren çeşitli temsili senaryolar bulunur.

 Derleyicinizi ve çıktısı, ürününüzün hata ayıklamayı ayarlamak için gerekenleri tespit ediyor. Derleyicinizi:

- Windows yerel işletim sistemini hedefler ve a yazar *. PDB* dosyası, ile tümleştirilmiş yerel kod hata ayıklama altyapısı (de) ile programlarda hata ayıklaması yapabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bir DE veya ifade değerlendirici uygulamanız gerekmez. İfade değerlendiricisi, C++ programlama dilinin sözdizimi için yazılmıştır.

- Microsoft ara dili (MSIL) çıkışı üretir, yönetilen kod hata ayıklama altyapısı ile, ayrıca ile tümleştirilmiş programlarda hata ayıklaması yapabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu nedenle, yalnızca bir ifade değerlendirici uygulamanız gerekir. Sizin için örnek bir ifade değerlendirici sunulmaktadır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   [İfade değerlendirmesi](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [İfadeleri değerlendirme](../../extensibility/debugger/evaluating-expressions.md)

   [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md)

   [Kesme modunda ifade değerlendirmesi](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Ortak dil çalışma zamanı ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Özel bir işletim sistemini veya diğer bir çalışma zamanı ortamını hedefler, kendi DE yazmanız gerekir. ATL COM kullanarak basit bir DE oluşturan bir öğretici sunulmaktadır. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

   [Özel hata ayıklama altyapısı oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Öğretici: ATL COM kullanarak hata ayıklama altyapısı oluşturma](/previous-versions/bb147024(v=vs.90))

   [Bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Örnekler](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlama](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)