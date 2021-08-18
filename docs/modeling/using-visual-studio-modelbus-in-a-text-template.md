---
title: Metin Şablonunda ModelBus Kullanma
description: ModelBus başvurularını içeren bir modeli okumak için metin şablonları yazarsanız hedef modellere erişmek için Visual Studio çözümleyebilirsiniz.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 1406479a021c365df817224b5ee0ad2381cb8f7f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150527"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Metin Şablonunda Visual Studio ModelBus'ı Kullanma

ModelBus başvurularını içeren bir modeli Visual Studio metin şablonları yazarsanız, hedef modellere erişmek için başvuruları çözümlemek istiyor olabilir. Bu durumda, metin şablonlarını ve başvurulan etki alanına özgü dilleri (DSL) uyarlamanız gerekir:

- Başvuruların hedefi olan DSL'nin, metin şablonlarından erişim için yapılandırılmış bir ModelBus Bağdaştırıcısı olması gerekir. DSL'ye başka bir koddan da erişersiniz, standart ModelBus Bağdaştırıcısına ek olarak yeniden yapılandırılmış bağdaştırıcı gereklidir.

     Bağdaştırıcı yöneticisi [VsTextTemplatingModelingAdapterManager'dan](/previous-versions/ee844317(v=vs.140)) devralmalı ve özniteliğine sahip `[HostSpecific(HostName)]` olmalı.

- Şablonun [ModelBusEnabledTextTransformation'dan devralması gerekir.](/previous-versions/ee844263(v=vs.140))

> [!NOTE]
> ModelBus başvuruları içermeden DSL modellerini okumak için DSL projelerinize oluşturulan yönerge işlemcilerini kullanabilirsiniz. Daha fazla bilgi için [bkz. Metin Şablonlarından Modellere Erişme.](../modeling/accessing-models-from-text-templates.md)

Metin şablonları hakkında daha fazla bilgi için bkz. T4 Metin [Şablonları kullanarak Tasarım Zamanı Kodu Oluşturma.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Metin Şablonlarından Erişim için Model Veri Veri Kutusu Bağdaştırıcısı Oluşturma

Metin şablonunda ModelBus başvurularını çözümlemek için hedef DSL'nin uyumlu bir bağdaştırıcıya sahip olması gerekir. Metin şablonları, Visual Studio belge düzenleyicilerinden ayrı bir AppDomain içinde yürütülür ve bu nedenle bağdaştırıcının DTE üzerinden erişmek yerine modeli yüklemesi gerekir.

1. Hedef DSL çözümünde **ModelBusAdapter** projesi yoksa Modelbus Uzantısı sihirbazını kullanarak bir tane oluşturun:

    1. Daha önce Visual Studio ModelBus Uzantısını indirip yükleyin. Daha fazla bilgi için [bkz. Görselleştirme ve Modelleme SDK'sı.](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

    2. DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve ardından Modelbus'ı **Etkinleştir'e tıklayın.**

    3. İletişim kutusunda Bu **DSL'yi ModelBus'ta göstermek istiyorum'ı seçin.** Bu DSL'nin modellerini ortaya çıkarmasını ve diğer DSL'lere başvurular tüketmesi için her iki seçeneği de seçebilirsiniz.

    4. **Tamam**'a tıklayın. DSL çözümüne yeni bir "ModelBusAdapter" projesi eklenir.

    5. Tüm **Şablonları Dönüştür'e tıklayın.**

    6. Çözümü yeniden derleyin.

2. DSL'ye hem metin şablonundan hem de komut gibi başka bir koddan erişmek için **ModelBusAdapter projesini çoğaltabilirsiniz:**

    1. Bu Windows **ModelBusAdapter.csproj** klasörünü kopyalayıp yapıştırın.

    2. Proje dosyasını yeniden adlandırın (örneğin, **T4ModelBusAdapter.csproj olarak).**

    3. Bu **Çözüm Gezgini,** çözüm düğümüne sağ tıklayın, Ekle'nin üzerine **gelin** ve ardından Var olan **Project.** Yeni bağdaştırıcı projesi **olan T4ModelBusAdapter.csproj'yi bulun.**

    4. Yeni `*.tt` projenin her dosyasında ad alanını değiştirebilirsiniz.

    5. Çözüm Gezgini'da **yeni projeye sağ tıklayın ve** ardından Özellikler'e **tıklayın.** Özellikler düzenleyicisinde, oluşturulan derlemenin ve varsayılan ad alanının adlarını değiştirin.

    6. DslPackage projesinde, her iki bağdaştırıcıya da başvurular içeren yeni bağdaştırıcı projesine bir başvuru ekleyin.

    7. DslPackage\source.extension.tt yeni bağdaştırıcı projenize başvurulan bir satır ekleyin.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Tüm Şablonları Dönüştür ve** çözümü yeniden oluşturun. Derleme hatası oluşmaz.

3. Yeni bağdaştırıcı projesinde, aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. Şu AdapterManager.tt:

    - AdapterManagerBase [bildirimini, VsTextTemplatingModelingAdapterManager'dan devralacak şekilde değiştirme.](/previous-versions/ee844317(v=vs.140))

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Dosyanın sonuna yakın bir yerde HostSpecific özniteliğini AdapterManager sınıfından önce değiştirin. Aşağıdaki satırı kaldırın:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Aşağıdaki satırı ekler:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Bu öznitelik, modelbus tüketicisi bir bağdaştırıcıyı ararken kullanılabilen bağdaştırıcı kümelerini filtreler.

5. **Tüm Şablonları Dönüştür ve** çözümü yeniden oluşturun. Derleme hatası oluşmaz.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>ModelBus Başvurularını Çözümleye bir Metin Şablonu Yazma

Genellikle bir "kaynak" DSL'den dosya okutan ve oluşturan bir şablonla başlarsınız. Bu şablon, kaynak model dosyalarını Metin Şablonlarından Modellere Erişme konusunda açıklanan şekilde okumak için kaynak DSL projesinde oluşturulan [yönergesini kullanır.](../modeling/accessing-models-from-text-templates.md) Ancak, kaynak DSL bir "hedef" DSL için ModelBus Başvuruları içerir. Bu nedenle, başvuruları çözümlemek ve hedef DSL'ye erişmek için şablon kodunu etkinleştirmek istiyorsanız. Bu nedenle, aşağıdaki adımları kullanarak şablonu uyarlamalısınız:

- Şablonun temel sınıfını [ModelBusEnabledTextTransformation olarak değiştirme.](/previous-versions/ee844263(v=vs.140))

- Şablon `hostspecific="true"` yönergesine dahil.

- Hedef DSL'ye ve bağdaştırıcısına derleme başvuruları ekleyin ve ModelBus'i etkinleştirin.

- Hedef DSL'nin parçası olarak oluşturulan yönergesine ihtiyacınız yok.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 Bu metin şablonu yürütülürken `SourceDsl` yönergesi dosyasını `Sample.source` yükler. Şablon, 'den başlayarak bu modelin öğelerine `this.ModelRoot` erişebilirsiniz. Kod, bu DSL'nin etki alanı sınıflarını ve özelliklerini kullanabilir.

 Ayrıca, şablon ModelBus Başvurularını çözümleyeblir. Başvurular Hedef modeli işaret ediyorsa, derleme yönergeleri kodun o modelin DSL'sinde etki alanı sınıflarını ve özelliklerini kullanmasına izin verir.

- DSL projesi tarafından oluşturulan bir yönergeyi kullanmayacaksanız, aşağıdakileri de dahil etmek gerekir.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- `this.ModelBus`ModelBus'a erişim elde etmek için kullanın.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Adım adım kılavuz: ModelBus Kullanan Bir Metin Şablonunu Test Etme
 Bu kılavuzda şu adımları izleyin:

1. İki DSL oluşturun. Bir DSL, *Tüketici*, diğer `ModelBusReference` DSL, Sağlayıcı başvurabilirsiniz bir özelliği *vardır.*

2. Sağlayıcıda iki ModelBus Bağdaştırıcısı oluşturun: biri metin şablonlarına göre erişim için, diğeri normal kod için.

3. Tek bir deneysel projede DSL'lerin örnek modellerini oluşturun.

4. Bir modelde etki alanı özelliğini diğer modeli işaret etmek için ayarlayın.

5. Işaret eden modeli açan bir çift tıklama işleyicisi yazın.

6. İlk modeli yükley kapasitesine sahip bir metin şablonu yazın, diğer model başvurularını izleyin ve diğer modeli okuyun.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>ModelBus tarafından erişilebilen bir DSL oluşturma

1. Yeni bir DSL çözümü oluşturun. Bu örnek için, Görev Yöneticisi Flow şablonunu seçin. Dil adını olarak, `MBProvider` dosya adı uzantısını ise ".provide" olarak ayarlayın.

2. DSL Tanımı diyagramında, diyagramın üst kısıma yakın olmayan boş bir parçasına sağ tıklayın ve ardından **Modelbus'ı Etkinleştir'e tıklayın.**

   Modelbus'i **Etkinleştir'i görmüyorsanız** VMSDK ModelBus uzantısını indirip yükleyin.

3. **Modelbus'ı Etkinleştir iletişim** kutusunda Bu DSL'yi ModelBus'ta ortaya **çıkar'ı seçin** ve ardından Tamam'a **tıklayın.**

    Çözüme yeni `ModelBusAdapter` bir proje ( ) eklenir.

Artık ModelBus aracılığıyla metin şablonları tarafından erişilebilen bir DSL'niz var. Başvurular komutlar, olay işleyicileri veya kuralların kodunda çözümlenebiliyor ve bunların hepsi model dosya düzenleyicisinin AppDomain'inde çalıştırıldı. Ancak, metin şablonları ayrı bir AppDomain içinde çalıştırıldı ve düzendeyken modele eriş kullanılamaz. Bu DSL'ye ModelBus başvurularına bir metin şablonundan erişmek için ayrı bir ModelBusAdapter'a sahip olmak gerekir.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Metin Şablonları için yapılandırılmış bir ModelBus Bağdaştırıcısı oluşturma

1. Bu Dosya Gezgini *ModelBusAdapter.csproj klasörünü kopyalayıp yapıştırın.*

    Klasöre **T4ModelBusAdapter adını girin.**

    *T4ModelBusAdapter.csproj proje dosyasını yeniden adlandırır.*

2. Bu Çözüm Gezgini MBProvider çözümüne T4ModelBusAdapter ekleyin. Çözüm düğümüne sağ tıklayın, Ekle'nin üzerine **gelin ve** ardından Mevcut **Uygulama'Project.**

3. T4ModelBusAdapter proje düğümüne sağ tıklayın ve ardından Özellikler'e tıklayın. Proje özellikleri penceresinde Derleme Adı ve Varsayılan **Ad** **Alanı'nın 'i olarak** `Company.MBProvider.T4ModelBusAdapters` değiştirin.

4. T4ModelBusAdapter'daki her *.tt dosyasına ad alanının son parçasına "T4" ekleyin; böylece satır aşağıdakine benzer.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. Projesine `DslPackage` bir proje başvurusu `T4ModelBusAdapter` ekleyin.

6. DslPackage\source.extension.tt altına aşağıdaki satırı `<Content>` ekleyin.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. Projeye şu `T4ModelBusAdapter` başvuruyu ekleyin: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Open T4ModelBusAdapter\AdapterManager.tt:

   1. AdapterManagerBase Taban sınıfını [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))olarak değiştirin. Dosyanın bu bölümü artık aşağıdakine benzer.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {
       ```

   2. Dosyanın sonuna yakın bir şekilde, aşağıdaki ek özniteliği AdapterManager sınıfının önüne ekleyin.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Sonuç aşağıdakine benzer.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }
       ```

9. Çözüm Gezgini başlık çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın.

10. **F5** tuşuna basın.

11. DSL 'nin çalıştığını doğrulayın. Deneysel projede öğesini açın `Sample.provider` . Visual Studio Deneysel örneğini kapatın.

    Bu DSL 'ye yönelik ModelBus başvuruları artık metin şablonlarında ve ayrıca sıradan kodda çözülebilir.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>ModelBus başvuru etki alanı özelliği ile DSL oluşturun

1. En küçük dil çözümü şablonunu kullanarak yeni bir DSL oluşturun. Dil Mbtüketicisini adlandırın ve dosya adı uzantısını ". tüketme" olarak ayarlayın.

2. DSL projesinde, MBProvider DSL derlemesine bir başvuru ekleyin. Sağ tıklayın  `MBConsumer\Dsl\References` ve ardından **Başvuru Ekle**' ye tıklayın. **Araştır** sekmesine şunu bulun`MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Bu, diğer DSL 'yi kullanan kodu oluşturmanızı sağlar. Birkaç DSLs başvurusu oluşturmak istiyorsanız, bunları da ekleyin.

3. DSL tanımı diyagramında diyagrama sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın. İletişim kutusunda, **ModelBus 'ı kullanmak için bu DSL 'Yi etkinleştir**' i seçin.

4. Sınıfında, `ExampleElement` Yeni bir etki alanı özelliği ekleyin `MBR` ve Özellikler penceresi, türünü olarak ayarlayın `ModelBusReference` .

5. Diyagramda etki alanı özelliğine sağ tıklayın ve sonra **ModelBusReference 'a özgü özellikleri düzenle**' ye tıklayın. İletişim kutusunda **bir model öğesi** seçin.

    Dosya iletişim kutusu filtresini aşağıdaki şekilde ayarlayın.

    `Provider File|*.provide`

    "&#124;" sonra alt dize dosya seçimi iletişim kutusu için bir filtredir. * Kullanarak herhangi bir dosyaya izin verecek şekilde ayarlayabilirsiniz.\*

    **Model öğe türü** listesinde, sağlayıcı DSL 'de bir veya daha fazla etki alanı sınıfının adını girin (örneğin, Company. MBProvider. Task). Soyut sınıflar olabilirler. Listeden boş bırakırsanız, Kullanıcı başvuruyu herhangi bir öğeye ayarlayabilir.

6. İletişim kutusunu kapatın ve **tüm şablonları dönüştürün**.

   Başka bir DSL içindeki öğelere başvurular içerebilen bir DSL oluşturdunuz.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Çözümdeki başka bir dosyaya ModelBus başvurusu oluşturma

1. MBConsumer çözümünde, CTRL + F5 tuşlarına basın. **mbconsumer\debugging** projesinde Visual Studio deneysel bir örneği açılır.

2. **Mbconsumer\debugging** projesine bir Sample. sağlamalısınız kopyası ekleyin. Bir ModelBus başvurusunun aynı çözümdeki bir dosyaya başvurması gerektiğinden, bu gereklidir.

   1. Hata ayıklama projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın.

   2. **Öğe Ekle** iletişim kutusunda, filtreyi **tüm dosyalar ( \* . \* )** olarak ayarlayın.

   3. Öğesine gidin `MBProvider\Debugging\Sample.provide` ve ardından **Ekle**' ye tıklayın.

3. `Sample.consume` dosyasını açın.

4. Bir örnek şekle tıklayın ve Özellikler penceresi, MBR özelliğinde **[...]** öğesine tıklayın. İletişim kutusunda, **Araştır** ' a tıklayın ve öğesini seçin `Sample.provide` . Öğeler penceresinde, tür görevi ' ni genişletin ve öğelerinden birini seçin.

5. Dosyayı kaydedin. (Visual Studio Deneysel örneğini henüz kapatmayın.)

   Başka bir modeldeki bir öğeye ModelBus başvurusu içeren bir model oluşturdunuz.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Metin şablonunda bir ModelBus başvurusunu çözümleyin

1. Visual Studio deneysel örneğinde bir örnek metin şablonu dosyası açın. İçeriğini aşağıdaki şekilde ayarlayın.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     Aşağıdaki noktalara dikkat edin:

    - `hostSpecific`Yönergesinin ve `inherits` özniteliklerinin `template` ayarlanması gerekir.

    - Tüketici modeline, bu DSL 'de oluşturulan yönerge işlemcisi aracılığıyla her zamanki şekilde erişilir.

    - Derleme ve içeri aktarma yönergeleri, ModelBus ve sağlayıcı DSL türlerine erişebilmelidir.

    - Birçok MBRs 'nin aynı modele bağlı olduğunu biliyorsanız, CreateAdapter 'ı yalnızca bir kez çağırmanız daha iyidir.

2. Şablonu kaydedin. Ortaya çıkan metin dosyasının şuna benzediğini doğrulayın.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Bir hareket işleyicisindeki ModelBus başvurusunu çözümleyin

1. çalışıyorsa, Visual Studio deneysel örneğini kapatın.

2. *Mbconsumer\dsl\custom.cs* adlı bir dosya ekleyin ve içeriğini şu şekilde ayarlayın:

    ```csharp
    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }
    ```

3. **CTRL** + **F5** tuşuna basın.

4. Visual Studio deneysel örneğinde, öğesini açın `Debugging\Sample.consume` .

5. Tek bir şekle çift tıklayın.

    Bu öğe üzerinde MBR ayarladıysanız, başvurulan model açılır ve başvurulan öğe seçilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Kod Oluşturma ve T4 Metin Şablonları](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
