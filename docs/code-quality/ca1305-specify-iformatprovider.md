---
title: 'CA1305: IFormatProvider belirtme'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 5a759b6eefe92b4168684b098b4025f589893b4b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444421"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider belirtme

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategori|Microsoft. Globalization|
|Son değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep

Bir yöntem veya Oluşturucu, <xref:System.IFormatProvider?displayProperty=fullName> parametresini kabul eden aşırı yüklemeleri olan bir veya daha fazla üyeyi çağırır ve yöntem veya Oluşturucu <xref:System.IFormatProvider> parametresini alan aşırı yüklemeyi çağırmaz.

Bu kural, <xref:System.IFormatProvider> parametresini yok saymakla belgelenen .NET yöntemlerine yapılan çağrıları yoksayar. Kural aşağıdaki yöntemleri de yoksayar:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Kural açıklaması

@No__t-0 veya <xref:System.IFormatProvider> nesnesi sağlanmadığında, aşırı yüklenmiş üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiye sahip olmayabilir. Ayrıca, .NET üyeleri, kodunuz için doğru olmayan varsayımlar temelinde varsayılan kültür ve biçimlendirme seçeneklerini de tercih edebilir. Kodunuzun senaryolarınız için beklendiği gibi çalıştığından emin olmak için, aşağıdaki yönergelere göre kültüre özgü bilgiler sağlamalısınız:

- Değer kullanıcıya görüntülenecektir, geçerli kültürü kullanın. Bkz. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Değer, yazılım (bir dosya veya veritabanına kalıcı olarak) tarafından depolanacaksa ve erişiliyorsa, sabit kültür ' i kullanın. Bkz. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Değerin hedefini belirtmediğinizde, veri tüketicisinin veya sağlayıcının kültürü belirtmesini sağlayabilirsiniz.

Aşırı yüklenmiş üyenin varsayılan davranışı gereksinimlerinize uygun olsa da, kodunuzun kendi kendine belgelenmesi ve daha kolay tutulması için kültüre özgü aşırı yüklemeyi açıkça çağırmak daha iyidir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme

Bu kural ihlalini onarmak için <xref:System.IFormatProvider> bağımsız değişkeni alan aşırı yüklemeyi kullanın. Ya da, [ C# enterpolasyonlu bir dize](/dotnet/csharp/tutorials/string-interpolation) kullanın ve <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> yöntemine geçirin.

## <a name="when-to-suppress-warnings"></a>Uyarıların ne zaman bastırılamıyor

Varsayılan biçimin doğru seçim olması ve kodun bakımınızın önemli bir geliştirme önceliği olmaması durumunda bu kuraldan gelen bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek

Aşağıdaki kodda `example1` dizesi CA1305 kuralını ihlal ediyor. @No__t-0 dizesi, <xref:System.IFormatProvider> uygulayan <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> ' i @no__t 3 ' e geçirerek kural CA1305 ' i karşılar. @No__t-0 dizesi, enterpolasyonlu bir dizeyi <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]> ' e geçirerek kural CA1305 karşılar.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>İlgili kurallar

- [CA1304: CultureInfo belirtin](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Ayrıca bkz.

- [CultureInfo sınıfını kullanma](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)
