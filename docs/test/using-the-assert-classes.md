---
title: MSTest onay sınıfları ve yöntemleri
description: Uygulama kodunuzun birim testi sırasında kod davranışının doğru olduğunu test etmek için Assert deyimlerini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 09edc60284a8ff4d26a670123427cbf3a3ae1385
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038363"
---
# <a name="use-assert-classes-for-unit-testing"></a>Birim testi için Onay sınıflarını kullanma

Belirli işlevleri doğrulamak için ad alanının Assert <xref:Microsoft.VisualStudio.TestTools.UnitTesting> sınıflarını kullanın. Birim testi yöntemi, uygulama kodundaki bir yöntemin kodunu kullanır, ancak yalnızca Assert deyimlerini dahil ediyorsanız kodun davranışının doğru olup olmadığını raporlar.

## <a name="kinds-of-asserts"></a>Onay türleri

Ad <xref:Microsoft.VisualStudio.TestTools.UnitTesting> alanı çeşitli türlerde Onay sınıfları sağlar.

Test yönteminde sınıfının gibi herhangi bir yöntemini <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> çağırebilirsiniz. sınıfının <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> seçecek birçok yöntemi vardır ve yöntemlerin çoğunda çeşitli aşırı yüklemeler vardır.

### <a name="compare-strings-and-collections"></a>Dizeleri ve koleksiyonları karşılaştırma

Nesne <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> koleksiyonlarını karşılaştırmak veya bir koleksiyonun durumunu doğrulamak için sınıfını kullanın.

Dizeleri <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> karşılaştırmak ve incelemek için sınıfını kullanın. Bu sınıf , ve gibi çeşitli yararlı <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> yöntemler <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType> içerir.

### <a name="exceptions"></a>Özel durumlar

Bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> test başarısız olduğunda özel durum oluşturur. Zaman out(lar) durumunda test başarısız olur, beklenmeyen bir özel durum oluşturur veya Başarısız sonuç üreten bir assert **deyimi** içerir.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>, bir test, Sonlu sonucu **ürettiğinde ortaya çıkan**. Genellikle teste üzerinde çalışmaya devam etmek için henüz çalıştırıla hazır olmadığını belirten <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> bir deyim eklersiniz.

> [!NOTE]
> Alternatif strateji, özniteliğiyle çalıştırmaya hazır olan bir testi <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> işaretlemektir. Ancak bu, uygulanmamış test sayısıyla ilgili kolayca rapor oluşturamama dezavantajı içerir.

Yeni bir onay özel durum sınıfı yazarsanız, özel durumu test veya üretim kodunuzdan beklenmeyen bir özel durum değil onay hatası olarak tanımlamayı kolaylaştırmak için temel <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException> sınıftan devralın.

Uygulama kodunda bir yöntem tarafından at olmasını beklediğiniz özel durumun gerçekten at olduğunu doğrulamak için yöntemini <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu birim testi](../test/unit-test-your-code.md)
