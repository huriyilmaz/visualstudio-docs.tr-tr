---
title: Etki Alanı Özelliklerinin Özellikleri
description: Bir etki alanı özelliğinin bir değeri tutabilecek bir model öğesinin özelliği olduğunu ve etki alanı özelliklerinin diyagramdaki etki alanı sınıfı kutusunda nasıl listeleneceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 82fa25201813e6a4380162a11fdcfcf5736c82be
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637561"
---
# <a name="properties-of-domain-properties"></a>Etki Alanı Özelliklerinin Özellikleri
Bir *alan özelliği* , bir değeri tutabilecek bir model öğesinin özelliğidir. Örneğin, `Person` etki alanı sınıfının özellikleri `Name` ve olabilir `BirthDate` . DSL tanımında etki alanı özellikleri, diyagramdaki etki alanı sınıfı kutusunda ve DSL Gezgini 'ndeki etki alanı sınıfında listelenir. Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> "Property" sözcüğünün iki kullanımı vardır. Bir *etki alanı özelliği* , bir etki alanı sınıfında tanımladığınız bir özelliktir. Buna karşılık, bir DSL 'nin birçok öğesi DSL tanımındaki **Özellikler** penceresinde listelenen *özelliklere* sahiptir. Örneğin, her etki alanı özelliği, bu konuda açıklanan bir dizi özellik içerir.

 Çalışma zamanında, bir kullanıcı etki alanı sınıfının örneklerini oluşturduğunda, etki alanı özelliklerinin değerleri Özellikler penceresi görünebilir ve şekiller üzerinde görüntülenebilir.

 Çoğu etki alanı özelliği sıradan CLR özellikleri olarak uygulanır. Ancak, bir programlama noktasından, etki alanı özellikleri sıradan program özelliklerinden daha zengin işlevlere sahiptir:

- Bir özelliğin durumunu izleyen kuralları ve olayları tanımlayabilirsiniz. Daha fazla bilgi için bkz. [değişiklikleri yanıtlama ve yayma](../modeling/responding-to-and-propagating-changes.md).

- İşlemler tutarsız durumları önlemeye yardımcı olur. Daha fazla bilgi için bkz. [program kodunda modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Bir diyagramda veya DSL Gezgininde bir etki alanı özelliği seçtiğinizde, Özellikler penceresi aşağıdaki öğeleri görebilirsiniz. Bu öğelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan değer|
|-|-|-|
|**Açıklama**|Oluşturulan tasarımcının Kullanıcı arabirimini (UI) belgelemek için kullanılan açıklama.|\<none>|
|**Görünen ad**|Bu etki alanı özelliği için oluşturulan tasarımcıda görüntülenecek ad. Boşluk ve noktalama işareti içerebilir, örneğin "şarkı başlığı".|\<none>|
|**Öğe adı sağlayıcı**|Bu yalnızca, olarak ayarlandıysa geçerlidir `Is Element Name` `true` . Bir etki alanı sınıfının yeni bir öğesi için bir ad sağlayan, varsayılan davranışı geçersiz kılan bir kod yazabilirsiniz.<br /><br /> DSL projesindeki bir kod dosyasında, öğesinden türetilmiş bir sınıf oluşturun <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> .<br /><br /> Ardından DSL Gezgini ' nde DSL köküne sağ tıklayın ve dış tür Ekle ' ye tıklayın. Sınıfınızın adını girin.<br /><br /> Bu etki alanı özelliğini yeniden seçin ve açılan listeden sınıfın adını seçin.|\<none>|
|**Alıcı erişim değiştiricisi**|Etki alanı sınıfına erişim düzeyi ( `public` veya `internal` ). Bu, program kodunun özelliğe erişebileceği kapsamı denetler.|`public`|
|**Help anahtar sözcüğü**|Bu etki alanı özelliği için F1 yardımını dizine eklemek için kullanılan isteğe bağlı anahtar sözcük.|\<none>|
|**Göz atılamaz**|Varsa `True` , bu DSL modelleri açık olduğunda, Özellikler penceresindeki kullanıcıya etki alanı özelliği görüntülenir.<br /><br /> İse `False` , etki alanı özelliği Kullanıcı arabiriminde gizlidir.<br /><br /> Etki alanı özelliğini görünür halde salt okunurdur, küme **yalnızca kullanıcı arabirimi salt okunurdur**.|`True`|
|**Öğe adı**|`True`Bu etki alanı özelliği, DSL Gezgini 'ndeki model öğesinin adı olarak görüntülenecektir.<br /><br /> Yeni model öğeleri, bu özellik için benzersiz bir varsayılan değer alacaktır. Bu değerlerin nasıl oluşturulduğunu denetlemek istiyorsanız, **öğe adı sağlayıcısı**' nı ayarlayın.|`False`|
|**UI salt okunurdur**|İse `True` , Domain özelliğinin değeri kullanıcı arabirimi kullanılarak değiştirilemez. Hala programlar tarafından ayarlanabilir ve Özellikler penceresi görünür olur.<br /><br /> Etki alanı özelliğini kullanıcıdan gizlemek istiyorsanız, **Bu ayarı göz atılamaz olarak** ayarlayın. Erişimi programlara göre denetlemek istiyorsanız, **ayarlayıcı erişim değiştiricisi**' ni ayarlayın.|`False`|
|**Tip**|Etki alanı özelliği türü ( `Normal` , `Calculated` veya `CustomStorage` ). daha fazla bilgi için bkz. [hesaplanan ve özel Depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Ad**|Bu etki alanı özelliğinin adı. Bunun geçerli bir tanımlayıcı olması gerekir, örneğin **SongTitle**.|\<none>|
|**Notlar**|Bu etki alanı özelliği ile ilişkili resmi olmayan notlar.|\<none>|
|**Ayarlayıcı erişim değiştiricisi**|Ayarlayıcı için erişim değiştiricisi. Bu, program kodunun özelliği ayarlayabileceği kapsamı denetler.|`public`|
|**Tür**|Özelliğin türü. Kullanılabilir türler listesine eklemek için DSL Gezgini 'ndeki DSL köküne sağ tıklayın ve **dış tür Ekle**' ye tıklayın.|`String`|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))