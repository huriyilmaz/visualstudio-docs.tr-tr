---
title: 'CA1040: boş arabirimlerden kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 50a36281edb144ddb949899fa24e0b5088080220
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668305"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Boş arabirimlerden kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Arabirim hiçbir üye bildirmiyor veya iki ya da daha fazla arabirim uygulayamaz.

## <a name="rule-description"></a>Kural Tanımı
 Arayüzler bir davranış veya kullanım sözleşmesi sağlayan üyeleri tanımlar. Arabirim tarafından tanımlanan fonksiyonellik herhangi bir tür tarafından türün kalıtım hiyerarşisinde nerede belirdiği önemsenmeksizin devralınabilir. Tür arabirimin üyeleri için uygulamaları sağlayarak bir arayüz uygular. Boş bir arabirim hiçbir üye tanımlamaz. Bu nedenle, uygulanabilecek bir sözleşme tanımlamaz.

 Tasarımınızda, türlerin uygulanması beklenen boş arabirimler varsa, büyük olasılıkla bir ara birim veya bir tür grubunu tanımlamak için bir yol kullanıyorsunuz. Bu kimlik çalışma zamanında gerçekleşecektir, bunu gerçekleştirmenin doğru yolu özel bir öznitelik kullanmaktır. Hedef türlerini tanımlamak için özniteliğin varlığını veya yokluğunu veya özniteliğin özelliklerini kullanın. Kimlik derleme zamanında gerçekleşmelidir, boş bir arabirim kullanılması kabul edilebilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Arabirimi kaldırın veya ona üye ekleyin. Boş arabirim bir tür kümesini etiketlemek için kullanılıyorsa, arabirimini özel bir öznitelik ile değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Arabirim, derleme zamanında bir tür kümesini tanımlamak için kullanıldığında, bu kuraldan bir uyarının bastırmasının güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte boş bir arabirim gösterilmektedir.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
