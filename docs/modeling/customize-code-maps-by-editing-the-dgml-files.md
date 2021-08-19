---
title: DGML dosyalarını düzenleyerek kod haritalarını özelleştirme
description: bir kod haritasını, yönlendirilmiş Graph biçimlendirme dili (. dgml) dosyasını düzenleyerek nasıl özelleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8b38af7e21d6aab6def7858bc251e5886a40bd57
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157546"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>DGML dosyalarını düzenleyerek kod haritalarını özelleştirme

bir kod eşlemesini özelleştirmek için, onun yönlendirilmiş Graph biçimlendirme dili (. dgml) dosyasını düzenleyebilirsiniz. Örneğin, özel stilleri belirlemek, kod öğelerine ve bağlantılarına Özellikler ve kategoriler atamak ya da belge veya URL 'Leri kod öğelerine ya da bağlantılara bağlamak için öğeleri düzenleyebilirsiniz. DGML öğeleri hakkında daha fazla bilgi için bkz. [yönlendirilmiş Graph biçimlendirme dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md).

Kod haritasının. dgml dosyasını bir metin veya XML düzenleyicisinde düzenleyin. eşleme Visual Studio çözümünüzün bir parçasıysa, **Çözüm Gezgini** içinde seçin, kısayol menüsünü açın ve **birlikte aç**, **XML (metin) düzenleyicisi**' ni seçin.

> [!NOTE]
> kod eşlemeleri oluşturmak için Visual Studio Enterprise sürüme sahip olmanız gerekir. Visual Studio bir kod haritasını düzenlediğinizde,. dgml dosyasını kaydettiğinizde kullanılmayan DGML öğelerini ve özniteliklerini temizler. Ayrıca, el ile yeni bağlantılar eklediğinizde kod öğeleri otomatik olarak oluşturulur. .dgml dosyasını kaydettiğinizde, bir öğeye eklediğiniz tüm öznitelikler kendilerini alfabetik sırada yeniden düzenleyebilir.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Kod öğelerini Gruplandır
 Yeni gruplar ekleyebilir veya varolan düğümleri bir gruba dönüştürebilirsiniz.

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Bir kod öğesini bir gruba dönüştürmek için, `<Node/>` Bu kod öğesi için öğesini bulun.

    \- veya

    Yeni bir grup eklemek için `<Nodes>` bölümünü bulun. Yeni bir `<Node/>` öğe ekleyin.

