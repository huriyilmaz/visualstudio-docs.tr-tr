---
title: Etki alanına özgü dilden kod oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 32cafb9e68fc2535ed3b570022a59d284f4c4cae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666104"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Etki Alanına Özgü Dilden Kod Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft, [!INCLUDE[dsl](../includes/dsl-md.md)] modeller halinde temsil edilen verilerden kod, belge, yapılandırma dosyası ve diğer yapıtlar oluşturmak için güçlü bir yol sağlar. Kullanarak [!INCLUDE[dsl](../includes/dsl-md.md)] , verilerinizi temsil eden bir sınıf kümesi oluşturabilir ve metin şablonlarınızı, adları ve özellikleri bu verileri yansıtan sınıflarda yazabilirsiniz.

 Örneğin, Fabrikam 'ın bir XML dosyası müşteri adı ve e-posta adresi vardır. Geliştiriciler, müşterinin Özellikler adı ve e-posta ile bir sınıf olduğu bir model oluşturur. Bir HTML sayfasının parçası olarak tüm müşterilerin bir tablosunu üreten bu parça dahil, verileri işlemek için birkaç metin şablonu Yazar:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

 Müşteri veritabanı işlendiğinde, XML dosyası model deposuna okunurdur. Kullanılarak oluşturulan bir *yönerge işlemcisi* [!INCLUDE[dsl](../includes/dsl-md.md)] , müşteri sınıfını metin şablonundaki kod için kullanılabilir hale getirir. Birçok metin şablonu aynı depoya karşı çalıştırılabilir.

 Metin şablonları için gereklidir [!INCLUDE[dsl](../includes/dsl-md.md)] . Bunlar, etki alanı modelinin öğelerinin yanı sıra VSPackage ve araçları tümleştirme için kullanılan denetimler için kaynak kodu oluşturmak üzere kullanılır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Bu bölümde, ' de kullanılan metin şablonlarını oluşturma, değiştirme ve hata ayıklama yöntemlerinden bazıları açıklanmaktadır [!INCLUDE[dsl](../includes/dsl-md.md)] .

## <a name="in-this-section"></a>Bu Bölümde
 [Metin Şablonlarından Modellere Erişme](../modeling/accessing-models-from-text-templates.md)

 Metin şablonlarındaki alana özgü dile başvurma hakkında temel bilgiler sağlar.

 [İzlenecek yol: Modele Erişen Metin Şablonunda Hata Ayıklama](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)

 Etki alanına özgü bir dile başvuran bir metin şablonunda sorun giderme ve hata ayıklama işlemlerinin nasıl yapılacağını açıklar.

 [İzlenecek yol: Üretilen bir Yönerge İşlemcisine Ana Bilgisayar Bağlama](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)

 Özel bir konağın oluşturulan yönerge işlemcisine nasıl bağlanacağını açıklar.

 [DslTextTransform Komutu](../modeling/the-dsltexttransform-command.md)

 Alana özgü dillere başvuran metin şablonları için komut satırında TextTransform yürütülebilirini yürüten komut dosyasını açıklar.

## <a name="reference"></a>Başvuru
 [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)

 Metin şablonu yönergelerinin ve denetim bloklarının sözdizimini sağlar.

## <a name="related-sections"></a>İlgili Bölümler
 [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

 Metin şablonu dönüştürme işlemini açıklar.

 [Derleme Sürecinde Kod Oluşturma](../modeling/code-generation-in-a-build-process.md)

 Bir yapı sunucusundaki bir DSL 'den dosya oluşturuyorsanız bu konuyu okuyun.
