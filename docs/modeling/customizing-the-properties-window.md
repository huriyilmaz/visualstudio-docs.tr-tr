---
title: Özellikler Penceresini Özelleştirme
description: Visual Studio 'da etki alanına özgü dilinizdeki (DSL) Özellikler penceresinin görünümünü ve davranışını nasıl özelleştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f7d4ac76b8b10fde0c193e3eda73cec611c1441
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362883"
---
# <a name="customize-the-properties-window"></a>Özellikler penceresi özelleştirme

Visual Studio 'da etki alanına özgü dilinizdeki (DSL) Özellikler penceresinin görünümünü ve davranışını özelleştirebilirsiniz. DSL tanımınızda, her bir etki alanı sınıfında etki alanı özelliklerini tanımlarsınız. Varsayılan olarak, bir diyagramda ya da Model Gezgini 'nde sınıfının bir örneğini seçtiğinizde, her etki alanı özelliği Özellikler penceresinde listelenir. Bu, onları diyagramdaki şekil alanlarıyla eşleştirmemiş olsanız bile, etki alanı özelliklerinin değerlerini görmenizi ve düzenlemenizi sağlar.

## <a name="names-descriptions-and-categories"></a>Adlar, açıklamalar ve Kategoriler

**Ad ve görünen ad**. Bir etki alanı özelliği tanımınızda, özelliğin görünen adı, Özellikler penceresinde çalışma zamanında görünen addır. Buna karşılık, bu ad, özelliği güncellemek için program kodu yazdığınızda kullanılır. Ad, doğru bir CLR alfasayısal adı olmalıdır, ancak görünen ad boşluk içerebilir.

DSL tanımındaki bir özelliğin adını belirlediğinizde, görünen adı otomatik olarak adının bir kopyasına ayarlanır. "Fuelölçer" gibi bir Pascal Kased adı yazarsanız, görünen ad otomatik olarak bir boşluk içerecektir: "yakıt ölçer". Ancak, görünen adı açıkça başka bir değere ayarlayabilirsiniz.

**Açıklama**. Bir etki alanı özelliğinin açıklaması iki yerde görünür:

- Kullanıcı özelliği seçtiğinde Özellikler penceresinin alt kısmında. Özelliği, özelliğin neyi temsil ettiğini kullanıcıya açıklamak için kullanabilirsiniz.

- Oluşturulan program kodunda. API belgelerini ayıklamak için belge tesislerini kullanırsanız, bu özelliğin API 'de açıklaması olarak görünür.

**Kategori**. Kategori, Özellikler penceresi bir başlık olur.

## <a name="expose-style-features"></a>Stil özelliklerini gösterme

Grafik öğelerinin bazı dinamik özellikleri, etki alanı *özellikleri olarak gösterilebilir veya gösterilebilir.* Bu şekilde sunulan bir özellik Kullanıcı tarafından güncelleştirilebilirler ve program koduna göre daha kolay bir şekilde güncelleştirebilirsiniz.

DSL tanımında bir şekil sınıfına sağ tıklayın, **gösterilen Ekle**' nin üzerine gelin ve ardından bir özellik seçin.

Şekiller üzerinde, **FillColor**, **OutlineColor**, **TextColor**, **outlinetirestyle**, **outlinekalınlığı** ve **FillGradientMode** özelliklerini kullanıma sunabilirsiniz. Bağlayıcılar üzerinde, **Color** `,` **TextColor**, **çizgi stili** ve **kalınlığı** özelliklerini kullanıma sunabilirsiniz. Diyagramlarda, **FillColor** ve **TextColor** özelliklerini kullanıma sunabilirsiniz.

## <a name="forwarding-display-properties-of-related-elements"></a>İletme: ilgili öğelerin özelliklerini görüntüle

DSL 'niz Kullanıcı bir modelde bir öğe seçtiğinde, bu öğenin özellikleri Özellikler penceresinde görüntülenir. Bununla birlikte, belirtilen ilişkili öğelerin özelliklerini de görüntüleyebilirsiniz. Birlikte çalışarak bir öğe grubunu tanımlamış olmanız durumunda bu yararlı olur. Örneğin, bir ana öğe ve isteğe bağlı bir eklenti öğesi tanımlayabilirsiniz. Ana öğe bir şekle eşlenmişse ve diğeri değilse, tüm özelliklerini tek bir öğe gibi görmek yararlıdır.

