---
title: Üretilen Sınıfları Geçersiz Kılma ve Genişletme
description: DSL Tanımınızı, etki alanına özgü bir dili temel alan güçlü bir araç kümesi oluşturmak için kullanılan bir platform olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07c44e7ff7a603f339ec268b06bd78cc84cd6be2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390951"
---
# <a name="override-and-extend-the-generated-classes"></a>Oluşturulan sınıfları geçersiz kılma ve genişletme

DSL Tanımınız, etki alanına özgü bir dili temel alan güçlü bir araç kümesi oluşturabilirsiniz. DSL Tanımından oluşturulan sınıfları geçersiz kılabilir ve genişleterek birçok uzantı ve uyarlama yapabilirsiniz. Bu sınıflar yalnızca DSL Tanım diyagramında açıkça tanımladığınız etki alanı sınıflarını değil araç kutusunu, gezgini, serileştirmeyi ve diğer sınıfları da içerir.

## <a name="extensibility-mechanisms"></a>Genişletilebilirlik Mekanizmaları

Oluşturulan kodu genişletmeye olanak sağlayan çeşitli mekanizmalar sağlanır.

### <a name="override-methods-in-a-partial-class"></a>Kısmi sınıftaki yöntemleri geçersiz kılma

Kısmi sınıf tanımları, bir sınıfın birden fazla yerde tanımlandığına olanak sağlar. Bu, oluşturulan kodu kendi yazmakta olduğu koddan ayırmaya olanak sağlar. El ile yazılmış kodunda, oluşturulan kod tarafından devralınan sınıfları geçersiz kılabilirsiniz.

Örneğin DSL Tanımında adlı bir etki alanı sınıfı tanımlarsanız geçersiz kılma `Book` yöntemleri ekleyen özel kodlar yazabilirsiniz:

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
> Oluşturulan bir sınıftaki yöntemleri geçersiz kılmak için kodunuzu her zaman oluşturulan dosyalardan ayrılmış bir dosyaya yazın. Dosya genellikle CustomCode adlı bir klasörde bulunur. Oluşturulan kodda değişiklik yaptısanız, DSL Tanımından kodu yeniden yeniden özel hale gelirsiniz.

Geçersiz kılarak hangi yöntemlerin olduğunu bulmak için sınıfında **geçersiz kılma** yazın ve ardından bir boşluk yazın. IntelliSense araç ipucu hangi yöntemlerin geçersiz kılınabilir olduğunu söyler.

### <a name="double-derived-classes"></a>Double-Derived Sınıfları

Oluşturulan sınıflarda yöntemlerin çoğu Modelleme ad alanlarındaki sabit bir sınıf kümesinden devralınır. Ancak, bazı yöntemler oluşturulan kodda tanımlanır. Normalde bu, bunları geçersiz kılamaz; Bir kısmi sınıfta, aynı sınıfın başka bir kısmi tanımında tanımlanan yöntemleri geçersiz kamazsiniz.

Bununla birlikte, etki alanı sınıfı için Çift Türetilmiş Oluştur bayrağını **ayarerek** bu yöntemleri geçersiz kılabilirsiniz. Bu, biri diğerin soyut bir temel sınıfı olmak için iki sınıfın oluşturularak neden olur. Tüm yöntem ve özellik tanımları temel sınıftadır ve yalnızca oluşturucu türetilmiş sınıftadır.

Örneğin, örnek Library.dsl'de, `CirculationBook` etki alanı sınıfının özelliği olarak `Generates``Double Derived` `true` ayarlanmıştır. Bu etki alanı sınıfı için oluşturulan kod iki sınıf içerir:

- `CirculationBookBase`, soyuttur ve tüm yöntemleri ve özellikleri içerir.

- `CirculationBook`, türetilen `CirculationBookBase` . Oluşturucuları dışında boştur.

Herhangi bir yöntemi geçersiz kılmak için türetilmiş sınıfın gibi kısmi bir tanımını `CirculationBook` oluşturun. Hem oluşturulan yöntemleri hem de modelleme çerçevesinden devralınan yöntemleri geçersiz kılebilirsiniz.

