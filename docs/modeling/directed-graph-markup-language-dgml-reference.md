---
title: Yönlendirilmiş Grafik Biçimlendirme Dili (DGML) başvurusu
description: Yönlendirilen Graf Biçimlendirme Dili'nin (DGML) görselleştirme için kullanılan bilgileri ve karmaşıklık analizini nasıl gerçekleştireceklerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adaa09ca7c58652c85cf6c3510e9e47bc4af00f3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389117"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Yönlendirilmiş Grafik Biçimlendirme Dili (DGML) başvurusu

Yönlendirilen Graf Biçimlendirme Dili (DGML), görselleştirme ve karmaşıklık analizi gerçekleştirmek için kullanılan bilgileri açıklar ve kod eşlemelerini görselleştirmede kalıcı hale Visual Studio. Hem döngüsel hem de döngüsel yönlendirilen grafikleri açıklamak için basit XML kullanır. Yönlendirilmiş bir grafik, bağlantılarla veya kenarlarla bağlanmış bir düğüm kümesidir. Düğümler ve bağlantılar, bir yazılım projesindeki öğeler gibi ağ yapılarını açıklamak için kullanılabilir.

Bazı sürüm sürümlerinin DGML Visual Studio yalnızca bir alt kümesini desteklemektedir. Bkz. Mimari ve modelleme [araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

> [!NOTE]
> Bir .dgml dosyasını düzenlerken, IntelliSense her öğe için kullanılabilen öznitelikleri ve değerlerini belirlemenize yardımcı olur. Bir öznitelikte renk belirlemek için "Mavi" gibi genel renklerin adlarını veya "#ffa0b1c3" gibi ARGB onaltılık değerlerini kullanın. DGML Windows Presentation Foundation (WPF) renk tanımı biçimlerinin küçük bir alt kümesini kullanır. Daha fazla bilgi için bkz. [Colors Sınıfı.](/dotnet/api/system.windows.media.colors?view=netframework-4.8&preserve-view=true)

## <a name="dgml-syntax"></a><a name="DGML"></a> DGML söz dizimi

Aşağıdaki tabloda DGML'de kullanılan öğe türleri açık almaktadır:

- `<DirectedGraph></DirectedGraph>`

   Bu öğe, kod eşlemesi (.dgml) belgesinin kök öğesidir. Diğer tüm DGML öğeleri, bu öğe kapsamı içinde görünür.

   Aşağıdaki liste dahil edebileceğiniz isteğe bağlı öznitelikleri tanımlar:

   `Background` - Harita arka planının rengi

   `BackgroundImage` - Harita arka planı olarak kullanmak üzere bir görüntü dosyasının konumu.

   `GraphDirection` - Harita ağaç düzenine ( ) ayarlanırsa, bağlantıların çoğunun belirtilen yönde akacak şekilde düğümleri `Sugiyama` ayarlayın: `TopToBottom` , , veya `BottomToTop` `LeftToRight` `RightToLeft` . Bkz. [Harita düzenini değiştirme.](../modeling/browse-and-rearrange-code-maps.md#Selecting)

   `Layout` - Haritayı şu düzenlere ayarlayın: `None` , `Sugiyama` (ağaç düzeni), `ForceDirected` (hızlı kümeler) veya `DependencyMatrix` . Bkz. [Harita düzenini değiştirme.](../modeling/browse-and-rearrange-code-maps.md#Selecting)

   `NeighborhoodDistance` - Harita ağaç düzenine veya hızlı küme düzenine ayarlanırsa, yalnızca seçili düğümlerden uzakta bağlantıların belirtilen sayıdaki (1-7) düğümlerini gösterir. Bkz. [Harita düzenini değiştirme.](../modeling/browse-and-rearrange-code-maps.md#Selecting)

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Bu isteğe bağlı öğe, `<Node/>` harita üzerinde düğümleri tanımlayan öğelerin listesini içerir. Daha fazla bilgi için `<Node/>` bkz. öğesi.

  > [!NOTE]
  > Bir öğedeki tanımsız bir düğüme `<Link/>` başvurduğda, eşleme otomatik olarak bir `<Node/>` öğe oluşturur.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Bu öğe tek bir düğümü tanımlar. Öğe listesinde `<Nodes><Nodes/>` görünür.

   Bu öğenin öznitelikleri şunlardır:

   `Id` - Ayrı bir öznitelik belirtilmezse düğümün benzersiz `Label` adı ve özniteliğin `Label` varsayılan değeri. Bu ad, ona `Source` `Target` başvurulan bağlantının veya özniteliğiyle eşleşmeli.

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` - Düğümün görünen adı.

   Stil öznitelikleri. Bkz. [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

   `Category` - Bu özniteliği paylaşan öğeleri tanımlayan bir kategorinin adı. Daha fazla bilgi için `<Category/>` bkz. öğesi.

   `Property` - Aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için `<Property/>` bkz. öğesi.

   `Group` - Düğüm başka düğümler içeriyorsa, içeriğini göstermek veya gizlemek için bu `Expanded` `Collapsed` özniteliği veya olarak ayarlayın. özniteliğini içeren ve üst düğümü kaynak düğüm ve alt düğümü hedef düğüm olarak `<Link/>` belirten bir öğe olması `Category="Contains"` gerekir. Bkz. [Kod öğelerini grupla.](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes)

   `Visibility` - Bu özniteliği `Visible` , veya olarak `Hidden` `Collapsed` ayarlayın. `System.Windows.Visibility`kullanır. Bkz. [Düğümleri ve bağlantıları gizleme veya gösterme.](../modeling/browse-and-rearrange-code-maps.md#HidingShowing)

   `Reference` - Bu özniteliği bir belgeye veya URL'ye bağlantı olarak ayarlayın. Bkz. [Belge veya URL'leri kod öğelerine ve bağlantılarına bağlama.](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences)

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Bu öğe, düğümler `<Link>` arasındaki bağlantıları tanımlayan öğelerin listesini içerir. Daha fazla bilgi için `<Link/>` bkz. öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Bu öğe, bir kaynak düğümünü hedef düğüme bağlayan tek bir bağlantıyı tanımlar. Öğe listesinde `<Links></Links>` görünür.

  > [!NOTE]
  > Bu öğe tanımlanmamış bir düğüme başvurursa, eşleme belgesi otomatik olarak belirtilen özniteliklere sahip bir düğüm oluşturur (varsa).

   Bu öğenin öznitelikleri şunlardır:

   `Source` - Bağlantının kaynak düğümü

   `Target` - Bağlantının hedef düğümü

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` - Bağlantının görünen adı

   Stil öznitelikleri. Bkz. [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

   `Category` - Bu özniteliği paylaşan öğeleri tanımlayan bir kategorinin adı. Daha fazla bilgi için `<Category/>` bkz. öğesi.

   `Property` - Aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için `<Property/>` bkz. öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Bu öğe öğe listesini `<Category/>` içerir. Daha fazla bilgi için `<Category/>` bkz. öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Bu öğe, `Category` bu özniteliği paylaşan öğeleri tanımlamak için kullanılan bir özniteliği tanımlar. Öznitelik, eşleme öğelerini düzenlemek, devralma yoluyla paylaşılan öznitelikler sağlamak veya ek meta `Category` veriler tanımlamak için kullanılabilir.

   Bu öğenin öznitelikleri şunlardır:

   `Id` - Ayrı bir öznitelik belirtilmezse, kategorinin benzersiz `Label` adı ve özniteliğin `Label` varsayılan değeri.

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` - Kategori için okuyucu dostu bir ad.

   `BasedOn` - Geçerli öğenin `<Category/>` öğesinin devralınma üst kategorisi.

   Bu öğenin örneğinde, `FailedTest` kategori özniteliğini `Stroke` kategoriden `PassedTest` devralıyor. DGML dosyalarını düzenleyerek kod haritalarını [özelleştirme'de "Hiyerarşik kategoriler oluşturmak](../modeling/customize-code-maps-by-editing-the-dgml-files.md)için" 'ye bakın.

   Kategoriler ayrıca bir haritada görüntülenen düğümlerin ve bağlantıların görünümünü kontrol eden bazı temel şablon davranışları da sağlar. Bkz. [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Bu öğe öğe listesini `<Property/>` içerir. Daha fazla bilgi için `<Property/>` bkz. öğesi.

   Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Bu öğe, kategoriler ve diğer özellikler de dahil olmak üzere herhangi bir DGML öğesine veya özniteliğine değer atamak `Property` için kullanabileceğiniz bir özniteliği tanımlar.

   Bu öğenin öznitelikleri şunlardır:

  - `Id` - Özelliğin benzersiz adı ve ayrı bir öznitelik `Label` belirtilmezse özniteliğin `Label` varsayılan değeri.

  - `DataType` - özelliği tarafından depolanan veri türü

    Özelliğin Özellikler penceresinde görünmesini **görmek için** özelliğini `Label` kullanarak özelliğin görünen adını belirtin.

    Bkz. [Kod öğelerine kategorileri atama ve bağlantıları.](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories)

    Örnek:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="aliases-for-commonly-used-paths"></a><a name="AddAlias"></a> Yaygın olarak kullanılan yollar için diğer adlar

Yaygın olarak kullanılan yolların takma adlarla değiştirilmesi .dgml dosyasının boyutunu azaltır ve dosyayı yüklemek veya kaydetmek için gereken süreyi kısaltır. Diğer ad oluşturmak için `<Paths></Paths>` .dgml dosyasının sonuna bir bölüm ekleyin. Bu bölümde, yol için `<Path/>` bir diğer ad tanımlamak üzere bir öğesi ekleyin:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

.dgml dosyasındaki bir öğeden diğer ada başvuru yapmak için öğenin içine bir dolar işareti ($) ve parantez `Id` \<Path/> (()) girin:

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
