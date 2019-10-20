---
title: Etki alanı özelliklerinin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cdba41913273b9db574afd87f5542df0fb597ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671478"
---
# <a name="properties-of-domain-properties"></a>Etki Alanı Özelliklerinin Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir *alan özelliği* , bir değeri tutabilecek bir model öğesinin özelliğidir. Örneğin, `Person` etki alanı sınıfı, `Name` ve `BirthDate` özelliklerine sahip olabilir. DSL tanımında etki alanı özellikleri, diyagramdaki etki alanı sınıfı kutusunda ve DSL Gezgini 'ndeki etki alanı sınıfında listelenir. Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> "Property" sözcüğünün iki kullanımı vardır. Bir *etki alanı özelliği* , bir etki alanı sınıfında tanımladığınız bir özelliktir. Buna karşılık, bir DSL 'nin birçok öğesi DSL tanımındaki **Özellikler** penceresinde listelenen *özelliklere*sahiptir. Örneğin, her etki alanı özelliği, bu konuda açıklanan bir dizi özellik içerir.

 Çalışma zamanında, bir kullanıcı etki alanı sınıfının örneklerini oluşturduğunda, etki alanı özelliklerinin değerleri Özellikler penceresi görünebilir ve şekiller üzerinde görüntülenebilir.

 Çoğu etki alanı özelliği sıradan CLR özellikleri olarak uygulanır. Ancak, bir programlama noktasından, etki alanı özellikleri sıradan program özelliklerinden daha zengin işlevlere sahiptir:

- Bir özelliğin durumunu izleyen kuralları ve olayları tanımlayabilirsiniz. Daha fazla bilgi için bkz. [değişiklikleri yanıtlama ve yayma](../modeling/responding-to-and-propagating-changes.md).

- İşlemler tutarsız durumları önlemeye yardımcı olur. Daha fazla bilgi için bkz. [program kodunda modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Bir diyagramda veya DSL Gezgininde bir etki alanı özelliği seçtiğinizde, Özellikler penceresi aşağıdaki öğeleri görebilirsiniz. Bu öğelerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan Değer|
|--------------|-----------------|-------------------|
|**Açıklama**|Oluşturulan tasarımcının Kullanıcı arabirimini (UI) belgelemek için kullanılan açıklama.|\<none >|
|**Görünen ad**|Bu etki alanı özelliği için oluşturulan tasarımcıda görüntülenecek ad. Boşluk ve noktalama işareti içerebilir, örneğin "şarkı başlığı".|\<none >|
|**Öğe adı sağlayıcı**|Bu, yalnızca `true` `Is Element Name` ayarladıysanız geçerlidir. Bir etki alanı sınıfının yeni bir öğesi için bir ad sağlayan, varsayılan davranışı geçersiz kılan bir kod yazabilirsiniz.<br /><br /> DSL projesindeki bir kod dosyasında, <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> türetilen bir sınıf oluşturun.<br /><br /> Ardından DSL Gezgini ' nde DSL köküne sağ tıklayın ve dış tür Ekle ' ye tıklayın. Sınıfınızın adını girin.<br /><br /> Bu etki alanı özelliğini yeniden seçin ve açılan listeden sınıfın adını seçin.|\<none >|
|**Alıcı erişim değiştiricisi**|Etki alanı sınıfına erişim düzeyi (`public` veya `internal`). Bu, program kodunun özelliğe erişebileceği kapsamı denetler.|`public`|
|**Help anahtar sözcüğü**|Bu etki alanı özelliği için F1 yardımını dizine eklemek için kullanılan isteğe bağlı anahtar sözcük.|\<none >|
|**Göz atılamaz**|@No__t_0, bu DSL modelleri açık olduğunda, Özellikler penceresindeki kullanıcıya etki alanı özelliği görüntülenir.<br /><br /> @No__t_0, etki alanı özelliği Kullanıcı arabiriminde gizlenir.<br /><br /> Etki alanı özelliğini görünür halde salt okunurdur, küme **yalnızca kullanıcı arabirimi salt okunurdur**.|`True`|
|**Öğe adı**|@No__t_0, bu etki alanı özelliği DSL Gezgini 'ndeki model öğesinin adı olarak görüntülenecektir.<br /><br /> Yeni model öğeleri, bu özellik için benzersiz bir varsayılan değer alacaktır. Bu değerlerin nasıl oluşturulduğunu denetlemek istiyorsanız, **öğe adı sağlayıcısı**' nı ayarlayın.|`False`|
|**UI salt okunurdur**|@No__t_0, Domain özelliğinin değeri kullanıcı arabirimi kullanılarak değiştirilemez. Hala programlar tarafından ayarlanabilir ve Özellikler penceresi görünür olur.<br /><br /> Etki alanı özelliğini kullanıcıdan gizlemek istiyorsanız, **Bu ayarı göz atılamaz olarak**ayarlayın. Erişimi programlara göre denetlemek istiyorsanız, **ayarlayıcı erişim değiştiricisi**' ni ayarlayın.|`False`|
|**Denetlenmesi**|Etki alanı özelliği türü (`Normal`, `Calculated` veya `CustomStorage`). Daha fazla bilgi için bkz. [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Ad**|Bu etki alanı özelliğinin adı. Bunun geçerli bir tanımlayıcı olması gerekir, örneğin **SongTitle**.|\<none >|
|**Notlar**|Bu etki alanı özelliği ile ilişkili resmi olmayan notlar.|\<none >|
|**Ayarlayıcı erişim değiştiricisi**|Ayarlayıcı için erişim değiştiricisi. Bu, program kodunun özelliği ayarlayabileceği kapsamı denetler.|`public`|
|**Türüyle**|Özelliğin türü. Kullanılabilir türler listesine eklemek için DSL Gezgini 'ndeki DSL köküne sağ tıklayın ve **dış tür Ekle**' ye tıklayın.|`String`|

## <a name="see-also"></a>Ayrıca Bkz.
 [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
