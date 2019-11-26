---
title: Bir metin şablonunda ModelBus kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 5ed3e5c2-f60f-43c7-8ef4-754f511339c5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0d18103d2990b2734e4db1d1e7dc4261e08e7a7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301363"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Metin Şablonunda Visual Studio ModelBus'ı Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus başvurularını içeren bir modeli okuyan metin şablonları yazarsanız, hedef modellere erişim için başvuruları çözümlemek isteyebilirsiniz. Bu durumda, metin şablonlarını ve başvurulan etki alanına özgü diller (DSL) uyarlamak için gerekenler:

- Hedefi olan başvuruları DSL erişim metin şablonları için yapılandırılmış bir ModelBus bağdaştırıcısı olmalıdır. DSL de başka bir koddan erişirseniz, yeniden yapılandırılmış bağdaştırıcısı ek olarak standart ModelBus bağdaştırıcısı gereklidir.

     Bağdaştırıcı yöneticisinin [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) 'dan devralması ve `[HostSpecific(HostName)]`özniteliğine sahip olması gerekir.

- Şablon [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))öğesinden devralması gerekir.

> [!NOTE]
> ModelBus başvuruları içermez DSL modeli okumak istiyorsanız, DSL projelerinizde oluşturulan yönerge işlemcileri kullanabilirsiniz. Daha fazla bilgi için bkz. [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md).

 Metin şablonları hakkında daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="creating-a-model-bus-adapter-for-access-from-text-templates"></a>Metin şablonlarından erişim için bir Model veri yolu bağdaştırıcısı oluşturma
 Metin şablonunda ModelBus başvuru çözmek için ' % s'hedefi DSL uyumlu bir bağdaştırıcı olmalıdır. Metin şablonları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] belge düzenleyicilerinden ayrı bir AppDomain içinde yürütülür ve bu nedenle bağdaştırıcının DTE aracılığıyla erişmek yerine modeli yüklemesi gerekir.

#### <a name="to-create-a-modelbus-adapter-that-is-compatible-with-text-templates"></a>Metin şablonları ile uyumlu bir ModelBus bağdaştırıcısı oluşturmak için

1. Hedef DSL çözümünde bir **ModelBusAdapter** projesi yoksa, ModelBus uzantı Sihirbazı 'nı kullanarak bir tane oluşturun:

    1. Bunu yapmadıysanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus uzantısını indirin ve yükleyin. Daha fazla bilgi için bkz. [görselleştirme ve modelleme SDK](https://go.microsoft.com/fwlink/?LinkID=185579).

    2. DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın.

    3. İletişim kutusunda **Bu DSL 'Yi ModelBus**' a göstermek istiyorum ' u seçin. Bu DSL modellerinin kullanıma sunmak ve diğer DSL'ler başvurular kullanmak istiyorsanız, iki seçenek de seçebilirsiniz.

    4. **Tamam**'a tıklayın. Yeni bir proje "ModelBusAdapter" DSL çözüme eklenir.

    5. **Tüm Şablonları Dönüştür**' e tıklayın.

    6. Çözümü yeniden derleyin.

2. DSL 'ye hem metin şablonundan hem de komut gibi diğer koddan erişmek istiyorsanız **ModelBusAdapter** projesini çoğaltın:

    1. Windows Gezgini 'nde, **ModelBusAdapter. csproj**içeren klasörü kopyalayıp yapıştırın.

    2. Proje dosyasını yeniden adlandırın (örneğin, **T4ModelBusAdapter. csproj**için).

    3. **Çözüm Gezgini**, çözüm düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın. Yeni **T4ModelBusAdapter. csproj**bağdaştırıcı projesini bulun.

    4. Yeni projenin her bir `*.tt` dosyasında, ad alanını değiştirin.

    5. Yeni Çözüm Gezgini'nde projeye sağ tıklayın ve ardından Özellikler seçeneğine tıklayın. Özellik Düzenleyicisi'nde oluşturulan derleme ve varsayılan ad alanı adını değiştirin.

    6. Her iki bağdaştırıcı başvuruları sahip olacak şekilde DslPackage projede yeni bağdaştırıcı projeye bir başvuru ekleyin.

    7. DslPackage\source.extension.tt içinde yeni bağdaştırıcı projeniz başvuran bir satır ekleyin.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Tüm şablonları dönüştürün** ve çözümü yeniden oluşturun. Derleme hataları gerçekleşmelidir.

3. Yeni bağdaştırıcı projesinde aşağıdaki derlemelere başvurular ekleyin:

    - Microsoft.VisualStudio.TextTemplating.11.0

         Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. AdapterManager.tt içinde:

    - ' In [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))öğesinden devralması Için AdapterManagerBase bildirimini değiştirin.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Dosyanın sonuna AdapterManager sınıfı önce HostSpecific özniteliği değiştirin. Şu satırı kaldırın:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Aşağıdaki satırı ekleyin:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Bu öznitelik modelbus tüketici için bir bağdaştırıcı aradığında, kullanılabilen bağdaştırıcıları kümesini filtreler.

5. **Tüm şablonları dönüştürün** ve çözümü yeniden oluşturun. Derleme hataları gerçekleşmelidir.

## <a name="writing-a-text-template-that-can-resolve-modelbus-references"></a>ModelBus başvuruları çözümlemek için metin şablonu yazma
 Genellikle, okuyan ve bir "kaynak" DSL dosyaları oluşturan bir şablon ile başlayın. Bu şablon, kaynak modeli dosyalarını [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md)bölümünde açıklanan şekilde okumak IÇIN kaynak DSL projesinde oluşturulan yönergeyi kullanır. Ancak, kaynak DSL bir "hedef" DSL ModelBus başvurular içerir. Bu nedenle başvurularını çözümlemek ve hedef DSL erişmek şablon kodunu etkinleştirmek istiyorsunuz. Bu nedenle aşağıdaki adımları izleyerek şablonu uyarlamanız gerekir:

- Şablonun temel sınıfını [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140))olarak değiştirin.

