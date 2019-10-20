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
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668901"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Yerel kaynaklara sahip olan türler atılabilir olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir tür, <xref:System.IntPtr?displayProperty=fullName> alanı, <xref:System.UIntPtr?displayProperty=fullName> alanı veya <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> alanı referans, ancak <xref:System.IDisposable?displayProperty=fullName> uygulamaz.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural <xref:System.IntPtr>, <xref:System.UIntPtr> ve <xref:System.Runtime.InteropServices.HandleRef> alanlarının yönetilmeyen kaynaklara işaretçiler depodığını varsayar. Yönetilmeyen kaynakları ayıran türler, arayanların bu kaynakları talep üzerine serbest bırakmasına ve kaynakları tutan nesnelerin ömrünü kısaltmasına izin vermek için <xref:System.IDisposable> ' i uygulamalıdır.

 Yönetilmeyen kaynakları temizlemek için önerilen tasarım modelinde, sırasıyla <xref:System.Object.Finalize%2A?displayProperty=fullName> yöntemi ve <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> yöntemi kullanılarak bu kaynakları serbest bırakmak için örtülü ve açık bir yol sağlamaktır. Çöp toplayıcı, nesnenin artık erişilebilir olmadığı belirlendikten sonra bir nesnenin <xref:System.Object.Finalize%2A> yöntemini bir belirsiz zamanda çağırır. @No__t_0 çağrıldıktan sonra, nesneyi serbest bırakmak için ek bir atık toplama gerekir. @No__t_0 yöntemi, çağıranın, atık toplayıcısına ayrıldıysa kaynaklardan daha önce kaynak olarak açıkça serbest bırakılacağını sağlar. Yönetilmeyen kaynakları temizledikten sonra, <xref:System.IDisposable.Dispose%2A> çöp toplayıcısının <xref:System.Object.Finalize%2A> artık çağrılması gerektiğini bilmesini sağlamak için <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodunu çağırmalıdır; Bu, ek çöp toplama gereksinimini ortadan kaldırır ve nesnenin yaşam süresini kısaltır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.IDisposable> ' ı uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Tür yönetilmeyen bir kaynağa başvurmadığından, bu kuraldan bir uyarının bastırmasının güvenli hale gelir. Aksi takdirde, <xref:System.IDisposable> uygulamadan bir uyarı bastırmayın, yönetilmeyen kaynakların kullanılamaz hale gelmesine veya az kullanılmamasına neden olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, yönetilmeyen bir kaynağı temizlemek için <xref:System.IDisposable> uygulayan bir türü gösterir.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2115: Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: GC.SuppressFinalize öğesini doğru çağırın](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Atılabilir alanlara sahip olan türler atılabilir olmalıdır](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Ayrıca Bkz.
  [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
