---
title: Ortak Dil Çalışma Zamanı İfade Değerlendiricisi Yazma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712319"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Ortak bir dil çalışma zamanı ifade değerlendiricisi yazma
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 İfade değerlendiricisi (EE), hata ayıklama altyapısının (DE) debugged kodu üreten programlama dilinin sözdizimini ve semantiğini işleyen bir parçasıdır. İfadeler bir programlama dili bağlamında değerlendirilmelidir. Örneğin, bazı dillerde "A+B" ifadesi "A ve B toplamı" anlamına gelir. Diğer dillerde, aynı ifade "A veya B" anlamına gelebilir. Bu nedenle, Visual Studio IDE'de ayrışacak nesne kodu oluşturan her programlama dili için ayrı bir EE yazılmalıdır.

 Visual Studio hata ayıklama paketinin bazı yönleri kodu programlama dili bağlamında yorumlamalıdır. Örneğin, yürütme bir kesme noktasında durduğunda, kullanıcının **Bir İzleme** penceresine yazdığı tüm ifadeler değerlendirilmeli ve görüntülenmelidir. Kullanıcı, bir ifadeyi **Bir İzleme** penceresine veya **Hemen** penceresine yazarak yerel bir değişkenin değerini değiştirebilir.

## <a name="in-this-section"></a>Bu bölümde
 [Ortak dil çalışma süresi ve ifade değerlendirmesi](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Özel programlama dilini Visual Studio IDE'ye entegre ederken, özel dil bağlamında ifadeleri değerlendirebilen bir EE yazmanın hata ayıklama motoru yazmadan bir Microsoft ara dili (MSIL) derlemenize olanak sağladığını açıklar.

 [İfade değerlendirici mimarisi](../../extensibility/debugger/expression-evaluator-architecture.md) Gerekli EE arabirimlerinin nasıl uygulanacağını ve ortak dil çalışma zamanı simge sağlayıcısını (SP) ve bağlayıcı arabirimlerini nasıl çağıracağını tartışır.

 [İfade değerlendiricisi kaydetme](../../extensibility/debugger/registering-an-expression-evaluator.md) EE'nin kendisini hem ortak dil çalışma zamanı hem de Visual Studio çalışma zamanı ortamlarına sahip bir sınıf fabrikası olarak kaydetmesi gerektiğini belirtir.

 [İfade değerlendiricisi uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md) Bir ifadeyi değerlendirme işleminin hata ayıklama altyapısını (DE), sembol sağlayıcısını (SP), bağlayıcı nesnesini ve ifade değerlendiricisi (EE) nasıl içerdiğini açıklar.

 [Yerel leri görüntüleyin](../../extensibility/debugger/displaying-locals.md) Yürütme durakladığında, hata ayıklama paketinin yerel değişkenlerin ve bağımsız değişkenlerin listesini almak için DE'yi nasıl aradığını açıklar.

 [Saat penceresi ifadesini değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Visual Studio hata ayıklama paketinin izleme listesindeki her ifadenin geçerli değerini belirlemek için DE'yi nasıl çağırdığını belgeler.

 [Yerel bir değer değiştirme](../../extensibility/debugger/changing-the-value-of-a-local.md) Yerel bir değer değiştirirken, Yerel pencerenin her satırının yerel bir ada, türü ve geçerli değerini sağlayan ilişkili bir nesnesi olduğunu açıklar.

 [Tür görselleştiricilerini ve özel görüntüleyicileri uygulama](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Tür görüntüleyicileri ve özel görüntüleyicileri desteklemek için hangi bileşen tarafından uygulanması gerektiğini açıklar.

## <a name="see-also"></a>Ayrıca bkz.
 [Visual Studio hata ayıklama genişletilebilirlik](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
