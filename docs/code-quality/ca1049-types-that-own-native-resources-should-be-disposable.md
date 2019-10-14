---
title: 'CA1049: Yerel kaynaklara sahip türler atılabilir olmalıdır'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: 03b8d222fc2349022ef324c9905279677fc86849
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306124"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Yerel kaynaklara sahip türler atılabilir olmalıdır

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni

Bir tür, <xref:System.IntPtr?displayProperty=fullName> alanı, <xref:System.UIntPtr?displayProperty=fullName> alanı veya <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> alanı referans, ancak <xref:System.IDisposable?displayProperty=fullName> uygulamaz.

## <a name="rule-description"></a>Kural açıklaması

Bu kural <xref:System.IntPtr>, <xref:System.UIntPtr> ve <xref:System.Runtime.InteropServices.HandleRef> alanlarının yönetilmeyen kaynaklara işaretçiler depodığını varsayar. Yönetilmeyen kaynakları ayıran türler, arayanların bu kaynakları talep üzerine serbest bırakmasına ve kaynakları tutan nesnelerin ömrünü kısaltmasına izin vermek için <xref:System.IDisposable> ' i uygulamalıdır.

Yönetilmeyen kaynakları temizlemek için önerilen tasarım deseninin, sırasıyla <xref:System.Object.Finalize%2A?displayProperty=fullName> yöntemini ve <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> yöntemini kullanarak bu kaynakları serbest bırakmak için hem örtük hem de açık bir yol sağlamaktır. Çöp toplayıcı, nesnenin artık erişilebilir olmadığı belirlendikten sonra bir nesnenin <xref:System.Object.Finalize%2A> yöntemini çağırır. @No__t-0 çağrıldıktan sonra, nesneyi serbest bırakmak için ek bir atık toplama gerekir. @No__t-0 yöntemi, çağıranın, atık toplayıcıya ayrılmışsa kaynakların serbest bırakılması durumunda, kaynakların isteğe bağlı olarak açıkça serbest bırakılacağını sağlar. Yönetilmeyen kaynakları temizledikten sonra, Atık toplayıcısının <xref:System.Object.Finalize%2A> ' nin artık çağrılması gerektiğini bilmesini sağlamak için <xref:System.IDisposable.Dispose%2A> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodunu çağırmalıdır. Bu, ek çöp toplama gereksinimini ortadan kaldırır ve nesnenin yaşam süresini kısaltır.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
Bu kural ihlalini onarmak için <xref:System.IDisposable> ' ı uygulayın.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor
Tür yönetilmeyen bir kaynağa başvurmadığından, bu kuraldan bir uyarının bastırmasının güvenli hale gelir. Aksi takdirde, bu kuraldan bir uyarıyı bastırmayın çünkü @no__t uygulama hatası, yönetilmeyen kaynakların kullanılamaz hale gelmesine veya az kullanılmamasına neden olabilir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, yönetilmeyen bir kaynağı temizlemek için <xref:System.IDisposable> uygulayan bir türü gösterir.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>İlgili kurallar
[CA2115: GC 'yi çağırın. Yerel kaynaklar kullanılırken KeepAlive @ no__t-0

[CA1816: GC 'yi çağırın. SuppressFinalize doğru @ no__t-0

[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir @ no__t-0

[CA1001: Atılabilir alanlara sahip olan türler atılabilir @ no__t-0 olmalıdır

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kaynakları Temizleme](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose Deseni](/dotnet/standard/design-guidelines/dispose-pattern)