3. `<Node/>`Öğesinde, `Group` grubun genişletilmiş mı yoksa daraltılmış mi göründüğünü belirtmek için bir öznitelik ekleyin. Örnek:

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. `<Links>`Bölümünde, `<Link/>` bir grup kodu öğesi ve onun alt kod öğeleri arasındaki her ilişki için aşağıdaki özniteliklere sahip olan bir öğenin bulunduğundan emin olun:

   - `Source`Grup Kodu öğesini belirten bir öznitelik

   - `Target`Alt kod öğesini belirten bir öznitelik

   - `Category` `Contains` Grup kodu öğesi ve onun alt kod öğesi arasındaki ilişkiyi belirten bir öznitelik

     Örnek:

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    Özniteliği hakkında daha fazla bilgi için `Category` bkz. [kod öğelerine ve bağlantılarına kategorileri atama](#AssignCategories).

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Haritanın stilini değiştirme
 Haritanın. dgml dosyasını düzenleyerek haritanın arka plan rengini ve kenarlık rengini değiştirebilirsiniz. Kod öğelerinin ve bağlantıların stilini değiştirmek için bkz. [kod öğelerinin ve bağlantılarının stilini değiştirme](#Highlight).

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<DirectedGraph>`Öğesinde, stilini değiştirmek için aşağıdaki özniteliklerin herhangi birini ekleyin:

     Arka plan rengi

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Kenarlık rengi

    ```xml
    Stroke="StrokeValue"
    ```

     Örnek:

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Kod öğelerinin ve bağlantıların stilini değiştirme

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

     Ana hat

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

     Örneğin, `Italic` metin stili olarak belirtebilirsiniz.

     Doku

    ```xml
    Style="Glass"
    ```

     - veya

    ```xml
    Style="Plain"
    ```

     Şekil

     Şekli bir simgeyle değiştirmek için, `Shape` özelliğini olarak ayarlayın `None` ve `Icon` özelliği simge dosyasının yolunu olarak ayarlayın.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Örnek:

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Özel bir stili tek bir bağlantıya uygulamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<Link/>`Hem kaynak kodu öğesi hem de hedef kod öğesi adlarını içeren öğeyi bulun.

3. `<Link/>`Öğesinde, stilini özelleştirmek için aşağıdaki özniteliklerin herhangi birini ekleyin:

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

     Örnek:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Bir kod öğesi veya bağlantı grubuna özel stiller uygulamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. Bir `<Styles></Styles>` öğe yoksa, öğesinden sonra bir öğesi ekleyin `<DirectedGraph></DirectedGraph>` `<Links></Links>` .

3. Öğesinde `<Styles></Styles>` , öğesinin altında, `<Style/>` aşağıdaki öznitelikleri belirtin:

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*Nameınstylepickerbox*`"`

     Tüm hedef türlere özel bir stil uygulamak için bir koşul kullanmayın.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Kod öğelerinin veya bağlantıların gruplarına koşullu bir stil uygulamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<Style/>`Öğesinde, `<Condition/>` `Expression` Boole değeri döndüren bir ifade belirtmek için özniteliği içeren bir öğesi ekleyin.

    Örnek:

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - veya

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - veya

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Bu ifade aşağıdaki Backus-Naur Form (BNF) sözdizimini kullanır:

    \<Expression> :: = \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; \<MemberBindings> &#124; \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; "+" \<Expression> &#124; "-" \<Expression>

    \<Operator> :: = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; "! =" &#124; "veya" &#124; "ve" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> :: = \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> :: = \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> :: = Tanımlayıcısı

    \<MethodArgs> :: = \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> :: = tek veya çift tırnaklı dize sabit değeri

    \<Number> :: = isteğe bağlı ondalık noktalı basamaklar dizesi

    `<Condition/>`Stili uygulamak için tümü doğru olması gereken birden çok öğe belirtebilirsiniz.

3. Öğesinden sonraki satırda `<Condition/>` , bir veya daha fazla öğe eklemek için bir `<Setter/>` `Property` özniteliği, sabit bir özniteliği `Value` veya `Expression` eşleme, kod öğeleri veya koşulu karşılayan bağlantılara uygulamak üzere hesaplanan bir özniteliği belirtin.

    Örnek:

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   Basit bir bütün örnek olarak, aşağıdaki koşul, `Passed` kategorisinin kategori veya olarak ayarlanmış olup olmadığına bağlı olarak bir kod öğesinin yeşil veya kırmızı göründüğünü belirtir `True` `False` :

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

 Yazı tipi boyutunu kod satırı sayısının bir işlevi olarak ayarlayın, bu da kod öğesinin boyutunu da değiştirir. Bu örnek, birden çok özellik ayarlamak için tek bir koşullu ifade `FontSize` kullanır `FontFamily` .

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

 Özelliği temel alarak bir kod öğesinin arka plan rengini ayarlayın `Coverage` . Stiller göründükleri sırada değerlendirilir, `if-else` deyimlerle benzerdir.

 Bu örnekte:

1. `Coverage`> 80 ise, `Background` özelliği yeşil olarak ayarlayın.

2. Değilse > 50 ise özelliği, `Coverage` `Background` özelliğin değerine bağlı olarak turuncu bir gölgeye ayarlayın `Coverage` .

3. Aksi takdirde özelliği, `Background` özelliğin değerine göre kırmızı bir gölgeye ayarlayın `Coverage` .

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

 Özelliği, `Shape` `None` simgenin şeklinin yerini alacak şekilde olarak ayarlayın. `Icon`Simgenin konumunu belirtmek için özelliğini kullanın.

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

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> Kod öğelerine ve bağlantılarına özellikler atama
 Kod öğelerini ve bağlantıları bunlara özellikler atayarak düzenleyebilirsiniz. Örneğin, belirli özellikleri olan kod öğelerini seçerek onları gruplandırabilir, stillerini değiştirebilir veya gizleyebilirsiniz.

#### <a name="to-assign-a-property-to-a-code-element"></a>Bir kod öğesine bir özellik atamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<Node/>`Bu kod öğesi için öğeyi bulun. Özelliğin adını ve değerini belirtin. Örnek:

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. `<Property/>` `<Properties>` Görünür adı ve veri türü gibi öznitelikleri belirtmek için bölümüne bir öğesi ekleyin:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Bağlantıya bir özellik atamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<Link/>`Hem kaynak kodu öğesi hem de hedef kod öğesi adlarını içeren öğeyi bulun.

3. `<Node/>`Öğesinde, özelliğin adını ve değerini belirtin. Örnek:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. `<Property/>` `<Properties>` Görünür adı ve veri türü gibi öznitelikleri belirtmek için bölümüne bir öğesi ekleyin:

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Kod öğelerine ve bağlantılarına kategoriler atama
 Aşağıdaki bölümlerde, bunlara kategoriler atayarak kod öğelerini nasıl düzenleyebileceğiniz ve kod öğelerini düzenlemenize ve devralma kullanarak alt kategorilere öznitelikler eklemenize yardımcı olan hiyerarşik Kategoriler oluşturabileceğiniz gösterilmektedir.

#### <a name="to-assign-a-category-to-a-code-element"></a>Bir kod öğesine kategori atamak için

- . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

- İstediğiniz `<Node/>` kod öğesi için öğesini bulun.

- `<Node/>`Öğesinde, `Category` kategorinin adını belirtmek için bir öznitelik ekleyin. Örnek:

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     `<Category/>` `<Categories>` `Label` Bu kategori için görüntüleme metnini belirtmek üzere özniteliğini kullanabilmeniz için bölümüne bir öğesi ekleyin:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Bir bağlantıya kategori atamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<Link/>`Hem kaynak kodu öğesi hem de hedef kod öğesi adlarını içeren öğeyi bulun.

3. `<Link/>`Öğesinde, `Category` kategorinin adını belirtmek için bir öznitelik ekleyin. Örnek:

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. `<Category/>` `<Categories>` `Label` Bu kategori için görüntüleme metnini belirtmek üzere özniteliğini kullanabilmeniz için bölümüne bir öğesi ekleyin:

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Hiyerarşik kategoriler oluşturmak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. `<Category/>`Üst kategori için bir öğe ekleyin ve sonra `BasedOn` özniteliği alt kategorinin `<Category/>` öğesine ekleyin.

     Örnek:

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

     Bu örnekte, öğesinin özniteliğinin özniteliği devraldığı için arka planı `MyFirstNode` yeşildir `Category` `Background` `MyParentCategory` .

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Belge veya URL 'Leri kod öğelerine ve bağlantılarına bağlama
 Harita. dgml dosyasını düzenleyerek veya bir bağlantı için öğesine bir öznitelik ekleyerek, belge veya URL 'Leri kod öğelerine veya bağlantılara bağlayabilirsiniz `Reference` `<Node/>` `<Link/>` . Daha sonra bu içeriği kod öğesinden veya bağlantıdan açabilir ve görüntüleyebilirsiniz. `Reference`Öznitelik, bu içeriğin yolunu belirtir. Bu, .dgml dosya konumu veya mutlak yol ile göreli bir yol olabilir.

> [!CAUTION]
> Göreli yollar kullanıyorsanız ve .dgml dosyası farklı bir konuma taşınırsa, bu yollar artık çözümlenmez. Bağlantılı içeriği açmaya ve görüntülemeye çalıştığınızda, içeriğin görüntülenemediğini bildiren bir hata ortaya çıkar.

 Örneğin, aşağıdaki kod öğelerini bağlamak isteyebilirsiniz:

- Bir sınıftaki değişiklikleri anlatmak için bir iş kodu öğesi, belge veya başka bir. dgml dosyasının URL 'sini bir sınıf için kod öğesine bağlayabilirsiniz.

- Bir bağımlılık diyagramını, Yazılımın mantıksal mimarisinde bir katmanı temsil eden bir grup kodu öğesine bağlayabilirsiniz.

- Bir arabirimi kullanıma sunan bir bileşen hakkında daha fazla bilgi görüntülemek için, bu arabirim için kod öğesine bir bileşen diyagramı bağlayabilirsiniz.

- bir kod öğesini Team Foundation Server iş öğesine veya hataya veya kod öğesiyle ilgili diğer bazı bilgilere bağlayın.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Bir belge veya URL 'YI bir kod öğesine bağlamak için

1. . Dgml dosyasını bir metin veya XML düzenleyicisinde açın.

2. İstediğiniz `<Node/>` kod öğesi için öğesini bulun.

3. Aşağıdaki tabloda yer alan görevlerden birini gerçekleştirin:

    Tek bir kod öğesi

   - `<Node/>`Veya `<Link/>` öğesinde, `Reference` kod öğesinin konumunu belirtmek için bir öznitelik ekleyin.

     > [!NOTE]
     > Öğe başına yalnızca bir özniteliğe sahip olabilirsiniz `Reference` .

     Örnek:

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Birden çok kod öğesi

   1. `<Node/>`Veya `<Link/>` öğesinde, her başvurunun konumunu belirtmek için yeni bir öznitelik ekleyin.

   2. `<Properties>`Bölümünde:

      1. `<Property/>`Her yeni başvuru türü için bir öğe ekleyin.

      2. `Id`Özniteliğini yeni başvuru özniteliğinin adı olarak ayarlayın.

      3. Özniteliği ekleyin `IsReference` ve `True` başvuruyu kod öğesinin **başvuruya git** kısayol menüsünde görünmesini sağlamak için olarak ayarlayın.

      4. `Label`Kod öğesinin **başvuruya git** kısayol menüsünde görüntü metnini belirtmek için özniteliğini kullanın.

      Örnek:

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

4. `ReferenceTemplate`Başvuru içindeki dizeyi yinelemek yerine birden çok başvuru tarafından kullanılan BIR URL gibi ortak bir dize belirtmek için özniteliğini kullanın.

    `ReferenceTemplate`Öznitelik, başvurunun değeri için bir yer tutucu belirtir. Aşağıdaki örnekte, `{0}` özniteliğinde yer tutucu, `ReferenceTemplate` `MyFirstReference` `MySecondReference` `<Node/>` tam yol oluşturmak için öğesindeki ve özniteliklerinin değerleriyle değiştirilmelidir:

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
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md)
