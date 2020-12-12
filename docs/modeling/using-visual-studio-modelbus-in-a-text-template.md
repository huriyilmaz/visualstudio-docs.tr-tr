---
title: Metin şablonunda ModelBus kullanma
description: Visual Studio ModelBus başvurularını içeren bir modeli okuyan metin şablonları yazarsanız, hedef modellere erişim başvurularını çözmeyi öğrenin.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1025e7d35c20dc18c87942e23cf71b598d85637a
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361371"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Metin Şablonunda Visual Studio ModelBus'ı Kullanma

Visual Studio ModelBus başvurularını içeren bir modeli okuyan metin şablonları yazarsanız, hedef modellere erişim için başvuruları çözümlemek isteyebilirsiniz. Bu durumda, metin şablonlarını ve başvurulan etki alanına özgü dilleri (DSLs) uyarlamanız gerekir:

- Başvuruların hedefi olan DSL 'nin metin şablonlarından erişim için yapılandırılmış bir ModelBus bağdaştırıcısı olmalıdır. Diğer koddan DSL 'ye de eriştiğinizde, standart ModelBus bağdaştırıcısına ek olarak yeniden yapılandırılmış bağdaştırıcı gerekir.

     Bağdaştırıcı Yöneticisi [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) 'dan devralması ve özniteliğe sahip olması gerekir `[HostSpecific(HostName)]` .

- Şablon [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))öğesinden devralması gerekir.

> [!NOTE]
> ModelBus başvuruları içermeyen DSL modellerini okumak istiyorsanız DSL projelerinizde oluşturulan yönerge işlemcilerini kullanabilirsiniz. Daha fazla bilgi için bkz. [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md).

Metin şablonları hakkında daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Metin şablonlarından erişim için model veri yolu bağdaştırıcısı oluşturma

Metin şablonunda bir ModelBus başvurusunu çözümlemek için, hedef DSL 'nin uyumlu bir bağdaştırıcısı olmalıdır. Metin şablonları, Visual Studio belge düzenleyicilerinden ayrı bir AppDomain içinde yürütülür ve bu nedenle bağdaştırıcının DTE aracılığıyla erişmek yerine modeli yüklemesi gerekir.

1. Hedef DSL çözümünde bir **ModelBusAdapter** projesi yoksa, ModelBus uzantı Sihirbazı 'nı kullanarak bir tane oluşturun:

    1. Bunu yapmadıysanız Visual Studio ModelBus uzantısını indirin ve yükleyin. Daha fazla bilgi için bkz. [görselleştirme ve modelleme SDK](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın.

    3. İletişim kutusunda **Bu DSL 'Yi ModelBus**' a göstermek istiyorum ' u seçin. Bu DSL 'nin modellerini sergilemesini ve diğer DSLs başvurularını kullanmasını istiyorsanız her iki seçeneği de belirleyebilirsiniz.

    4. **Tamam** düğmesine tıklayın. DSL çözümüne yeni bir "ModelBusAdapter" projesi eklenir.

    5. **Tüm Şablonları Dönüştür**' e tıklayın.

    6. Çözümü yeniden derleyin.

2. DSL 'ye hem metin şablonundan hem de komut gibi diğer koddan erişmek istiyorsanız **ModelBusAdapter** projesini çoğaltın:

    1. Windows Gezgini 'nde, **ModelBusAdapter. csproj** içeren klasörü kopyalayıp yapıştırın.

    2. Proje dosyasını yeniden adlandırın (örneğin, **T4ModelBusAdapter. csproj** için).

    3. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın. Yeni **T4ModelBusAdapter. csproj** bağdaştırıcı projesini bulun.

    4. `*.tt`Yeni projenin her bir dosyasında, ad alanını değiştirin.

    5. **Çözüm Gezgini** yeni projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler düzenleyicisinde, oluşturulan derlemenin adlarını ve varsayılan ad alanını değiştirin.

    6. DslPackage projesinde, her iki bağdaştırıcıya da başvurular olması için yeni bağdaştırıcı projesine bir başvuru ekleyin.

    7. DslPackage\source.extension.tt ' de, yeni bağdaştırıcı projenize başvuran bir satır ekleyin.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Tüm şablonları dönüştürün** ve çözümü yeniden oluşturun. Hiçbir derleme hatası oluşmaz.

3. Yeni bağdaştırıcı projesinde, aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft. VisualStudio. Textşablon. 11.0
    - Microsoft. VisualStudio. Textşablon. model. 11.0

4. AdapterManager.tt içinde:

    - ' In [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))öğesinden devralması Için AdapterManagerBase bildirimini değiştirin.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Dosyanın sonuna yaklaşmadan önce, HostSpecific özniteliğini AdapterManager sınıfından önce değiştirin. Aşağıdaki satırı kaldırın:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Aşağıdaki satırı ekleyin:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Bu öznitelik, bir ModelBus tüketicisi bir bağdaştırıcı ararken kullanılabilen bağdaştırıcı kümesini filtreler.

5. **Tüm şablonları dönüştürün** ve çözümü yeniden oluşturun. Hiçbir derleme hatası oluşmaz.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>ModelBus başvurularını çözebilecek bir metin şablonu yazma

Genellikle, "kaynak" DSL 'den dosyaları okuyan ve üreten bir şablonla başlarsınız. Bu şablon, kaynak modeli dosyalarını [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md)bölümünde açıklanan şekilde okumak IÇIN kaynak DSL projesinde oluşturulan yönergeyi kullanır. Ancak, kaynak DSL "hedef" DSL 'ye ModelBus başvuruları içerir. Bu nedenle, başvuruları çözümlemek ve hedef DSL 'ye erişmek için şablon kodunu etkinleştirmek istiyorsunuz. Bu nedenle, aşağıdaki adımları izleyerek şablonu uyarlamanız gerekir:

- Şablonun temel sınıfını [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))olarak değiştirin.

