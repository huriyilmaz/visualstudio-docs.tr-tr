---
title: Windows Forms Tabanlı bir Alana Özgü Dil Oluşturma
description: Etki alanına özgü bir dil Windows Forms durumunu görüntülemek için etki alanı adlarını kullanma hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9a77a22b7ed888b28f12154974d735213952899c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389546"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Windows Forms tabanlı bir Domain-Specific Dili oluşturma

DSL diyagramı Windows Forms etki alanına özgü dil (DSL) modelinin durumunu görüntülemek için etki alanına özgü dil (DSL) modelini kullanabilirsiniz. Bu konu başlığında, Visual Studio Görselleştirme ve Modelleme SDK'sı kullanarak windows formunu DSL'ye bağlama konusunda size yol açıklanmıştır.

Aşağıdaki görüntüde, bir DSL örneğinin Windows Form kullanıcı arabirimi ve model gezgini yer amektedir:

![Visual Studio'de DSL örneği](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>DSL Windows Forms oluşturma

Minimal **WinForm Designer** DSL şablonu, kendi gereksinimlerinize uyacak şekilde değiştirebilirsiniz minimal bir DSL oluşturur.

1. **Minimal WinForm** Designer şablonundan DSL oluşturun.

    Bu kılavuzda aşağıdaki adlar varsayılır:

    - Çözüm ve DSL adı: `FarmApp`
    - Ad Alanı: `Company.FarmApp`

2. Şablonun sağladığı ilk örnekle denemeler oluşturun:

   1. Tüm Şablonları Dönüştür.

   2. Örneği derleme ve çalıştırma (**Ctrl** + **F5**).

   3. Visual Studio'nin deneysel `Sample` örneğinde, hata ayıklama projesinde dosyasını açın.

        Bir denetimde görüntülendiğinden Windows Forms.

        Modelin öğelerini Gezgin'de de görüntüleniyor.

        Forma veya Gezgin'e bazı öğeler ekleyin ve bunların diğer görüntüde görüntüleniyor olduğunu görün.

   Ana örnek Visual Studio DSL çözümü hakkında aşağıdaki noktalara dikkat değiştirilebilir:

- `DslDefinition.dsl` diyagram öğeleri içerir. Bunun nedeni, bu DSL'nin örnek modellerini görüntülemek için DSL diyagramlarını kullanmamanızdır. Bunun yerine, modele bir Windows Formu bağlar ve form öğeleri modeli görüntüler.

- ve projelerine ek olarak çözüm, kullanıcı arabirimi denetimi tanımını içeren UI projesi `Dsl` adlı üçüncü bir Windows Forms `DslPackage` `UI.`  içerir. `DslPackage` , `UI` ve `UI` 'ye `Dsl` bağlıdır.

- `DslPackage`Projesinde, `UI\DocView.cs` projede tanımlanan Windows Forms gösteren kodu `UI` içerir.

- Proje, `UI` DSL'ye bağlı bir form denetimi için çalışan bir örnek içerir. Ancak DSL Tanımını değiştirmişken bu çalışmaz. Proje `UI` şunları içerir:

  - adlı Windows Forms bir `ModelViewControl` sınıf.

  - ek bir `DataBinding.cs` kısmi tanımı içeren adlı bir `ModelViewControl` dosya. İçeriğini görmek için Çözüm Gezgini **dosyasındaki** kısayol menüsünü açın ve Kodu Görüntüle'yi **seçin.**

### <a name="about-the-ui-project"></a>UI projesi hakkında

DSL Tanım dosyasını kendi DSL'nizi tanımlamak üzere güncelleştirin, DSL'nizi görüntülemek için `UI` proje denetiminizi güncelleştirmeniz gerekir. ve `Dsl` `DslPackage` projelerinden farklı `UI` olarak, örnek proje'den `DslDefinitionl.dsl` oluşturulmaz. Kodu oluşturmak için .tt dosyaları ekebilirsiniz, ancak bu adım adım kılavuzda ele değildir.

## <a name="update-the-dsl-definition"></a>DSL tanımını güncelleştirme

Aşağıdaki görüntü, bu kılavuzda kullanılan DSL tanımıdır.

![DSL tanımı](../modeling/media/dsl-wpf-1.png)

1. DSL tasarımcısında DslDefinition.dsl'i açın.

2. **ExampleElement Silme**

3. **ExampleModel etki alanı sınıfını** olarak yeniden adlandırabilirsiniz. `Farm`

     `Size` **Int32** türünde ve Boole türünde adlı `IsOrganic` ek etki alanı özellikleri **sağlar.**

    > [!NOTE]
    > Kök etki alanı sınıfını siler ve ardından yeni bir kök oluşturun, Düzenleyici Kök Sınıfı özelliğini sıfırlamanız gerekir. **DSL Gezgini'nde** Düzenleyici'yi **seçin.** Ardından, Özellikler penceresi **Sınıf'ı olarak** `Farm` ayarlayın.

4. Aşağıdaki etki **alanı sınıflarını** oluşturmak için Adlandırılmış Etki Alanı Sınıfı aracını kullanın:

    - `Field` - Buna adlı ek bir etki alanı özelliği `Size` ver.

    - `Animal`- Bu Özellikler penceresi, Devralma **Değiştirici'sini Soyut** olarak **ayarlayın.**

5. Aşağıdaki sınıfları **oluşturmak** için Etki Alanı Sınıfı aracını kullanın:

    - `Sheep`

    - `Goat`

6. devralmak **ve** 'den devralmak `Goat` için Devralma aracını `Sheep` `Animal` kullanın.

7. ve **altına eklemek için** Ekleme `Field` aracını `Animal` `Farm` kullanın.

8. Diyagramı düzenli bir şekilde toplamanız iyi olabilir. Yinelenen öğe sayısını azaltmak için yaprak öğelerin **kısayol menüsündeki** Alt Ağacı Buraya Getir komutunu kullanın.

9. **Uygulamanın araç çubuğundaki** Tüm Şablonları Çözüm Gezgini.

10. Dsl **projesini** derleme.

    > [!NOTE]
    > Bu aşamada, diğer projeler hata olmadan derlemez. Ancak, derlemenin Veri Kaynağı Sihirbazı'nda kullanılabilir olması için Dsl projesini derlemek istiyoruz.

## <a name="update-the-ui-project"></a>KULLANıCı arabirimi projesini güncelleştirme

Artık DSL modelinde depolanan bilgileri görüntüecek yeni bir kullanıcı denetimi oluşturabilirsiniz. Kullanıcı denetimlerini modele bağlamanın en kolay yolu veri bağlamalarıdır. **ModelingBindingSource** adlı veri bağlama uyarıcı türü, ÖZELLIKLE VMSDK olmayan arabirimlere DSL'leri bağlamak için tasarlanmıştır.

### <a name="define-your-dsl-model-as-a-data-source"></a>DSL modelinizi veri kaynağı olarak tanımlama

1. Veri menüsünde **Veri** Kaynaklarını **Göster'i seçin.**

     Veri **Kaynakları** penceresi açılır.

     Yeni **Veri Kaynağı Ekle'yi seçin.** Veri **Kaynağı Yapılandırma Sihirbazı** açılır.

2. Nesne, **Ardından'ı seçin.** 

     **Dsl**, **Company.FarmApp öğesini genişletin** ve **modelinizin** kök sınıfı olan Grup'ı seçin. **Son**’u seçin.

     Kullanıcı Çözüm Gezgini artık **Properties\DataSources\Farm.datasource** içeriyor 

     Model sınıfınıza ilişkin özellikler ve ilişkiler Veri Kaynakları penceresinde görüntülenir.

     ![Veri kaynakları penceresi](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Modelinizi bir forma bağlama

1. KULLANıCı **arabirimi projesinde** tüm mevcut .cs dosyalarını silin.

2. KULLANıCı arabirimi **projesine adlı** yeni `FarmControl` bir Kullanıcı Denetimi **dosyası** ekleyin.

3. Veri **Kaynakları penceresinde,** Grup'daki açılan menüden **Ayrıntılar'ı** **seçin.**

    Diğer özellikler için varsayılan ayarları bırakın.

4. Tasarım görünümünde FarmControl.cs'yi açın.

    Veri **Kaynakları** penceresinden Farm'ı FarmControl'a sürükleyin.

    Her özellik için bir denetim kümesi görüntülenir. İlişki özellikleri denetim oluşturmaz.

5. **farmBindingNavigator'ı silin.** Bu, tasarımcıda da otomatik `FarmControl` olarak oluşturulur, ancak bu uygulama için kullanışlı değildir.

6. Araç kutusunu kullanarak iki **DataGridView** örneği oluşturun ve bunları ve olarak `AnimalGridView` adlarını `FieldGridView` girin.

   > [!NOTE]
   > Alternatif bir adım, Veri Kaynakları penceresindeki Hayvanlar ve Alanlar öğelerini denetime sürüklemektir. Bu eylem, kılavuz görünümü ile veri kaynağı arasında otomatik olarak veri kılavuzlarını ve bağlamaları oluşturur. Ancak bu bağlama, DSL'ler için doğru şekilde çalışmıyor. Bu nedenle, veri kılavuzlarını ve bağlamaları el ile oluşturmak daha iyidir.

7. Araç Kutusu **ModelingBindingSource aracını içeriyorsa** ekleyin. Veri sekmesinin kısayol menüsünde **Öğeleri** Seç'i **seçin.** Araç Kutusu **Öğelerini Seç iletişim kutusunda,** araç **sekmesinden ModelingBindingSource'.NET Framework** seçin. 

8. Araç Kutusunu kullanarak Iki **ModelingBindingSource** örneği oluşturun ve bunları ve olarak `AnimalBinding` `FieldBinding` adlar.

9. Her **ModelingBindingSource** için **DataSource** özelliğini **farmBindingSource olarak ayarlayın.**

     **DataMember özelliğini Hayvanlar** veya **Alanlar** olarak **ayarlayın.**

10. veri **kaynağı özelliklerini** `AnimalGridView` olarak, ve özelliklerini olarak `AnimalBinding`  `FieldGridView` `FieldBinding` ayarlayın.

11. Farm denetimi düzenini istediğiniz gibi ayarlayın.

    **ModelingBindingSource,** DSL'lere özgü çeşitli işlevleri gerçekleştiren bir bağdaştırıcıdır:

- Bir VMSDK Depolama İşlemsinde güncelleştirmeleri sarmalar.

   Örneğin, kullanıcı veri görünümü kılavuzundan bir satır silebilir, normal bir bağlama bir işlem özel durumuna neden olur.

- Kullanıcı bir satır seçerek veri kılavuzu Özellikler penceresi ilgili model öğesinin özelliklerini görüntülemeyi sağlar.

  ![DSL bağlama şeması](../modeling/media/dslwpf4.png)
  
  Veri kaynakları ve görünümler arasındaki bağlantıların şeması.

### <a name="complete-the-bindings-to-the-dsl"></a>DSL bağlamalarını tamamlama

1. Ui projesine ayrı bir kod dosyasına aşağıdaki **kodu** ekleyin:

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

2. Deneysel Visual Studio Örnek **dosyasını** açın.

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

     Alanın içeriğini değiştirmelisiniz ve Farm modelinin ilgili özelliği hemen değişir.

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
