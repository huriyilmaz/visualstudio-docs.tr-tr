---
title: 'CA1801: Kullanılmayan parametreleri gözden geçir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: caf1ec865d604545940b0a5442947ef61bd60f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671525"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Kullanılmayan parametreleri gözden geçir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1801: Kullanılmayan parametreleri gözden geçirme](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Bozuk olmayan-üye, yaptığınız değişiklikten bağımsız olarak, derleme dışında görünür değilse.<br /><br /> Parçalama-üyeyi, gövdesi içinde parametresini kullanacak şekilde değiştirirseniz.<br /><br /> Parçalama-parametreyi kaldırırsanız ve derleme dışında görünür hale gelir.|

## <a name="cause"></a>Sebep
 Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir. Bu kural aşağıdaki yöntemleri incelemez:

- Bir temsilci tarafından başvurulan Yöntemler.

- Olay işleyicileri olarak kullanılan yöntemler.

- @No__t_0 (Visual Basic `MustOverride`) değiştiricisiyle belirtilen Yöntemler.

- @No__t_0 (Visual Basic `Overridable`) değiştiricisiyle belirtilen Yöntemler.

- @No__t_0 (Visual Basic `Overrides`) değiştiricisiyle belirtilen Yöntemler.

- @No__t_0 (Visual Basic `Declare` ifadesiyle) değiştiricisiyle belirtilen Yöntemler.

## <a name="rule-description"></a>Kural Tanımı
 Yöntem gövdesinde kullanılmayan sanal olmayan metotlarda bulunan parametreleri gözden geçirin ve bunlara erişmek için hata etrafında doğruluk olmadığından emin olun. Kullanılmayan parametreler bakım ve performans maliyetleri doğurur.

 Bazen bu kuralın ihlali yönteminde bir uygulama hatasına işaret edebilir. Örneğin, parametresi metot gövdesinde kullanılmış olmalıdır. Geriye dönük uyumluluk nedeniyle parametrenin mevcut olması halinde bu kuralın uyarılarını gizleyin.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için kullanılmayan parametreyi (bir son değişiklik) kaldırın veya yöntem gövdesinde (kırılmamış değişiklik) parametreyi kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Daha önce sevk edilen kodun bir uyarı olması için bu kuraldan daha önce sevkedilme bir uyarı görüntülenmesini güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte iki yöntem gösterilmektedir. Bir yöntem kuralı çiğneniyor ve diğer yöntem kuralı karşılar.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Örneklendirilmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
