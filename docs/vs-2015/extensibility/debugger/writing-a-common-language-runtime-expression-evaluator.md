---
title: Ortak dil çalışma zamanı Ifade Değerlendiricisi yazma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 961a4d646a61fedda381f9451902b3bcdcc956d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64818379"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Ortak Dil Çalışma Zamanı İfade Değerlendiricisi Yazma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İfade değerlendirici (EE), hata ayıklamakta olan kodu üreten programlama dilinin söz dizimini ve semantiğini işleyen bir hata ayıklama altyapısının (DE) parçasıdır. İfadeler bir programlama dilinin bağlamı içinde değerlendirilmelidir. Örneğin, bazı dillerde "A + B" ifadesi "A ve B toplamı" anlamına gelir. Diğer dillerde de aynı ifade "A veya B" anlamına gelebilir. Bu nedenle, Visual Studio IDE 'de hataları ayıklanmak üzere nesne kodu üreten her bir programlama dili için ayrı bir EE yazılması gerekir.  
  
 Visual Studio hata ayıklama paketinin bazı yönleri, programlama dilinin bağlamındaki kodu yorumlamalıdır. Örneğin, yürütme bir kesme noktasında durarsa, kullanıcının bir **Gözcü** penceresinde girdiği tüm ifadeler değerlendirilmeli ve gösterilmelidir. Ayrıca, Kullanıcı bir **Gözcü** penceresine veya **hemen** penceresine bir ifade yazarak yerel değişkenin değerini değiştirebilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Ortak Dil Çalışma Zamanı ve İfade Değerlendirme](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Özel programlama dilini Visual Studio IDE ile tümleştirdiğinizde, özel dil bağlamı dahilinde ifadeleri değerlendirebilen bir EE yazmak, bir hata ayıklama altyapısı yazmadan bir Microsoft ara dili 'ne (MSIL) derlemenize olanak tanır.  
  
 [İfade Değerlendirici Mimarisi](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Gerekli EE arabirimlerinin nasıl uygulanacağını ve ortak dil çalışma zamanı sembol sağlayıcısı (SP) ve Ciltçi arabirimlerini çağırmayı açıklar.  
  
 [İfade Değerlendiricisi Kaydetme](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 EE 'ın kendisini hem ortak dil çalışma zamanı hem de Visual Studio çalışma zamanı ortamlarına sahip bir sınıf fabrikası olarak kaydetmesi gerektiğini not edin.  
  
 [ifade Değerlendiricisi Uygulama](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Bir ifadeyi değerlendirme işleminin hata ayıklama altyapısını (DE), sembol sağlayıcısını (SP), Ciltçi nesnesini ve ifade değerlendiricisi (EE) nasıl içerdiğini açıklar.  
  
 [Yerel Öğeleri Görüntüleme](../../extensibility/debugger/displaying-locals.md)  
 Yürütme durakladığında, hata ayıklama paketinin yerel değişkenlerin ve bağımsız değişkenlerin bir listesini almak için DE ' yi çağırdığını açıklar.  
  
 [Gözcü Penceresi İfadesini Değerlendirme](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Visual Studio hata ayıklama paketinin, izleme listesindeki her bir ifadenin geçerli değerini belirlemede DE nasıl çağırtuğılarından oluşan belgeler.  
  
 [Yerel Bir Öğenin Değerini Değiştirme](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Yerel değerin değerinin değişmekte olduğu, Yereller penceresinin her satırının, bir yerel öğenin adını, türünü ve geçerli değerini sağlayan ilişkili bir nesnesi olduğunu açıklar.  
  
 [Tür Görselleştiricileri ve Özel Görüntüleyiciler Uygulama](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Tür görselleştiricilerin ve özel görüntüleyicilerin hangi bileşen tarafından hangi arabirimde uygulanması gerektiği açıklanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Hata Ayıklayıcı Genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