Bu efekt, *özellik iletme* olarak adlandırılır ve çeşitli durumlarda otomatik olarak gerçekleşir. Diğer durumlarda, bir etki alanı türü tanımlayıcısı tanımlayarak özellik iletme elde edebilirsiniz.

### <a name="default-property-forwarding-cases"></a>Varsayılan özellik iletme durumları

Kullanıcı bir şekil veya bağlayıcı ya da gezgin içindeki bir öğe seçtiğinde, Özellikler penceresi aşağıdaki özellikler görüntülenir:

- Temel sınıflarda tanımlananlar da dahil olmak üzere, model öğesinin etki alanı sınıfında tanımlanan etki alanı özellikleri. Bir özel durum, sizin ayarladığınız ve göz **atılabilen** etki alanı özellikleridir `False` .

- Çokluğu 0.. 1 olan ilişkilerle bağlantılı öğelerin adları. Bu, ilişki için bir bağlayıcı eşlemesi tanımlamadınız bile, isteğe bağlı olarak bağlı öğeleri görmek için kullanışlı bir yöntem sağlar.

- Öğeyi hedefleyen katıştırma ilişkisinin etki alanı özellikleri. Ekleme ilişkileri genellikle açıkça görüntülenmediğinden, kullanıcının özelliklerini görmesini sağlar.

- Seçilen şekil veya bağlayıcı üzerinde tanımlanan etki alanı özellikleri.

### <a name="add-property-forwarding"></a>Özellik iletme Ekle

Bir özelliği iletmek için, bir etki alanı türü tanımlayıcısı tanımlarsınız. İki etki alanı sınıfı arasında bir etki alanı ilişkiniz varsa, ilk sınıfta bir etki alanı özelliğini ikinci etki alanı sınıfındaki bir etki alanı özelliğinin değerine ayarlamak için bir etki alanı türü tanımlayıcısı kullanabilirsiniz. Örneğin, bir **kitap** etki alanı sınıfı ve **Yazar** etki alanı sınıfı arasında bir ilişkiniz varsa, Kullanıcı kitabı seçtiğinde kitap **yazarının** **ad** özelliğinin Özellikler penceresi görünmesini sağlamak için bir etki alanı türü tanımlayıcısı kullanabilirsiniz.

> [!NOTE]
> Özellik iletme yalnızca Kullanıcı bir modeli düzenlediğinde Özellikler penceresi etkiler. Alıcı sınıfta bir etki alanı özelliği tanımlamaz. DSL tanımının diğer bölümlerinde veya program kodunda iletilen etki alanı özelliğine erişmek istiyorsanız, iletme öğesine erişmeniz gerekir.

Aşağıdaki yordamda bir DSL oluşturduğunuzu varsayılmaktadır. İlk birkaç adım önkoşulları özetler.

#### <a name="forward-a-property-from-another-element"></a>Bir özelliği başka bir öğeden ilet

1. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]Bu örnekte **kitap** ve **Yazar** olarak adlandırılan en az iki sınıf içeren bir çözüm oluşturun. **Kitap** ve **Yazar** arasında her iki türden bir ilişki olmalıdır.

    Kaynak rolün çoğulluğu ( **kitap** tarafındaki rol) 0.. 1 veya 1.. 1 olmalıdır, böylece her **kitapta** bir **Yazar** bulunur.

2. **DSL Gezgini**' nde, **kitap** etki alanı sınıfına sağ tıklayın ve sonra **Yeni DomainTypeDescriptor Ekle**' ye tıklayın.

    Özel **özellik tanımlayıcılarının yolları** adlı bir düğüm, **özel tür tanımlayıcısı** düğümünün altında görünür.

3. **Özel tür tanımlayıcısı** düğümüne sağ tıklayın ve ardından **yeni PropertyPath Ekle**' ye tıklayın.

    **Özel özellik tanımlayıcısı düğümünün yolları** altında yeni bir özellik yolu görüntülenir.

