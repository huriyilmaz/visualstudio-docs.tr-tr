---
title: Üretilen Sınıfları Geçersiz Kılma ve Genişletme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3374f67f4fba11543e3dbbca47fef621dd2e714
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595897"
---
# <a name="override-and-extend-the-generated-classes"></a>Oluşturulan sınıfları geçersiz kılma ve genişletme

DSL tanımınız, etki alanına özgü bir dili temel alan güçlü bir araç kümesi oluşturabileceğiniz bir platformdur. Birçok uzantı ve uyarlamalar, DSL tanımından oluşturulan sınıfları geçersiz kılarak ve genişleterek yapılabilir. Bu sınıflar yalnızca DSL tanım diyagramında açıkça tanımladığınız etki alanı sınıflarını değil, ayrıca araç kutusu, Gezgin, serileştirme vb. tanımlayan diğer sınıfları da içerir.

## <a name="extensibility-mechanisms"></a>Genişletilebilirlik mekanizmaları

Oluşturulan kodu genişletmenize olanak tanımak için çeşitli mekanizmalar sağlanır.

### <a name="override-methods-in-a-partial-class"></a>Kısmi sınıftaki yöntemleri geçersiz kıl

Kısmi sınıf tanımları, bir sınıfın birden fazla yerde tanımlanmasını sağlar. Bu, oluşturduğunuz kodu kendi yazdığınız koddan ayırmanızı sağlar. El ile yazılmış kodunuzda, oluşturulan kod tarafından devralınan sınıfları geçersiz kılabilirsiniz.

Örneğin, DSL tanımınızda adlı bir etki alanı sınıfı tanımlarsanız `Book` , geçersiz kılma yöntemleri ekleyen özel kod yazabilirsiniz:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Oluşturulan bir sınıftaki yöntemleri geçersiz kılmak için, her zaman kodunuzu oluşturulan dosyalardan ayrılmış bir dosyaya yazın. Genellikle, dosya CustomCode adlı bir klasörde yer alır. Oluşturulan kodda değişiklik yaparsanız, bu kod, DSL tanımından kodu yeniden oluşturduğunuzda kaybedilir.

Geçersiz kılabileceğiniz yöntemleri öğrenmek için, sınıfa **geçersiz kılma** yazın ve ardından bir boşluk girin. IntelliSense araç ipucu size hangi yöntemlerin geçersiz kılınabileceğini söyleyecektir.

### <a name="double-derived-classes"></a>Çift türetilmiş sınıflar

Oluşturulan sınıflarda yöntemlerin çoğu, modelleme ad alanlarındaki sabit bir sınıf kümesinden devralınır. Ancak, bazı yöntemler oluşturulan kodda tanımlanmıştır. Normalde bu, bunları geçersiz kılamazsınız demektir; aynı sınıfın başka bir kısmi tanımında tanımlanan yöntemlerin tek bir kısmi sınıfta geçersiz kılınamaz.

Bununla birlikte, etki alanı sınıfı için **Double türetilmiş** bayrağını ayarlayarak bu yöntemleri geçersiz kılabilirsiniz. Bu, biri diğerinin soyut taban sınıfı olmak üzere iki sınıfın oluşturulmasına neden olur. Tüm Yöntem ve özellik tanımları temel sınıfta bulunur ve yalnızca Oluşturucu türetilmiş sınıfta bulunur.

Örneğin, örnek Library. dsl ' de, `CirculationBook` etki alanı sınıfının `Generates``Double Derived` özelliği olarak ayarlanır `true` . Bu alan sınıfı için oluşturulan kod iki sınıf içerir:

- `CirculationBookBase`, bir soyut ve tüm yöntem ve özellikleri içerir.

- `CirculationBook`, öğesinden türetilmiş `CirculationBookBase` . Oluşturucular dışında boştur.

Herhangi bir yöntemi geçersiz kılmak için, gibi türetilmiş sınıfın kısmi bir tanımını oluşturursunuz `CirculationBook` . Oluşturulan yöntemleri ve modelleme çerçevesinden devralınan yöntemleri geçersiz kılabilirsiniz.