- Şablon yönergesine `hostspecific="true"` ekleyin.

- ' % S'hedef DSL ve onun bağdaştırıcısı ve Modelbus'ı etkinleştirmek için derleme başvuruları ekleyin.

- DSL hedef bir parçası olarak oluşturulan yönergesi gerekli değildir.

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
    // (Let’s assume they’re all in the same model file):
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

 Bu metin şablonu yürütüldüğünde, `SourceDsl` yönergesi dosyayı `Sample.source`yükler. Şablon, `this.ModelRoot`başlayarak bu modelin öğelerine erişebilir. Kod etki alanı sınıfları ve bu DSL özelliklerini kullanabilirsiniz.

 Ayrıca, şablonu ModelBus başvuruları çözebilirsiniz. Hedef model için başvuru noktası olduğunda, etki alanı sınıfları ve bu modelin DSL özelliklerini kullanmak kod derleme yönergeleri sağlar.

- DSL projesi tarafından üretilen bir yönerge kullanmazsanız, aynı zamanda içermelidir.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- ModelBus 'a erişim sağlamak için `this.ModelBus` kullanın.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>İzlenecek yol: Modelbus'ı kullanan bir metin şablonu test etme
 Bu kılavuzda, aşağıdaki adımları izleyin:

1. İki DSL'ler oluşturun. Bir DSL, *Tüketici*, diğer DSL 'ye başvurabilen bir `ModelBusReference` özelliğine *sahiptir.*

2. Sağlayıcı iki ModelBus bağdaştırıcısı oluşturma: erişim metin şablonları, sıradan bir kod için.

3. DSL örneği modelleri tek bir Deneysel projesi oluşturun.

4. Bir alan özelliği bir modeldeki diğer modele işaret edecek şekilde ayarlayın.

5. İşaret edilen modeli açılan bir çift tıklama işleyicisi yazma.

6. Birinci modelin yük, diğer bir Modeli'ne başvuru izleyin ve diğer modeli okumak bir metin şablonu yazarsınız.

#### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>ModelBus için erişilebilir olan bir DSL oluşturun

1. Yeni bir DSL çözümü oluşturun. Bu örnekte, Görev akışı çözüm şablonu seçin. Dil adını `MBProvider` ve dosya adı uzantısını ". sağla" olarak ayarlayın.