4. Yeni özellik yolunu seçin ve **Özellikler** penceresinde, uygun model öğesinin yolu olarak **özellik** yolunu ayarlayın.

    Bu özelliğin sağındaki aşağı oka tıklayarak bir ağaç görünümündeki yolu düzenleyebilirsiniz. Etki alanı yolları hakkında daha fazla bilgi için bkz. [etki alanı yol sözdizimi](../modeling/domain-path-syntax.md). Bu dosyayı düzenlediğinizde yol, **Bookreferencesauthveya. Author/! şeklinde olmalıdır Yazar**.

5. **Özelliği** , **yazarın** **Name** Domain özelliğine ayarlayın.

6. **Görünen adı** **Yazar adı** olarak ayarlayın.

7. Tüm şablonları dönüştürün, DSL derleyin ve çalıştırın.

8. Model diyagramında bir kitap, yazar oluşturun ve başvuru ilişkisini kullanarak bunları bağlayın. Kitap öğesini seçin ve Özellikler penceresi kitabın özelliklerine ek olarak yazar adı ' nı görmeniz gerekir. Bağlantılı yazarın adını değiştirin veya kitabı farklı bir yazara bağlayın ve kitabın yazar adının değiştiğini gözlemleyin.

## <a name="custom-property-editors"></a>Özel özellik düzenleyicileri

Özellik penceresi, her bir etki alanı özelliğinin türü için uygun bir varsayılan düzen deneyimi sağlar. Örneğin, numaralandırılmış bir tür için Kullanıcı bir açılan liste görür ve sayısal bir özellik için Kullanıcı rakam girebilir. Bu yalnızca yerleşik türler için geçerlidir. Bir dış tür belirtirseniz, Kullanıcı özelliğin değerlerini görebilir, ancak düzenleyemez.

Ancak, aşağıdaki düzenleyicileri ve türleri belirtebilirsiniz:

1. Standart tür ile kullanılan başka bir düzenleyici. Örneğin, bir dize özelliği için bir dosya yolu Düzenleyicisi belirtebilirsiniz.

2. Etki alanı özelliği için bir dış tür ve BT için bir düzenleyici.

3. Dosya yolu Düzenleyicisi gibi bir .NET Düzenleyicisi veya kendi özel özellik düzenleyicinizi oluşturabilirsiniz.

   Bir dış tür ve varsayılan düzenleyiciye sahip dize gibi bir tür arasında dönüştürme.

   Bir DSL 'de, *dış tür* basit türlerden (Boolean veya Int32 gibi) veya dize olmayan herhangi bir türdür.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Dış türü olan bir etki alanı özelliği tanımlayın

1. **Çözüm Gezgini**, **DSL** projesinde dış türü içeren derlemeye (dll) bir başvuru ekleyin.

    Derleme bir .NET derlemesi ya da sizin tarafınızdan sağlanan bir derleme olabilir.

2. Daha önce yapmadıysanız, türü **etki alanı türleri** listesine ekleyin.

   1. DslDefinition. dsl 'yi açın ve **DSL Gezgini**'nde kök düğüme sağ tıklayın ve ardından **yeni dış tür Ekle**' ye tıklayın.

        **Etki alanı türleri** düğümünün altında yeni bir giriş görüntülenir.

       > [!WARNING]
       > Menü öğesi, **etki alanı türleri** düğümü değil DSL kök düğümünde bulunur.

   2. Özellikler penceresi yeni türün adını ve ad alanını ayarlayın.

3. Her zamanki şekilde bir etki alanı sınıfına bir etki alanı özelliği ekleyin.

    Özellikler penceresi, **tür** alanındaki aşağı açılan listeden dış türü seçin.

   Bu aşamada, kullanıcılar özelliğin değerlerini görüntüleyebilir, ancak düzenleyemezsiniz. Görüntülenen değerler `ToString()` işlevinden alınır. Özelliğin değerini ayarlayan program kodunu (örneğin, bir komut veya kural) yazabilirsiniz.

### <a name="set-a-property-editor"></a>Özellik Düzenleyicisi ayarlama

Aşağıdaki biçimde, Domain özelliğine bir CLR özniteliği ekleyin:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

Bir özellikte özniteliği, Özellikler penceresi **özel öznitelik** girişini kullanarak ayarlayabilirsiniz.

