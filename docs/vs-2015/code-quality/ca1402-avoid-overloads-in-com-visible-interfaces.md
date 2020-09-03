---
title: 'CA1402: COM görünebilir arabirimlerde aşırı yüklerini önleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5c1e3af0e35bf92d72e853948c455893b417998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534946"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: COM görünebilir arabirimler içinde aşırı yüklemelerden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bileşen nesne modeli (COM) görünür arabirimi, aşırı yüklenmiş yöntemleri bildirir.

## <a name="rule-description"></a>Kural Tanımı
 Aşırı yüklenmiş yöntemler COM istemcilerine maruz kaldığında, sadece ilk yöntem aşırı yüklemesi adını korur. Sonraki aşırı yüklemeler, ada bir alt çizgi karakteri olan ' _ ' ve aşırı yükleme bildiriminin sırasına karşılık gelen bir tamsayı eklenerek benzersiz olarak yeniden adlandırılır. Örneğin, aşağıdaki yöntemleri göz önünde bulundurun.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Bu yöntemler aşağıdaki gibi COM istemcilerine sunulur.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6 COM istemcileri, ad içinde bir alt çizgi kullanarak arabirim yöntemleri uygulayamaz.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, aşırı yüklenmiş yöntemleri adların benzersiz olması için yeniden adlandırın. Alternatif olarak, erişilebilirliği `internal` ( `Friend` ın) olarak değiştirerek [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] veya <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> özniteliğini olarak ayarlayarak, arabirimi com 'a görünmez hale getirin `false` .

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, kuralı ve kuralı karşılayan bir arabirimi ihlal eden bir arabirim gösterilmektedir.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: COM görünebilir türler içinde statik üyelerden kaçının](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Derlemeleri ComVisibleAttribute ile işaretleyin](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen kod](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [uzun veri türüyle](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) birlikte çalışma
