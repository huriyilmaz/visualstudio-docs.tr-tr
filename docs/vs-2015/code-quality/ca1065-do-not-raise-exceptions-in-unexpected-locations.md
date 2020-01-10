---
title: 'CA1065: beklenmeyen konumlarda özel durum yükseltmeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2df740abf25344253627b614fdbd80dce86c7bfa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847480"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Beklenmedik konumlarda özel durumlar harekete geçirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategori|Microsoft.Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 İstisna atılmasını beklemeyen yöntem bir istisna atar.

## <a name="rule-description"></a>Kural Tanımı
 Özel durum oluşturması beklenmeyen yöntemler aşağıdaki şekilde kategorize edilebilir:

- Özellik get yöntemleri

- Olay erişimci yöntemleri

- Eşittir yöntemleri

- GetHashCode yöntemleri

- ToString yöntemleri

- Statik Oluşturucular

- Sonlandırıcılar

- Dispose yöntemleri

- Eşitlik İşleçleri

- Örtük atama Işleçleri

  Aşağıdaki bölümler bu yöntem türlerini tartışır.

### <a name="property-get-methods"></a>Özellik get yöntemleri
 Özellikler temel olarak akıllı alanlardır. Bu nedenle, mümkün olduğunca bir alan gibi davranmalıdır. Alanlar özel durum oluşturmaz ve özelliklerden hiçbirine sahip değildir. Özel durum oluşturan bir özelliğe sahipseniz, bunu bir yöntemi yapmayı düşünün.

 Aşağıdaki özel durumların bir özellik Get yönteminden yapılmasına izin verilir:

- <xref:System.InvalidOperationException?displayProperty=fullName> ve tüm türetme (<xref:System.ObjectDisposedException?displayProperty=fullName>dahil)

- <xref:System.NotSupportedException?displayProperty=fullName> ve tüm türetme işlemleri

- <xref:System.ArgumentException?displayProperty=fullName> (yalnızca dizinli Get 'ten)

- <xref:System.Collections.Generic.KeyNotFoundException> (yalnızca dizinli Get 'ten)

### <a name="event-accessor-methods"></a>Olay erişimci yöntemleri
 Olay erişimcileri özel durum oluşturmaz basit işlemler olmalıdır. Olay işleyicisi eklemeyi veya kaldırmayı denediğinizde bir olay özel durum oluşturmaz.

 Aşağıdaki özel durumların bir olay accesveya bir olay aracılığıyla yapılmasına izin verilir:

- <xref:System.InvalidOperationException?displayProperty=fullName> ve tüm türetme (<xref:System.ObjectDisposedException?displayProperty=fullName>dahil)

- <xref:System.NotSupportedException?displayProperty=fullName> ve tüm türetme işlemleri

- <xref:System.ArgumentException> ve türetme

### <a name="equals-methods"></a>Eşittir yöntemleri
 Aşağıdaki **eşittir** yöntemleri özel durum oluşturmaz:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- [M:IEquatable.Equals](https://msdn2.microsoft.com/library/ms131190(VS.80).aspx)

  Bir **Equals** yöntemi, özel durum oluşturmak yerine `true` veya `false` döndürmelidir. Örneğin, eşittir iki eşleşmeyen tür geçirtiyse, bir <xref:System.ArgumentException>oluşturmak yerine yalnızca `false` döndürmelidir.

### <a name="gethashcode-methods"></a>GetHashCode yöntemleri
 Aşağıdaki **GetHashCode** yöntemleri genellikle özel durum oluşturmaz:

- <xref:System.Object.GetHashCode%2A>

- [M:iequalitycomparer.asp GetHashCode (T)](https://msdn2.microsoft.com/library/system.collections.iequalitycomparer.gethashcode.aspx)

  **GetHashCode** her zaman bir değer döndürmelidir. Aksi takdirde, karma tablodaki öğeleri kaybedebilirsiniz.

  Bağımsız değişken alan **GetHashCode** sürümleri bir <xref:System.ArgumentException>oluşturabilir. Ancak **Object. GetHashCode** asla bir özel durum oluşturmaz.

### <a name="tostring-methods"></a>ToString yöntemleri
 Hata ayıklayıcı, dize biçimindeki nesneler hakkında bilgi görüntülemeye yardımcı olması için <xref:System.Object.ToString%2A?displayProperty=fullName> kullanır. Bu nedenle, **ToString** bir nesnenin durumunu değiştirmemelidir ve özel durum oluşturmaz.

### <a name="static-constructors"></a>Statik Oluşturucular
 Statik bir oluşturucudan özel durumlar oluşturmak, türün geçerli uygulama etki alanında kullanılamaz hale gelmesine neden olur. Statik bir oluşturucudan özel durum oluşturmak için çok iyi bir nedeniniz (güvenlik sorunu gibi) olmalıdır.

### <a name="finalizers"></a>Sonlandırıcılar
 Sonlandırıcının bir özel durum oluşturmak, CLR 'nin hızlı bir şekilde başarısız olmasına neden olur ve bu da işlemi kapatır. Bu nedenle, bir sonlandırıcının özel durumların oluşturulması her zaman kaçınılmalıdır.

### <a name="dispose-methods"></a>Dispose yöntemleri
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> yöntemi özel durum oluşturmaz. Dispose, genellikle bir `finally` yan tümcesindeki Temizleme mantığının bir parçası olarak çağırılır. Bu nedenle, Dispose 'ten özel bir durum açıkça oluşturmak, kullanıcıyı `finally` yan tümcesinin içinde özel durum işleme eklemeye zorlar.

 **Dispose (false)** kod yolu hiçbir zaman özel durum oluşturmaz, çünkü bu neredeyse her zaman bir sonlandırıcının çağrısıdır.

### <a name="equality-operators--"></a>Eşitlik Işleçleri (= =,! =)
 Eşittir yöntemlerine benzer şekilde, eşitlik işleçleri `true` ya da `false` döndürmelidir ve özel durumlar oluşturmamalıdır.

### <a name="implicit-cast-operators"></a>Örtük atama Işleçleri
 Kullanıcı genellikle örtük bir atama işlecinin çağrıldığından emin olmadığı için örtük atama işleci tarafından oluşturulan bir özel durum tamamen beklenmiyor. Bu nedenle, örtük atama işleçlerinden hiçbir özel durum atılmamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Özellik kodlayıcıları için, mantığı, artık özel durum oluşturmak zorunda olmayacak şekilde değiştirin ya da özelliği bir yönteme değiştirin.

 Daha önce listelenen diğer tüm yöntem türleri için mantığı, artık özel durum oluşturması için değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 İhlalin oluşan özel durum yerine bir özel durum bildirimi neden olduysa, bu kuraldan bir uyarı bastırılması güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Tasarım Uyarıları](../code-quality/design-warnings.md)
