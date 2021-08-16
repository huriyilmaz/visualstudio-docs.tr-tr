---
title: Etki Alanına Özgü Dilden Kod Oluşturma
description: Domain-Specific Araçları'nın modellerde temsil edilen verilerden kod, belge ve diğer yapıtlar oluşturmanın güçlü bir yolunu nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 57dc7ca55bcc0508cd3b78f5ea334b848322d17dd8e666ff051c25f6a7695ae3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121288717"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Etki Alanına Özgü Dilden Kod Oluşturma

Microsoft, [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] modellerde temsil edilen verilerden kod, belge, yapılandırma dosyası ve diğer yapıtlar oluşturmak için güçlü bir yol sağlar. kullanarak, verilerinizi temsil eden bir sınıf kümesi oluşturabilir ve metin şablonlarınızı, adları ve özellikleri bu verileri yansıtan [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] sınıflara yazabilirsiniz.

Örneğin, Fabrikam'da müşteri adlarının ve e-posta adreslerinin yer alan bir XML dosyası vardır. Geliştiricileri, Müşteri'nin bir sınıf olduğu, özellik adı ve e-posta ile bir model oluştur. Bir HTML sayfasının parçası olarak tüm müşterilerin bir tabloyu üreten bu parça dahil olmak üzere verileri işlemeye yardımcı olacak birkaç metin şablonu yazar:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Müşteri veritabanı işlendiğinde XML dosyası model deposuna okunur. kullanılarak *oluşturulan yönerge* işlemcisi, Customer [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] sınıfını metin şablonundaki kod için kullanılabilir yapar. Aynı depoda birçok metin şablonu çalıştırabilirsiniz.

Metin şablonları için [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] gereklidir. Etki alanı modelinin öğelerinin yanı sıra VSPackage ve araçları etki alanıyla tümleştiren denetimler için kaynak kodu oluşturmak için Visual Studio.

Bu bölümde, içinde kullanılan metin şablonları oluşturma, değiştirme ve hata ayıklama yollarından bazıları ele [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] almaktadır.

## <a name="in-this-section"></a>Bu Bölümde

[Metin Şablonlarından Modellere Erişme](../modeling/accessing-models-from-text-templates.md)\
Metin şablonlarında etki alanına özgü dile başvuru hakkında temel bilgiler sağlar.

[Kılavuz: Modele Erişen Metin Şablonunda Hata Ayıklama](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
Etki alanına özgü bir dile başvuran bir metin şablonunda sorun giderme ve hata ayıklamanın nasıl olduğunu açıklar.

[Kılavuz: Bir Ana Bilgisayarı Oluşturulan Yönerge İşlemcisine Bağlama](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
Özel bir ana bilgisayarı oluşturulan yönerge işlemcisine bağlamayı açıklar.

[DslTextTransform Komutu](../modeling/the-dsltexttransform-command.md)\
Etki alanına özgü dillere başvurulan metin şablonları için komut satırı üzerinde TextTransform yürütülebilir dosyasını yürüten komut dosyasını açıklar.

## <a name="reference"></a>Başvuru

[T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)\
Metin şablonu yönergelerinin ve denetim bloklarının söz dizimlerini sağlar.

## <a name="related-sections"></a>İlgili Bölümler

[T4 Metin Şablonları kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Metin şablonu dönüştürme işlemini açıklar.

[Derleme sürecinde kod oluşturma](../modeling/code-generation-in-a-build-process.md)\
Derleme sunucusunda dsl'den dosya üretiyorsanız bu konuyu okuyun.
