---
title: 'CA1064: özel durumlar genel olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5e704793aeef211ccabd4f2c9993834af205a14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663619"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Özel durumlar genel olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Genel olmayan bir özel durum doğrudan <xref:System.Exception>, <xref:System.SystemException> veya <xref:System.ApplicationException> türetilir.

## <a name="rule-description"></a>Kural Tanımı
 İç özel durum yalnızca kendi iç kapsamı içinde görülebilir. İç kapsam dışında kalan özel durumlardan sonra, sadece basit istisnalar istisna yakalamak için kullanılabilir. İç özel durum <xref:System.Exception>, <xref:System.SystemException> veya <xref:System.ApplicationException> ' den devralınmışsa, dış kodun özel durumla ne yapacaklarından haberdar olmak için yeterli bilgileri olmayacaktır.

 Ancak, kodun daha sonra iç özel durum için temel olarak kullanıldığı ortak bir özel durum varsa, kodun daha fazla çıkış için temel özel durumla akıllı bir şey yapabildiğini varsaymak mantıklı olur. Genel özel durum, T:System.Exception, T:System.SystemException veya T:System.applicationexceptiontarafından sağlandıkından daha fazla bilgiye sahip olacaktır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Özel durumu genel yapın veya <xref:System.Exception>, <xref:System.SystemException> veya <xref:System.ApplicationException> olmayan bir genel özel durumdan iç özel durum türetebilirsiniz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Özel özel durumun kendi iç kapsamı içinde yakalanıp tüm durumlarda emin değilseniz, bu kuraldan bir ileti gizleyin.

## <a name="example"></a>Örnek
 Özel durum sınıfı doğrudan özel durumdan türetildiğinden ve iç iş olduğundan, bu kural ilk örnek yöntemi ' FirstCustomException ' de ateşlenir. Sınıf, doğrudan özel durumdan türediğinden, sınıf genel olarak bildirildiği için, bu kural SecondCustomException sınıfında başlatılmıyor. Ayrıca, üçüncü sınıf <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName> veya <xref:System.ApplicationException?displayProperty=fullName> doğrudan türemediği için kuralı tetiklemez.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
