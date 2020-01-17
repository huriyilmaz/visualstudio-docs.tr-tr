---
title: Windows Forms Tabanlı Etki Alanına Özgü Dil Oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f565184dcb9570ecc34b61f1f2d4d0e2ce2a4110
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114886"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Windows Forms tabanlı bir etki alanına özgü dil oluşturma

Bir DSL diyagramı kullanmak yerine, etki alanına özgü dil (DSL) modelinin durumunu göstermek için Windows Forms kullanabilirsiniz. Bu konu başlığında, Visual Studio görselleştirme ve modelleme SDK 'sını kullanarak bir Windows formunu DSL 'ye bağlama işlemi adım adım gösterilmektedir.

Aşağıdaki görüntüde bir DSL örneği için Windows form kullanıcı arabirimi ve Model Gezgini gösterilmektedir:

![Visual Studio 'da DSL örneği](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Windows Forms DSL oluşturma

**En az WinForm Designer** DSL şablonu, kendi gereksinimlerinize uyacak şekilde değiştirebileceğiniz BIR minimum DSL oluşturur.

1. **Minimal WinForm tasarımcı** ŞABLONUNDAN bir DSL oluşturun.

    Bu kılavuzda, aşağıdaki adlar varsayılır:

   | | |
   |-|-|
   | Çözüm ve DSL adı | FarmApp |
   | Ad alanı | Şirket. FarmApp |

2. Şablonun sağladığı ilk örnekle denemeler yapın:

   1. Tüm Şablonları Dönüştür.

   2. Örneği derleyin ve çalıştırın (**Ctrl**+**F5**).

   3. Visual Studio 'nun deneysel örneğinde, hata ayıklama projesindeki `Sample` dosyasını açın.

        Windows Forms denetiminde görüntülendiğine dikkat edin.

        Ayrıca, bu modelin gezgin 'de görüntülenmesini sağlayabilirsiniz.

        Form ya da Gezgin içinde bazı öğeleri ekleyin ve diğer ekranda görünmediğine dikkat edin.

   Visual Studio 'nun ana örneğinde DSL çözümü hakkında aşağıdaki noktalara dikkat edin:

- `DslDefinition.dsl` diyagram öğesi içermiyor. Bunun nedeni, DSL diyagramlarını bu DSL 'nin örnek modellerini görüntülemek için kullanmayacak. Bunun yerine, bir Windows formunu modele bağlayacaksınız ve formdaki öğeler modeli görüntüleyecektir.

- `Dsl` ve `DslPackage` projelerine ek olarak çözüm, Windows Forms denetiminin tanımını içeren `UI.`**UI** projesi adlı üçüncü bir proje içerir. `DslPackage` `UI`bağlıdır ve `UI` `Dsl`bağlıdır.

- `DslPackage` projesinde, `UI\DocView.cs` `UI` projesinde tanımlanan Windows Forms denetimini görüntüleyen kodu içerir.

- `UI` projesi, DSL 'ye göre bir form denetiminin çalışan bir örneğini içerir. Ancak, DSL tanımını değiştirdiğiniz zaman çalışmaz. `UI` projesi şunları içerir:

  - `ModelViewControl`adlı bir Windows Forms sınıfı.

  - `ModelViewControl`ek kısmi tanımını içeren `DataBinding.cs` adlı bir dosya. İçeriğini görmek için, **Çözüm Gezgini**' de, dosyanın kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

### <a name="about-the-ui-project"></a>UI projesi hakkında

Dsl tanım dosyasını kendi DSL 'yi tanımlayacak şekilde güncelleştirdiğinizde, DSL 'nizi göstermek için `UI` projesindeki denetimi güncelleştirmeniz gerekir. `Dsl` ve `DslPackage` projelerinin aksine, örnek `UI` proje `DslDefinitionl.dsl`oluşturulmaz. İsterseniz kodu oluşturmak için. tt dosyası ekleyebilirsiniz, ancak bu kılavuzda kapsanmaz.

## <a name="update-the-dsl-definition"></a>DSL tanımını güncelleştirme

Bu kılavuzda aşağıdaki DSL tanımı kullanılır.

![DSL&#45;WPF&#45;1](../modeling/media/dsl-wpf-1.png)

1. DSL tasarımcısında DslDefinition. dsl 'yi açın.

2. **Örnek öğeyi** Sil

3. **ExampleModel** etki alanı sınıfını `Farm`olarak yeniden adlandırın.

     Buna **Int32**türü `Size` adlı ek etki alanı özellikleri ve **Boole**türü `IsOrganic` verin.

    > [!NOTE]
    > Kök etki alanı sınıfını silip yeni bir kök oluşturursanız, düzenleyici kök sınıfı özelliğini sıfırlamanız gerekir. **DSL Gezgini**' nde **Düzenleyici**' yi seçin. Ardından Özellikler penceresi, **kök sınıfı** `Farm`olarak ayarlayın.

4. Aşağıdaki etki alanı sınıflarını oluşturmak için **adlandırılmış etki alanı sınıfı** aracını kullanın:

    - `Field`-buna `Size`adlı ek bir etki alanı özelliği verin.

    - `Animal`-Özellikler penceresi, **Devralma değiştiricisini** **soyut**olarak ayarlayın.

5. Aşağıdaki sınıfları oluşturmak için **etki alanı sınıfı** aracını kullanın:

    - `Sheep`

    - `Goat`

6. **Devralma** aracını kullanarak `Goat` ve `Sheep` `Animal`devralın.

7. `Field` eklemek ve `Farm`altına `Animal` eklemek için **ekleme** aracını kullanın.

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

     **DSL**, **Company. FarmApp**' yi genişletin ve modelinizin kök sınıfı olan **Grup**' u seçin. Seçin **son**.

     Çözüm Gezgini, **Kullanıcı arabirimi** projesi artık **Properties\DataSources\Farm.DataSource** içerir

     Model sınıfınızın özellikleri ve ilişkileri veri kaynakları penceresinde görünür.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Modelinizi bir forma bağlama

1. **UI** projesinde, var olan tüm. cs dosyalarını silin.

2. **UI** projesine `FarmControl` adlı yeni bir **Kullanıcı denetim** dosyası ekleyin.

3. **Veri kaynakları** penceresinde, **gruptaki**açılan menüde **Ayrıntılar**' ı seçin.

    Diğer özellikler için varsayılan ayarları bırakın.

4. Tasarım görünümünde FarmControl.cs öğesini açın.

    **Grubu** veri kaynakları penceresinden FarmControl üzerine sürükleyin.

    Her özellik için bir dizi denetim görüntülenir. İlişki özellikleri denetim oluşturmaz.

5. **Farmbindingnavigator**'ı silin. Bu ayrıca `FarmControl` tasarımcısında otomatik olarak oluşturulur, ancak bu uygulama için yararlı değildir.

6. Araç kutusunu kullanarak, iki **DataGridView**örneği oluşturun ve `AnimalGridView` ve `FieldGridView`adlandırın.

   > [!NOTE]
   > Alternatif bir adım, hayvanlar ve alanlar öğelerini veri kaynakları penceresinden denetim üzerine sürüklemektir. Bu eylem, kılavuz görünümü ve veri kaynağı arasındaki veri kılavuzlarını ve bağlamaları otomatik olarak oluşturur. Ancak, bu bağlama DSLs için doğru çalışmaz. Bu nedenle, veri kılavuzlarını ve bağlamaları el ile oluşturmak daha iyidir.

7. Araç kutusu **ModelingBindingSource** aracını içermiyorsa, ekleyin. **Veri** sekmesinin kısayol menüsünde **öğeleri seç**' i seçin. **Araç kutusu öğelerini Seç** iletişim kutusunda, **.NET Framework** sekmesinden **ModelingBindingSource** ' u seçin.

8. Araç kutusunu kullanarak, **ModelingBindingSource**'un iki örneğini oluşturun ve `AnimalBinding` ve `FieldBinding`adlandırın.

9. Her **ModelingBindingSource** 'un **DataSource** özelliğini **farmBindingSource**olarak ayarlayın.

     **DataMember** özelliğini **hayvanlar** veya **alanlar**olarak ayarlayın.

10. `AnimalGridView` **veri kaynağı** özelliklerini `AnimalBinding`ve `FieldGridView` `FieldBinding`olarak ayarlayın.

11. Grup denetiminin yerleşimini sizin için ayarlayın.

    **ModelingBindingSource** , DSLs 'e özgü çeşitli işlevler gerçekleştiren bir bağdaştırıcıdır:

- Güncelleştirme, bir VMSDK mağaza hareketinde kaydırılır.

   Örneğin, Kullanıcı veri görünümü kılavuzundan bir satırı sildiğinde, düzenli bir bağlama bir işlem özel durumuyla sonuçlanır.

- Kullanıcı bir satır seçtiğinde Özellikler penceresi, veri kılavuzu satırı yerine karşılık gelen model öğesinin özelliklerini görüntülediğinden emin olur.

  veri kaynakları ve görünümler arasındaki bağlantıların DslWpf4](../modeling/media/dslwpf4.png) şeması ![.

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

     `Goat1` **hayvanlar** görünümünde görüntülenir.

    > [!WARNING]
    > **Hayvanlar** düğümünü değil, **Grup** düğümünde kısayol menüsünü kullanmanız gerekir.

4. **Grup** kök düğümünü seçin ve özelliklerini görüntüleyin.

     Form görünümünde, grubun **adını** veya **boyutunu** değiştirin.

     Formdaki her bir alandan uzaklaştığınızda, ilgili özellik Özellikler penceresi değişir.

## <a name="enhance-the-dsl"></a>DSL 'yi geliştirme

### <a name="make-the-properties-update-immediately"></a>Özelliklerin hemen güncelleştirilmesini sağlama

1. FarmControl.cs 'ın Tasarım görünümünde ad, boyut veya ıorganic gibi basit bir alan seçin.

2. Özellikler penceresi, **DataBindings** ' i genişletin ve açın **(Gelişmiş)** .

     **Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda, **veri kaynağı güncelleştirme modu**' nun altında **OnPropertyChanged**' i seçin.

3. Çözümü derleyin ve çalıştırın.

     Alanın içeriğini değiştirdiğinizde, Grup modelinin karşılık gelen özelliğinin hemen değiştiğini doğrulayın.

### <a name="provide-add-buttons"></a>Ekleme düğmeleri sağla

1. FarmControl.cs Tasarım görünümünde, form üzerinde bir düğme oluşturmak için araç kutusunu kullanın.

    Düğmenin adını ve metnini (örneğin `New Sheep`) düzenleyin.

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

Bu nedenle, yeni öğeler oluşturmak için <xref:Microsoft.VisualStudio.Modeling.ElementOperations> kullanmanızı öneririz. Daha fazla bilgi için bkz. [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
