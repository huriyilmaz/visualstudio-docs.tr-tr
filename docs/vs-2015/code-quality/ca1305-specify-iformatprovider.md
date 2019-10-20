---
title: 'CA1305: IFormatProvider belirtin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 299e8bfec526dc3a5e8dc166d9ab405d51037cbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661438"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem veya Oluşturucu, <xref:System.IFormatProvider?displayProperty=fullName> parametresini kabul eden aşırı yüklemeleri olan bir veya daha fazla üyeyi çağırır ve yöntem veya Oluşturucu <xref:System.IFormatProvider> parametresini alan aşırı yüklemeyi çağırmaz. Bu kural, <xref:System.IFormatProvider> parametresini yoksayarak ve aşağıdaki yöntemleri ek olarak belgelenen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] yöntemlerine yapılan çağrıları yoksayar:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 Bir <xref:System.Globalization.CultureInfo?displayProperty=fullName> veya <xref:System.IFormatProvider> nesnesi sağlanmadığında, aşırı yüklenmiş üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiye sahip olmayabilir. Ayrıca, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Üyeler kodunuzda doğru olmayan varsayımlar temelinde varsayılan kültür ve biçimlendirme seçer. Kodunuzun senaryolarınız için beklendiği gibi çalıştığından emin olmak için, aşağıdaki yönergelere göre kültüre özgü bilgiler sağlamalısınız:

- Değer kullanıcıya görüntülenecektir, geçerli kültürü kullanın. Bkz. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Değer, yazılım (bir dosya veya veritabanına kalıcı olarak) tarafından depolanacaksa ve erişiliyorsa, sabit kültür ' i kullanın. Bkz. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Değerin hedefini belirtmediğinizde, veri tüketicisinin veya sağlayıcının kültürü belirtmesini sağlayabilirsiniz.

  @No__t_0, yalnızca <xref:System.Resources.ResourceManager?displayProperty=fullName> sınıfının bir örneğini kullanarak yerelleştirilmiş kaynakları almak için kullanılır.

  Aşırı yüklenmiş üyenin varsayılan davranışı gereksinimlerinize uygun olsa da, kodunuzun kendi kendine belgelenmesi ve daha kolay tutulması için kültüre özgü aşırı yüklemeyi açıkça çağırmak daha iyidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Globalization.CultureInfo> veya <xref:System.IFormatProvider> alan aşırı yüklemeyi kullanın ve daha önce listelenen yönergelere göre bağımsız değişkenini belirtin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Varsayılan kültür/biçim sağlayıcının doğru seçim olması ve kodun bakımınızın önemli bir geliştirme önceliği olmaması durumunda bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `BadMethod` Bu kuralın iki ihlaline neden olur. `GoodMethod`, sabit kültürü <xref:System.String.Compare%2A> geçirerek ilk ihlayi düzeltir ve `string3` kullanıcıya görüntülenmediği için geçerli kültürü <xref:System.String.ToLower%2A> geçirerek ikinci ihlalin düzeltmesini düzeltir.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.DateTime> türü tarafından seçilen varsayılan <xref:System.IFormatProvider> ' da geçerli kültürün etkisini gösterir.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **6/4/1900 12:15:12 PM** 
**06/04/1900 12:15:12**
## <a name="related-rules"></a>İlgili kurallar
 [CA1304: CultureInfo belirtin](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [NIB: CultureInfo sınıfını kullanma](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
