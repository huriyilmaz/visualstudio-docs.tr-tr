---
title: Etki Alanı Özelliklerinin Özellikleri
description: Etki alanı özelliğinin değer tutan bir model öğesinin özelliği olduğunu ve etki alanı özelliklerinin diyagramda etki alanı sınıfı kutusunda nasıl listelenmiş olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f2f026f62c5440b48b04d05e080515c47dd11979
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390652"
---
# <a name="properties-of-domain-properties"></a>Etki Alanı Özelliklerinin Özellikleri
Etki *alanı özelliği,* değer tutan bir model öğesinin özelliğidir. Örneğin, etki `Person` alanı sınıfı ve özelliklerine sahip `Name` `BirthDate` olabilir. DSL Tanımında, etki alanı özellikleri diyagramda etki alanı sınıfı kutusunda ve DSL Gezgini'nde etki alanı sınıfı altında listelenir. Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> "property" sözcüğünde iki kullanım vardır. Etki *alanı özelliği,* bir etki alanı sınıfında tanımladığınız bir özelliktir. Buna karşılık, BIR DSL'nin birçok *öğeleri,* DSL Tanımı'nın **Özellikler penceresinde** listelenen özelliklerine sahiptir. Örneğin, her etki alanı özelliği, bu konuda açıklanan bir özellik kümesine sahiptir.

 Çalışma zamanında, bir kullanıcı etki alanı sınıfının örneklerini oluşturduğunda, etki alanı özelliklerinin değerleri Özellikler penceresi ve şekillerde görüntülenebilir.

 Çoğu etki alanı özelliği normal CLR özellikleri olarak uygulanır. Ancak, programlama açısından, etki alanı özellikleri sıradan program özelliklerine göre daha zengin işlevlere sahiptir:

- Bir özelliğin durumunu izlemek için kurallar ve olaylar tanımlayabilirsiniz. Daha fazla bilgi için [bkz. Değişiklikleri Yanıt verme ve Yayma.](../modeling/responding-to-and-propagating-changes.md)

- İşlemler tutarsız durumları önlemeye yardımcı olur. Daha fazla bilgi için [bkz. Program Kodunda Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

  Diyagramda veya DSL Gezgini'nde bir Etki Alanı Özelliği'ni seçerek aşağıdaki öğeleri Özellikler penceresi. Bu öğelerin kullanımı hakkında daha fazla bilgi için, [bkz. Domain-Specific Dili Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Özellik|Açıklama|Varsayılan değer|
|-|-|-|
|**Açıklama**|Oluşturulan tasarımcının kullanıcı arabirimini (UI) belgeley etmek için kullanılan açıklama.|\<none>|
|**Görünen Ad**|Bu etki alanı özelliği için oluşturulan tasarımcıda görüntülenecek ad. Boşluklar ve noktalama işaretleri içerebilir, örneğin "Şarkı Başlığı".|\<none>|
|**Öğe Adı Sağlayıcısı**|Bu yalnızca olarak ayarlanmışsa `Is Element Name` `true` geçerlidir. Varsayılan davranışı geçersiz karak bir etki alanı sınıfının yeni öğesi için ad sağlayan kodlar yazabilirsiniz.<br /><br /> DSL projesinde bir kod dosyasında, 'den türetilen bir sınıf <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> oluşturun.<br /><br /> Ardından DSL Gezgini'nde DSL'nin köküne sağ tıklayın ve Dış Tür Ekle'ye tıklayın. Sınıfnizin adını girin.<br /><br /> Bu etki alanı özelliğini yeniden seçin ve açılan listeden sınıfın adını seçin.|\<none>|
|**Getter Erişim Değiştiricisi**|Etki alanı sınıfının erişim düzeyi ( veya `public` `internal` ). Bu, program kodunun özelliğine erişe kapsamını kontrol eder.|`public`|
|**Help Anahtar Sözcüğü**|Bu etki alanı özelliği için F1 yardım dizinini dizine eklemek için kullanılan isteğe bağlı anahtar sözcük.|\<none>|
|**Gözatılabilir**|ise, `True` bu DSL modelleri açık olduğunda, özellikler penceresinde kullanıcıya etki alanı özelliği görüntülenir.<br /><br /> ise, `False` etki alanı özelliği kullanıcı arabiriminde gizlidir.<br /><br /> Etki alanı özelliğini görünür ancak salt okunur yapmak için Kullanıcı Arabirimi Salt Okunur **olarak ayarlayın.**|`True`|
|**Öğe Adı**|ise, `True` bu etki alanı özelliği DSL Gezgini'nde model öğesinin adı olarak görüntülenir.<br /><br /> Yeni model öğeleri bu özellik için benzersiz bir varsayılan değer alır. Bu değerlerin nasıl oluşturul olduğunu kontrol etmek için Öğe Adı **Sağlayıcısı'nın öğesini ayarlayın.**|`False`|
|**Kullanıcı Arabirimi Salt Okunur mu?**|ise, `True` etki alanı özelliğinin değeri kullanıcı arabirimi kullanılarak değiştirilemez. Yine de programlar tarafından ayarlansa da, bu ayar Özellikler penceresi.<br /><br /> Etki alanı özelliğini kullanıcıdan gizlemek için Gözatılabilir olarak **ayarlayın.** Programlara göre erişimi kontrol etmek için Ayarlayıcı Erişim **Değiştiricisi'ne ayarlayın.**|`False`|
|**Tip**|Etki alanı özelliğinin tür ( `Normal` , `Calculated` veya `CustomStorage` ). Daha fazla bilgi için [bkz. Hesaplanan ve Özel Depolama Özellikleri.](../modeling/calculated-and-custom-storage-properties.md)|`Normal`|
|**Ad**|Bu etki alanı özelliğinin adı. Geçerli bir tanımlayıcı olmalıdır, örneğin **SongTitle**.|\<none>|
|**Notlar**|Bu etki alanı özelliğiyle ilişkili resmi olmayan notlar.|\<none>|
|**Ayarlayıcı Erişim Değiştiricisi**|Ayarlayıcı için erişim değiştiricisi. Bu, program kodunun özelliğini ayarlandır olduğu kapsamı kontrol eder.|`public`|
|**Tür**|Özelliğin türü. Kullanılabilir türler listesine eklemek için DSL gezgininde DSL'nin köküne sağ tıklayın ve Dış Tür **Ekle'ye tıklayın.**|`String`|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))