---
title: MSTest assert sınıfları ve yöntemleri
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c36916c79bd783ed2c6ce960b068e85478b9971d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592054"
---
# <a name="use-assert-classes-for-unit-testing"></a>Birim testi için Assert sınıflarını kullanma

Belirli işlevleri doğrulamak <xref:Microsoft.VisualStudio.TestTools.UnitTesting> için ad alanının Assert sınıflarını kullanın. Birim test yöntemi, uygulamanızın kodundaki bir yöntemin kodunu uygular, ancak yalnızca Assert deyimleri eklerseniz kodun davranışının doğruluğunu bildirir.

## <a name="kinds-of-asserts"></a>İddia türleri

Ad <xref:Microsoft.VisualStudio.TestTools.UnitTesting> alanı çeşitli türde Assert sınıfları sağlar.

Test yönteminizde, sınıfın herhangi bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> yöntemini çağırabilirsiniz, örneğin. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> Sınıfın <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> aralarından seçim yapabileceğiniz birçok yöntemi vardır ve yöntemlerin çoğunda birden fazla yükleme vardır.

### <a name="compare-strings-and-collections"></a>Dizeleri ve koleksiyonları karşılaştırma

Nesnelerin <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> koleksiyonlarını karşılaştırmak veya koleksiyonun durumunu doğrulamak için sınıfı kullanın.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> Dizeleri karşılaştırmak ve incelemek için sınıfı kullanın. Bu sınıf, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, , <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType>ve <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>.

### <a name="exceptions"></a>Özel durumlar

Bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> test başarısız olduğunda özel durum atılır. Bir sınama zaman ları dışarı çıkarsa, beklenmeyen bir özel durum oluşturursa veya başarısız bir sonuç üreten bir assert deyimi içeriyorsa **başarısız olur.**

Bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException> test **Sonuçsuz**bir sonuç üretir zaman atılır. Genellikle, henüz çalıştırılmaya hazır olmadığını belirtmek için üzerinde çalıştığınız bir teste bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> deyim eklersiniz.

> [!NOTE]
> Alternatif bir strateji öznitelik ile <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> çalışmaya hazır olmayan bir test işaretlemektir. Ancak, bu, uygulanmayan test sayısı hakkında kolayca bir rapor oluşturamamanız dezavantajına sahiptir.

Yeni bir genel durum özel durum sınıfı <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> yazarsanız, özel durumu test veya üretim kodunuzdan atılan beklenmeyen bir özel durum yerine bir hata olarak tanımlamayı kolaylaştırmak için taban sınıftan devralın.

Uygulama kodunuzdaki bir yöntemtarafından atılmasını beklediğiniz bir özel durum <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> olduğunu doğrulamak için yöntemi kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Birim kodunuzu test edin](../test/unit-test-your-code.md)