2. DSL tanımı diyagramında, en üstte yer alan diyagramın boş bir kısmına sağ tıklayın ve ardından **ModelBus 'ı etkinleştir**' e tıklayın.

   - **ModelBus 'ı etkinleştir**' i GÖRMÜYORSANıZ, vmsdk ModelBus uzantısını indirmeniz ve kurmanız gerekir. VMSDK sitesinde bulun: [görselleştirme ve modelleme SDK](https://go.microsoft.com/fwlink/?LinkID=185579).

3. ModelBus 'ı **Etkinleştir** iletişim kutusunda, **Bu DSL 'Yi ModelBus için kullanıma sunun**' ı seçin ve ardından **Tamam**' a tıklayın.

    `ModelBusAdapter`yeni bir proje, çözüme eklenir.

   Artık ModelBus metin şablonlarını tarafından erişilebilecek bir DSL var. Komutlar, olay işleyicileri veya model dosya Düzenleyicisi AppDomain içinde çalışan tüm kuralları, kod başvuruları çözümlenebilir. Bununla birlikte, metin şablonları ayrı bir AppDomain içinde çalıştırın ve onu düzenlenirken bir model erişemez. Bu DSL ModelBus başvurular bir metin şablonundan erişmek istiyorsanız, ayrı bir ModelBusAdapter olması gerekir.

#### <a name="to-create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Metin şablonları için yapılandırılmış bir ModelBus bağdaştırıcısı oluşturmak için

1. Windows Gezgini'nde, kopyalayın ve ModelBusAdapter.csproj içeren klasöre yapıştırın.

    T4ModelBusAdapter klasörün adı.

    Proje dosyası T4ModelBusAdapter.csproj yeniden adlandırın.

2. Çözüm Gezgini'nde T4ModelBusAdapter MBProvider çözüme ekleyin. Çözüm düğümüne sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Varolan proje**' ye tıklayın.

3. T4ModelBusAdapter proje düğümüne sağ tıklayın ve ardından Özellikler seçeneğine tıklayın. Proje Özellikleri penceresinde, **derleme adı** ve **varsayılan ad alanını** `Company.MBProvider.T4ModelBusAdapters`olarak değiştirin.

4. Satır aşağıdakine benzer olacak şekilde T4ModelBusAdapter her *.tt dosyasında "T4" son kısmını, ad alanı yerleştirin.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. `DslPackage` projesinde, `T4ModelBusAdapter`bir proje başvurusu ekleyin.

6. DslPackage\source.extension.tt ' de `<Content>`altına aşağıdaki satırı ekleyin.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. `T4ModelBusAdapter` projesinde,: **Microsoft. VisualStudio. Textşablon. model. 11.0** öğesine bir başvuru ekleyin

8. Open T4ModelBusAdapter\AdapterManager.tt:

   1. AdapterManagerBase Taban sınıfını [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))olarak değiştirin. Bu bölümü dosyasının aşağıdakine benzer.

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

   2. Dosyanın sonuna, aşağıdaki ek öznitelik sınıfı AdapterManager önüne ekleyin.

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

10. Çözümü yeniden derleyin. F5'e tıklayın.

11. F5 tuşuna basarak DSL çalışır durumda olduğunu doğrulayın. Deneysel projede `Sample.provider`açın. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Deneysel örneğini kapatın.

    Bu DSL ModelBus başvuruları artık metin şablonlarında ve ayrıca sıradan bir kod çözülebilir.

#### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Bir DSL ModelBus başvuru etki alanı özelliği ile oluşturun

1. En az bir dil çözümü şablonu kullanarak yeni bir DSL oluşturun. MBConsumer dil adı ve dosya adı uzantısı için ".consume" olarak ayarlayın.

2. DSL projesinde MBProvider DSL derlemesine bir başvuru ekleyin. `MBConsumer\Dsl\References` öğesine sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın. **Araştır** sekmesinde `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll` bulun

    Bu, diğer DSL kullanan kodu oluşturmanıza olanak sağlar. Birden çok DSL başvuruları oluşturmak istiyorsanız, bunları da ekleyin.

3. DSL tanımı diyagramında diyagrama sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın. İletişim kutusunda, **ModelBus 'ı kullanmak için bu DSL 'Yi etkinleştir**' i seçin.