- `hostspecific="true"`Şablon yönergesine dahil edin.

- Hedef DSL ve bağdaştırıcıya derleme başvuruları ekleyin ve ModelBus 'ı etkinleştirin.

- Hedef DSL 'nin bir parçası olarak oluşturulan yönergeye ihtiyacınız yoktur.

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

 Bu metin şablonu yürütüldüğünde, `SourceDsl` yönerge dosyayı yükler `Sample.source` . Şablon, bu modelin öğesinden başlayarak öğelerine erişebilir `this.ModelRoot` . Kod, bu DSL 'nin etki alanı sınıflarını ve özelliklerini kullanabilir.

 Ayrıca, şablon ModelBus başvurularını da çözümleyebilir. Başvuruların hedef modele işaret ettiği yerlerde, derleme yönergeleri kodun, bu modelin DSL 'nin etki alanı sınıflarını ve özelliklerini kullanmasına izin verir.

- DSL projesi tarafından oluşturulan bir yönergeyi kullanmıyorsanız, aşağıdakileri de eklemeniz gerekir.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- `this.ModelBus`ModelBus 'a erişim elde etmek için kullanın.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>İzlenecek yol: ModelBus kullanan bir metin şablonunu test etme
 Bu kılavuzda aşağıdaki adımları izleyeceğinizi görürsünüz:

1. İki DSLs oluşturun. Bir DSL, *Tüketici*, `ModelBusReference` diğer DSL 'ye başvurabilen bir özelliğe sahiptir. 

2. Sağlayıcıda iki ModelBus bağdaştırıcı oluşturun: biri metin şablonlarına, diğeri ise sıradan koda göre.

3. Tek bir deneysel projede DSLs örnek modellerini oluşturun.

4. Bir modeldeki bir etki alanı özelliğini diğer modele işaret etmek için ayarlayın.

5. İşaret edilen modeli açan çift tıklama işleyicisi yazın.

6. İlk modeli yükleyen bir metin şablonu yazın, diğer modele olan başvuruyu izleyin ve diğer modeli okuyun.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>ModelBus tarafından erişilebilen bir DSL oluşturun

1. Yeni bir DSL çözümü oluşturun. Bu örnekte, görev akışı çözüm şablonunu seçin. Dil adını `MBProvider` ve dosya adı uzantısını ". sağla" olarak ayarlayın.

2. DSL tanımı diyagramında, en üstte yer alan diyagramın boş bir kısmına sağ tıklayın ve ardından **ModelBus 'ı etkinleştir**' e tıklayın.

   **ModelBus 'ı etkinleştir**' i GÖRMÜYORSANıZ, vmsdk ModelBus uzantısını indirip yükleyin.

