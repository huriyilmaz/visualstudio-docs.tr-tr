---
title: Modelbus kullanarak modelleri tümleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9abb8bd82f8a00c37cb76588ded8813ec984067
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298904"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus, modeller ve diğer araçlardan modeller arasında bağlantı oluşturmak için bir yöntem sağlar. Örneğin, etki alanına özgü dil (DSL) modelleri ve UML modellerini bağlayabilirsiniz. DSL tümleşik bir dizi oluşturabilirsiniz.

 ModelBus benzersiz bir Modeli'ne veya bir model içinde belirli bir öğeye başvuru oluşturmanıza olanak sağlar. Bu başvuru modeli dışında Örneğin, başka bir modelinde bir öğedeki depolanabilir. Bir sonraki fırsatta, bir aracı öğeye erişmek istediğinde, Model veri yolu altyapı uygun model yüklenemiyor ve öğesini döndürür. İsterseniz, model kullanıcıya görüntüleyebilirsiniz. Dosyayı önceki konumuna erişilemiyor, ModelBus bulmak için kullanıcı sorar. Kullanıcı dosyasını bulursa, bu dosyaya yapılan tüm başvurular ModelBus düzeltir.

> [!NOTE]
> ModelBus 'ın geçerli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulamasında, bağlantılı modeller aynı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümünde öğeler olmalıdır.

 Ek bilgi ve örnek kod için bkz:

- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Visual Studio için modelleme SDK 'Sı](https://www.microsoft.com/download/details.aspx?id=48148)

## <a name="provide"></a>DSL erişimi sağlama
 Bir model veya öğelerini ModelBus başvuruları oluşturabilmek için DSL ModelBusAdapter tanımlamanız gerekir. Bunu yapmanın en kolay yolu, DSL Tasarımcısı komutları ekleyen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model veri yolu uzantısını kullanmaktır.

### <a name="expose"></a>Bir DSL tanımını model veri yoluna göstermek için

