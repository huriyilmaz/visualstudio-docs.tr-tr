---
title: 'CA1032: Standart özel durum oluşturucuları uygulayın'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a73a615c08b538f4580a8d40765dcd7603722aa1
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446713"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standart özel durum oluşturucuları uygulayın

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategori|Microsoft. Design|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Bir tür <xref:System.Exception?displayProperty=fullName> ' i uzatır, ancak gereken tüm oluşturucuları bildirmiyor.

## <a name="rule-description"></a>Kural açıklaması

Özel durum türleri aşağıdaki üç Oluşturucu gerçekleştirmelidir:

- Ortak NewException ()

- Public NewException (dize)

- Public NewException (dize, özel durum)

Ayrıca, [.net Compiler platform tabanlı FxCop çözümleyicileri](../code-quality/roslyn-analyzers-overview.md)'nin aksine eski FxCop analizini çalıştırıyorsanız, dördüncü bir oluşturucunun olmaması de bir ihlal üretir:

- korumalı veya özel NewException (SerializationInfo, StreamingContext)

Yapıcıların tüm ayarlamasını sağlamaktaki başarısızlık, istisnalarla başa çıkmayı zorlaştırabilir. Örneğin, `NewException(string, Exception)` imzasına sahip Oluşturucu, diğer özel durumların neden olduğu özel durumlar oluşturmak için kullanılır. Bu Oluşturucu olmadan, bu tür bir durumda hangi yönetilen kodun yapması gerektiği bir iç (iç içe) özel durumu içeren özel özel durumunuzun bir örneğini oluşturamaz ve oluşturamıyoruz.

İlk üç özel durum Oluşturucusu kurala göre ortaktır. Dördüncü Oluşturucu korumasız sınıflarda korunur ve korumalı sınıflarda özeldir. Daha fazla bilgi için bkz. [CA2229: serileştirme oluşturucuları uygulama](../code-quality/ca2229.md).

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini düzeltmek için, eksik oluşturucuları özel duruma ekleyin ve doğru erişilebilirliğe sahip olduklarından emin olun.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

İhlalin genel oluşturucular için farklı bir erişim düzeyi kullanmasından kaynaklanan bu kuraldan bir uyarıyı bastırmak güvenlidir. Ayrıca, taşınabilir bir sınıf kitaplığı (PCL) oluşturuyorsanız `NewException(SerializationInfo, StreamingContext)` oluşturucusuna yönelik uyarıyı bastırmaya de devam edebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bu kuralı ihlal eden bir özel durum türü ve doğru şekilde uygulanan bir özel durum türü içerir.

[!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

[CA2229: Serileştirme oluşturucularını uygulayın](../code-quality/ca2229.md)