3. ModelBus 'ı **Etkinleştir** iletişim kutusunda, **Bu DSL 'Yi ModelBus için kullanıma sunun**' ı seçin ve ardından **Tamam**' a tıklayın.

    Yeni bir proje, `ModelBusAdapter` çözüme eklenir.

Artık ModelBus üzerinden metin şablonları tarafından erişilebilen bir DSL 'ye sahipsiniz. Bu başvuru, bir bütün olarak model dosya düzenleyicisinin AppDomain öğesinde çalışan komutların, olay işleyicilerinin veya kuralların kodunda çözülebilir. Ancak, metin şablonları ayrı bir uygulama etki alanında çalışır ve düzenleme sırasında modele erişemez. Bir metin şablonundan bu DSL 'ye ModelBus başvurularına erişmek istiyorsanız ayrı bir ModelBusAdapter olmalıdır.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Metin şablonları için yapılandırılmış bir ModelBus bağdaştırıcısı oluşturma

1. Dosya Gezgini 'nde, *ModelBusAdapter. csproj* içeren klasörü kopyalayıp yapıştırın.

    Klasörü **T4ModelBusAdapter** olarak adlandırın.

    *T4ModelBusAdapter. csproj* proje dosyasını yeniden adlandırın.

2. Çözüm Gezgini, MBProvider çözümüne T4ModelBusAdapter ekleyin. Çözüm düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın.

3. T4ModelBusAdapter proje düğümüne sağ tıklayın ve ardından Özellikler ' e tıklayın. Proje Özellikleri penceresinde, **derleme adı** ve **varsayılan ad alanını** olarak değiştirin `Company.MBProvider.T4ModelBusAdapters` .

4. T4ModelBusAdapter içindeki her *. tt dosyasında, "T4" öğesini ad alanının son bölümüne ekleyin, böylece satır aşağıdakine benzer.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. `DslPackage`Projede, öğesine bir proje başvurusu ekleyin `T4ModelBusAdapter` .

6. DslPackage\source.extension.tt içinde aşağıdaki satırı altına ekleyin `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. `T4ModelBusAdapter`Projede,: **Microsoft. VisualStudio. Textşablon. model. 11.0** öğesine bir başvuru ekleyin

8. Açık T4ModelBusAdapter\AdapterManager.tt:

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

11. DSL 'nin çalıştığını doğrulayın. Deneysel projede öğesini açın `Sample.provider` . Visual Studio 'nun Deneysel örneğini kapatın.

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

1. MBConsumer çözümünde, CTRL + F5 tuşlarına basın. **Mbconsumer\debugging** projesinde, Visual Studio 'nun deneysel bir örneği açılır.

2. **Mbconsumer\debugging** projesine bir Sample. sağlamalısınız kopyası ekleyin. Bir ModelBus başvurusunun aynı çözümdeki bir dosyaya başvurması gerektiğinden, bu gereklidir.

   1. Hata ayıklama projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın.

   2. **Öğe Ekle** iletişim kutusunda, filtreyi **tüm dosyalar ( \* . \* )** olarak ayarlayın.

   3. Öğesine gidin `MBProvider\Debugging\Sample.provide` ve ardından **Ekle**' ye tıklayın.

3. `Sample.consume` dosyasını açın.

4. Bir örnek şekle tıklayın ve Özellikler penceresi, MBR özelliğinde **[...]** öğesine tıklayın. İletişim kutusunda, **Araştır** ' a tıklayın ve öğesini seçin `Sample.provide` . Öğeler penceresinde, tür görevi ' ni genişletin ve öğelerinden birini seçin.

5. Dosyayı kaydedin. (Visual Studio 'nun Deneysel örneğini henüz kapatmayın.)

   Başka bir modeldeki bir öğeye ModelBus başvurusu içeren bir model oluşturdunuz.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Metin şablonunda bir ModelBus başvurusunu çözümleyin

1. Visual Studio 'nun deneysel örneğinde bir örnek metin şablonu dosyası açın. İçeriğini aşağıdaki şekilde ayarlayın.

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

1. Çalışıyorsa, Visual Studio 'nun Deneysel örneğini kapatın.

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

4. Visual Studio 'nun deneysel örneğinde öğesini açın `Debugging\Sample.consume` .

5. Tek bir şekle çift tıklayın.

    Bu öğe üzerinde MBR ayarladıysanız, başvurulan model açılır ve başvurulan öğe seçilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Kod Oluşturma ve T4 Metin Şablonları](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
