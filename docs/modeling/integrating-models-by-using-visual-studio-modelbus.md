---
title: Modelbus kullanarak Modelleri Tümleştirme
description: ModelBus Visual Studio nın modeller arasında ve diğer araçlardan modellere bağlantı oluşturmak için bir yöntem sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: e59383e5ef150cce7bb342f7759289898e2c31805a316a25b8de4a9d0811daaf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356133"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Visual Studio Modelbus kullanarak modelleri tümleştirin

Visual Studio ModelBus, modeller arasında ve diğer araçlardan modellere bağlantılar oluşturmak için bir yöntem sağlar. Örneğin, etki alanına özgü dil (DSL) modellerini ve UML modellerini bağlayabilirsiniz. Tümleşik bir DSL kümesi oluşturabilirsiniz.

ModelBus, bir modele veya modelin içindeki belirli bir öğeye benzersiz bir başvuru oluşturmanıza olanak sağlar. Bu başvuru, modelin dışında, örneğin başka bir modeldeki bir öğede depolandırabilir. Daha sonraki bir durumda, bir araç öğeye erişim elde etmek isterse, Model Bus altyapısı uygun modeli yükecek ve öğeyi geri dönecektir. 2008'de modeli kullanıcıya görüntüleniyor. Dosyaya önceki konumdan erişilemiyorsa ModelBus kullanıcıdan dosyayı bulmasını sorar. Kullanıcı dosyayı bulursa ModelBus bu dosyaya yapılan tüm başvuruları düzeltir.

> [!NOTE]
> ModelBus'Visual Studio geçerli uygulama modelinde bağlı modellerin aynı çözümdeki öğeler Visual Studio gerekir.

Ek bilgi ve örnek kod için bkz:

- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Visual Studio için Modelleme SDK'sı](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> DSL'ye Erişim Sağlama
 Modele veya öğelerine ModelBus başvuruları oluşturamadan önce DSL için bir ModelBusAdapter tanımlamanız gerekir. Bunu yapmanın en kolay yolu, Visual Studio'ye komut ekleyen DSL Tasarımcısı.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> DSL Tanımını Model Bus'a göstermek için

1. DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve ardından Modelbus'ı **Etkinleştir'e tıklayın.**

2. İletişim kutusunda Bu **DSL'yi ModelBus'ta göstermek istiyorum'ı seçin.** Bu DSL'nin modellerini ortaya çıkararak diğer DSL'lere başvurular tüketmesi için her iki seçeneği de seçebilirsiniz.

3. **Tamam**'a tıklayın. DSL çözümüne yeni bir "ModelBusAdapter" projesi eklenir.