4. Sınıfında `ExampleElement`yeni bir etki alanı özelliği `MBR`ekleyin ve Özellikler penceresi türünü `ModelBusReference`olarak ayarlayın.

5. Diyagramda etki alanı özelliğine sağ tıklayın ve sonra **ModelBusReference 'a özgü özellikleri düzenle**' ye tıklayın. İletişim kutusunda **bir model öğesi**seçin.

    Dosya iletişim filtresi için aşağıdaki ayarlayın.

    `Provider File|*.provide`

    Alt dizeden sonra "&#124;" dosya seçimi iletişim kutusu için bir filtredir. \* Kullanarak herhangi bir dosyaya izin verecek şekilde ayarlayabilirsiniz.\*

    **Model öğe türü** listesinde, sağlayıcı DSL 'de bir veya daha fazla etki alanı sınıfının adını girin (örneğin, Company. MBProvider. Task). Soyut sınıflar olabilirler. Liste boş bırakırsanız, kullanıcı herhangi bir öğeye başvuru ayarlayabilirsiniz.

6. İletişim kutusunu kapatın ve **tüm şablonları dönüştürün**.

   Başka bir DSL öğelerine başvurular içeren bir DSL oluşturdunuz.

#### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Çözümdeki başka bir dosyaya ModelBus başvuru oluşturun

1. MBConsumer çözümde, CTRL + F5 tuşlarına basın. **Mbconsumer\debugging** projesinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deneysel bir örneği açılır.

2. **Mbconsumer\debugging** projesine bir Sample. sağlamalısınız kopyası ekleyin. Bunun gerekli olmasının nedeni ModelBus başvuru aynı çözüm içindeki bir dosyaya başvurmalıdır.

   1. Hata ayıklama projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın.

   2. **Öğe Ekle** iletişim kutusunda, filtreyi **tüm dosyalar (\*.\*)** olarak ayarlayın.

   3. `MBProvider\Debugging\Sample.provide` gidin ve **Ekle**' ye tıklayın.

3. `Sample.consume` programını açın.

4. Bir örnek şekle tıklayın ve Özellikler penceresi, MBR özelliğinde **[...]** öğesine tıklayın. İletişim kutusunda, **Araştır** ' a tıklayın ve `Sample.provide`' yi seçin. Öğeleri penceresinde görev türü genişletin ve öğelerden birini seçin.

5. Dosyayı kaydedin.

    ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Deneysel örneğini henüz kapatmayın.)

   Başka bir modelinde bir öğedeki ModelBus başvuru içeren bir model oluşturdunuz.

#### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Metin şablonunda ModelBus başvuru çözümleyin

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]deneysel örneğinde bir örnek metin şablonu dosyası açın. İçeriği aşağıdaki gibi ayarlayın.

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

    1. `template` yönergesinin `hostSpecific` ve `inherits` özniteliklerinin ayarlanması gerekir.

    2. Tüketici modeli, her zamanki şekilde bu DSL içinde oluşturulan bir yönerge işlemcisi aracılığıyla erişilir.

    3. Derleme ve içeri aktarma yönergeleri ModelBus ve sağlayıcı DSL türlerine erişebilir olması gerekir.

    4. Birçok MBRs aynı modele bağlı olduğunu biliyorsanız, yalnızca bir kez CreateAdapter çağırmak daha iyidir.

2. Şablonu kaydedin. Elde edilen metin dosyası aşağıdakine benzer olduğunu doğrulayın.

    ```

    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2

    ```

#### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Bir hareket işleyicisi ModelBus başvuru çözümleyin

1. Çalışıyorsa, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Deneysel örneğini kapatın.

2. MBConsumer\Dsl\Custom.cs adlı ve içeriğini aşağıdaki ayarlı bir dosya ekleyin.

    ```

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

3. CTRL + F5 tuşlarına basın.

4. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]deneysel örneğinde `Debugging\Sample.consume`açın.

5. Bir şekil çift tıklayın.

     Bu öğe üzerindeki MBR ayarladıysanız, başvurulan model açar ve başvurulan öğe seçilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [Code Generation ve T4 metin şablonlarını](../modeling/code-generation-and-t4-text-templates.md) kullanarak modelleri tümleştirme
