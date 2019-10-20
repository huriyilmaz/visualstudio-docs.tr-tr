---
title: DSL kitaplığı kullanarak DSLs arasında sınıfları paylaşma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 093cc277fa1cbe1915099fd9663fc1ccb797ca3a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671175"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirme ve modelleme SDK [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], başka bir DSL 'ye aktarabileceğiniz tamamlanmamış bir DSL tanımı oluşturabilirsiniz. Bu, benzer modellerin ortak parçalarını çarpanlara katmanızı sağlar.

## <a name="creating-and-using-dsl-libraries"></a>DSL kitaplıklarını oluşturma ve kullanma

#### <a name="to-create-a-dsl-library"></a>DSL kitaplığı oluşturmak için

1. Yeni bir DSL projesi oluşturun ve DSL kitaplığı çözüm şablonunu seçin.

     Tek bir DSL projesi, boş bir modelle oluşturulacaktır.

2. Etki alanı sınıfları, ilişkiler, şekiller vb. ekleyebilirsiniz.

     Kitaplıktaki öğelerin tek bir ekleme ağacı oluşturmak zorunda değildir.

     İçeri aktarıcılar tarafından kullanılabilecek bir ilişki tanımlamak için iki etki alanı sınıfı oluşturun ve aralarında ilişki oluşturun.

     Etki alanı sınıflarının **Devralma değiştiricisini** `Abstract` olarak ayarlamayı düşünün.

3. DSL Gezgini ' nde tanımladığınız öğeleri (bağlantı oluşturucular gibi) ekleyebilirsiniz.

4. Doğrulama kısıtlamaları gibi ek kod gerektiren özelleştirmeler ekleyebilirsiniz.

5. **Tüm Şablonları Dönüştür**' e tıklayın.

6. Projeyi oluşturun.

7. Diğer kişilerin kullanması için DSL dağıtırken, hem derlenen derleme (DLL) hem de dosya `DslDefinition.dsl` sağlamanız gerekir. Derlenen derlemeyi `Dsl\bin\*` altında bir klasörde bulabilirsiniz

#### <a name="to-import-a-dsl-library"></a>DSL kitaplığını içeri aktarmak için

1. Başka bir DSL tanımında, **DSL Gezgini**' nde, DSL kök sınıfına sağ tıklayın ve ardından **Yeni DslLibrary içeri aktarma Ekle**' ye tıklayın.

2. Özellikler penceresi, kitaplığın **dosya yolunu** ayarlayın. Göreli veya mutlak bir yol kullanabilirsiniz.

    İçeri aktarılan kitaplık, salt okuma modunda DSL Gezgini 'nde görünür.

3. İçeri aktarılan sınıfları temel sınıflar olarak kullanabilirsiniz. İçeri aktarma DSL 'de bir etki alanı sınıfı oluşturun ve Özellikler penceresi, **temel sınıfı** içeri aktarılan bir sınıfa ayarlayın.

4. Tüm Şablonları Dönüştür ' e tıklayın.

5. DSL kitaplığı projesi tarafından oluşturulan derlemeye (DLL) bir başvuru olan DSL projesine ekleyin.

6. Çözümü oluşturun.

   DSL kitaplığı, diğer kitaplıkları içeri aktarabilir. Bir kitaplığı içeri aktardığınızda, içeri aktarmaları de otomatik olarak DSL Gezgini 'nde görünür.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
