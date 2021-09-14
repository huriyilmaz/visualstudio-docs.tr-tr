---
title: DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma
description: görselleştirme ve modelleme SDK Visual Studio, başka bir dsl 'ye aktarabileceğiniz tamamlanmamış bir dsl tanımı oluşturabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 7b4f6deca3320a5c2182030d8e5cdec99a36c023
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637430"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma
görselleştirme ve modelleme SDK Visual Studio, başka bir dsl 'ye aktarabileceğiniz tamamlanmamış bir dsl tanımı oluşturabilirsiniz. Bu, benzer modellerin ortak parçalarını çarpanlara katmanızı sağlar.

## <a name="creating-and-using-dsl-libraries"></a>DSL kitaplıklarını oluşturma ve kullanma

#### <a name="to-create-a-dsl-library"></a>DSL kitaplığı oluşturmak için

1. Yeni bir DSL projesi oluşturun ve DSL kitaplığı çözüm şablonunu seçin.

     Tek bir DSL projesi, boş bir modelle oluşturulacaktır.

2. Etki alanı sınıfları, ilişkiler, şekiller vb. ekleyebilirsiniz.

     Kitaplıktaki öğelerin tek bir ekleme ağacı oluşturmak zorunda değildir.

     İçeri aktarıcılar tarafından kullanılabilecek bir ilişki tanımlamak için iki etki alanı sınıfı oluşturun ve aralarında ilişki oluşturun.

     Etki alanı sınıflarının **Devralma değiştiricisini** olarak ayarlamayı düşünün `Abstract` .

3. DSL Gezgini ' nde tanımladığınız öğeleri (bağlantı oluşturucular gibi) ekleyebilirsiniz.

4. Doğrulama kısıtlamaları gibi ek kod gerektiren özelleştirmeler ekleyebilirsiniz.

5. **Tüm Şablonları Dönüştür**' e tıklayın.

6. Projeyi derleyin.

7. Diğer kişilerin kullanması için DSL dağıtırken, hem derlenen derleme (DLL) hem de dosya sağlamanız gerekir `DslDefinition.dsl` . Derlenen derlemeyi, altındaki bir klasörde bulabilirsiniz `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>DSL kitaplığını içeri aktarmak için

1. Başka bir DSL tanımında, **DSL Gezgini**' nde, DSL kök sınıfına sağ tıklayın ve ardından **Yeni DslLibrary içeri aktarma Ekle**' ye tıklayın.

2. Özellikler penceresi, kitaplığın **dosya yolunu** ayarlayın. Göreli veya mutlak bir yol kullanabilirsiniz.

    İçeri aktarılan kitaplık, salt okuma modunda DSL Gezgini 'nde görünür.

3. İçeri aktarılan sınıfları temel sınıflar olarak kullanabilirsiniz. İçeri aktarma DSL 'de bir etki alanı sınıfı oluşturun ve Özellikler penceresi, **temel sınıfı** içeri aktarılan bir sınıfa ayarlayın.

4. Tüm Şablonları Dönüştür ' e tıklayın.

5. DSL kitaplığı projesi tarafından oluşturulan derlemeye (DLL) bir başvuru olan DSL projesine ekleyin.

6. Çözümü derleyin.

   DSL kitaplığı, diğer kitaplıkları içeri aktarabilir. Bir kitaplığı içeri aktardığınızda, içeri aktarmaları de otomatik olarak DSL Gezgini 'nde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
