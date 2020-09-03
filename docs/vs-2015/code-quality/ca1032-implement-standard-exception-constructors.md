---
title: 'CA1032: Standart özel durum oluşturucuları uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542291"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standart özel durum oluşturucularını uygulayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir tür genişletilir <xref:System.Exception?displayProperty=fullName> ve gerekli tüm oluşturucuların bildirimini yapmaz.

## <a name="rule-description"></a>Kural Tanımı
 Özel durum türleri aşağıdaki oluşturucuları gerçekleştirmelidir:

- Ortak NewException ()

- Public NewException (dize)

- Public NewException (dize, özel durum)

- korumalı veya özel NewException (SerializationInfo, StreamingContext)

  Yapıcıların tüm ayarlamasını sağlamaktaki başarısızlık, istisnalarla başa çıkmayı zorlaştırabilir. Örneğin, imzaya sahip Oluşturucu `NewException(string, Exception)` diğer özel durumların neden olduğu özel durumlar oluşturmak için kullanılır. Bu Oluşturucu olmadan, bu tür bir durumda hangi yönetilen kodun yapması gerektiği bir iç (iç içe) özel durumu içeren özel bir özel durumun örneğini oluşturamaz ve oluşturamazsınız. İlk üç özel durum Oluşturucusu kurala göre ortaktır. Dördüncü Oluşturucu korumasız sınıflarda korunur ve korumalı sınıflarda özeldir. Daha fazla bilgi için bkz [. CA2229: serileştirme oluşturucuları uygulama](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için, eksik oluşturucuları özel duruma ekleyin ve doğru erişilebilirliğe sahip olduklarından emin olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İhlalin genel oluşturucular için farklı bir erişim düzeyi kullanılarak neden olduğunda, bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir özel durum türü ve doğru şekilde uygulanan bir özel durum türü içerir.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
