---
title: Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c52b3bd352c2ecb2272ad8e229a0fe52a9ee5b41
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238367"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Windows Forms tabanlı bir etki alanına özgü dil oluşturma

Bir DSL diyagramı kullanmak yerine, etki alanına özgü dil (DSL) modelinin durumunu göstermek için Windows Forms kullanabilirsiniz. Bu konu başlığında, Visual Studio görselleştirme ve modelleme SDK 'sını kullanarak bir Windows formunu DSL 'ye bağlama işlemi adım adım gösterilmektedir.

Aşağıdaki görüntüde bir DSL örneği için Windows form kullanıcı arabirimi ve Model Gezgini gösterilmektedir:

![Visual Studio 'da DSL örneği](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Windows Forms DSL oluşturma

**En az WinForm Designer** DSL şablonu, kendi gereksinimlerinize uyacak şekilde değiştirebileceğiniz BIR minimum DSL oluşturur.

1. **Minimal WinForm tasarımcı** ŞABLONUNDAN bir DSL oluşturun.

    Bu kılavuzda, aşağıdaki adlar varsayılır:

    - Çözüm ve DSL adı: `FarmApp`
    - Uzayına `Company.FarmApp`

2. Şablonun sağladığı ilk örnekle denemeler yapın:

   1. Tüm Şablonları Dönüştür.

   2. Örneği derleyin ve çalıştırın (**CTRL** + **F5**).

   3. Visual Studio 'nun deneysel örneğinde `Sample` dosyayı hata ayıklama projesinde açın.

        Windows Forms denetiminde görüntülendiğine dikkat edin.

        Ayrıca, bu modelin gezgin 'de görüntülenmesini sağlayabilirsiniz.

        Form ya da Gezgin içinde bazı öğeleri ekleyin ve diğer ekranda görünmediğine dikkat edin.

   Visual Studio 'nun ana örneğinde DSL çözümü hakkında aşağıdaki noktalara dikkat edin:

- `DslDefinition.dsl` diyagram öğesi içermiyor. Bunun nedeni, DSL diyagramlarını bu DSL 'nin örnek modellerini görüntülemek için kullanmayacak. Bunun yerine, bir Windows formunu modele bağlayacaksınız ve formdaki öğeler modeli görüntüleyecektir.

- Ve projelerine ek olarak `Dsl` `DslPackage` çözüm, Kullanıcı Arabirimi projesi adlı üçüncü bir proje içerir `UI.` **UI** Windows Forms denetimin tanımını içerir. `DslPackage` öğesine bağlıdır `UI` ve bağımlıdır `UI` `Dsl` .

- `DslPackage`Projesinde, `UI\DocView.cs` projede tanımlanan Windows Forms denetimini görüntüleyen kodu içerir `UI` .

- `UI`Proje, DSL 'ye göre bir form denetiminin çalışan bir örneğini içerir. Ancak, DSL tanımını değiştirdiğiniz zaman çalışmaz. `UI`Proje şunları içerir:

  - Adlı bir Windows Forms sınıfı `ModelViewControl` .

  - `DataBinding.cs`Ek kısmi tanımını içeren adlı adlı bir dosya `ModelViewControl` . İçeriğini görmek için, **Çözüm Gezgini**' de, dosyanın kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

### <a name="about-the-ui-project"></a>UI projesi hakkında

Dsl tanım dosyasını kendi DSL 'yi tanımlayacak şekilde güncelleştirdiğinizde, `UI` DSL 'nizi göstermek için projedeki denetimi güncelleştirmeniz gerekir. `Dsl`Ve projelerinin aksine `DslPackage` , örnek `UI` Proje öğesinden oluşturulmaz `DslDefinitionl.dsl` . İsterseniz kodu oluşturmak için. tt dosyası ekleyebilirsiniz, ancak bu kılavuzda kapsanmaz.

## <a name="update-the-dsl-definition"></a>DSL tanımını güncelleştirme

Bu kılavuzda aşağıdaki DSL tanımı kullanılır.

![DSL&#45;WPF&#45;1](../modeling/media/dsl-wpf-1.png)

1. DSL tasarımcısında DslDefinition. dsl 'yi açın.

2. **Örnek öğeyi** Sil

3. **ExampleModel** etki alanı sınıfını olarak yeniden adlandırın `Farm` .

     Buna `Size` **Int32**türü ve `IsOrganic` **Boole**türü adlı ek etki alanı özellikleri verin.

    > [!NOTE]
    > Kök etki alanı sınıfını silip yeni bir kök oluşturursanız, düzenleyici kök sınıfı özelliğini sıfırlamanız gerekir. **DSL Gezgini**' nde **Düzenleyici**' yi seçin. Ardından Özellikler penceresi, **kök sınıfı** olarak ayarlayın `Farm` .

4. Aşağıdaki etki alanı sınıflarını oluşturmak için **adlandırılmış etki alanı sınıfı** aracını kullanın:

    - `Field` -Buna adlı ek bir etki alanı özelliği verin `Size` .

    - `Animal` -Özellikler penceresi, **Devralma değiştiricisini** **soyut**olarak ayarlayın.

5. Aşağıdaki sınıfları oluşturmak için **etki alanı sınıfı** aracını kullanın:

    - `Sheep`

    - `Goat`

6. **Devralma** aracını kullanarak `Goat` ve `Sheep` öğesinden devralın `Animal` .

7. Eklemek için **ekleme** aracını kullanın `Field` `Animal` `Farm` .

8. Diyagramı kullanmak isteyebilirsiniz. Yinelenen öğe sayısını azaltmak için yaprak öğelerinin kısayol menüsündeki **alt ağacı buraya getir** komutunu kullanın.

9. Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür** .

10. **DSL** projesi oluşturun.

    > [!NOTE]
    > Bu aşamada, diğer projeler hata olmadan derlenmeyecektir. Bununla birlikte, bütünleştirilmiş kod veri kaynağı Sihirbazı tarafından kullanılabilir olacak şekilde DSL projesi oluşturmak istiyoruz.

## <a name="update-the-ui-project"></a>UI projesini güncelleştir

Artık DSL modelinde depolanan bilgileri görüntüleyecek yeni bir kullanıcı denetimi oluşturabilirsiniz. Kullanıcı denetimini modele bağlamanın en kolay yolu veri bağlamaları kullanmaktır. **ModelingBindingSource** adlı veri bağlama bağdaştırıcısı türü, DSLs 'yi VMSDK olmayan arabirimlere bağlamak için özel olarak tasarlanmıştır.

### <a name="define-your-dsl-model-as-a-data-source"></a>DSL modelinizi bir veri kaynağı olarak tanımlama

1. **Veri** menüsünde **veri kaynaklarını göster**' i seçin.

     **Veri kaynakları** penceresi açılır.

     **Yeni veri kaynağı Ekle**' yi seçin. **Veri kaynağı Yapılandırma Sihirbazı** açılır.

2. **Nesne**, **İleri**' yi seçin.

     **DSL**, **Company. FarmApp**' yi genişletin ve modelinizin kök sınıfı olan **Grup**' u seçin. **Son**’u seçin.

     Çözüm Gezgini, **Kullanıcı arabirimi** projesi artık **Properties\DataSources\Farm.DataSource** içerir

     Model sınıfınızın özellikleri ve ilişkileri veri kaynakları penceresinde görünür.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Modelinizi bir forma bağlama

1. **UI** projesinde, var olan tüm. cs dosyalarını silin.

2. UI projesine adlı yeni bir **Kullanıcı denetim** dosyası ekleyin `FarmControl` . **UI**

3. **Veri kaynakları** penceresinde, **gruptaki**açılan menüde **Ayrıntılar**' ı seçin.

    Diğer özellikler için varsayılan ayarları bırakın.

4. Tasarım görünümünde FarmControl.cs öğesini açın.

    **Grubu** veri kaynakları penceresinden FarmControl üzerine sürükleyin.

    Her özellik için bir dizi denetim görüntülenir. İlişki özellikleri denetim oluşturmaz.

5. **Farmbindingnavigator**'ı silin. Bu, tasarımcıda de otomatik olarak oluşturulur `FarmControl` , ancak bu uygulama için yararlı değildir.

6. Araç kutusunu kullanarak, iki **DataGridView**örneği oluşturun ve bunları ve olarak adlandırın `AnimalGridView` `FieldGridView` .

   > [!NOTE]
   > Alternatif bir adım, hayvanlar ve alanlar öğelerini veri kaynakları penceresinden denetim üzerine sürüklemektir. Bu eylem, kılavuz görünümü ve veri kaynağı arasındaki veri kılavuzlarını ve bağlamaları otomatik olarak oluşturur. Ancak, bu bağlama DSLs için doğru çalışmaz. Bu nedenle, veri kılavuzlarını ve bağlamaları el ile oluşturmak daha iyidir.

7. Araç kutusu **ModelingBindingSource** aracını içermiyorsa, ekleyin. **Veri** sekmesinin kısayol menüsünde **öğeleri seç**' i seçin. **Araç kutusu öğelerini Seç** iletişim kutusunda, **.NET Framework** sekmesinden **ModelingBindingSource** ' u seçin.

8. Araç kutusunu kullanarak, **ModelingBindingSource**'un iki örneğini oluşturun ve bunları ve olarak `AnimalBinding` adlandırın `FieldBinding` .

9. Her **ModelingBindingSource** 'un **DataSource** özelliğini **farmBindingSource**olarak ayarlayın.

     **DataMember** özelliğini **hayvanlar** veya **alanlar**olarak ayarlayın.

10. ' A ve ' nin **veri kaynağı** özelliklerini olarak ayarlayın `AnimalGridView` `AnimalBinding`  `FieldGridView` `FieldBinding` .

11. Grup denetiminin yerleşimini sizin için ayarlayın.

    **ModelingBindingSource** , DSLs 'e özgü çeşitli işlevler gerçekleştiren bir bağdaştırıcıdır:

- Güncelleştirme, bir VMSDK mağaza hareketinde kaydırılır.

   Örneğin, Kullanıcı veri görünümü kılavuzundan bir satırı sildiğinde, düzenli bir bağlama bir işlem özel durumuyla sonuçlanır.

- Kullanıcı bir satır seçtiğinde Özellikler penceresi, veri kılavuzu satırı yerine karşılık gelen model öğesinin özelliklerini görüntülediğinden emin olur.

  ![](../modeling/media/dslwpf4.png)Veri kaynakları ve görünümler arasındaki bağlantıların DslWpf4 şeması.

### <a name="complete-the-bindings-to-the-dsl"></a>DSL bağlantılarını doldurun

1. Aşağıdaki kodu **UI** projesindeki ayrı bir kod dosyasına ekleyin:

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2. **DslPackage** projesinde, aşağıdaki değişken tanımını güncelleştirmek için **Dslpackage\docview.exe** ' i düzenleyin:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>DSL 'yi test etme

DSL çözümü artık oluşturabilir ve çalıştırılabilir, ancak daha sonra daha fazla iyileştirmeler eklemek isteyebilirsiniz.

1. Çözümü derleyin ve çalıştırın.

2. Visual Studio 'nun deneysel örneğinde **örnek** dosyayı açın.

3. **FarmApp Gezgini**' nde, **Grup** kök düğümünde kısayol menüsünü açın ve **Yeni Goat Ekle**' yi seçin.

     `Goat1`**hayvanlar** görünümünde görüntülenir.

    > [!WARNING]
    > **Hayvanlar** düğümünü değil, **Grup** düğümünde kısayol menüsünü kullanmanız gerekir.

4. **Grup** kök düğümünü seçin ve özelliklerini görüntüleyin.

     Form görünümünde, grubun **adını** veya **boyutunu** değiştirin.

     Formdaki her bir alandan uzaklaştığınızda, ilgili özellik Özellikler penceresi değişir.

## <a name="enhance-the-dsl"></a>DSL 'yi geliştirme

### <a name="make-the-properties-update-immediately"></a>Özelliklerin hemen güncelleştirilmesini sağlama

1. FarmControl.cs 'ın Tasarım görünümünde ad, boyut veya ıorganic gibi basit bir alan seçin.

2. Özellikler penceresi, **DataBindings** ' i genişletin ve açın **(Gelişmiş)**.

     **Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda, **veri kaynağı güncelleştirme modu**' nun altında **OnPropertyChanged**' i seçin.

3. Çözümü derleyin ve çalıştırın.

     Alanın içeriğini değiştirdiğinizde, Grup modelinin karşılık gelen özelliğinin hemen değiştiğini doğrulayın.

### <a name="provide-add-buttons"></a>Ekleme düğmeleri sağla

1. FarmControl.cs Tasarım görünümünde, form üzerinde bir düğme oluşturmak için araç kutusunu kullanın.

    Düğmenin adını ve metnini (örneğin,) düzenleyin `New Sheep` .

2. Düğmenin arkasındaki kodu açın (örneğin, çift tıklayarak).

    Aşağıdaki gibi düzenleyin:

   ```csharp
   private void NewSheepButton_Click(object sender, EventArgs e)
   {
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
     {
       elementOperations.MergeElementGroup(farm,
         new ElementGroup(new Sheep(farm.Partition)));
       t.Commit();
     }
   }

   // The following code is shared with other add buttons:
   private ElementOperations operationsCache = null;
   private ElementOperations elementOperations
   {
     get
     {
       if (operationsCache == null)
       {
         operationsCache = new ElementOperations(farm.Store, farm.Partition);
       }
       return operationsCache;
     }
   }
   private Farm farm
   {
     get { return this.farmBindingSource.DataSource as Farm; }
   }
   ```

    Ayrıca aşağıdaki yönergeyi de eklemeniz gerekir:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Goats ve alanlar için benzer düğmeler ekleyin.

4. Çözümü derleyin ve çalıştırın.

5. Yeni düğmenin bir öğe eklediğini doğrulayın. Yeni öğe hem FarmApp Gezgini hem de uygun veri kılavuzu görünümünde görünmelidir.

    Veri kılavuzu görünümünde öğenin adını düzenleyebilmelisiniz. Ayrıca, oradan da silebilirsiniz.

   ![DSL&#45;WPF&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Öğe ekleme kodu hakkında

Yeni öğe düğmeleri için, aşağıdaki alternatif kod biraz daha basittir.

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}
```

Ancak, bu kod yeni öğe için varsayılan bir ad belirtmiyor. Bu, DSL 'nin **öğe birleştirme yönergelerinden** tanımlamış olabileceğiniz herhangi bir özelleştirilmiş birleştirme çalıştırmaz ve tanımlanmış olabilecek özel bir birleştirme kodu çalıştırmaz.

Bu nedenle, <xref:Microsoft.VisualStudio.Modeling.ElementOperations> yeni öğeler oluşturmak için kullanmanızı öneririz. Daha fazla bilgi için bkz. [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