Bu yöntemi model öğeleri, ilişkiler, şekiller, diyagramlar ve bağlayıcılar dahil olmak üzere tüm öğe türleriyle birlikte kullanabilirsiniz. Ayrıca, oluşturulan diğer sınıfların yöntemlerini geçersiz kılabilirsiniz. ToolboxHelper gibi oluşturulan bazı sınıflar her zaman iki kez türetilmiştir.

### <a name="custom-constructors"></a>Özel Oluşturucular

Oluşturucu geçersiz kılınamaz. Çift türetilmiş sınıflarda bile, oluşturucu türetilmiş sınıfta yer amalıdır.

Kendi oluşturucularınızı sağlamak için DSL Tanımı'nın etki alanı sınıfı `Has Custom Constructor` ayarını kullanarak bunu yapabiliriz. Tüm Şablonları **Dönüştür'e tıklarsanız,** oluşturulan kod o sınıf için bir oluşturucu eklemez. Eksik oluşturucuya bir çağrı içerir. Bu, çözümü derleme sırasında bir hata raporuna neden olur. Oluşturulan kodda neleri sağlamanız gerektiğini açıklayan bir açıklama görmek için hata raporuna çift tıklayın.

Oluşturulan dosyalardan ayrı bir dosyada kısmi sınıf tanımı yazın ve oluşturucusu sağlar.

### <a name="flagged-extension-points"></a>Bayraklı Uzantı Noktaları

Bayraklı uzantı noktası, DSL Tanımı'nın içinde özel bir yöntem belirtecek bir özellik veya onay kutusu ayaryabilirsiniz. Özel oluşturucular bir örnektir. Diğer örnekler arasında, bir etki alanı özelliğinin Hesaplanmış veya Özel Depolama olarak ayarlanması veya bağlantı `Kind` oluşturucuda **Özeldir** bayrağının ayarlanması yer almaktadır.

Her durumda bayrağını ayarip kodu yeniden üretip derleme hatasıyla sonuçlandırabilirsiniz. Sağlamanız gerekenleri açıklayan bir açıklama görmek için hataya çift tıklayın.

### <a name="rules"></a>Kurallar

İşlem yöneticisi, bir özelliğinde değişiklik gibi belirlenmiş bir olayın meydana geldiği bir işlem sona ermeden önce çalıştıracak kuralları tanımlamanıza olanak sağlar. Kurallar genellikle depoda bulunan farklı öğeler arasında zaman uyumluluk sağlamak için kullanılır. Örneğin, diyagramda modelin geçerli durumunun görüntü olduğundan emin olmak için kurallar kullanılır.

Kurallar, her nesne için kuralı kaydeden koda sahip olmak zorunda olmadığınız için sınıf bazında tanımlanır. Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

### <a name="store-events"></a>Olayları Depolama

Modelleme deposu, öğe ekleme ve silme, özellik değerlerinde yapılan değişiklikler gibi depoda belirli değişiklik türlerini dinlemek için kullanabileceğiniz bir olay mekanizması sağlar. Olay işleyicileri, değişikliklerin olduğu işlem kapat edildikten sonra çağrılır. Bu olaylar genellikle depo dışındaki kaynakları güncelleştirmek için kullanılır.

### <a name="net-events"></a>.NET Olayları

Şekiller üzerinde bazı olaylara abone olabilirsiniz. Örneğin, bir şekle fare tıklamalarını dinleyebilirsiniz. Her nesne için olayına abone olan kod yazmanız gerekir. Bu kod InitializeInstanceResources() geçersiz kılınarak yazabilir.

Şekil Alanlarına bazı olaylar oluşturulur ve bu olaylar bir şekle dekoratör çizmek için kullanılır. Bir örnek için, [bkz. How to: Intercept a Click on a Shape or Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Bu olaylar genellikle bir işlem içinde oluşmaz. Mağazada değişiklik yapmak için bir işlem oluşturmanız gerekir.
