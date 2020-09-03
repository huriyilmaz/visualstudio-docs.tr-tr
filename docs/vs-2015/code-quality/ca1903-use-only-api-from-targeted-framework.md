---
title: 'CA1903: hedeflenen çerçeveden yalnızca API kullan | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10649b4106a280089fd6b086167c7e92bff1300b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545255"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Yalnızca hedeflenen çerçeveden API kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1903: hedeflenen çerçeveden yalnızca API kullanma](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|Öğe|Değer|
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategori|Microsoft. taşınabilirlik|
|Yeni Değişiklik|Parçalama-dışarıdan görünen bir üyenin veya türün imzasına karşı harekete geçirildi.<br /><br /> Bir yöntemin gövdesinde Tetiklenmeyen-bölünmez.|

## <a name="cause"></a>Nedeni
 Üye veya tür, projenin hedeflenen çerçevesine dahil olmayan bir hizmet paketinde tanıtılan bir üye veya tür kullanıyor.

## <a name="rule-description"></a>Kural Tanımı
 Yeni Üyeler ve türler .NET Framework 2,0 Service Pack 1 ve 2, .NET Framework 3,0 Service Pack 1 ve 2 ve .NET Framework 3,5 Service Pack 1 ' de yer almaktadır. .NET Framework ana sürümlerini hedefleyen projeler, bu yeni API 'lerde istemeden bağımlılıklar alabilir. Bu bağımlılığı engellemek için bu kural, varsayılan olarak projenin hedef çerçevesine dahil olmayan yeni üyelerin ve türlerin kullanımları üzerinde ateşlenir.

 **Hedef Framework ve hizmet paketi bağımlılıkları**

|Öğe|Değer|
|-|-|
|Hedef Framework olduğunda|İçinde tanıtılan üyelerin kullanımları ateşlenir|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1 |
|.NET Framework 4|Yok|

 Projenin hedef çerçevesini değiştirmek için, bkz. [belirli bir .NET Framework sürümünü hedefleme](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Hizmet paketindeki bağımlılığı kaldırmak için, yeni üyenin veya türün tüm kullanımlarını kaldırın. Bu bir bilinçli bağımlılığı ise, uyarıyı gizleyin ya da bu kuralı kapatın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural, belirtilen hizmet paketinde bir bilinçli bağımlılığı değilse bu kuraldan bir uyarıyı bastırmayın. Bu durumda, uygulamanız bu hizmet paketinin yüklü olmadığı sistemlerde çalışmayabilir. Bu bir bilinçli bağımlılığıdır, uyarıyı gizleyin veya bu kuralı kapatın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek yalnızca .NET 2,0 hizmet paketi 1 ' de bulunan DateTimeOffset türünü kullanan bir sınıfı gösterir. Bu örnek, proje özelliklerindeki hedef Framework aşağı açılan listesinde 2,0 .NET Framework seçilmesini gerektirir.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, DateTimeOffset türünün kullanımlarını tarih saat türüyle değiştirerek daha önce açıklanan ihlalin düzeltir.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Belirli bir .NET Framework sürümünü hedefleyen](../ide/targeting-a-specific-dotnet-framework-version.md) [taşınabilirlik uyarıları](../code-quality/portability-warnings.md)
