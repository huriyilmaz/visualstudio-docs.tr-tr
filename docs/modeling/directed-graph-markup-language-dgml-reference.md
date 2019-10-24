---
title: Yönlendirilmiş Grafik Biçimlendirme Dili (DGML) başvurusu
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b038acd9527cae197223e288349e431e81ea6dd6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748402"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Yönlendirilmiş Grafik Biçimlendirme Dili (DGML) başvurusu

Yönlendirilmiş grafik biçimlendirme dili (DGML) görselleştirme için kullanılan bilgileri açıklar ve karmaşıklık Analizi gerçekleştirir ve Visual Studio 'da kod eşlemelerini kalıcı hale getirmek için kullanılan biçimdir. Hem döngüsel hem de döngüsel olarak yönlendirilmiş grafikleri anlatmak için basit XML kullanır. Yönlendirilmiş bir grafik, bağlantılarla veya kenarlarla bağlanmış bir düğüm kümesidir. Düğümler ve bağlantılar, bir yazılım projesindeki öğeler gibi ağ yapılarını açıklamak için kullanılabilir.

Visual Studio 'nun bazı sürümlerinin yalnızca DGML özellikleri alt kümesini desteklediğine, bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Bir .dgml dosyasını düzenlerken, IntelliSense her öğe için kullanılabilen öznitelikleri ve değerlerini belirlemenize yardımcı olur. Bir öznitelikte renk belirlemek için "Mavi" gibi genel renklerin adlarını veya "#ffa0b1c3" gibi ARGB onaltılık değerlerini kullanın. DGML Windows Presentation Foundation (WPF) renk tanımı biçimlerinin küçük bir alt kümesini kullanır. Daha fazla bilgi için bkz. [renkler sınıfı](http://go.microsoft.com/fwlink/?LinkId=182345).

## <a name="DGML"></a>DGML sözdizimi

Aşağıdaki tabloda DGML 'de kullanılan öğelerin türleri açıklanmaktadır:

- `<DirectedGraph></DirectedGraph>`

   Bu öğe, kod Haritası (. dgml) belgesinin kök öğesidir. Diğer tüm DGML öğeleri, bu öğe kapsamı içinde görünür.

   Aşağıdaki liste dahil edebileceğiniz isteğe bağlı öznitelikleri tanımlar:

   `Background`-harita arka planının rengi

   `BackgroundImage`-harita arka planı olarak kullanılacak bir görüntü dosyasının konumu.

   `GraphDirection`-harita ağaç düzenine (`Sugiyama`) ayarlandığında, bağlantıların çoğunun belirtilen yönde akmasını sağlamak için düğümleri düzenleyin: `TopToBottom`, `BottomToTop`, `LeftToRight` veya `RightToLeft`. Bkz. [harita yerleşimini değiştirme](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout`-Haritayı şu düzenlerle ayarlayın: `None`, `Sugiyama` (ağaç düzeni), `ForceDirected` (hızlı kümeler) veya `DependencyMatrix`. Bkz. [harita yerleşimini değiştirme](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance`-eşleme ağaç düzenine veya hızlı kümeler düzenine ayarlandığında, seçilen düğümlerden uzakta bulunan bağlantıların yalnızca belirtilen sayısı (1-7) olan düğümleri gösterir. Bkz. [harita yerleşimini değiştirme](../modeling/browse-and-rearrange-code-maps.md#Selecting).

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

   Bu isteğe bağlı öğe, haritadaki düğümleri tanımlayan `<Node/>` öğelerinin bir listesini içerir. Daha fazla bilgi için `<Node/>` öğesine bakın.

  > [!NOTE]
  > Bir `<Link/>` öğesinde tanımsız bir düğüme başvurduğunuzda, eşleme otomatik olarak bir `<Node/>` öğesi oluşturur.

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

   Bu öğe tek bir düğümü tanımlar. @No__t_0 öğesi listesi içinde görünür.

   Bu öğenin öznitelikleri şunlardır:

   `Id`-ayrı bir `Label` özniteliği belirtilmediyse, düğümün benzersiz adı ve `Label` özniteliğinin varsayılan değeri. Bu ad, ona başvuran bağlantının `Source` veya `Target` özniteliğiyle eşleşmelidir.

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label`-düğümün görünen adı.

   Stil öznitelikleri. Bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`-bu özniteliği paylaşan öğeleri tanımlayan kategorinin adı. Daha fazla bilgi için `<Category/>` öğesine bakın.

   `Property`-aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için `<Property/>` öğesine bakın.

   `Group`-düğüm diğer düğümleri içeriyorsa, içeriğini göstermek veya gizlemek için bu özniteliği `Expanded` veya `Collapsed` olarak ayarlayın. @No__t_1 özniteliğini içeren bir `<Link/>` öğesi olmalıdır ve kaynak düğüm ve alt düğüm olarak ana düğümü hedef düğüm olarak belirtir. Bkz. [grup kodu öğeleri](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility`-bu özniteliği `Visible`, `Hidden` veya `Collapsed` olarak ayarlayın. @No__t_0 kullanır. Bkz. [düğümleri ve bağlantıları gizleme veya gösterme](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference`-bu özniteliği bir belge veya URL bağlantısı olacak şekilde ayarlayın. Bkz. [belge veya URL 'leri kod öğelerine ve bağlantılarına bağlama](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

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

   Bu öğe, düğümler arasındaki bağlantıları tanımlayan `<Link>` öğelerinin listesini içerir. Daha fazla bilgi için `<Link/>` öğesine bakın.

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

   Bu öğe, bir kaynak düğümünü hedef düğüme bağlayan tek bir bağlantıyı tanımlar. @No__t_0 öğesi listesi içinde görünür.

  > [!NOTE]
  > Bu öğe tanımsız bir düğüme başvuruyorsa, eşleme belgesi, varsa belirtilen özniteliklere sahip bir düğümü otomatik olarak oluşturur.

   Bu öğenin öznitelikleri şunlardır:

   `Source`-bağlantının kaynak düğümü

   `Target`-bağlantının hedef düğümü

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label`-bağlantının görünen adı

   Stil öznitelikleri. Bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`-bu özniteliği paylaşan öğeleri tanımlayan kategorinin adı. Daha fazla bilgi için `<Category/>` öğesine bakın.

   `Property`-aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için `<Property/>` öğesine bakın.

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

   Bu öğe `<Category/>` öğelerinin listesini içerir. Daha fazla bilgi için `<Category/>` öğesine bakın.

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

   Bu öğe, bu özniteliği paylaşan öğeleri tanımlamak için kullanılan bir `Category` özniteliğini tanımlar. Bir `Category` özniteliği harita öğelerini düzenlemek, devralma yoluyla paylaşılan öznitelikler sağlamak veya ek meta veri tanımlamak için kullanılabilir.

   Bu öğenin öznitelikleri şunlardır:

   `Id`, ayrı bir `Label` özniteliği belirtilmediyse kategorinin benzersiz adı ve `Label` özniteliğinin varsayılan değeri.

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label`-kategori için bir okuyucu kolay adı.

   `BasedOn`-geçerli öğenin `<Category/>` devraldığı üst kategori.

   Bu öğe için örneğinde, `FailedTest` kategorisi `PassedTest` kategorisinden `Stroke` özniteliğini devralır. [Dgml dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)bölümünde "Hiyerarşik kategoriler oluşturmak için" bölümüne bakın.

   Kategoriler Ayrıca, bir haritada görüntülendiklerinde düğümlerin ve bağlantıların görünümünü denetleyen bazı temel şablon davranışlarını de sağlar. Bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

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

   Bu öğe `<Property/>` öğelerinin listesini içerir. Daha fazla bilgi için `<Property/>` öğesine bakın.

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

   Bu öğe, Kategoriler ve diğer özellikler de dahil olmak üzere herhangi bir DGML öğesine veya özniteliğe değer atamak için kullanabileceğiniz bir `Property` özniteliği tanımlar.

   Bu öğenin öznitelikleri şunlardır:

  - `Id`-ayrı bir `Label` özniteliği belirtilmediyse özelliğin benzersiz adı ve `Label` özniteliğinin varsayılan değeri.

  - `DataType`-özellik tarafından depolanan verilerin türü

    Özelliğin **Özellikler** penceresinde görünmesini istiyorsanız, özelliğin görünen adını belirtmek için `Label` özelliğini kullanın.

    Bkz. [kod öğelerine ve bağlantılara kategori atama](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

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

### <a name="AddAlias"></a>Yaygın olarak kullanılan yolların diğer adları

Yaygın olarak kullanılan yolların takma adlarla değiştirilmesi .dgml dosyasının boyutunu azaltır ve dosyayı yüklemek veya kaydetmek için gereken süreyi kısaltır. Bir diğer ad oluşturmak için. dgml dosyasının sonuna bir `<Paths></Paths>` bölümü ekleyin. Bu bölümde, yol için bir diğer ad tanımlamak üzere bir `<Path/>` öğesi ekleyin:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

. Dgml dosyasındaki bir öğeden diğer ada başvuru yapmak için \<Path/> öğesinin `Id` dolar işareti ($) ve parantez (()) arasına koyun:

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
- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)