1. İndirin ve zaten yüklemiş olduğunuz sürece, Visual Studio Model veri yolu uzantıyı yükleyin. Daha fazla bilgi için bkz. [görselleştirme ve modelleme SDK](https://go.microsoft.com/fwlink/?LinkID=185579).

2. DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın.

3. İletişim kutusunda **Bu DSL 'Yi ModelBus**' a göstermek istiyorum ' u seçin. Bu DSL modellerinin kullanıma sunmak ve diğer DSL'ler başvurular kullanmak istiyorsanız, iki seçenek de seçebilirsiniz.

4. **Tamam**'a tıklayın. Yeni bir proje "ModelBusAdapter" DSL çözüme eklenir.

5. DSL bir metin şablonundan erişmek istiyorsanız, yeni projede AdapterManager.tt değiştirmeniz gerekir. Komutlar ve olay işleyicileri gibi diğer koddan DSL erişmek istiyorsanız bu adımı atlayın. Daha fazla bilgi için bkz. [bir metin şablonunda Visual Studio ModelBus kullanma](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. AdapterManagerBase Taban sınıfını [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140))olarak değiştirin.

   2. Dosyanın sonuna, bu ek öznitelik sınıfı AdapterManager önüne ekleyin:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. ModelBusAdapter projesi başvuruları ' nda, **Microsoft. VisualStudio. Textşablon. model. 11.0**ekleyin.

      Metin şablonları ve diğer kod DSL erişmek istiyorsanız, iki bağdaştırıcı, biri değiştirilmiş ve biri üzerinde değişiklik yapılmadan gerekir.

6. **Tüm Şablonları Dönüştür**' e tıklayın.

7. Çözümü yeniden derleyin.

   Artık bu DSL örneklerini açmak için ModelBus mümkündür.

   `ModelBusAdapters\bin\*` klasörü, `Dsl` projesi ve `ModelBusAdapters` projesi tarafından oluşturulan derlemeleri içerir. Bu DSL başka bir DSL başvurmak için bu bütünleştirilmiş kodları almanız gerekir.

### <a name="making-sure-that-elements-can-be-referenced"></a>Öğeleri başvurulabilir emin olma
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus bağdaştırıcıları, varsayılan olarak tanımlamak için bir öğenin GUID 'ini kullanır. Bu tanımlayıcılar, bu nedenle model dosyasında kalıcı olmasını.

##### <a name="to-ensure-that-element-ids-are-persisted"></a>Bu öğe kimlikleri kalıcı emin olmak için

1. DslDefinition.dsl açın.

2. DSL Gezgini ' nde **XML serileştirme davranışı**' nı ve ardından **sınıf verileri**' ni genişletin.

3. Model veri yolu oluşturmak istediğiniz her bir sınıf için başvuruyor:

    Sınıf düğümüne tıklayın ve Özellikler penceresi **seri hale getirme kimliğinin** `true`olarak ayarlandığından emin olun.

   Alternatif olarak, öğe adları yerine GUID öğeleri tanımlamak için kullanmak istiyorsanız, oluşturulan bağdaştırıcıların bölümlerini geçersiz kılabilirsiniz. Bağdaştırıcı sınıfı aşağıdaki yöntemleri geçersiz kıl:

- Kullanmak istediğiniz tanımlayıcıyı döndürmek için `GetElementId` geçersiz kılın. Bu yöntem, başvuruları oluştururken çağrılır.

- Model veri yolu başvurusundan doğru öğeyi bulmak için `ResolveElementReference` geçersiz kılın.

## <a name="editRef"></a>Başka bir DSL 'den DSL 'ye erişme
 Bir etki alanı özelliği DSL model veri yolu başvuruları depolayabilirsiniz ve bunları kullanan özel kod yazabilirsiniz. Ayrıca kullanıcının bir model dosyası ve bir öğesiyle seçerek bir modeli bus başvurusu oluşturmasını sağlayabilirsiniz.

 Bir DSL 'yi başka bir DSL 'ye yönelik başvuruları kullanmak üzere etkinleştirmek için, ilk olarak veri yolu başvurularını bir *Tüketici* yapmanız gerekir.

#### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Bir DSL oluşturulan bir DSL başvurular kullanmak üzere etkinleştirmek için

1. DSL tanımı diyagramında, diyagramın ana kısmına sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın.

2. İletişim kutusunda, **model veri yolu başvurularını tüketmek için bu modeli etkinleştirmek istiyorum**' u seçin.

3. Alıcı DSL Dsl projesinde aşağıdaki derlemeler projenin başvurular ekleyin. Bu derlemeleri (. dll dosyaları), sunulan DSL 'nin ModelBusAdapter\bin\\* dizininde bulacaksınız.

    - Sunulan DSL derlemesi, örneğin **fabrikam. FamilyTree. dsl. dll**

    - Sunulan model veri yolu bağdaştırıcısı derlemesi, örneğin **fabrikam. FamilyTree. ModelBusAdapter. dll**

4. Aşağıdaki .NET derlemelerini alıcı DSL proje proje başvurular ekleyin.

    1. **Microsoft. VisualStudio. modellemesi. SDK. Integration. 11.0. dll**

    2. **Microsoft. VisualStudio. model. SDK. Integration. Shell. 11.0. dll**

#### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Bir etki alanı özelliği bir Model veri yolu başvuru depolamak için

1. Alıcı DSL DSL tanımındaki alan sınıfı için bir alan özelliği ekleyin ve adını ayarlayın.

2. Özellikler penceresi, etki alanı özelliği seçili olarak, **türü** `ModelBusReference`olarak ayarlayın.

   Bu aşamada, program kodu özellik değeri ayarlayabilirsiniz ancak Özellikler penceresinde salt okunur.

   Özelleştirilmiş bir ModelBus başvuru düzenleyici ile özelliğini ayarlamak kullanıcılar izin verebilirsiniz. Bu düzenleyicinin veya *seçicinin* iki sürümü vardır: biri, kullanıcıların bir model dosyası seçmesini sağlar ve diğeri ise modelin içindeki bir model dosyası ve bir öğe seçmesine olanak sağlar.

#### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Model veri yolu başvuru bir etki alanı özelliği ayarlamak izin vermek için

1. Etki alanı özelliğine sağ tıklayın ve ardından **ModelBusReference 'a özgü özellikleri düzenle**' ye tıklayın. Bir iletişim kutusu açılır. Bu *model veri yolu seçicisinin*.

2. Uygun **türde ModelBusReference**: bir modele veya bir modelin içindeki bir öğeye tıklayın.

3. Dosya iletişim kutusu filtre dizesinde, `Family Tree files |*.ftree`gibi bir dize girin. DEVICEHIGH sunulan DSL'nizi dosya uzantısı.

4. Bir modeldeki bir öğeye başvuru seçerseniz, kullanıcı seçebilirsiniz, örneğin Company.FamilyTree.Person türlerinin bir listesini ekleyebilirsiniz.

5. **Tamam**' a ve ardından Çözüm Gezgini araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın.

    > [!WARNING]
    > Geçerli model veya varlık seçmediyseniz, Tamam düğmesine etkin görünebilir olsa bile hiçbir etkisi gerekir.

6. Company.FamilyTree.Person gibi hedef türlerinin bir listesi belirtilmişse, ardından bir bütünleştirilmiş kod başvurusu DSL projenize DLL hedef DSL, örneğin Company.FamilyTree.Dsl.dll başvuru eklemeniz gerekir

#### <a name="to-test-a-model-bus-reference"></a>Model veri yolu başvuru test etmek için

1. Kullanıma sunulan ve alıcı DSL'ler oluşturun.

2. Bir DSL, Deneysel modda F5 veya CTRL + F5 tuşlarına basarak çalıştırın.

3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Deneysel örneğindeki hata ayıklama projesinde, her DSL örneği olan dosyaları ekleyin.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus yalnızca aynı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümünde öğe olan modellere yönelik başvuruları çözümleyebilir. Örneğin, dosya sisteminizi başka bir kısmında bir model dosyasına bir başvuru oluşturulamıyor.

4. Bazı öğeleri ve bağlantılarına sunulan DSL örneğini oluşturun ve kaydedin.

5. Alıcı DSL örneği açın ve model veri yolu başvuru özelliğine sahip bir model öğesini seçin.

6. Özellikler penceresinde model veri yolu başvuru özelliği çift tıklayın. Seçici iletişim kutusunu açar.

7. **Araştır** ' a tıklayın ve sunulan DSL örneğini seçin.

     Model veri yolu başvurusu özel öğe türü belirtilirse Seçici Ayrıca, modeldeki bir öğe seçin olanak tanır.

## <a name="creating-references-in-program-code"></a>Program kodunda başvuruları oluşturma
 Bir model veya model içindeki bir öğeye başvuru saklamak istediğinizde, bir `ModelBusReference`oluşturursunuz. İki tür `ModelBusReference`vardır: model başvuruları ve öğe başvuruları.

 Model başvurusu oluşturmak için, modelin bir örnek, dosya adı veya [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje öğesi olduğu DSL 'nin AdapterManager 'a ihtiyacınız vardır.

 Bir öğe başvurusu oluşturmak için model dosyası ve başvurmak istediğiniz öğeyi için bir bağdaştırıcı gerekir.

> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus ile, yalnızca aynı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümdeki öğelere başvurular oluşturabilirsiniz.

### <a name="import-the-exposed-dsl-assemblies"></a>İfşa edilen DSL derlemeler Al
 Kullanan projenin proje başvurularına sunulan DSL DSL ve ModelBusAdapter derlemeleri ekleyin.

 Örneğin, öğeleri MusicLibrary DSL'nin ModelBus başvuruları depolamak istediğinizi varsayalım. ModelBus başvuruları FamilyTree DSL öğelerine başvuracaktır. MusicLibrary çözümünün `Dsl` projesinde, başvurular düğümünde, aşağıdaki derlemelere başvurular ekleyin:

- Fabrikam.FamilyTree.Dsl.dll - sunulan DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll - sunulan DSL ModelBus Bağdaştırıcısı'nı tıklatın.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Bu derlemeler, `bin\*`altında sunulan DSL 'nin `ModelBusAdapters` projesinde bulunabilir.

  Başvuruları oluşturacağı kod dosyasında, genellikle aşağıdaki ad alanlarını içeri aktarın gerekecektir:

```
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Bir Modeli'ne başvuru oluşturmak için
 Model başvuru oluşturmak için AdapterManager erişmek için kullanıma sunulan DSL ve model için bir başvuru oluşturmak için bunu kullanın. Bir dosya yolu ya da bir `EnvDTE.ProjectItem`belirtebilirsiniz.

 AdapterManager modelinde öğelere erişim sağlayan bir bağdaştırıcı elde edebilirsiniz.

> [!NOTE]
> İşiniz bittiğinde ile bir bağdaştırıcı dispose gerekir. Bunu gerçekleştirmenin en kolay yolu bir `using` deyimidir. Aşağıdaki örnek bunu göstermektedir.

```
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

 `modelReference` daha sonra kullanmak istiyorsanız, bunu dış tür `ModelBusReference`sahip bir etki alanı özelliğinde saklayabilirsiniz:

```
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

 Kullanıcıların bu etki alanı özelliğini düzenlemesine izin vermek için, düzenleyici özniteliğinde parametre olarak `ModelReferenceEditor` kullanın. Daha fazla bilgi için bkz. [kullanıcının bir başvuruyu düzenlemesine Izin verme](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Öğeye bir başvuru oluşturmak için
 Model için oluşturduğunuz bağdaştırıcısı oluşturmak ve başvuruları çözümlemek için kullanılabilir.

```
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

 `elementReference` daha sonra kullanmak istiyorsanız, bunu dış tür `ModelBusReference`sahip bir etki alanı özelliğinde saklayabilirsiniz. Kullanıcıların düzenleme yapmasına izin vermek için düzenleyici özniteliğinde parametresi olarak `ModelElementReferenceEditor` kullanın. Daha fazla bilgi için bkz. [kullanıcının bir başvuruyu düzenlemesine Izin verme](#editRef).

### <a name="resolving-references"></a>Başvurular çözümleniyor
 Bir `ModelBusReference` (MBR) varsa, modeli veya başvurduğu model öğesini elde edebilirsiniz. Öğe bir diyagram veya diğer görünüm sunulmazsa, görünümü açın ve öğeyi seçin.

 Bir bağdaştırıcı bir MBR'yi oluşturabilirsiniz. Bağdaştırıcısından modelin kökü elde edebilirsiniz. Ayrıca, model içindeki belirli öğelere başvuran MBRs çözebilirsiniz.

```
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

##### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Metin şablonunda ModelBus başvurularını çözümlemek için

1. Erişmek istediğiniz DSL erişimi için metin şablonları tarafından yapılandırılan bir ModelBus bağdaştırıcısı olmalıdır. Daha fazla bilgi için bkz. [DSL 'ye erişim sağlama](#provide).

2. Genellikle, DSL Model veri yolu başvurusu (MBR) kullanarak bir DSL kaynakta depolanan bir hedef erişim sağlarlar. Şablonunuz, bu nedenle MBR çözümlenecek yönergesi kaynak DSL ek olarak kodu içerir. Metin şablonları hakkında daha fazla bilgi için bkz. [etki alanına özgü dilden kod üretme](../modeling/generating-code-from-a-domain-specific-language.md).

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

## <a name="serializing-a-modelbusreference"></a>Bir ModelBusReference seri hale getirme
 Bir `ModelBusReference` (MBR) bir dize biçiminde depolamak istiyorsanız, bunu seri hale getirebilirsiniz:

```
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

 Bu şekilde serileştirilmiş bir MBR bağlamında bağımsızdır. Basit dosya tabanlı Model veri yolu bağdaştırıcısı kullanıyorsanız, MBR bir mutlak dosya yolunu içerir. Bu örnek model dosyaları hiçbir zaman geçmeniz durumunda yeterlidir. Ancak, model dosyaları genellikle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projesindeki öğeler olur. Kullanıcılarınızın, dosya sisteminin farklı bölümlerine tüm projeye taşımak ister. Ayrıca projenin kaynak denetimi altında tutun ve farklı bilgisayarlarda açmak beklediği. Dosyaları içeren proje konumu göreli yol adları bu nedenle seri hale.

### <a name="serializing-relative-to-a-specified-file-path"></a>Belirtilen dosya yolu göreli seri hale getirme
 `ModelBusReference`, içinde serileştirilmesi gereken dosya yolu gibi bilgileri depolayabilmeniz için bir sözlük olan `ReferenceContext`içerir.

 Göreli bir yol serileştirmek için:

```
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

 Dizeden başvuru almak için:

```
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>Diğer bağdaştırıcıları tarafından oluşturulan ModelBusReferences
 Aşağıdaki bilgiler, kendi bağdaştırıcısı oluşturmak istiyorsanız yararlıdır.

 `ModelBusReference` (MBR) iki bölümden oluşur: model veri yolu tarafından seri durumdan çıkarılan MBR üst bilgisi ve belirli bağdaştırıcı Yöneticisi tarafından işlenen bağdaştırıcıya özel. Bu, kendi bağdaştırıcısı serileştirme biçimi sağlamanıza olanak sağlar. Örneğin, bir dosya yerine bir veritabanına başvurabilir veya ek bilgileri bağdaştırıcısı başvurusunda depolayabilir. Kendi bağdaştırıcınız `ReferenceContext`daha fazla bilgi yerleştirebilir.

 Bir MBR serisini olduğunda, ardından MBR nesnesinde depolanan bir ReferenceContext sağlamanız gerekir. Bir MBR seri olduğunda, depolanan ReferenceContext dizesi oluşturmak amacıyla bağdaştırıcı tarafından kullanılır. Seri durumdan çıkarılmış dize ReferenceContext tüm bilgileri içermiyor. Örneğin, basit dosya tabanlı bağdaştırıcısında ReferenceContext serileştirilmiş MBR dizesinde depolanmaz kök dosya yolu içerir.

 MBR iki aşamada seri durumda:

- `ModelBusReferencePropertySerializer`, MBR üstbilgisiyle ilgilenen standart seri hale getirici. Anahtar `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`kullanılarak `ReferenceContext` depolanan standart DSL `SerializationContext` özellik paketini kullanır. Özellikle `SerializationContext`, bir `ModelBus`örneği içermelidir.

- ModelBus bağdaştırıcınızı MBR bağdaştırıcısı özel bölümü ile ilgilidir. Bunu yapmak için MBR ' ReferenceContext içinde depolanan ek bilgileri kullanabilirsiniz. Basit dosya tabanlı bağdaştırıcı, `FilePathLoadContextKey` ve `FilePathSaveContextKey`anahtarlarını kullanarak kök dosya yollarını korur.

     Yalnızca kullanıldığında bir bağdaştırıcı başvuru bir model dosyası seri durumdan.

## <a name="to-create-a-model"></a>Bir Model oluşturmak için

### <a name="creating-opening-and-editing-a-model"></a>Oluşturma, açma ve bir modeli düzenleme
 Aşağıdaki parçası VMSDK Web sitesinde Durum makinesi örnekten alınır. Bunu ModelBusReferences oluşturmak ve bir modeli açmak için ve modelle ilişkili diyagram elde etmek için kullanımını gösterir.

 Bu örnekte, Durum makinesi ' % s'hedef DSL adıdır. Birden fazla ad kendisinden model sınıfı adını ve ModelBusAdapter adı gibi türetilir.

```
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

## <a name="validating-references"></a>Başvuruları doğrulanıyor
 BrokenReferenceDetector ModelBusReferences tutabilen bir Store içinde yer alan tüm etki alanı özellikleri test eder. Eylemi çağırır, herhangi bir eylemde bulunduğu sağlayın. Bu doğrulama yöntemleri için özellikle yararlıdır. Aşağıdaki doğrulama yöntemi modeli kaydedin girişimi mağaza test eder ve bozuk başvurularda ise hatalar penceresinde raporları:

```
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
 Aşağıdaki bilgileri gerekli değildir, ancak kapsamlı kullanımını ModelBus yaparsanız yararlı olabilir.

 ModelBus uzantısı DSL çözümünüzde aşağıdaki değişiklikleri yapar.

 DSL tanımı diyagramına sağ tıkladığınızda, **ModelBus 'ı etkinleştir**' e tıklayın ve ardından **ModelBus 'ı kullanmak için bu DSL 'yi etkinleştir**' i seçin:

- DSL projesinde, **Microsoft. VisualStudio. modellemesi. SDK. Integration. 11.0. dll** ' ye bir başvuru eklenir

- DSL tanımında, bir dış tür başvurusu eklenir: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Başvuruyu, **etki alanı türleri**altında **DSL Gezgini**'nde görebilirsiniz. Dış tür başvurularını el ile eklemek için kök düğümüne sağ tıklayın.

- Yeni bir şablon dosyası eklenmiştir, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

  Bir etki alanı özelliğinin türünü ModelBusReference olarak belirlediğinizde, özelliği sağ tıklatın ve **ModelBusReference 'a özgü özellikleri etkinleştir**' e tıklayın:

- Birden çok CLR öznitelikleri etki alanı özelliğine eklenir. Özellikler penceresindeki özel öznitelikler alanında görebilirsiniz. **Dsl\GeneratedCode\DomainClasses.cs**' de, özellik bildiriminde öznitelikleri görebilirsiniz:

  ```
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

- `ModelBusAdapter` bir başvuru `DslPackage` projesine eklenir. `ModelBusAdapter`, `Dsl` projesine bir başvuru içerir.

- **DslPackage\source.Extention.tt**' de, `|ModelBusAdapter|` MEF bileşeni olarak eklenir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: program kodunda dosyadan model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md) [UML modellerini diğer modeller ve araçlarla tümleştirme](../modeling/integrate-uml-models-with-other-models-and-tools.md) nasıl yapılır: [metin şablonunda Visual Studio ModelBus kullanarak](../modeling/using-visual-studio-modelbus-in-a-text-template.md) [bir sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
