---
title: 'CA1304: CultureInfo belirtin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 202f3759026bbedd5e99e94bba76e956b83357b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661463"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem veya Oluşturucu bir <xref:System.Globalization.CultureInfo?displayProperty=fullName> parametresi kabul eden aşırı yüküne sahip bir üyeyi çağırır ve yöntem veya Oluşturucu <xref:System.Globalization.CultureInfo> parametresini alan aşırı yüklemeyi çağırmaz. Bu kural, aşağıdaki yöntemlere yapılan çağrıları yoksayar:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 Bir <xref:System.Globalization.CultureInfo> veya <xref:System.IFormatProvider?displayProperty=fullName> nesnesi sağlanmadığında, aşırı yüklenmiş üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiye sahip olmayabilir. Ayrıca, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Üyeler kodunuzda doğru olmayan varsayımlar temelinde varsayılan kültür ve biçimlendirme seçer. Senaryolarınız için kodun beklendiği gibi çalıştığından emin olmak için, aşağıdaki yönergelere göre kültüre özgü bilgiler sağlamalısınız:

- Değer kullanıcıya görüntülenecektir, geçerli kültürü kullanın. Bkz. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Değer, yazılım tarafından depolanacaksa, diğer bir deyişle, bir dosya veya veritabanına kalıcı hale getirilir, sabit kültür ' i kullanın. Bkz. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Değerin hedefini belirtmediğinizde, veri tüketicisinin veya sağlayıcının kültürü belirtmesini sağlayabilirsiniz.

  @No__t_0, yalnızca <xref:System.Resources.ResourceManager?displayProperty=fullName> sınıfının bir örneğini kullanarak yerelleştirilmiş kaynakları almak için kullanılır.

  Aşırı yüklenmiş üyenin varsayılan davranışı gereksinimlerinize uygun olsa da, kodunuzun kendi kendine belgelenmesi ve daha kolay tutulması için kültüre özgü aşırı yüklemeyi açıkça çağırmak daha iyidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Globalization.CultureInfo> veya <xref:System.IFormatProvider> alan aşırı yüklemeyi kullanın ve daha önce listelenen yönergelere göre bağımsız değişkenini belirtin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Varsayılan kültür/biçim sağlayıcısının doğru seçim olması ve kodun bakımınızın önemli bir geliştirme önceliği olmaması durumunda bu kuraldan bir uyarının gösterilmemesi güvenlidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `BadMethod` Bu kuralın iki ihlaline neden olur. `GoodMethod`, sabit kültürü System. String. Compare 'e geçirerek ilk ihlayi düzeltir ve `string3` kullanıcıya görüntülenmediği için geçerli kültürü <xref:System.String.ToLower%2A> geçirerek ikinci ihlalin düzeltmesini düzeltir.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.DateTime> türü tarafından seçilen varsayılan <xref:System.IFormatProvider> ' da geçerli kültürün etkisini gösterir.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **6/4/1900 12:15:12 PM** 
**06/04/1900 12:15:12**
## <a name="related-rules"></a>İlgili kurallar
 [CA1305: IFormatProvider belirtin](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [NIB: CultureInfo sınıfını kullanma](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
