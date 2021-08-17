---
title: Windows Forms Tabanlı bir Alana Özgü Dil Oluşturma
description: etki alanına özgü dil modelinin durumunu göstermek için Windows Forms kullanma hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 456eecfbc00c210f4110fb62e96dbaff960e962ab6998cd61faab77ff9c50f85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370833"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Windows Forms tabanlı Domain-Specific dili oluşturma

bir DSL diyagramı kullanmak yerine, etki alanına özgü dil (dsl) modelinin durumunu göstermek için Windows Forms kullanabilirsiniz. bu konu, Visual Studio görselleştirme ve modelleme SDK 'sını kullanarak Windows formu DSL 'ye bağlama işleminde size rehberlik eder.

aşağıdaki görüntüde bir DSL örneği için Windows Form kullanıcı arabirimi ve model gezgini gösterilmektedir:

![Visual Studio DSL örneği](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Windows Forms DSL oluşturma

**En az WinForm Designer** DSL şablonu, kendi gereksinimlerinize uyacak şekilde değiştirebileceğiniz BIR minimum DSL oluşturur.

1. **Minimal WinForm tasarımcı** ŞABLONUNDAN bir DSL oluşturun.

    Bu kılavuzda, aşağıdaki adlar varsayılır:

    - Çözüm ve DSL adı: `FarmApp`
    - Ad Alanı: `Company.FarmApp`

2. Şablonun sağladığı ilk örnekle denemeler yapın:

   1. Tüm Şablonları Dönüştür.

   2. Örneği derleyin ve çalıştırın (**CTRL** + **F5**).

   3. Visual Studio deneysel örneğinde, `Sample` dosyayı hata ayıklama projesinde açın.

        Windows Forms denetiminde görüntülendiğine dikkat edin.

        Ayrıca, bu modelin gezgin 'de görüntülenmesini sağlayabilirsiniz.

        Form ya da Gezgin içinde bazı öğeleri ekleyin ve diğer ekranda görünmediğine dikkat edin.

   Visual Studio ana örneğinde DSL çözümü hakkında aşağıdaki noktalara dikkat edin:

- `DslDefinition.dsl` diyagram öğesi içermiyor. Bunun nedeni, DSL diyagramlarını bu DSL 'nin örnek modellerini görüntülemek için kullanmayacak. bunun yerine, modele bir Windows formu bağlayacaksınız ve formdaki öğelerin modeli görüntülemesi gerekir.

- ve projelerine ek olarak `Dsl` `DslPackage` çözüm, kullanıcı arabirimi projesi adlı üçüncü bir proje içerir `UI.`  Windows Forms denetimin tanımını içerir. `DslPackage` öğesine bağlıdır `UI` ve bağımlıdır `UI` `Dsl` .

- `DslPackage`projesinde, `UI\DocView.cs` projede tanımlanan Windows Forms denetimini görüntüleyen kodu içerir `UI` .

- `UI`Proje, DSL 'ye göre bir form denetiminin çalışan bir örneğini içerir. Ancak, DSL tanımını değiştirdiğiniz zaman çalışmaz. `UI`Proje şunları içerir:

  - adlı bir Windows Forms sınıfı `ModelViewControl` .

  - `DataBinding.cs`Ek kısmi tanımını içeren adlı adlı bir dosya `ModelViewControl` . İçeriğini görmek için, **Çözüm Gezgini**' de, dosyanın kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

### <a name="about-the-ui-project"></a>UI projesi hakkında

Dsl tanım dosyasını kendi DSL 'yi tanımlayacak şekilde güncelleştirdiğinizde, `UI` DSL 'nizi göstermek için projedeki denetimi güncelleştirmeniz gerekir. `Dsl`Ve projelerinin aksine `DslPackage` , örnek `UI` Proje öğesinden oluşturulmaz `DslDefinitionl.dsl` . İsterseniz kodu oluşturmak için. tt dosyası ekleyebilirsiniz, ancak bu kılavuzda kapsanmaz.

## <a name="update-the-dsl-definition"></a>DSL tanımını güncelleştirme

Aşağıdaki görüntü, bu kılavuzda kullanılan DSL tanımıdır.

![DSL tanımı](../modeling/media/dsl-wpf-1.png)

1. DSL tasarımcısında DslDefinition. dsl 'yi açın.

2. **Örnek öğeyi** Sil

3. **ExampleModel** etki alanı sınıfını olarak yeniden adlandırın `Farm` .

     Buna `Size` **Int32** türü ve `IsOrganic` **Boole** türü adlı ek etki alanı özellikleri verin.

    > [!NOTE]
    > Kök etki alanı sınıfını silip yeni bir kök oluşturursanız, düzenleyici kök sınıfı özelliğini sıfırlamanız gerekir. **DSL Gezgini**' nde **Düzenleyici**' yi seçin. Ardından Özellikler penceresi, **kök sınıfı** olarak ayarlayın `Farm` .

4. Aşağıdaki etki alanı sınıflarını oluşturmak için **adlandırılmış etki alanı sınıfı** aracını kullanın:

    - `Field` -Buna adlı ek bir etki alanı özelliği verin `Size` .

    - `Animal` -Özellikler penceresi, **Devralma değiştiricisini** **soyut** olarak ayarlayın.

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

     ![Veri kaynakları penceresi](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>modelinize bir form Bağlan

1. **UI** projesinde, var olan tüm. cs dosyalarını silin.

2. UI projesine adlı yeni bir **Kullanıcı denetim** dosyası ekleyin `FarmControl` . 

3. **Veri kaynakları** penceresinde, **gruptaki** açılan menüde **Ayrıntılar**' ı seçin.

    Diğer özellikler için varsayılan ayarları bırakın.

4. Tasarım görünümünde FarmControl. cs ' i açın.

    **Grubu** veri kaynakları penceresinden FarmControl üzerine sürükleyin.

    Her özellik için bir dizi denetim görüntülenir. İlişki özellikleri denetim oluşturmaz.

5. **Farmbindingnavigator**'ı silin. Bu, tasarımcıda de otomatik olarak oluşturulur `FarmControl` , ancak bu uygulama için yararlı değildir.

6. Araç kutusunu kullanarak, iki **DataGridView** örneği oluşturun ve bunları ve olarak adlandırın `AnimalGridView` `FieldGridView` .

   > [!NOTE]
   > Alternatif bir adım, hayvanlar ve alanlar öğelerini veri kaynakları penceresinden denetim üzerine sürüklemektir. Bu eylem, kılavuz görünümü ve veri kaynağı arasındaki veri kılavuzlarını ve bağlamaları otomatik olarak oluşturur. Ancak, bu bağlama DSLs için doğru çalışmaz. Bu nedenle, veri kılavuzlarını ve bağlamaları el ile oluşturmak daha iyidir.

7. Araç kutusu **ModelingBindingSource** aracını içermiyorsa, ekleyin. **Veri** sekmesinin kısayol menüsünde **öğeleri seç**' i seçin. **araç kutusu öğelerini seç** iletişim kutusunda, **.NET Framework** sekmesinden **modelingbindingsource** ' u seçin.

8. Araç kutusunu kullanarak, **ModelingBindingSource**'un iki örneğini oluşturun ve bunları ve olarak `AnimalBinding` adlandırın `FieldBinding` .

9. Her **ModelingBindingSource** 'un **DataSource** özelliğini **farmBindingSource** olarak ayarlayın.

     **DataMember** özelliğini **hayvanlar** veya **alanlar** olarak ayarlayın.

10. ' A ve ' nin **veri kaynağı** özelliklerini olarak ayarlayın `AnimalGridView` `AnimalBinding`  `FieldGridView` `FieldBinding` .

11. Grup denetiminin yerleşimini sizin için ayarlayın.

    **ModelingBindingSource** , DSLs 'e özgü çeşitli işlevler gerçekleştiren bir bağdaştırıcıdır:

- Güncelleştirme, bir VMSDK mağaza hareketinde kaydırılır.

   Örneğin, kullanıcı veri görünümü kılavuzundan bir satır silebilir, normal bir bağlama bir işlem özel durumuna neden olur.

- Kullanıcı bir satır seçerek veri kılavuzu Özellikler penceresi ilgili model öğesinin özelliklerini görüntülemeyi sağlar.

  ![DSL bağlama şeması](../modeling/media/dslwpf4.png)
  
  Veri kaynakları ve görünümler arasındaki bağlantıların şeması.

### <a name="complete-the-bindings-to-the-dsl"></a>DSL bağlamalarını tamamlama

1. Ui projesinde ayrı bir kod dosyasına aşağıdaki **kodu** ekleyin:

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

2. **DslPackage projesinde** **DslPackage\DocView.tt** değişken tanımını güncelleştirmek için düzenleyin:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>DSL'i test etmek

DSL çözümü artık derleme ve çalıştırmaya devam ediyor, ancak daha sonra daha fazla geliştirme eklemek istiyor olabilirsiniz.

1. Çözümü derleyin ve çalıştırın.

2. Deneysel Visual Studio örnek dosyasını **açın.**

3. **FarmApp Explorer'da,** Farm kök düğümünde kısayol menüsünü açın **ve** Yeni Keçi **Ekle'yi seçin.**

     `Goat1` , Hayvanlar **görünümünde** görünür.

    > [!WARNING]
    > Hayvanlar düğümünde değil, **Grup düğümünde** kısayol menüsünü **kullanabilirsiniz.**

4. Grup kök **düğümünü** seçin ve özelliklerini görüntüleme.

     Form görünümünde, grubu ad **veya** **boyut** olarak değiştirebilirsiniz.

     Formda her bir alandan uzaklaşıyor olurken, karşılık gelen özellik Özellikler penceresi.

## <a name="enhance-the-dsl"></a>DSL'i geliştirme

### <a name="make-the-properties-update-immediately"></a>Özellikleri hemen güncelleştirme

1. FarmControl.cs'nin tasarım görünümünde Ad, Boyut veya IsOrganic gibi basit bir alan seçin.

2. Veri Özellikler penceresi **DataBindings'i genişletin** ve **(Gelişmiş) 'i açın.**

     Biçimlendirme ve **Gelişmiş Bağlama iletişim kutusunun** Veri Kaynağı Güncelleştirme Modu **altında** **OnPropertyChanged öğesini seçin.**

3. Çözümü derleyin ve çalıştırın.

     Alanın içeriğini değiştirmiyorken Farm modelinin karşılık gelen özelliğinin hemen değişmektedir.

### <a name="provide-add-buttons"></a>Düğme ekle'yi sağlama

1. FarmControl.cs'nin tasarım görünümünde, formda bir düğme oluşturmak için araç kutusunu kullanın.

    Düğmenin adını ve metnini (örneğin, olarak) `New Sheep` düzenleyin.

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

    Ayrıca aşağıdaki yönergeyi de eklemelisiniz:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Keçiler ve Alanlar için benzer düğmeler ekleyin.

4. Çözümü derleyin ve çalıştırın.

5. Yeni düğmenin bir öğe ekleyeni olduğunu doğrulayın. Yeni öğenin hem FarmApp Explorer'da hem de uygun veri kılavuzu görünümünde görünmesi gerekir.

    Veri kılavuzu görünümünde öğenin adını düzenleyebilirsiniz. Buradan da silebilirsiniz.

   ![Örnek veri kılavuzu görünümü](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Öğe eklemek için kod hakkında

Yeni öğe düğmeleri için aşağıdaki alternatif kod biraz daha basittir.

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

Ancak, bu kod yeni öğe için varsayılan bir ad ayarlamaz. DSL'nin Öğe Birleştirme Yönergelerinde tanımlanmamış olabileceğiniz özelleştirilmiş birleştirmeyi çalıştırmaz ve tanımlanmış herhangi bir özel birleştirme kodunu çalıştırmaz. 

Bu nedenle, kullanarak yeni <xref:Microsoft.VisualStudio.Modeling.ElementOperations> öğeler oluşturmanızı öneririz. Daha fazla bilgi için [bkz. Öğe Oluşturma ve Taşımayı Özelleştirme.](../modeling/customizing-element-creation-and-movement.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Domain-Specific Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)
- [Domain-Specific Dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