Türünün `AnEditor` ikinci parametrede belirtilen türden türetilmesi gerekir. İkinci parametre ya da olmalıdır <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.ComponentEditor> . Daha fazla bilgi için bkz. <xref:System.ComponentModel.EditorAttribute>.

Kendi düzenleyicinizi veya ya da gibi bir .NET düzenleyicisini belirtebilirsiniz <xref:System.Windows.Forms.Design.FileNameEditor> <xref:System.Drawing.Design.ImageEditor> . Örneğin, kullanıcının bir dosya adı girebileceği bir özelliği olması için aşağıdaki yordamı kullanın.

#### <a name="define-a-file-name-domain-property"></a>Bir dosya adı etki alanı özelliği tanımlayın

1. DSL tanımınızdaki bir etki alanı sınıfına bir etki alanı özelliği ekleyin.

2. Yeni özelliği seçin. Özellikler penceresi **özel öznitelik** alanına aşağıdaki özniteliği girin. Bu özniteliği girmek için, üç nokta ( **...]** simgesine tıklayın ve ardından öznitelik adını ve parametreleri ayrı olarak girin:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Domain özelliğinin türünü varsayılan **dize** ayarında bırakın.

4. Düzenleyiciyi test etmek için, kullanıcıların etki alanı özelliğini düzenlemek üzere dosya adı düzenleyicisini açabildiğini doğrulayın.

    1. CTRL + F5 veya F5 tuşlarına basın. Hata ayıklama çözümünde bir test dosyası açın. Etki alanı sınıfının bir öğesini oluşturun ve seçin.

    2. Özellikler penceresi, domain özelliğini seçin. Değer alanı bir üç nokta gösterir **[...]**.

    3. Üç nokta simgesine tıklayın. Bir dosya iletişim kutusu görüntülenir. Bir dosya seçin ve iletişim kutusunu kapatın. Dosya yolu artık Domain özelliğinin değeridir.

### <a name="define-your-own-property-editor"></a>Kendi özellik düzenleyicinizi tanımlama

Kendi düzenleyicinizi tanımlayabilirsiniz. Bunu, kullanıcının tanımladığınız bir türü düzenlemesine veya standart bir türü özel bir şekilde düzenlemenize izin vermek için yapabilirsiniz. Örneğin, kullanıcının bir formülü temsil eden bir dize girişine izin verebilirsiniz.

Sınıfından türetilmiş bir sınıf yazarak bir düzenleyici tanımlarsınız <xref:System.Drawing.Design.UITypeEditor> . Sınıfınız geçersiz kılmalıdır:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, kullanıcıyla etkileşime geçmek ve özellik değerini güncelleştirmek için.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, Düzenleyicinizde bir iletişim kutusu açıp açmayacağını veya açılan bir menü belirtin.

Özellik kılavuzunda görüntülenecek özelliğin değerinin grafik gösterimini de sağlayabilirsiniz. Bunu yapmak için `GetPaintValueSupported` , ve geçersiz kılın `PaintValue` .  Daha fazla bilgi için bkz. <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Kodu **DSL** projesindeki ayrı bir kod dosyasına ekleyin.

Örneğin:

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

Bu düzenleyiciyi kullanmak için, bir etki alanı özelliğinin **özel özniteliğini** şu şekilde ayarlayın:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Daha fazla bilgi için bkz. <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Aşağı açılan değerlerin bir listesini sağlayın

Bir kullanıcının aralarından seçim yapabileceğiniz bir değer listesi sağlayabilirsiniz.

> [!NOTE]
> Bu teknik, çalışma zamanında değişebilir değerlerin bir listesini sağlar. Değişmez bir liste sağlamak istiyorsanız, bunun yerine, etki alanı özelliği türü olarak numaralandırılmış bir tür kullanmayı göz önünde bulundurun.

Standart değerlerin bir listesini tanımlamak için, aşağıdaki biçime sahip bir CLR özniteliği olan etki alanı özelliğine eklersiniz:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Öğesinden türetilen bir sınıf tanımlayın <xref:System.ComponentModel.TypeConverter> . Kodu **DSL** projesindeki ayrı bir dosyaya ekleyin. Örneğin:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
