---
title: ModelBus kullanarak modelleri tümleştirme
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a222d5f69d19d2891b4aa20239c1874f55a056e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536948"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Visual Studio ModelBus kullanarak modelleri tümleştirme

Visual Studio ModelBus modeller ve diğer araçlardan modeller arasında bağlantı oluşturmak için bir yöntem sağlar. Örneğin, etki alanına özgü dil (DSL) modellerini ve UML modellerini bağlayabilirsiniz. Tümleşik bir DSLs kümesi oluşturabilirsiniz.

ModelBus, bir modele veya bir modelin içindeki belirli bir öğeye benzersiz bir başvuru oluşturmanıza imkan tanır. Bu başvuru modelin dışında, örneğin başka bir modeldeki bir öğede depolanabilir. Daha sonra bir araç, bir aracı öğeye erişim almak istediğinde, model veri yolu altyapısı uygun modeli yükler ve öğesini döndürür. İsterseniz, modeli kullanıcıya gösterebilirsiniz. Dosyanın önceki konumunda erişilebilir durumda değilse, ModelBus kullanıcıdan onu bulmasını ister. Kullanıcı dosyayı bulursa, ModelBus bu dosyaya yapılan tüm başvuruları düzeltir.

> [!NOTE]
> ModelBus 'ın geçerli Visual Studio uygulamasında, bağlantılı modeller aynı Visual Studio çözümünde öğeler olmalıdır.

Ek bilgi ve örnek kod için bkz.:

- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Visual Studio için modelleme SDK 'Sı](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> DSL erişimi sağlama
 Bir modele veya öğelerine ModelBus başvuruları oluşturabilmeniz için önce DSL için bir ModelBusAdapter tanımlamanız gerekir. Bunu yapmanın en kolay yolu, DSL Tasarımcısı komutları ekleyen Visual Studio Model veri yolu uzantısını kullanmaktır.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> Bir DSL tanımını model veri yoluna göstermek için

1. DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın.

2. İletişim kutusunda **Bu DSL 'Yi ModelBus**' a göstermek istiyorum ' u seçin. Bu DSL 'nin modellerini sergilemesini ve diğer DSLs başvurularını kullanmasını istiyorsanız her iki seçeneği de belirleyebilirsiniz.

3. **Tamam**’a tıklayın. DSL çözümüne yeni bir "ModelBusAdapter" projesi eklenir.

4. DSL 'ye bir metin şablonundan erişmek istiyorsanız, yeni projedeki AdapterManager.tt öğesini değiştirmeniz gerekir. DSL 'ye komutlar ve olay işleyicileri gibi diğer koddan erişmek istiyorsanız bu adımı atlayın. Daha fazla bilgi için bkz. [bir metin şablonunda Visual Studio ModelBus kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. AdapterManagerBase Taban sınıfını [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))olarak değiştirin.

   2. Dosyanın sonuna yakın bir şekilde, bu ek özniteliği AdapterManager sınıfının önüne ekleyin:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. ModelBusAdapter projesi başvuruları ' nda, **Microsoft. VisualStudio. Textşablon. model. 11.0**ekleyin.

      DSL 'ye hem metin şablonlarından hem de diğer koddan erişmek istiyorsanız, biri değiştirilmiş ve bir değiştirilmemiş iki bağdaştırıcıya ihtiyacınız vardır.

5. **Tüm Şablonları Dönüştür**' e tıklayın.

6. Çözümü yeniden derleyin.

   Bu, artık ModelBus 'in bu DSL örneklerini açmasını olanaklı hale gelir.

   Klasör, `ModelBusAdapters\bin\*` Proje ve proje tarafından oluşturulan derlemeleri içerir `Dsl` `ModelBusAdapters` . Bu DSL 'yi başka bir DSL 'ye başvurmak için bu derlemeleri içeri aktarmanız gerekir.

### <a name="ensure-that-elements-can-be-referenced"></a>Öğelerin başvurulduğundan emin olun

Visual Studio ModelBus bağdaştırıcılar, varsayılan olarak onu tanımlamak için bir öğenin GUID 'ini kullanır. Bu tanımlayıcıların model dosyasında kalıcı olması gerekir.

Öğe kimliklerinin kalıcı olduğundan emin olmak için:

1. DslDefinition. dsl 'yi açın.

2. DSL Gezgini ' nde **XML serileştirme davranışı**' nı ve ardından **sınıf verileri**' ni genişletin.

