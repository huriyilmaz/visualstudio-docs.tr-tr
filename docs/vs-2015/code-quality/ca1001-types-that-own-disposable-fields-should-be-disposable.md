---
title: 'CA1001: atılabilir alanlarının sahibi olan türler atılabilir olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dab4532f082bd81eaa7b812eb038c5957636d453
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548323"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Atılabilen alanlara sahip türler atılabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Not-tür, derlemenin dışında görünmüyorsa bölünmez.<br /><br /> Parçalama-tür derleme dışında görünüyorsa.|

## <a name="cause"></a>Nedeni
 Bir sınıf, türü olan bir örnek alanı bildirir ve uygular <xref:System.IDisposable?displayProperty=fullName> ve sınıfı uygulamaz <xref:System.IDisposable> .

## <a name="rule-description"></a>Kural Tanımı
 Bir sınıf, <xref:System.IDisposable> sahip olduğu yönetilmeyen kaynakların atılırken arabirimini uygular. Türü olan bir örnek alan <xref:System.IDisposable> , alanın yönetilmeyen bir kaynağa sahip olduğunu gösterir. Bir alanı, yönetilmeyen bir <xref:System.IDisposable> kaynağa dolaylı olarak bildiren ve arabirimini uygulaması gereken bir sınıf <xref:System.IDisposable> . Sınıf, hiçbir yönetilmeyen kaynağa doğrudan sahip değilse, bir Sonlandırıcı uygulamamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, yöntemini uygulayın <xref:System.IDisposable> ve öğesinden, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> <xref:System.IDisposable.Dispose%2A> alan yöntemini çağırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını ihlal eden bir sınıfı ve uygulayarak kuralını karşılayan bir sınıfı gösterir <xref:System.IDisposable> . Sınıf, hiçbir yönetilmeyen kaynağa doğrudan sahip olmadığından, sınıf bir Sonlandırıcı uygulamaz.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Atma metotları taban sınıf atmayı çağırmalıdır](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Yerel kaynaklara sahip türler atılabilir olmalıdır](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
