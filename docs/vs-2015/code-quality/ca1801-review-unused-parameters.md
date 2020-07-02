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
ms.openlocfilehash: c87836f99684c7e16c022e3e9f15bf546ba82d62
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547790"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Kullanılmayan parametreleri gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1801: Kullanılmayan parametreleri gözden geçirme](/visualstudio/code-quality/ca1801-review-unused-parameters).

|Öğe|Değer|
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Bozuk olmayan-üye, yaptığınız değişiklikten bağımsız olarak, derleme dışında görünür değilse.<br /><br /> Parçalama-üyeyi, gövdesi içinde parametresini kullanacak şekilde değiştirirseniz.<br /><br /> Parçalama-parametreyi kaldırırsanız ve derleme dışında görünür hale gelir.|

## <a name="cause"></a>Nedeni
 Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir. Bu kural aşağıdaki yöntemleri incelemez:

- Bir temsilci tarafından başvurulan Yöntemler.

- Olay işleyicileri olarak kullanılan yöntemler.

- `abstract`( `MustOverride` Visual Basic) değiştiricisiyle belirtilen Yöntemler.

- `virtual`( `Overridable` Visual Basic) değiştiricisiyle belirtilen Yöntemler.

- `override`( `Overrides` Visual Basic) değiştiricisiyle belirtilen Yöntemler.

- `extern`( `Declare` Visual Basic) değiştiricisiyle belirtilen Yöntemler.

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
 [CA1811: Çağırılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Örneklenmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Kullanılmayan yerelleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
