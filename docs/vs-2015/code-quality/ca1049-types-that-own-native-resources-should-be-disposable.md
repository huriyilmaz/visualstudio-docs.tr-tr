---
title: 'CA1049: yerel kaynaklara sahip türler atılabilir olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49c56b98e3be01675c2c21cd11c2961dd75f4877
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546815"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Yerel kaynaklara sahip türler atılabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir tür bir <xref:System.IntPtr?displayProperty=fullName> alana, <xref:System.UIntPtr?displayProperty=fullName> alana veya <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> alana başvurur, ancak uygulamaz <xref:System.IDisposable?displayProperty=fullName> .

## <a name="rule-description"></a>Kural Tanımı
 Bu kural <xref:System.IntPtr> , <xref:System.UIntPtr> ve <xref:System.Runtime.InteropServices.HandleRef> alanlarının yönetilmeyen kaynaklara işaretçiler depodığını varsayar. Yönetilmeyen kaynakları ayıran türler, <xref:System.IDisposable> Arayanların bu kaynakları talep üzerine serbest bırakmasına ve kaynakları tutan nesnelerin yaşam sürelerini kısaltmasına imkan sağlamak için uygulamalıdır.

 Yönetilmeyen kaynakları temizlemek için önerilen tasarım deseninin, <xref:System.Object.Finalize%2A?displayProperty=fullName> sırasıyla yöntemi ve yöntemi kullanılarak bu kaynakları serbest bırakmak için hem örtük hem de açık bir yol sağlamaktır <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> . Çöp toplayıcı, <xref:System.Object.Finalize%2A> nesnenin artık erişilebilir olmadığı belirlendikten sonra bir nesnenin yöntemini belirsiz bir zamanda çağırır. Çağrıldıktan sonra <xref:System.Object.Finalize%2A> , nesneyi serbest bırakmak için ek bir atık toplama gerekir. <xref:System.IDisposable.Dispose%2A>Yöntemi, çağıranın kaynak atık toplayıcıya ayrıldıysa, kaynakların önceden açık şekilde kaynak serbest bırakıldığını sağlar. Yönetilmeyen kaynakları temizledikten sonra <xref:System.IDisposable.Dispose%2A> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> çöp toplayıcısının artık çağrılmamasına izin vermek için yöntemini çağırmalıdır <xref:System.Object.Finalize%2A> ; Bu, ek çöp toplama gereksinimini ortadan kaldırır ve nesnenin yaşam süresini kısaltır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için uygulamasını uygulayın <xref:System.IDisposable> .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tür yönetilmeyen bir kaynağa başvurmadığından, bu kuraldan bir uyarının bastırmasının güvenli hale gelir. Aksi takdirde, uygulama hatası <xref:System.IDisposable> yönetilmeyen kaynakların kullanılamaz hale gelmesine veya az kullanılmamasına neden olabileceğinden, bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.IDisposable> yönetilmeyen bir kaynağı temizlemek için uygulayan bir türü gösterir.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2115: Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize'ı doğru çağırın](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Atılabilen alanlara sahip türler atılabilir olmalıdır](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Ayrıca Bkz.
  [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