Model öğeleri, ilişkiler, şekiller, diyagramlar ve bağlayıcılar dahil olmak üzere tüm öğe türleriyle bu yöntemi kullanabilirsiniz. Ayrıca, diğer oluşturulan sınıfların yöntemlerini geçersiz kılabilirsiniz. ToolboxHelper gibi bazı oluşturulan sınıflar her zaman çift türetilir.

### <a name="custom-constructors"></a>Özel oluşturucular

Oluşturucuyu geçersiz kılamazsınız. Çift türetilmiş sınıflarda bile, Oluşturucu türetilmiş sınıfta olmalıdır.

Kendi oluşturucuyu sağlamak istiyorsanız, `Has Custom Constructor` dsl tanımındaki etki alanı sınıfı için ayarı yaparak bunu yapabilirsiniz. **Tüm Şablonları Dönüştür**' e tıkladığınızda, oluşturulan kod bu sınıf için bir Oluşturucu içermez. Eksik oluşturucuya bir çağrı içerecektir. Bu, çözümü oluşturduğunuzda bir hata raporuna neden olur. Elde etmeniz gerekenleri açıklayan oluşturulan kodda bir açıklama görmek için hata raporuna çift tıklayın.

Oluşturulan dosyalardan ayrı bir dosyaya kısmi bir sınıf tanımı yazın ve oluşturucuyu sağlayın.

### <a name="flagged-extension-points"></a>Bayrak eklenmiş uzantı noktaları

Bayrak eklenmiş bir uzantı noktası, DSL tanımında bir özellik veya bir özel yöntem sağlayabileceğiniz bir onay kutusu ayarlayabileceğiniz yerdir. Özel oluşturucular bir örnektir. Diğer örneklerde, `Kind` bir etki alanı özelliğinin hesaplanmış veya özel depolama olarak ayarlanması ya da bir bağlantı oluşturucusunun **özel** bayrağını ayarlanması dahildir.

Her durumda, bayrağını ayarlayıp kodu yeniden oluşturduğunuzda bir yapı hatası olur. Sağlamanız gerekenleri açıklayan bir açıklama görmek için hataya çift tıklayın.

### <a name="rules"></a>Kurallar

İşlem Yöneticisi, bir özellikte değişiklik gibi, belirtilen bir olayın gerçekleştiği bir işlemin sonundan önce çalışan kurallar tanımlamanızı sağlar. Kurallar genellikle depodaki farklı öğeler arasında eşitlemeyi sürdürmek için kullanılır. Örneğin, diyagramın modelin geçerli durumunu görüntülediğinden emin olmak için kurallar kullanılır.

Kurallar her bir nesne için bir kural kaydeden koda sahip olmanız gerekmez, her sınıf temelinde tanımlanır. Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Olayları depola

Modelleme deposu, depodaki belirli değişiklik türlerini dinlemek için kullanabileceğiniz, öğelerin eklenmesi ve silinmesi, özellik değerlerinde değişiklikler vb. gibi bir olay mekanizması sağlar. Olay işleyicileri, değişikliklerin gerçekleştirildiği işlemin kapandıktan sonra çağrılır. Genellikle, bu olaylar mağaza dışındaki kaynakları güncelleştirmek için kullanılır.

### <a name="net-events"></a>.NET etkinlikleri

Şekillerdeki bazı olaylara abone olabilirsiniz. Örneğin, fare tıklamalarını bir şekle dönüştürebilirsiniz. Her nesne için olaya abone olan bir kod yazmanız gerekir. Bu kod, ınitializeınstanceresobir geçersiz kılma () ile yazılabilir.

Bazı olaylar, bir şekle dekoratörler çizmek için kullanılan ShapeFields üzerinde oluşturulur. Bir örnek için bkz. [nasıl yapılır: bir şekle veya Dekorata tıklama](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Bu olaylar genellikle bir işlem içinde gerçekleşmez. Mağazada değişiklik yapmak istiyorsanız bir işlem oluşturmanız gerekir.