3. Model veri yolu başvuruları oluşturmak istediğiniz her sınıf için:

    Sınıf düğümüne tıklayın ve Özellikler penceresi **SERILEŞTIRME kimliği** ' nin olarak ayarlandığından emin olun `true` .

   Alternatif olarak, GUID yerine öğeleri tanımlamak için öğe adlarını kullanmak istiyorsanız, oluşturulan bağdaştırıcıların parçalarını geçersiz kılabilirsiniz. Bağdaştırıcı sınıfında aşağıdaki yöntemleri geçersiz kılın:

- `GetElementId`Kullanmak istediğiniz tanımlayıcıyı döndürmek için geçersiz kılın. Bu yöntem, başvurular oluşturulurken çağrılır.

- `ResolveElementReference`Model veri yolu başvurusundan doğru öğeyi bulmak için geçersiz kılın.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Başka bir DSL 'den DSL 'ye erişme

Model veri yolu başvurularını DSL içindeki bir etki alanı özelliğinde depolayabilmeniz ve bunları kullanan özel kod yazabilirsiniz. Ayrıca, bir model dosyası ve içindeki bir öğe seçerek kullanıcının model veri yolu başvurusu oluşturmasına izin verebilirsiniz.

Bir DSL 'yi başka bir DSL 'ye yönelik başvuruları kullanmak üzere etkinleştirmek için, ilk olarak veri yolu başvurularını bir *Tüketici* yapmanız gerekir.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Bir DSL 'nin sunulan bir DSL 'ye yönelik başvuruları kullanmasını sağlamak için

1. DSL tanımı diyagramında, diyagramın ana kısmına sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın.

2. İletişim kutusunda, **model veri yolu başvurularını tüketmek için bu modeli etkinleştirmek istiyorum**' u seçin.

3. Tüketen DSL 'nin DSL projesinde, proje başvurularına aşağıdaki derlemeleri ekleyin. Bu derlemeleri (. dll dosyaları), sunulan DSL 'nin ModelBusAdapter\bin \\ * dizininde bulacaksınız.

    - Örneğin **Fabrikam.FamilyTree.Dsl.dll** , sunulan DSL derlemesi

    - Örneğin **Fabrikam.FamilyTree.ModelBusAdapter.dll** gösterilen model veri yolu bağdaştırıcısı derlemesi

4. Aşağıdaki .NET derlemelerini, tüketen DSL projesinin proje başvurularına ekleyin.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Bir model veri yolu başvurusunu bir etki alanı özelliğinde depolamak için

1. Tüketen DSL 'nin DSL tanımında, bir etki alanı sınıfına bir etki alanı özelliği ekleyin ve adını ayarlayın.

2. Özellikler penceresi, etki alanı özelliği seçili olarak, **türü** olarak ayarlayın `ModelBusReference` .

   Bu aşamada, program kodu özellik değerini ayarlayabilir, ancak Özellikler penceresi salt okunurdur.

   Kullanıcıların özelliği özelleşmiş bir ModelBus başvuru Düzenleyicisi ile ayarlamaya izin verebilirsiniz. Bu düzenleyicinin veya *seçicinin* iki sürümü vardır: biri, kullanıcıların bir model dosyası seçmesini sağlar ve diğeri ise modelin içindeki bir model dosyası ve bir öğe seçmesine olanak sağlar.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Kullanıcının bir etki alanı özelliğinde model veri yolu başvurusu ayarlamaya izin vermek için

1. Etki alanı özelliğine sağ tıklayın ve ardından **ModelBusReference 'a özgü özellikleri düzenle**' ye tıklayın. Bir iletişim kutusu açılır. Bu *model veri yolu seçicisinin*.

2. Uygun **türde ModelBusReference**: bir modele veya bir modelin içindeki bir öğeye tıklayın.

3. Dosya iletişim kutusu filtre dizesinde, gibi bir dize girin `Family Tree files |*.ftree` . Sunulan DSL 'nin dosya uzantısını yerine koyun.

4. Modeldeki bir öğeye başvuru yapmayı seçerseniz, kullanıcının seçebileceğiniz türlerin bir listesini ekleyebilirsiniz, örneğin Company. FamilyTree. Person.

5. **Tamam**' a ve ardından **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın.

    > [!WARNING]
    > Geçerli bir model veya varlık seçmediyseniz, etkin görünmesine rağmen Tamam düğmesinin etkisi olmayacaktır.

6. Şirket. FamilyTree. Person gibi hedef türlerin bir listesini belirttiyseniz, hedef DSL DLL 'sine başvurarak DSL projenize bir derleme başvurusu eklemeniz gerekir, örneğin Company.FamilyTree.Dsl.dll

