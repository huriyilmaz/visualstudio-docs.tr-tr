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
ms.openlocfilehash: 025d76f8e946dd3021141d6736c6b4bd40d57170
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539092"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider belirt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategori|Microsoft. Globalization|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir yöntem veya Oluşturucu bir parametreyi kabul eden aşırı yüklemeleri olan bir veya daha fazla üyeyi çağırır <xref:System.IFormatProvider?displayProperty=fullName> ve yöntem veya Oluşturucu parametreyi alan aşırı yüklemeyi çağırmaz <xref:System.IFormatProvider> . Bu kural [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , parametresini yok saymakla belgelenen yöntemlere yapılan çağrıları <xref:System.IFormatProvider> ve ayrıca aşağıdaki yöntemleri yoksayar:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>Veya <xref:System.IFormatProvider> nesnesi sağlanmadığında, aşırı yüklenmiş üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiye sahip olmayabilir. Ayrıca, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Üyeler kodunuzda doğru olmayan varsayımlar temelinde varsayılan kültür ve biçimlendirme seçer. Kodunuzun senaryolarınız için beklendiği gibi çalıştığından emin olmak için, aşağıdaki yönergelere göre kültüre özgü bilgiler sağlamalısınız:

- Değer kullanıcıya görüntülenecektir, geçerli kültürü kullanın. Bkz. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Değer, yazılım (bir dosya veya veritabanına kalıcı olarak) tarafından depolanacaksa ve erişiliyorsa, sabit kültür ' i kullanın. Bkz. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Değerin hedefini belirtmediğinizde, veri tüketicisinin veya sağlayıcının kültürü belirtmesini sağlayabilirsiniz.

  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>Yalnızca, sınıfının bir örneğini kullanarak yerelleştirilmiş kaynakları almak için kullanıldığını unutmayın <xref:System.Resources.ResourceManager?displayProperty=fullName> .

  Aşırı yüklenmiş üyenin varsayılan davranışı gereksinimlerinize uygun olsa da, kodunuzun kendi kendine belgelenmesi ve daha kolay tutulması için kültüre özgü aşırı yüklemeyi açıkça çağırmak daha iyidir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, bir <xref:System.Globalization.CultureInfo> veya alan <xref:System.IFormatProvider> ve daha önce listelenen yönergelere göre bağımsız değişkenini belirten aşırı yüklemeyi kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Varsayılan kültür/biçim sağlayıcının doğru seçim olması ve kodun bakımınızın önemli bir geliştirme önceliği olmaması durumunda bu kuraldan bir uyarının görüntülenmesini güvenli hale gelir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `BadMethod` Bu kuralın iki ihlaline neden olur. `GoodMethod` Sabit kültürü öğesine geçirerek ilk <xref:System.String.Compare%2A> ihlayi düzeltir ve geçerli kültürü kullanıcıya geçirilerek ikinci ihlalin düzeltmesini düzeltir <xref:System.String.ToLower%2A> `string3` .

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek, geçerli <xref:System.IFormatProvider> kültürün, türü tarafından seçilen varsayılan değer olan etkisini gösterir <xref:System.DateTime> .

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **6/4/1900 12:15:12 PM** 
 **06/04/1900 12:15:12**
## <a name="related-rules"></a>İlgili kurallar
 [CA1304: CultureInfo belirt](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [NIB: CultureInfo sınıfını kullanma](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
