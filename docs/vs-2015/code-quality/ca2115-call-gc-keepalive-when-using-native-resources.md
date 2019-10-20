---
title: "CA2115: GC 'yi çağırın. Yerel kaynaklar kullanılırken KeepAlive | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0aa10cc453919a2a79ee6d3d46db95c19d8756e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658696"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Sonlandırıcıyı içeren bir tür içinde belirtilen bir yöntem, bir <xref:System.IntPtr?displayProperty=fullName> veya <xref:System.UIntPtr?displayProperty=fullName> alanına başvurur, ancak <xref:System.GC.KeepAlive%2A?displayProperty=fullName> çağırmaz.

## <a name="rule-description"></a>Kural Tanımı
 Yönetilen kodda kendisine daha fazla başvuru yoksa çöp toplama bir nesneyi sonlandırır. Nesnelere yönetilmeyen başvurular çöp toplamayı engellemez. Bu kural, yönetimsiz kod içinde kullanıldığı sırada yönetilmeyen kaynağın sonlandırılması nedeniyle oluşabilecek hataları algılar.

 Bu kural <xref:System.IntPtr> ve <xref:System.UIntPtr> alanlarının yönetilmeyen kaynaklara işaretçiler depolayabileceği varsayılır. Sonlandırıcının amacı, yönetilmeyen kaynakları serbest yönlendirtiğinden, bu, sonlandırıcının işaretçi alanları tarafından işaret edilen yönetilmeyen kaynağı serbest olarak kabul ettiği varsayılır. Bu kural ayrıca yöntemin yönetilmeyen kaynağa yönetilmeyen koda iletilmesi için işaretçi alanına başvuracağını varsayar.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için yöntemine <xref:System.GC.KeepAlive%2A> bir çağrı ekleyin ve bağımsız değişken olarak geçerli örneği (`this` içinde C# ve C++) geçirerek. Çağrıyı, nesnenin çöp toplamadan korunması gereken son kod satırından sonra konumlandırın. @No__t_0 çağrısından hemen sonra nesne, kendisine yönetilen başvuru olmadığı varsayılarak çöp toplama için hazır olarak kabul edilir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural, yanlış pozitiflere yol açabilecek bazı varsayımlar yapar. Şu durumlarda bu kuraldan bir uyarıyı güvenle gizleyebilirsiniz:

- Sonlandırıcı, yöntem tarafından başvurulan <xref:System.IntPtr> veya <xref:System.UIntPtr> alanının içeriğini serbest vermez.

- Yöntem <xref:System.IntPtr> veya <xref:System.UIntPtr> alanını yönetilmeyen koda iletmez.

  Diğer iletileri hariç tutarak dikkatle gözden geçirin. Bu kural, yeniden oluşturulması ve hata ayıklaması zor olan hataları algılar.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `BadMethod` `GC.KeepAlive` ' e bir çağrı içermez ve bu nedenle kuralı ihlal eder. `GoodMethod` düzeltilen kodu içerir.

> [!NOTE]
> Bu örnek, kod derlense ve çalıştırılsa da, yönetilmeyen bir kaynak oluşturulmadığından veya serbest bırakıldığı için uyarının tetiklenmemesine rağmen sözde koddur.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName><xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Dispose Deseni](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