4. DSL'ye bir metin şablonundan erişmek için yeni projede AdapterManager.tt değiştirmeniz gerekir. DSL'ye komutlar ve olay işleyicileri gibi diğer kodlardan erişmek için bu adımı atlarsınız. Daha fazla bilgi için [bkz. Visual Studio Şablonunda ModelBus Kullanma.](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

   1. AdapterManagerBase temel sınıfını [VsTextTemplatingModelingAdapterManager olarak değiştirme.](/previous-versions/ee844317(v=vs.140))

   2. Dosyanın sonuna yakın bir yerde AdapterManager sınıfının önüne şu ek özniteliğini ekler:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. ModelBusAdapter Başvurusu projesine **Microsoft.VisualStudio.TextTemplating.Modeling.11.0 ekleyin.**

      DSL'ye hem metin şablonlarından hem de başka bir koddan erişmek için biri değiştirilmiş ve biri değiştirilmemiş iki bağdaştırıcı gerekir.

5. Tüm **Şablonları Dönüştür'e tıklayın.**

6. Çözümü yeniden derleyin.

   ModelBus'ın bu DSL örneklerini açması artık mümkündür.

   klasörü, `ModelBusAdapters\bin\*` proje ve proje tarafından inşa edilen `Dsl` derlemeleri `ModelBusAdapters` içerir. Bu DSL'ye başka bir DSL'den başvuru yapmak için bu derlemeleri içeri aktarmanız gerekir.

### <a name="ensure-that-elements-can-be-referenced"></a>Öğelere başvurulanın sağlana olduğundan emin olmak

Visual Studio ModelBus bağdaştırıcıları, bir öğeyi tanımlamak için varsayılan olarak guid'lerini kullanır. Bu nedenle bu tanımlayıcıların model dosyasında kalıcı olması gerekir.

Öğe kimliklerini kalıcı olmasını sağlamak için:

1. DslDefinition.dsl'i açın.

2. DSL Gezgini'nde **Xml Serileştirme Davranışı'nın ardından** Sınıf **Verileri'ni genişletin.**

3. Model Bus başvurularını oluşturmak istediğiniz her sınıf için:

    Sınıf düğümüne tıklayın ve Özellikler penceresi Serileştirme **Kimliği'nin olarak ayarlanmış** olduğundan emin `true` olun.

   Alternatif olarak, GUID'ler yerine öğeleri tanımlamak için öğe adlarını kullanmak için, oluşturulan bağdaştırıcıların bölümlerini geçersiz kılabilirsiniz. Bağdaştırıcı sınıfında aşağıdaki yöntemleri geçersiz kılın:

- Kullanmak `GetElementId` istediğiniz tanımlayıcıyı geri almak için geçersiz kılın. Bu yöntem, başvurular oluşturulurken çağrılır.

- `ResolveElementReference`Model Bus başvurusundan doğru öğeyi bulmak için geçersiz kılın.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Başka bir DSL'den DSL'ye erişme

Model veri verisi başvurularını DSL'de bir etki alanı özelliğinde depolar ve bunları kullanan özel kodlar yazabilirsiniz. Ayrıca bir model dosyası ve içindeki bir öğeyi seçerek kullanıcının model veri veri sistemi başvurusu oluşturmasına da izin veebilirsiniz.

DSL'nin başka bir DSL'ye başvurular kullanmalarını sağlamak için önce bunu model veri *yol* başvurularının tüketicisi yapmanız gerekir.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>DSL'nin, ortaya çıkarılan DSL başvurularını tüketmesi için

1. DSL Tanımı diyagramında diyagramın ana parçasına sağ tıklayın ve ardından Modelbus'ı **Etkinleştir'e tıklayın.**

2. İletişim kutusunda Bu modelin **model veri verisi başvurularını tüketmesi için etkinleştirmek istiyorum'ı seçin.**

3. Tüketen DSL'nin Dsl projesine aşağıdaki derlemeleri proje başvurularını ekleyin. Bu derlemeleri (.dll dosyaları) açığa çıkarılacak DSL'nin ModelBusAdapter\bin \\ * dizininde bulabilirsiniz.

    - Maruz kalan DSL derlemesi, **örneğinFabrikam.FamilyTree.Dsl.dll**

    - Açık model veri veri verisi bağdaştırıcısı derlemesi, **örneğinFabrikam.FamilyTree.ModelBusAdapter.dll**

4. Aşağıdaki .NET derlemelerini, kullanan DSL projesinin proje başvurularına ekleyin.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Model Bus Başvurularını bir etki alanı özelliğinde depolamak için

1. Tüketen DSL'nin DSL Tanımında, bir etki alanı sınıfına bir etki alanı özelliği ekleyin ve adını ayarlayın.

2. Etki Özellikler penceresi etki alanı özelliği seçiliyken Tür **olarak** `ModelBusReference` ayarlayın.

   Bu aşamada, program kodu özellik değerini ayarlayabilirsiniz, ancak bu özellik Özellikler penceresi.

   Kullanıcıların özelliği özelleştirilmiş bir ModelBus başvuru düzenleyicisiyle ayarlamasına izin veebilirsiniz. Bu düzenleyicinin veya seçicinin iki sürümü *vardır:* biri kullanıcıların bir model dosyası seçmelerini sağlarken diğeri ise kullanıcıların model dosyası ve model içindeki bir öğeyi seçmelerini sağlar.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Kullanıcının bir etki alanı özelliğinde Model Bus Başvurusu ayarlamasına izin vermek için

1. Etki alanı özelliğine sağ tıklayın ve ardından Modeli **DüzenleBusReference'a özgü özellikler'e tıklayın.** Bir iletişim kutusu açılır. Bu Model *VeriSi Seçicisi'dir.*

2. Uygun **Model TürBusReference:** öğesini bir modele veya modelin içindeki bir öğeye seçin.

3. Dosya iletişim kutusu filtre dizesine gibi bir dize `Family Tree files |*.ftree` girin. Maruz kalan DSL'nizin dosya uzantısını kullanın.

4. Modeldeki bir öğeye başvurursanız, kullanıcının seçerek seçerek türlerin listesini ekleyebilirsiniz, örneğin Company.FamilyTree.Person.

5. Tamam **'a** tıklayın ve ardından **araç çubuğunda tüm** şablonları **Çözüm Gezgini** tıklayın.

    > [!WARNING]
    > Geçerli bir model veya varlık seçilmediyse, etkin görünse bile Tamam düğmesinin hiçbir etkisi olmaz.

6. Company.FamilyTree.Person gibi hedef türlerin listesini belirttiysanız, DSL projenize hedef DSL'nin DLL'sine başvuran bir derleme başvurusu eklemeniz gerekir, örneğin Company.FamilyTree.Dsl.dll

### <a name="to-test-a-model-bus-reference"></a>Model Veri Veri Modeli Başvurularını test etmek için

1. Hem açığa hem de tüketen DSL'leri derleme.

2. F5 veya CTRL+F5 tuşlarına basarak DENEYSEL modda DSL'lerden birini çalıştırın.

3. Visual Studio'nin deneysel örneğinde hata ayıklama projesinde, her DSL'nin örneği olan dosyaları ekleyin.

    > [!NOTE]
    > Visual Studio ModelBus yalnızca aynı çözümdeki öğeler olan modellere Visual Studio çözümleyebilirsiniz. Örneğin, dosya sisteminizin başka bir bölümünde model dosyasına başvuru oluşturamazsiniz.

4. Ortaya çıkarnan DSL örneğinde bazı öğeler ve bağlantılar oluşturun ve kaydedin.

5. Kullanan DSL'nin bir örneğini açın ve model veri verisi başvuru özelliğine sahip bir model öğesi seçin.

6. Bu Özellikler penceresi model veri verisi başvuru özelliğine çift tıklayın. Seçici iletişim kutusu açılır.

7. **Gözat'a** tıklayın ve ortaya çıkarnan DSL örneğini seçin.

     Seçici, öğeye özgü model veri veri yol başvurusu türü belirttiyebilirsiniz.

## <a name="creating-references-in-program-code"></a>Program Kodunda Başvuru Oluşturma

Bir modele veya bir öğeye bir başvuru depolamak istediğiniz zaman, bir oluşturmanız `ModelBusReference` gerekir. İki tür `ModelBusReference` vardır: model başvuruları ve öğe başvuruları.

Model başvurusu oluşturmak için, modelin örnek olduğu DSL'nin AdapterManager'ı ve modelin dosya adı Visual Studio proje öğesi gerekir.

Öğe başvurusu oluşturmak için model dosyası için bir bağdaştırıcıya ve başvurmak istediğiniz öğeye ihtiyacınız vardır.

> [!NOTE]
> ModelBus Visual Studio kullanarak yalnızca aynı çözümdeki öğelere Visual Studio oluşturabilirsiniz.

### <a name="import-the-exposed-dsl-assemblies"></a>Sunulan DSL derlemelerini içeri aktarma

Tüketim projesinde, sunulan DSL 'nin DSL ve ModelBusAdapter derlemelerine proje başvuruları ekleyin.

Örneğin, ModelBus başvurularını bir MusicLibrary DSL öğelerinde depolamak istediğinizi varsayalım. ModelBus başvuruları FamilyTree DSL öğelerine başvuracaktır. `Dsl`MusicLibrary çözümünün projesinde, başvurular düğümünde, aşağıdaki derlemelere başvurular ekleyin:

- Fabrikam.FamilyTree.Dsl.dll-sunulan DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll-sunulan DSL 'nin ModelBus bağdaştırıcısı.

- Microsoft. VisualStudio. model. SDK. Integration. 11.0

- Microsoft. VisualStudio. model. SDK. Integration. Shell. 11.0

  Bu derlemeler `ModelBusAdapters` , altında sunulan DSL projesinde bulunabilir `bin\*` .

  Başvuruları oluşturacağınız kod dosyasında, genellikle bu ad alanlarını içeri aktarmanız gerekir:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Bir modele başvuru oluşturmak için

Bir model başvurusu oluşturmak için, sunulan DSL için AdapterManager 'a erişir ve modeli bir başvuru oluşturmak için kullanabilirsiniz. Ya da bir dosya yolu belirtebilirsiniz `EnvDTE.ProjectItem` .

AdapterManager 'da, modeldeki ayrı öğelere erişim sağlayan bir bağdaştırıcı elde edebilirsiniz.

> [!NOTE]
> İşiniz bittiğinde bağdaştırıcıyı atmalısınız. Bunu gerçekleştirmenin en kolay yolu bir `using` deyimidir. Aşağıdaki örnek bunu göstermektedir.

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

`modelReference`Daha sonra kullanabilmek istiyorsanız, onu dış türüne sahip bir etki alanı özelliğinde saklayabilirsiniz `ModelBusReference` :

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Kullanıcıların bu etki alanı özelliğini düzenlemesine izin vermek için, `ModelReferenceEditor` Düzenleyici özniteliğinde parametresi olarak kullanın. Daha fazla bilgi için bkz. [kullanıcının bir başvuruyu düzenlemesine Izin verme](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Bir öğeye başvuru oluşturmak için

Model için oluşturduğunuz bağdaştırıcı, başvuruları oluşturmak ve çözümlemek için kullanılabilir.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

`elementReference`Daha sonra kullanabilmek istiyorsanız, onu dış türüne sahip bir etki alanı özelliğinde saklayabilirsiniz `ModelBusReference` . Kullanıcıların düzenleme yapmasına izin vermek için `ModelElementReferenceEditor` Düzenleyici özniteliğinde parametresi olarak kullanın. Daha fazla bilgi için bkz. [kullanıcının bir başvuruyu düzenlemesine Izin verme](#editRef).

### <a name="resolving-references"></a>Başvuruları çözme

Bir `ModelBusReference` (MBR) varsa, modeli veya başvurduğu model öğesini elde edebilirsiniz. Öğe bir diyagramda veya başka bir görünümde sunulursa, görünümü açıp öğesini seçebilirsiniz.

MBR 'den bir bağdaştırıcı oluşturabilirsiniz. Bağdaştırıcıdan, modelin kökünü elde edebilirsiniz. Ayrıca, model içindeki belirli öğelere başvuran MBRs 'leri de çözebilirsiniz.

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Bir metin şablonundaki ModelBus başvurularını çözümlemek için

1. Erişmek istediğiniz DSL 'nin metin şablonları tarafından erişim için yapılandırılmış bir ModelBus bağdaştırıcısı olmalıdır. Daha fazla bilgi için bkz. [DSL 'ye erişim sağlama](#provide).

2. Genellikle, bir kaynak DSL 'de depolanan model veri yolu başvurusunu (MBR) kullanarak bir hedef DSL 'ye erişirsiniz. Bu nedenle, şablonunuz kaynak DSL yönergesini ve MBR 'yi çözecek kodu içerir. Metin şablonları hakkında daha fazla bilgi için bkz. [Domain-Specific dilden kod üretme](../modeling/generating-code-from-a-domain-specific-language.md).

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   daha fazla bilgi ve bir anlatım için bkz. [metin şablonunda Visual Studio ModelBus kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>ModelBusReference seri hale getiriliyor

Bir `ModelBusReference` dize biçiminde bir (MBR) depolamak istiyorsanız, seri hale getirebilirsiniz:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

Bu şekilde seri hale getirilen bir MBR bağlamdan bağımsızdır. Basit dosya tabanlı model veri yolu bağdaştırıcısı kullanıyorsanız MBR, mutlak bir dosya yolu içerir. Örnek model dosyaları hiçbir şekilde hareket etmeyeceğinden bu yeterlidir. ancak, model dosyaları genellikle Visual Studio projesindeki öğeler olur. Kullanıcılarınız tüm projeyi dosya sisteminin farklı bölümlerine taşıyabilecek. Ayrıca, projeyi kaynak denetimi altında tutabilmek ve farklı bilgisayarlarda açabilmeleri beklenir. Bu nedenle yol adları, dosyaları içeren projenin konumuna göre serileştirilmelidir.

### <a name="serializing-relative-to-a-specified-file-path"></a>Belirtilen dosya yoluna göre serileştirme

`ModelBusReference` `ReferenceContext` , İçinde serileştirilmesi gereken dosya yolu gibi bilgileri depolayabilmeniz için bir sözlük olan bir içerir.

Bir yola göre seri hale getirmek için:

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

Dizeden başvuru almak için:

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Diğer bağdaştırıcılar tarafından oluşturulan ModelBusReferences
 Kendi bağdaştırıcınızı oluşturmak istiyorsanız aşağıdaki bilgiler yararlı olur.

 `ModelBusReference`(MBR) iki bölümden oluşur: model veri yolu tarafından seri durumdan ÇıKARıLAN MBR üst bilgisi ve belirli bağdaştırıcı Yöneticisi tarafından işlenen bağdaştırıcıya özel. Bu, kendi bağdaştırıcı serileştirme biçiminizi sağlamanıza olanak tanır. Örneğin, bir dosya yerine bir veritabanına başvurabilirsiniz veya bağdaştırıcı başvurusunda ek bilgi saklayabilirsiniz. Kendi bağdaştırıcınız içinde ek bilgiler yerleştirebilir `ReferenceContext` .

 MBR 'yi serisini kaldırdığınızda, daha sonra MBR nesnesinde depolanan bir ReferenceContext sağlamalısınız. Bir MBR 'yi seri hale getirerek, depolanan ReferenceContext bağdaştırıcı tarafından, dizeyi oluşturmaya yardımcı olmak için kullanılır. Seri durumdan çıkarılan dize, ReferenceContext içindeki tüm bilgileri içermiyor. Örneğin, basit dosya tabanlı bağdaştırıcıda ReferenceContext, serileştirilmiş MBR dizesinde depolanmayan bir kök dosya yolu içerir.

 MBR, iki aşamada seri durumdan çıkarılacak:

- `ModelBusReferencePropertySerializer` , MBR üstbilgisiyle ilgilenen standart serileştirici. `SerializationContext`Anahtarı kullanılarak içinde depolanan standart dsl özellik paketini kullanır `ReferenceContext` `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` . Özellikle, `SerializationContext` öğesinin bir örneğini içermesi gerekir `ModelBus` .

- ModelBus bağdaştırıcınız, MBR 'nin bağdaştırıcıya özgü bölümüyle ilgilenir. MBR 'nin ReferenceContext öğesinde depolanan ek bilgileri kullanabilir. Basit dosya tabanlı bağdaştırıcı, ve anahtarlarını kullanarak kök dosya yollarını korur `FilePathLoadContextKey` `FilePathSaveContextKey` .

     Model dosyasındaki bir bağdaştırıcı başvurusu yalnızca kullanıldığı zaman seri durumdan çıkarılacak.

## <a name="to-create-a-model"></a>Bir model oluşturmak için

### <a name="creating-opening-and-editing-a-model"></a>Model oluşturma, açma ve düzenlemeyle
 Aşağıdaki parça, VMSDK Web sitesindeki durum makinesi örneğinden alınmıştır. Model oluşturmak ve açmak ve modelle ilişkili diyagramı almak için ModelBusReferences 'ın kullanımını gösterir.

 Bu örnekte, hedef DSL adı StateMachine ' dir. Birçok ad, model sınıfının adı ve ModelBusAdapter adı gibi, bundan türetilir.

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>Başvuruları doğrulama
 Brokenreferencealgılayıcı, ModelBusReferences 'ı tutan bir depodaki tüm etki alanı özelliklerini sınar. Herhangi bir eylemin bulunduğu yere sağlayan eylemi çağırır. Bu, özellikle doğrulama yöntemleri için yararlıdır. Aşağıdaki doğrulama yöntemi, modeli kaydetme denemesinden depoyu sınar ve hatalar penceresinde bozuk başvuruları raporlar:

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>ModelBus uzantısı tarafından gerçekleştirilen eylemler

Aşağıdaki bilgiler gerekli değildir, ancak ModelBus ' ın geniş bir kullanımını yaparsanız yararlı olabilir.

ModelBus uzantısı, DSL çözümünüzde aşağıdaki değişiklikleri yapar.

DSL tanımı diyagramına sağ tıkladığınızda, **ModelBus 'ı etkinleştir**' e tıklayın ve ardından **ModelBus 'ı kullanmak için bu DSL 'yi etkinleştir**' i seçin:

- DSL projesinde **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll** öğesine bir başvuru eklenir

- DSL tanımında, bir dış tür başvurusu eklenir: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference` .

   Başvuruyu, **etki alanı türleri** altında **DSL Gezgini**'nde görebilirsiniz. Dış tür başvurularını el ile eklemek için kök düğümüne sağ tıklayın.

- Yeni bir şablon dosyası eklenmiştir, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

Bir etki alanı özelliğinin türünü ModelBusReference olarak belirlediğinizde, özelliği sağ tıklatın ve **ModelBusReference 'a özgü özellikleri etkinleştir**' e tıklayın:

- Etki alanı özelliğine birkaç CLR özniteliği eklenir. Bunları Özellikler penceresi özel öznitelikler alanında görebilirsiniz. **Dsl\GeneratedCode\DomainClasses.cs**' de, özellik bildiriminde öznitelikleri görebilirsiniz:

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

DSL tanımı diyagramına sağ tıkladıktan sonra ModelBus 'ı etkinleştir ' e tıklayın ve **Bu DSL 'Yi ModelBus**' a **etkin hale** getirebilir:

- Çözüme yeni bir proje `ModelBusAdapter` eklenir.

- Projeye bir başvuru `ModelBusAdapter` eklenir `DslPackage` . `ModelBusAdapter` projeye bir başvuru içerir `Dsl` .

- **DslPackage\source.Extention.tt** IÇINDE, `|ModelBusAdapter|` MEF bileşeni olarak eklenmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Metin Şablonunda Visual Studio ModelBus'ı Kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
