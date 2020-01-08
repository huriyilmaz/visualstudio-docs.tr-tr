---
title: DGML dosyalarını düzenleyerek kod haritalarını özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b79fd73713de535c11062fd6396abde6b1a0131
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590520"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>DGML dosyalarını düzenleyerek kod haritalarını özelleştirme

Bir kod eşlemesini özelleştirmek için, onun yönlendirilmiş grafik biçimlendirme dili (. dgml) dosyasını düzenleyebilirsiniz. Örneğin, özel stilleri belirlemek, kod öğelerine ve bağlantılarına Özellikler ve kategoriler atamak ya da belge veya URL 'Leri kod öğelerine ya da bağlantılara bağlamak için öğeleri düzenleyebilirsiniz. DGML öğeleri hakkında daha fazla bilgi için bkz. [yönlendirilmiş grafik biçimlendirme dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md).

Kod haritasının. dgml dosyasını bir metin veya XML düzenleyicisinde düzenleyin. Eşleme, Visual Studio çözümünüzün bir parçasıysa, **Çözüm Gezgini**seçin, kısayol menüsünü açın ve **birlikte Aç**, **XML (metin) Düzenleyicisi**' ni seçin.

> [!NOTE]
> Kod eşlemeleri oluşturmak için Visual Studio Enterprise sürüme sahip olmanız gerekir. Visual Studio 'da bir kod haritasını düzenlediğinizde,. dgml dosyasını kaydettiğinizde kullanılmayan DGML öğelerini ve özniteliklerini temizler. Ayrıca, el ile yeni bağlantılar eklediğinizde kod öğeleri otomatik olarak oluşturulur. .dgml dosyasını kaydettiğinizde, bir öğeye eklediğiniz tüm öznitelikler kendilerini alfabetik sırada yeniden düzenleyebilir.

## <a name="OrganizeNodes"></a>Kod öğelerini Gruplandır
 Yeni gruplar ekleyebilir veya varolan düğümleri bir gruba dönüştürebilirsiniz.

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Bir kod öğesini bir gruba dönüştürmek için, bu kod öğesi için `<Node/>` öğesini bulun.

    \- veya -

    Yeni bir grup eklemek için `<Nodes>` bölümünü bulun. Yeni bir `<Node/>` öğesi ekleyin.

