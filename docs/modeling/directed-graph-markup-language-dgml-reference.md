---
title: Yönlendirilmiş Grafik Biçimlendirme Dili (DGML) başvurusu
description: Yönlendirilmiş grafik biçimlendirme dili 'nin (DGML) görselleştirme için kullanılan bilgileri nasıl açıklar ve karmaşıklık Analizi gerçekleştirmesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9abc3d3596a64c04bf25c0471d32a00f1cb7705d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935085"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Yönlendirilmiş Grafik Biçimlendirme Dili (DGML) başvurusu

Yönlendirilmiş grafik biçimlendirme dili (DGML) görselleştirme için kullanılan bilgileri açıklar ve karmaşıklık Analizi gerçekleştirir ve Visual Studio 'da kod eşlemelerini kalıcı hale getirmek için kullanılan biçimdir. Hem döngüsel hem de döngüsel olarak yönlendirilmiş grafikleri anlatmak için basit XML kullanır. Yönlendirilmiş bir grafik, bağlantılarla veya kenarlarla bağlanmış bir düğüm kümesidir. Düğümler ve bağlantılar, bir yazılım projesindeki öğeler gibi ağ yapılarını açıklamak için kullanılabilir.

Visual Studio 'nun bazı sürümlerinin yalnızca DGML özellikleri alt kümesini desteklediğine, bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Bir .dgml dosyasını düzenlerken, IntelliSense her öğe için kullanılabilen öznitelikleri ve değerlerini belirlemenize yardımcı olur. Bir öznitelikte renk belirlemek için "Mavi" gibi genel renklerin adlarını veya "#ffa0b1c3" gibi ARGB onaltılık değerlerini kullanın. DGML Windows Presentation Foundation (WPF) renk tanımı biçimlerinin küçük bir alt kümesini kullanır. Daha fazla bilgi için bkz. [renkler sınıfı](/dotnet/api/system.windows.media.colors?view=netframework-4.8&preserve-view=true).

## <a name="dgml-syntax"></a><a name="DGML"></a> DGML sözdizimi

Aşağıdaki tabloda DGML 'de kullanılan öğelerin türleri açıklanmaktadır:

- `<DirectedGraph></DirectedGraph>`

   Bu öğe, kod Haritası (. dgml) belgesinin kök öğesidir. Diğer tüm DGML öğeleri, bu öğe kapsamı içinde görünür.

   Aşağıdaki liste dahil edebileceğiniz isteğe bağlı öznitelikleri tanımlar:

   `Background` -Harita arka planının rengi

   `BackgroundImage` -Harita arka planı olarak kullanılacak bir görüntü dosyasının konumu.

   `GraphDirection` -Eşleme ağaç düzenine ( `Sugiyama` ) ayarlandığında, bağlantıların çoğunun belirtilen yönde akmasını sağlamak için düğümleri düzenleyin: `TopToBottom` , `BottomToTop` , `LeftToRight` veya `RightToLeft` . Bkz. [harita yerleşimini değiştirme](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout` -Haritayı şu düzenlerle ayarlayın: `None` , `Sugiyama` (ağaç düzeni), `ForceDirected` (hızlı kümeler) veya `DependencyMatrix` . Bkz. [harita yerleşimini değiştirme](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance` -Eşleme ağaç düzenine veya hızlı kümeler düzenine ayarlandığında, seçilen düğümlerden uzakta yalnızca belirtilen sayı (1-7) olan düğümleri gösterir. Bkz. [harita yerleşimini değiştirme](../modeling/browse-and-rearrange-code-maps.md#Selecting).

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

   Bu isteğe bağlı öğe `<Node/>` , haritadaki düğümleri tanımlayan öğelerin bir listesini içerir. Daha fazla bilgi için, bkz `<Node/>` . öğesi.

  > [!NOTE]
  > Bir öğesinde tanımsız bir düğüme başvurduğunuzda `<Link/>` , eşleme `<Node/>` otomatik olarak bir öğe oluşturur.

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

   Bu öğe tek bir düğümü tanımlar. Öğe listesi içinde görüntülenir `<Nodes><Nodes/>` .

   Bu öğenin öznitelikleri şunlardır:

   `Id` -Düğümün benzersiz adı ve `Label` ayrı bir öznitelik belirtilmemişse özniteliğin varsayılan değeri `Label` . Bu ad, `Source` `Target` ona başvuran bağlantının veya özniteliğiyle eşleşmelidir.

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` -Düğümün görünen adı.

   Stil öznitelikleri. Bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` -Bu özniteliği paylaşan öğeleri tanımlayan kategorinin adı. Daha fazla bilgi için, bkz `<Category/>` . öğesi.

   `Property` -Aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için, bkz `<Property/>` . öğesi.

   `Group` -Düğüm başka düğümler içeriyorsa, bu özniteliği `Expanded` `Collapsed` içeriğini göstermek veya gizlemek için veya olarak ayarlayın. `<Link/>`Özniteliği içeren bir öğe olmalıdır `Category="Contains"` ve hedef düğüm olarak ana düğümü kaynak düğüm ve alt düğüm olarak belirtir. Bkz. [grup kodu öğeleri](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility` -Bu özniteliği `Visible` , veya olarak ayarlayın `Hidden` `Collapsed` . Kullanır `System.Windows.Visibility` . Bkz. [düğümleri ve bağlantıları gizleme veya gösterme](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` -Bu özniteliği bir belge veya URL bağlantısı olacak şekilde ayarlayın. Bkz. [belge veya URL 'leri kod öğelerine ve bağlantılarına bağlama](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

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

   Bu öğe `<Link>` , düğümler arasındaki bağlantıları tanımlayan öğelerin listesini içerir. Daha fazla bilgi için, bkz `<Link/>` . öğesi.

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

   Bu öğe, bir kaynak düğümünü hedef düğüme bağlayan tek bir bağlantıyı tanımlar. Öğe listesi içinde görüntülenir `<Links></Links>` .

  > [!NOTE]
  > Bu öğe tanımsız bir düğüme başvuruyorsa, eşleme belgesi, varsa belirtilen özniteliklere sahip bir düğümü otomatik olarak oluşturur.

   Bu öğenin öznitelikleri şunlardır:

   `Source` -Bağlantının kaynak düğümü

   `Target` -Bağlantının hedef düğümü

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` -Bağlantının görünen adı

   Stil öznitelikleri. Bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category` -Bu özniteliği paylaşan öğeleri tanımlayan kategorinin adı. Daha fazla bilgi için, bkz `<Category/>` . öğesi.

   `Property` -Aynı özellik değerine sahip öğeleri tanımlayan bir özelliğin adı. Daha fazla bilgi için, bkz `<Property/>` . öğesi.

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

   Bu öğe, öğelerin listesini içerir `<Category/>` . Daha fazla bilgi için, bkz `<Category/>` . öğesi.

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

   Bu öğe `Category` , bu özniteliği paylaşan öğeleri tanımlamak için kullanılan bir özniteliği tanımlar. `Category`Öznitelik, harita öğelerini düzenlemek, devralma yoluyla paylaşılan öznitelikler sağlamak veya ek meta veri tanımlamak için kullanılabilir.

   Bu öğenin öznitelikleri şunlardır:

   `Id` -Kategorinin benzersiz adı ve `Label` ayrı bir öznitelik belirtilmemişse özniteliğin varsayılan değeri `Label` .

   Aşağıdaki liste, dahil edebileceğiniz isteğe bağlı özniteliklerin bazılarını açıklar:

   `Label` -Kategori için bir okuyucu kolay adı.

   `BasedOn` -Geçerli öğenin içinden devraldığı üst kategori `<Category/>` .

   Bu öğe için örneğinde `FailedTest` Kategori, `Stroke` kategorisinden özniteliğini devralır `PassedTest` . [Dgml dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)bölümünde "Hiyerarşik kategoriler oluşturmak için" bölümüne bakın.

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

   Bu öğe, öğelerin listesini içerir `<Property/>` . Daha fazla bilgi için, bkz `<Property/>` . öğesi.

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

   Bu öğe `Property` , herhangi BIR dgml öğesine veya özniteliğe bir değer atamak için kullanabileceğiniz bir özniteliği tanımlar, Kategoriler ve diğer özellikler dahil.

   Bu öğenin öznitelikleri şunlardır:

  - `Id` -Özelliğin benzersiz adı ve `Label` ayrı bir öznitelik belirtilmemişse özniteliğin varsayılan değeri `Label` .

  - `DataType` -Özelliği tarafından depolanan verilerin türü

    Özelliğin **Özellikler** penceresinde görünmesini istiyorsanız, özelliğin `Label` görünen adını belirtmek için özelliğini kullanın.

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

### <a name="aliases-for-commonly-used-paths"></a><a name="AddAlias"></a> Yaygın olarak kullanılan yolların diğer adları

Yaygın olarak kullanılan yolların takma adlarla değiştirilmesi .dgml dosyasının boyutunu azaltır ve dosyayı yüklemek veya kaydetmek için gereken süreyi kısaltır. Bir diğer ad oluşturmak için `<Paths></Paths>` . dgml dosyasının sonuna bir bölüm ekleyin. Bu bölümde, `<Path/>` yol için bir diğer ad tanımlamak üzere bir öğesi ekleyin:

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

. Dgml dosyasındaki bir öğeden diğer ada başvuru yapmak için, `Id` \<Path/> öğesini bir dolar işareti ($) ve parantez (()) ile birlikte alın:

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
