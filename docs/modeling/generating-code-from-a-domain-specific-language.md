---
title: Etki Alanına Özgü Dilden Kod Oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5000b8b6150fe630959f4cc4bbc58617e98d4a3a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662028"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Etki Alanına Özgü Dilden Kod Oluşturma

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], modeller halinde temsil edilen verilerden kod, belge, yapılandırma dosyası ve diğer yapıtları oluşturmak için güçlü bir yol sağlar. @No__t_0 kullanarak, verilerinizi temsil eden bir sınıf kümesi oluşturabilir ve metin şablonlarınızı, adları ve özellikleri bu verileri yansıtan sınıflarda yazabilirsiniz.

Örneğin, Fabrikam 'ın bir XML dosyası müşteri adı ve e-posta adresi vardır. Geliştiriciler, müşterinin Özellikler adı ve e-posta ile bir sınıf olduğu bir model oluşturur. Bir HTML sayfasının parçası olarak tüm müşterilerin bir tablosunu üreten bu parça dahil, verileri işlemek için birkaç metin şablonu Yazar:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Müşteri veritabanı işlendiğinde, XML dosyası model deposuna okunurdur. @No__t_1 kullanılarak oluşturulan *yönerge işlemcisi*, müşteri sınıfını metin şablonundaki kod için kullanılabilir hale getirir. Birçok metin şablonu aynı depoya karşı çalıştırılabilir.

@No__t_0 için metin şablonları gereklidir. Bunlar, etki alanı modelinin öğelerinin yanı sıra VSPackage ve araçları Visual Studio ile tümleştirmede kullanılan denetimler için kaynak kodu oluşturmak üzere kullanılır.

Bu bölümde [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] ' de kullanılan metin şablonlarını oluşturma, değiştirme ve hata ayıklama yöntemlerinden bazıları açıklanmaktadır.

## <a name="in-this-section"></a>Bu Bölümde

[Metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md) \
Metin şablonlarındaki alana özgü dile başvurma hakkında temel bilgiler sağlar.

[Izlenecek yol: modele erişen metin şablonunda hata ayıklama](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md) \
Etki alanına özgü bir dile başvuran bir metin şablonunda sorun giderme ve hata ayıklama işlemlerinin nasıl yapılacağını açıklar.

[Izlenecek yol: bir konağı oluşturulan yönerge Işlemcisine bağlama](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md) \
Özel bir konağın oluşturulan yönerge işlemcisine nasıl bağlanacağını açıklar.

[DslTextTransform komutu](../modeling/the-dsltexttransform-command.md) \
Alana özgü dillere başvuran metin şablonları için komut satırında TextTransform yürütülebilirini yürüten komut dosyasını açıklar.

## <a name="reference"></a>Başvuru

[T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md) \
Metin şablonu yönergelerinin ve denetim bloklarının sözdizimini sağlar.

## <a name="related-sections"></a>İlgili Bölümler

[T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md) \
Metin şablonu dönüştürme işlemini açıklar.

[Yapı Işlemindeki kod üretimi](../modeling/code-generation-in-a-build-process.md) \
Bir yapı sunucusundaki bir DSL 'den dosya oluşturuyorsanız bu konuyu okuyun.