3. `<Node/>` öğesinde, grubun genişletilmiş mı yoksa daraltılmış mi göründüğünü belirtmek için bir `Group` özniteliği ekleyin. Örneğin:

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. `<Links>` bölümünde, bir grup kodu öğesi ve onun alt kod öğeleri arasındaki her ilişki için aşağıdaki özniteliklere sahip bir `<Link/>` öğesinin bulunduğundan emin olun:

   - Grup Kodu öğesini belirten bir `Source` özniteliği

   - Alt kod öğesini belirten bir `Target` özniteliği

   - Grup kodu öğesi ve onun alt kod öğesi arasında bir `Contains` ilişkisi belirten `Category` özniteliği

     Örneğin:

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    `Category` özniteliği hakkında daha fazla bilgi için bkz. [kod öğelerine ve bağlantılarına kategori atama](#AssignCategories).

## <a name="ChangeGraphStyle"></a>Haritanın stilini değiştirme
 Haritanın. dgml dosyasını düzenleyerek haritanın arka plan rengini ve kenarlık rengini değiştirebilirsiniz. Kod öğelerinin ve bağlantıların stilini değiştirmek için bkz. [kod öğelerinin ve bağlantılarının stilini değiştirme](#Highlight).

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<DirectedGraph>` öğesinde, stilini değiştirmek için aşağıdaki özniteliklerin herhangi birini ekleyin:

     Arka plan rengi

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Kenarlık rengi

    ```xml
    Stroke="StrokeValue"
    ```

     Örneğin:

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="Highlight"></a>Kod öğelerinin ve bağlantıların stilini değiştirme

### <a name="CreateCustomStyles"></a>
 Aşağıdaki kod öğelerine özel stiller uygulayabilirsiniz:

- Tek kod öğeleri ve bağlantılar

- Kod öğesi ve bağlantı grupları

- Belirli koşullara göre kod öğesi ve bağlantı grupları

> [!TIP]
> Birçok kod öğesi veya bağlantı üzerinde yinelenen stiller varsa, bu kod öğelerine veya bağlantılarına bir kategori uygulamayı ve ardından bu kategoriye bir stil uygulamayı düşünebilirsiniz. Daha fazla bilgi için bkz. [kod öğelerine ve bağlantılarına kategori atama](#AssignCategories) ve [kod öğelerine ve bağlantılarına özellikler atama](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Tek bir kod öğesine özel bir stil uygulamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Kod öğesinin `<Node/>` öğesini bulun. Stilini özelleştirmek için bu özniteliklerin herhangi birini ekleyin:

     Arka plan rengi

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Anahat

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Anahat kalınlığı

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Metin rengi

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Simge

    ```xml
    Icon="IconFilePathLocation"
    ```

     Metin boyutu

    ```xml
    FontSize="FontSizeValue"
    ```

     Metin türü

    ```xml
    FontFamily="FontFamilyName"
    ```

     Metin ağırlığı

    ```xml
    FontWeight="FontWeightValue"
    ```

     Metin stili

    ```xml
    FontStyle="FontStyleName"
    ```

     Örneğin, metin stili olarak `Italic` belirtebilirsiniz.

     Doku

    ```xml
    Style="Glass"
    ```

     - veya -

    ```xml
    Style="Plain"
    ```

     Şekil

     Şekli bir simgeyle değiştirmek için `Shape` özelliğini `None` olarak ayarlayın ve `Icon` özelliğini simge dosyası ile yol olarak ayarlayın.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Örneğin:

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Özel bir stili tek bir bağlantıya uygulamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Hem kaynak kodu öğesinin hem de hedef kod öğesinin adlarını içeren `<Link/>` öğesini bulun.

3. `<Link/>` öğesinde, stilini özelleştirmek için aşağıdaki özniteliklerin herhangi birini ekleyin:

     Anahat ve ok ucu rengi

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Anahat kalınlığı

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Anahat stili

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Örneğin:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Bir kod öğesi veya bağlantı grubuna özel stiller uygulamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Bir `<Styles></Styles>` öğesi yoksa, `<Links></Links>` öğeden sonra `<DirectedGraph></DirectedGraph>` öğesinin altına bir tane ekleyin.

3. `<Styles></Styles>` öğesinde, `<Style/>` öğesi altında ve aşağıdaki öznitelikleri belirtin:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="` *NameInLegendBox* `"`

   - `ValueLabel="` *Nameınstylepickerbox* `"`

     Tüm hedef türlere özel bir stil uygulamak için bir koşul kullanmayın.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Kod öğelerinin veya bağlantıların gruplarına koşullu bir stil uygulamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<Style/>` öğesinde, Boole değeri döndüren bir ifade belirtmek için `Expression` özniteliği içeren bir `<Condition/>` öğesi ekleyin.

    Örneğin:

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - veya -

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - veya -

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Bu ifade aşağıdaki Backus-Naur Form (BNF) sözdizimini kullanır:

    \<Ifade >:: = \<BinaryExpression > &#124; \<UnaryExpression > &#124; "("\<Expression > ")" &#124; \<Memberbindings &#124; > \<sabit > &#124; \<sayı >

    \<BinaryExpression >:: = \<Ifade > \<Işleç > \<Ifade >

    \<UnaryExpression >:: = "!" \<Ifadesi > &#124; "+" \<Expression > &#124; "-" \<ifadesi >

    \<işleci >:: = "<" &#124; "\<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "veya" &#124; "ve" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings >:: = \<MemberBindings > &#124; \<MemberBinding > "." \<MemberBinding >

    \<MemberBinding >:: = \<MethodCall > &#124; \<propertyget >

    \<MethodCall >:: = \<tanımlayıcı > "(" \<Methodarg > ")"

    \<PropertyGet >:: = tanımlayıcı

    \<Methodarg >:: = \<Ifadesi > &#124; \<Expression > "," \<MethodArgs > &#124; boş \<

    \<tanımlayıcı >:: = [^. ]*

    \<değişmez >:: = tek veya çift tırnaklı dize sabit değeri

    \<Number >:: = isteğe bağlı ondalık noktalı basamaklar dizesi

    Stili uygulamak için tümü doğru olması gereken birden çok `<Condition/>` öğesi belirtebilirsiniz.

3. `<Condition/>` öğeden sonraki satırda, bir veya daha fazla `<Setter/>` öğesini, bir `Property` özniteliği ve bir sabit `Value` özniteliği veya bir eşleme, kod öğeleri veya koşulu karşılayan bağlantılara uygulamak için bir hesaplanmış `Expression` özniteliği belirtmek üzere ekleyin.

    Örneğin:

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   Basit bir örnek olarak, aşağıdaki koşul, `Passed` kategorisinin `True` veya `False`olarak ayarlanmış olup olmadığına bağlı olarak bir kod öğesinin yeşil veya kırmızı göründüğünü belirtir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 Aşağıdaki tabloda kullanabileceğiniz bazı örnek koşullar bulunmaktadır:

 Yazı tipi boyutunu kod satırı sayısının bir işlevi olarak ayarlayın, bu da kod öğesinin boyutunu da değiştirir. Bu örnek, `FontSize` ve `FontFamily`birden çok özellik ayarlamak için tek bir koşullu ifade kullanır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Bir kod öğesinin arka plan rengini `Coverage` özelliğine göre ayarlayın. Stiller göründükleri sırada değerlendirilir, `if-else` deyimlerine benzer.

 Bu örnekte:

1. `Coverage` > 80 ise `Background` özelliğini yeşil olarak ayarlayın.

2. Değilse, `Coverage` > 50 ise, `Coverage` özelliğinin değerine bağlı olarak `Background` özelliğini turuncu bir gölgeye ayarlayın.

3. `Background` özelliğini, `Coverage` özelliğinin değerine göre kırmızı bir gölgeye ayarlayın.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Simgenin şeklin yerini değiştirmesi için `Shape` özelliğini `None` olarak ayarlayın. Simgenin konumunu belirtmek için `Icon` özelliğini kullanın.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="AssignProperties"></a>Kod öğelerine ve bağlantılarına özellikler atama
 Kod öğelerini ve bağlantıları bunlara özellikler atayarak düzenleyebilirsiniz. Örneğin, belirli özellikleri olan kod öğelerini seçerek onları gruplandırabilir, stillerini değiştirebilir veya gizleyebilirsiniz.

#### <a name="to-assign-a-property-to-a-code-element"></a>Bir kod öğesine bir özellik atamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Bu kod öğesi için `<Node/>` öğesini bulun. Özelliğin adını ve değerini belirtin. Örneğin:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Görünür adı ve veri türü gibi öznitelikleri belirtmek için `<Properties>` bölümüne `<Property/>` öğesi ekleyin:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Bağlantıya bir özellik atamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Hem kaynak kodu öğesinin hem de hedef kod öğesinin adlarını içeren `<Link/>` öğesini bulun.

3. `<Node/>` öğesinde, özelliğin adını ve değerini belirtin. Örneğin:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Görünür adı ve veri türü gibi öznitelikleri belirtmek için `<Properties>` bölümüne `<Property/>` öğesi ekleyin:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="AssignCategories"></a>Kod öğelerine ve bağlantılarına kategoriler atama
 Aşağıdaki bölümlerde, bunlara kategoriler atayarak kod öğelerini nasıl düzenleyebileceğiniz ve kod öğelerini düzenlemenize ve devralma kullanarak alt kategorilere öznitelikler eklemenize yardımcı olan hiyerarşik Kategoriler oluşturabileceğiniz gösterilmektedir.

#### <a name="to-assign-a-category-to-a-code-element"></a>Bir kod öğesine kategori atamak için

- . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

- İstediğiniz kod öğesi için `<Node/>` öğesini bulun.

- `<Node/>` öğesinde kategorinin adını belirtmek için bir `Category` özniteliği ekleyin. Örneğin:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Bu kategori için görüntüleme metnini belirtmek üzere `Label` özniteliğini kullanabilmeniz için `<Categories>` bölümüne `<Category/>` öğesi ekleyin:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Bir bağlantıya kategori atamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Hem kaynak kodu öğesinin hem de hedef kod öğesinin adlarını içeren `<Link/>` öğesini bulun.

3. `<Link/>` öğesinde kategorinin adını belirtmek için bir `Category` özniteliği ekleyin. Örneğin:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Bu kategori için görüntüleme metnini belirtmek üzere `Label` özniteliğini kullanabilmeniz için `<Categories>` bölümüne `<Category/>` öğesi ekleyin:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Hiyerarşik kategoriler oluşturmak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Üst kategori için bir `<Category/>` öğesi ekleyin ve sonra alt kategorinin `<Category/>` öğesine `BasedOn` özniteliğini ekleyin.

     Örneğin:

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     Bu örnekte, `MyFirstNode` arka planı yeşildir çünkü `Category` özniteliği `MyParentCategory``Background` özniteliğini devralır.

## <a name="AddReferences"></a>Belge veya URL 'Leri kod öğelerine ve bağlantılarına bağlama
 Harita. dgml dosyasını düzenleyerek veya bir bağlantı için bir kod `<Link/>` öğesi için `<Node/>` öğesine bir `Reference` özniteliği ekleyerek, belge veya URL 'Leri kod öğelerine veya bağlantılara bağlayabilirsiniz. Daha sonra bu içeriği kod öğesinden veya bağlantıdan açabilir ve görüntüleyebilirsiniz. `Reference` özniteliği bu içeriğin yolunu belirtir. Bu, .dgml dosya konumu veya mutlak yol ile göreli bir yol olabilir.

> [!CAUTION]
> Göreli yollar kullanıyorsanız ve .dgml dosyası farklı bir konuma taşınırsa, bu yollar artık çözümlenmez. Bağlantılı içeriği açmaya ve görüntülemeye çalıştığınızda, içeriğin görüntülenemediğini bildiren bir hata ortaya çıkar.

 Örneğin, aşağıdaki kod öğelerini bağlamak isteyebilirsiniz:

- Bir sınıftaki değişiklikleri anlatmak için bir iş kodu öğesi, belge veya başka bir. dgml dosyasının URL 'sini bir sınıf için kod öğesine bağlayabilirsiniz.

- Bir bağımlılık diyagramını, Yazılımın mantıksal mimarisinde bir katmanı temsil eden bir grup kodu öğesine bağlayabilirsiniz.

- Bir arabirimi kullanıma sunan bir bileşen hakkında daha fazla bilgi görüntülemek için, bu arabirim için kod öğesine bir bileşen diyagramı bağlayabilirsiniz.

- Bir kod öğesini Team Foundation Server iş öğesine veya hataya veya kod öğesiyle ilgili diğer bazı bilgilere bağlayın.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Bir belge veya URL 'YI bir kod öğesine bağlamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. İstediğiniz kod öğesi için `<Node/>` öğesini bulun.

3. Aşağıdaki tabloda yer alan görevlerden birini gerçekleştirin:

    Tek bir kod öğesi

   - `<Node/>` veya `<Link/>` öğesinde, kod öğesinin konumunu belirtmek için bir `Reference` özniteliği ekleyin.

     > [!NOTE]
     > Öğe başına yalnızca bir `Reference` özniteliğine sahip olabilirsiniz.

     Örneğin:

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Birden çok kod öğesi

   1. `<Node/>` veya `<Link/>` öğesinde, her başvurunun konumunu belirtmek için yeni bir öznitelik ekleyin.

   2. `<Properties>` bölümünde:

      1. Her yeni başvuru türü için `<Property/>` öğesi ekleyin.

      2. `Id` özniteliğini yeni başvuru özniteliğinin adı olarak ayarlayın.

      3. `IsReference` özniteliğini ekleyin ve başvuruyu kod öğesinin **başvuruya git** kısayol menüsünde görünmesini sağlamak için `True` olarak ayarlayın.

      4. Kod öğesinin **başvuruya git** kısayol menüsünde görüntü metnini belirtmek için `Label` özniteliğini kullanın.

      Örneğin:

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Haritada, kod öğesinin adı altı çizili olarak görünür. Kod öğesi veya bağlantı için kısayol menüsünü açtığınızda, seçeceğiniz bağlantılı kod öğelerini içeren **başvuruya git** kısayol menüsünü görürsünüz.

4. Başvuru içindeki dizeyi yinelemek yerine birden çok başvuru tarafından kullanılan bir URL gibi ortak bir dize belirtmek için `ReferenceTemplate` özniteliğini kullanın.

    `ReferenceTemplate` özniteliği başvurunun değeri için bir yer tutucu belirtir. Aşağıdaki örnekte, `ReferenceTemplate` özniteliğinde `{0}` yer tutucusu, `<Node/>` öğesindeki `MyFirstReference` ve `MySecondReference` özniteliklerinin bir tam yol oluşturacak şekilde yerine geçer:

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. Başvurulan kod öğesini veya kod öğelerini haritadan görüntülemek için, kod öğesi veya bağlantı için kısayol menüsünü açın. **Başvuruya git** ' i ve ardından kod öğesini seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md)
