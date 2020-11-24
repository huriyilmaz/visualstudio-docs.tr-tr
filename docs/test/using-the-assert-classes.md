---
title: MSTest onaylama sınıfları ve yöntemleri
description: Uygulama kodunuzun birim testi sırasında kod davranışınızı doğruluğunu test etmek için onay deyimlerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c5401fb15a19d069c0bf454661d6d9283abb2585
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598204"
---
# <a name="use-assert-classes-for-unit-testing"></a>Birim testi için onaylama sınıfları kullanma

<xref:Microsoft.VisualStudio.TestTools.UnitTesting>Belirli işlevleri doğrulamak için ad alanının onaylama sınıflarını kullanın. Bir birim testi yöntemi uygulamanızın kodundaki bir yöntemin kodunu, ancak onay deyimleri dahil ederseniz kodun davranışının doğruluğunu bildirir.

## <a name="kinds-of-asserts"></a>Onay türleri

<xref:Microsoft.VisualStudio.TestTools.UnitTesting>Ad alanı çeşitli tür onaylama sınıfları sağlar.

Test yönteminde, sınıfının herhangi bir yöntemini (gibi) çağırabilirsiniz <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> . <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>Sınıfın aralarından seçim yapabileceğiniz birçok yöntemi vardır ve çoğu yöntemin birçok aşırı yüklemesi vardır.

### <a name="compare-strings-and-collections"></a>Dizeleri ve koleksiyonları karşılaştırın

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>Nesne koleksiyonlarını karşılaştırmak veya bir koleksiyonun durumunu doğrulamak için sınıfını kullanın.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>Dizeleri karşılaştırmak ve incelemek için sınıfını kullanın. Bu sınıf, ve gibi çeşitli yararlı yöntemler içerir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType> .

### <a name="exceptions"></a>Özel Durumlar

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>Bir test başarısız olduğunda özel durum oluşturulur. Test zaman aşımına uğrarsa başarısız olur, beklenmeyen bir özel durum oluşturur veya **başarısız** bir sonuç üreten bir onay açıklaması içerir.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>Bir test, **Sonuçlandırılamayan** bir sonuç üretdiğinde oluşturulur. Genellikle, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> hala üzerinde çalıştığınız bir teste, henüz çalıştırılmaya hazırlanma olduğunu göstermek için bir ifade eklersiniz.

> [!NOTE]
> Alternatif bir strateji, özniteliğiyle çalıştırılmaya hazırlanmayan bir testi işaretlemenize olanak sağlar <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> . Ancak, bu, uygulanmayan testlerin sayısı üzerinde kolayca rapor oluşturmamalarınızın dezavantajı vardır.

Yeni bir onay özel durum sınıfı yazarsanız, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> özel durumu test veya üretim kodunuzda oluşan beklenmeyen bir özel durum yerine bir onaylama hatası olarak belirlemeyi kolaylaştırmak için temel sınıftan ' ı yapıştırın.

Uygulama kodunuzda bir yöntem tarafından oluşturulması beklenen bir özel durumun gerçekten oluşturulmuş olduğunu doğrulamak için <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> yöntemini kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzun birim testi](../test/unit-test-your-code.md)