### <a name="to-test-a-model-bus-reference"></a>Model veri yolu başvurusunu test etmek için

1. Hem sunulma hem de tüketen DSLs oluşturun.

2. F5 veya CTRL + F5 tuşlarına basarak DSLs 'den birini deneysel modda çalıştırın.

3. Visual Studio 'nun Deneysel örneğindeki hata ayıklama projesinde, her DSL örneği olan dosyaları ekleyin.

    > [!NOTE]
    > Visual Studio ModelBus, yalnızca aynı Visual Studio çözümündeki öğeler olan modellere yönelik başvuruları çözümleyebilir. Örneğin, dosya sisteminizin başka bir bölümünde bir model dosyası başvurusu oluşturamazsınız.

4. Sunulan DSL örneğinde bazı öğeleri ve bağlantıları oluşturun ve kaydedin.

5. Tüketim DSL 'nin bir örneğini açın ve model veri yolu başvurusu özelliği olan bir model öğesi seçin.

6. Özellikler penceresi, model veri yolu başvurusu özelliğine çift tıklayın. Seçici iletişim kutusu açılır.

7. **Araştır** ' a tıklayın ve sunulan DSL örneğini seçin.

     Ayrıca, öğe özgü model veri yolu başvurusunu belirttiyseniz, seçici modeldeki bir öğeyi seçmenizi sağlar.

## <a name="creating-references-in-program-code"></a>Program kodunda başvurular oluşturma

Bir modelin veya bir modelin içindeki bir öğenin başvurusunu depolamak istediğinizde, oluşturun `ModelBusReference` . İki tür vardır `ModelBusReference` : model başvuruları ve öğe başvuruları.

Bir model başvurusu oluşturmak için, modelin bir örnek ve dosya adı ya da Visual Studio proje öğesi olduğu DSL 'nin AdapterManager 'a ihtiyacınız vardır.

Bir öğe başvurusu oluşturmak için, model dosyası ve başvurmak istediğiniz öğe için bir bağdaştırıcıya ihtiyacınız vardır.

> [!NOTE]
> Visual Studio ModelBus, yalnızca aynı Visual Studio çözümündeki öğelere başvurular oluşturabilirsiniz.

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

2. Genellikle, bir kaynak DSL 'de depolanan model veri yolu başvurusunu (MBR) kullanarak bir hedef DSL 'ye erişirsiniz. Bu nedenle, şablonunuz kaynak DSL yönergesini ve MBR 'yi çözecek kodu içerir. Metin şablonları hakkında daha fazla bilgi için bkz. [etki alanına özgü dilden kod üretme](../modeling/generating-code-from-a-domain-specific-language.md).

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

   Daha fazla bilgi ve bir anlatım için bkz. [bir metin şablonunda Visual Studio ModelBus kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>ModelBusReference seri hale getiriliyor

Bir `ModelBusReference` dize biçiminde bir (MBR) depolamak istiyorsanız, seri hale getirebilirsiniz:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

Bu şekilde seri hale getirilen bir MBR bağlamdan bağımsızdır. Basit dosya tabanlı model veri yolu bağdaştırıcısı kullanıyorsanız MBR, mutlak bir dosya yolu içerir. Örnek model dosyaları hiçbir şekilde hareket etmeyeceğinden bu yeterlidir. Ancak, model dosyaları genellikle Visual Studio projesindeki öğeler olur. Kullanıcılarınız tüm projeyi dosya sisteminin farklı bölümlerine taşıyabilecek. Ayrıca, projeyi kaynak denetimi altında tutabilmek ve farklı bilgisayarlarda açabilmeleri beklenir. Bu nedenle yol adları, dosyaları içeren projenin konumuna göre serileştirilmelidir.

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

   Başvuruyu, **etki alanı türleri**altında **DSL Gezgini**'nde görebilirsiniz. Dış tür başvurularını el ile eklemek için kök düğümüne sağ tıklayın.

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

DSL tanımı diyagramına sağ tıkladıktan sonra ModelBus 'ı etkinleştir ' e tıklayın ve **Bu DSL 'Yi ModelBus**' a **etkin hale**getirebilir:

- Çözüme yeni bir proje `ModelBusAdapter` eklenir.

- Projeye bir başvuru `ModelBusAdapter` eklenir `DslPackage` . `ModelBusAdapter` projeye bir başvuru içerir `Dsl` .

- **DslPackage\source.Extention.tt**IÇINDE, `|ModelBusAdapter|` MEF bileşeni olarak eklenmiştir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Program Kodunda Dosyadan Model Açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Metin Şablonunda Visual Studio ModelBus'ı Kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
