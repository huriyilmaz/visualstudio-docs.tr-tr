---
title: Onaylama sınıflarını kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6a4f7f1631ac4bfc651f5df347db010cf47a656
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657130"
---
# <a name="using-the-assert-classes"></a>Onay Sınıfları Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Belirli işlevleri doğrulamak için UnitTestingFramework ad alanının onaylama sınıflarını kullanın. Bir birim testi yöntemi, geliştirme kodunuzda bir yöntemin kodunu, ancak yalnızca onaylama deyimleri dahil etmeniz durumunda kodun davranışının doğruluğunu bildirir.

## <a name="kinds-of-asserts"></a>Onay türleri
 @No__t_0 ad alanı çeşitli tür onaylama sınıfları sağlar:

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 Test yönteminde, onay sınıfının herhangi bir sayıda yöntemini (örneğin, onay. Areeşittir ()) çağırabilirsiniz. Onaylama sınıfının, aralarından seçim yapabileceğiniz birçok yöntemi vardır ve bu yöntemlerin çoğunda birçok aşırı yükleme vardır.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 Nesne koleksiyonlarını karşılaştırmak ve bir veya daha fazla koleksiyonun durumunu doğrulamak için Collectiononaylama sınıfını kullanın.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 Dizeleri karşılaştırmak için Stringonaylama sınıfını kullanın. Bu sınıf, Stringonaylama. Contains, Stringonaylama. eşleşmelerin ve Stringonaylama. StartsWith gibi yararlı yöntemler içerir.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 AssertFailedException özel durumu bir test başarısız olduğunda oluşturulur. Test zaman aşımına uğrarsa başarısız olur, beklenmeyen bir özel durum oluşturur veya başarısız bir sonuç üreten bir onay açıklaması içerir.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 Bir test Sonuçlandırılamayan bir sonuç üretdiğinde AssertInconclusiveException oluşturur oluşturulur. Genellikle, henüz çalıştırılmaya devam etmemiş olduğunu göstermek için üzerinde çalışmakta olduğunuz teste bir onaylama. ınsonuçlandırım ekleyin.

> [!NOTE]
> Alternatif bir strateji, yoksayma özniteliğiyle çalıştırılmaya hazırlanmayan bir testi işaretlemek olacaktır. Ancak, bu, uygulamak istediğiniz testlerin sayısı üzerinde kolayca rapor oluşturmamalarınızın dezavantajı vardır.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Yeni bir onay özel durum sınıfı yazarsanız, bu sınıfın UnitTestAssertException temel sınıfından devralmasını sağlamak, özel durumun test veya üretim kodunuzda oluşan beklenmeyen bir özel durum yerine bir onaylama hatası olarak tanımlanmasını kolaylaştırır.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Test yönteminin, geliştirme kodunuzda bir yöntem tarafından oluşturulması beklendiğini doğrulamak istediğiniz bir özel durumun bu yöntemde gerçekten atılmakta olduğunu doğrulamak istediğinizde, ExpectedExceptionAttribute özniteliğiyle bir test yöntemi süsleyerek.

## <a name="see-also"></a>Ayrıca Bkz.
 [mevcut kod Için birim testleri oluşturma ve çalıştırma](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
