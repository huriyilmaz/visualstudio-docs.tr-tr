---
title: Ortak Dil Çalışma Zamanı İfade Değerlendiricisi | Microsoft Docs
description: Hata ayıklanan kod dilindeki ifadeleri değerlendiren ortak dil çalışma zamanı için bir ifade değerlendiricisi yazma hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: f7121e28284044ce54d6aa8ffbde7f87edd60e97
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125185"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Ortak dil çalışma zamanı ifade değerlendiricisi yazma
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 İfade değerlendirici (EE), hata ayıklama kodunu üreten programlama dilinin söz dizimlerini ve semantiklerini ele alan bir hata ayıklama altyapısının (DE) parçasıdır. İfadelerin bir programlama dili bağlamında değerlendirilmesi gerekir. Örneğin, bazı dillerde "A+B" ifadesi "A ve B'nin toplamı" anlamına gelir. Diğer dillerde aynı ifade "A veya B" anlamına geliyor olabilir. Bu nedenle, EE IDE'de hata ayıklamak için nesne kodu oluşturan her programlama dili için ayrı bir Visual Studio gerekir.

 Hata ayıklama paketinin Visual Studio programlama dili bağlamında kodu yorumlaması gerekir. Örneğin, yürütme bir kesme noktası üzerinde durdurulduğu zaman, kullanıcının bir  İzleme penceresine yazmış olduğu ifadelerin değerlendirilmesi ve görüntülenebilir. Kullanıcı, bir İzleme penceresine veya Anında pencereye bir ifade **yazarak** yerel değişkenin **değerini değiştirebilir.**

## <a name="in-this-section"></a>Bu bölümde
 [Ortak dil çalışma zamanı ve ifade değerlendirmesi](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Özel programlama dilini Visual Studio IDE ile tümleştirerek özel dil bağlamında ifadeleri değerlendirebilecek bir EE yazmanın hata ayıklama altyapısı yazmadan bir Microsoft ara diline (MSIL) derlemenizi mümkün kıl olduğunu açıklar.

 [İfade değerlendirici mimarisi](../../extensibility/debugger/expression-evaluator-architecture.md) Gerekli ağ arabirimlerini uygulama ve ortak EE çalışma zamanı sembol sağlayıcısı (SP) ve bağlayıcı arabirimlerini çağırmayı açıklar.

 [İfade değerlendiriciyi kaydetme](../../extensibility/debugger/registering-an-expression-evaluator.md) Uygulamanın EE hem ortak dil çalışma zamanı hem de çalışma zamanı ortamlarına sahip bir sınıf Visual Studio kaydetmesi gerektiğini belirtir.

 [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md) Bir ifadeyi değerlendirme işleminin hata ayıklama altyapısını (DE), sembol sağlayıcısını (SP), bağlayıcı nesnesini ve ifade değerlendiriciyi (EE) nasıl dahil olduğunu açıklar.

 [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md) Yürütme duraklatılırken hata ayıklama paketinin yerel değişkenlerin ve bağımsız değişkenlerin listesini almak için DE'nin nasıl çağrılmasına neden olduğunu açıklar.

 [Saat penceresi ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Hata ayıklama Visual Studio izleme listesinde her bir ifadenin geçerli değerini belirlemek için DE'nin nasıl çağrıl olduğunu belgeler.

 [Yerel değeri değiştirme](../../extensibility/debugger/changing-the-value-of-a-local.md) Yerel değeri değiştirerek, Yereller penceresinin her bir satırı, yerelin adını, türünü ve geçerli değerini sağlayan ilişkili bir nesnesine sahip olduğunu açıklar.

 [Tür görselleştiricileri ve özel görüntüleyicileri uygulama](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Tür görselleştiricileri ve özel görüntüleyicileri desteklemek için hangi bileşenin hangi arabirim tarafından uygulanması gerektiğini açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [Visual Studio ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
