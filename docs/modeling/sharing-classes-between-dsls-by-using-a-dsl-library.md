---
title: DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma
description: Visual Studio Görselleştirme ve Modelleme SDK'sı'sinde, başka bir DSL'ye içeri aktarabilirsiniz tamamlanmamış bir DSL Tanımı oluşturabilirsiniz.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085383"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma
Görselleştirme Visual Studio Modelleme SDK'sı içinde, başka bir DSL'ye içeri aktarabilirsiniz tamamlanmamış bir DSL Tanımı oluşturabilirsiniz. Bu, benzer modellerin ortak bölümlerini çarpanlara alır.

## <a name="creating-and-using-dsl-libraries"></a>DSL Kitaplıkları oluşturma ve kullanma

#### <a name="to-create-a-dsl-library"></a>DSL Kitaplığı oluşturmak için

1. Yeni bir DSL projesi oluşturun ve DSL Kitaplığı çözüm şablonunu seçin.

     Boş bir modelle tek bir DSL projesi oluşturulur.

2. Etki alanı sınıfları, ilişkiler, şekiller ve daha birçok şey ekleme.

     Kitaplıkta öğelerin tek bir ekleme ağacı oluşturması gerek değildir.

     İçeri aktaranların kullanabileceği bir ilişki tanımlamak için iki etki alanı sınıfı oluşturun ve aralarında ilişki oluşturun.

     Etki alanı **sınıflarının Devralma Değiştiricisini** olarak ayarlamayı göz önünde bulundurabilirsiniz. `Abstract`

3. DSL Gezgini'nde tanımladığınız Bağlantı Oluşturucuları gibi öğeleri ekleyebilirsiniz.

4. Doğrulama kısıtlamaları gibi ek kod gerektiren özelleştirmeler ebilirsiniz.

5. Tüm **Şablonları Dönüştür'e tıklayın.**

6. Projeyi derleyin.

7. DSL'i diğer kişilerin kullanımı için dağıtırken, hem derlenmiş derlemeyi (DLL) hem de dosyasını `DslDefinition.dsl` sağlamalıdır. Derlenmiş derlemeyi altındaki bir klasörde bulabilirsiniz `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>DSL Kitaplığını içeri aktarma

1. Başka bir DSL Tanımında, **DSL Gezgini'nde** DSL'nin kök sınıfına sağ tıklayın ve ardından Ekle **Yeni DslLibrary İçeri Aktarma'ya tıklayın.**

2. Dosya Özellikler penceresi **kitaplığının Dosya Yolu'Özellikler penceresi** ayarlayın. Göreli veya mutlak bir yol kullanabilirsiniz.

    İçe aktarılan kitaplık DSL Gezgini'nde salt okunur modda görünür.

3. İçe aktarılan sınıfları temel sınıflar olarak kullanabilirsiniz. İçeri aktarma DSL'sinde bir etki alanı sınıfı oluşturun ve Özellikler penceresi sınıfını **içeri aktarılan bir** sınıfa ayarlayın.

4. Tüm Şablonları Dönüştür'e tıklayın.

5. DSL projesine DSL Kitaplığı projesi tarafından inşa edilen derlemeye (DLL) bir başvuru ekleyin.

6. Çözümü derleyin.

   DSL Kitaplığı diğer kitaplıkları içeri aktarabilirsiniz. Bir kitaplığı içeri aktarıyorsanız, kitaplığın içeri aktarmaları otomatik olarak DSL Gezgini'nde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
