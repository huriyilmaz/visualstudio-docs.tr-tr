---
title: UML modelinden dosya oluştur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 832dc3f7fea959ff4d2834aba921cd16f1117b5c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666143"
---
# <a name="generate-files-from-a-uml-model"></a>UML modeli aracılığıyla dosya oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir UML modelinde, program kodu, şemalar, belgeler, kaynaklar ve herhangi bir türden diğer yapıtlar oluşturabilirsiniz. UML modelden metin dosyaları oluşturmanın kullanışlı bir yöntemi, [metin şablonlarını](../modeling/code-generation-and-t4-text-templates.md)kullanmaktır. Bunlar, program kodunu oluşturmak istediğiniz metnin içine eklemenizi sağlar.

 Üç ana senaryo vardır:

- [Bir menü komutundan veya hareket içinden dosyalar oluşturma](#Command) . UML modellerinde kullanılabilen bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komutu tanımlarsınız.

- [Uygulamadan dosyalar oluşturma](#Application). UML modellerini okuyan ve dosyalar üreten bir uygulama yazarsınız.

- [Tasarım zamanında oluşturuluyor](#Design). Uygulama işlevlerinden bazılarını tanımlamak ve [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Çözümünüzde kod, kaynak, vb. oluşturmak için bir model kullanırsınız.

  Bu konu, [metin oluşturma 'nın nasıl kullanılacağına](#What)ilişkin bir tartışmayla sonlanır. Daha fazla bilgi için bkz. [kod oluşturma ve T4 Metin şablonları](../modeling/code-generation-and-t4-text-templates.md).

## <a name="Command"></a>Bir menü komutundan dosyalar oluşturma
 Bir UML menü komutu içinde önceden işlem metin şablonlarını kullanabilirsiniz. Metin şablonunun kodu içinde veya ayrı bir kısmi sınıfta, diyagram tarafından görüntülenen modeli okuyabilirsiniz.

 Bu özellikler hakkında daha fazla bilgi için aşağıdaki konuları okuyun:

- [Modelleme diyagramında menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [T4 Metin Şablonları İle Çalışma Süresi Metni Oluşturma](../modeling/run-time-text-generation-with-t4-text-templates.md)

- [UML modelinde gezinme](../modeling/navigate-the-uml-model.md)

  Aşağıdaki örnekte gösterilen yaklaşım, işlemi model diyagramlarından birinden başlattığınızda tek bir modelden metin oluşturmaya uygundur. Modeli ayrı bir bağlamda işlemek için [Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md) kullanarak modele ve onun öğelerine erişin.

### <a name="example"></a>Örnek
 Bu örneği çalıştırmak için bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension (VSıX) projesi oluşturun. Bu örnekte kullanılan proje adı `VdmGenerator`. **Source. Extension. valtmanifest** dosyasında, **İçerik Ekle** ' ye tıklayın ve tür alanını **MEF bileşeni** ve geçerli projeye başvuran kaynak yolu olarak ayarlayın. Bu tür bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

 Projeye aşağıdaki kodu içeren bir C# dosya ekleyin. Bu sınıf, UML sınıf diyagramında görünecek bir menü komutu tanımlar.

```
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace VdmGenerator
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  public class GenerateVdmFromClasses : ICommandExtension
  {
    [Import] public IDiagramContext DiagramContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      // Initialize the template with the Model Store.
      VdmGen generator = new VdmGen(
             DiagramContext.CurrentDiagram.ModelStore);
      // Generate the text and write it.
      System.IO.File.WriteAllText
        (System.IO.Path.Combine(
            Environment.GetFolderPath(
                Environment.SpecialFolder.Desktop),
            "Generated.txt")
         , generator.TransformText());
    }
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }
    public string Text
    { get { return "Generate VDM"; } }
  }
}
```

 Aşağıdaki dosya, metin şablonudur. Modeldeki her UML sınıfı için bir metin satırı ve her bir sınıftaki her öznitelik için bir satır oluşturur. Modeli okuma kodu, `<# ... #>` ile ayrılmış metne katıştırılır.

 Bu dosyayı oluşturmak için Çözüm Gezgini ' de projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın. **Önceden Işlenmiş metin şablonu**' nu seçin. Bu örnek için dosya adı **VdmGen.tt**olmalıdır. Dosyanın **özel araç** özelliği **Texttemplatingfileönişlemci**olmalıdır. Önceden işlenmiş metin şablonları hakkında daha fazla bilgi için bkz. [T4 metin şablonlarıyla çalışma zamanı metin üretimi](../modeling/run-time-text-generation-with-t4-text-templates.md).

```
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#
   foreach (IClass classElement in store.AllInstances<IClass>())   {
#>
Type <#= classElement.Name #> ::
<#
     foreach (IProperty attribute in classElement.OwnedAttributes)     {
#>
       <#= attribute.Name #> : <#=
           attribute.Type == null ? ""
                                  : attribute.Type.Name #>
<#
     }   }
#>
```

 Metin şablonu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projenizin C# bir parçası haline gelen kısmi bir sınıf oluşturur. Ayrı bir dosyada, aynı sınıfın başka bir kısmi bildirimini ekleyin. Bu kod, şablonu UML Model deposuna erişimi sağlar:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
namespace VdmGenerator
{
    public partial class VdmGen
    {
        private IModelStore store;
        public VdmGen(IModelStore s)
        { store = s; }
    }
}
```

 Projeyi test etmek için **F5**'e basın. @No__t_0 yeni bir örneği başlayacaktır. Bu örnekte, bir sınıf diyagramı içeren bir UML modeli açın veya oluşturun. Diyagrama bazı sınıflar ekleyin ve her sınıfa bazı öznitelikler ekleyin. Diyagramda sağ tıklayın ve ardından `Generate VDM` örnek komutuna tıklayın. Komut `C:\Generated.txt` dosya oluşturur. Bu dosyayı inceleyin. İçeriği aşağıdaki metne benzemelidir, ancak kendi sınıflarınızı ve öznitelerinizi listelemelidir:

```
Type Class1 ::
          Attribute1 : int
          Attribute2 : string
Type Class2 ::
          Attribute3 : string
```

## <a name="Application"></a>Uygulamadan dosyalar oluşturma
 Bir UML modeli okuyan uygulamadan dosyalar oluşturabilirsiniz. Bu amaçla, modele ve öğelerine erişmenin en esnek ve sağlam yöntemi [Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md)' dir.

 Ayrıca, modeli yüklemek için temel API 'yi de kullanabilir ve önceki bölümde olduğu gibi aynı teknikleri kullanarak modeli metin şablonlarına geçirebilirsiniz. Model yükleme hakkında daha fazla bilgi için bkz. [program kodunda UML modeli okuma](../modeling/read-a-uml-model-in-program-code.md).

## <a name="Design"></a>Tasarım zamanında dosyalar oluşturma
 Projenizde UML 'i kod olarak yorumlama standart bir yöntemi varsa, bir UML modelinden projeniz içinde kod oluşturmanıza olanak sağlayan metin şablonları oluşturabilirsiniz. Genellikle, UML Model projesini ve uygulama kodu için bir veya daha fazla projeyi içeren bir çözümünüz vardır. Her kod projesi, modelin içeriğine göre program kodu, kaynakları ve yapılandırma dosyaları üreten çeşitli şablonlar içerebilir. Geliştirici, Çözüm Gezgini araç çubuğundaki **Tüm Şablonları Dönüştür** ' ü tıklayarak tüm şablonları çalıştırabilir. Program kodu, genellikle el ile yazılmış parçaları tümleştirmeyi kolaylaştırmak için kısmi sınıflar biçiminde oluşturulur.

 Bu tür bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projesi bir şablon biçiminde dağıtılabilir, böylece bir ekibin her üyesi aynı şekilde bir modelden kod üreten projeler oluşturabilir. Genellikle, şablon, oluşturma kodu önkoşulları 'nın karşılanmasını sağlamak için modelde doğrulama kısıtlamaları içeren bir uzantı paketinin bir parçasıdır.

### <a name="outline-procedure-for-generating-files"></a>Dosya oluşturmak için ana hat yordamı

- Bir projeye şablon eklemek için yeni dosya Ekle iletişim kutusunda **metin şablonu** ' nu seçin. Çoğu proje türüne şablon ekleyebilirsiniz, ancak modelleme projelerine uygulanmaz.

- Şablon dosyasının özel araçlar özelliği **TextTemplatingFileGenerator**olmalıdır ve dosya adı uzantısı. tt olmalıdır.

- Şablonda en az bir çıkış yönergesi olmalıdır:

     `<#@ output extension=".cs" #>`

     Uzantı alanını projenizin diline göre ayarlayın.

- Şablonunuzda kodun modele erişmesini sağlamak için, bir UML modelini okumak için gereken derlemeler için `<#@ assembly #>` yönergeler yazın. Modeli açmak için `ModelingProject.LoadReadOnly()` kullanın. Daha fazla bilgi için bkz. [program kodunda BIR UML modeli okuma](../modeling/read-a-uml-model-in-program-code.md).

- Şablon, kaydettiğinizde ve Çözüm Gezgini araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıkladığınızda yürütülür.

- Bu şablon türü hakkında daha fazla bilgi için bkz. [T4 Metin şablonları kullanarak tasarım zamanı kodu oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

- Tipik bir projede, aynı modelden farklı dosyalar oluşturan birkaç şablonunuz olur. Her şablonun ilk kısmı aynı olacaktır. Bu yinelemeyi azaltmak için, ortak parçaları ayrı bir metin dosyasına taşıyın ve ardından her şablonda yönerge `<#@include file="common.txt"#>` kullanarak bunu çağırın.

- Ayrıca, metin oluşturma sürecine parametreler sağlamanıza olanak tanıyan özel bir yönerge işlemcisi de tanımlayabilirsiniz. Daha fazla bilgi için bkz. [T4 Metin Dönüştürmeyi Özelleştirme](../modeling/customizing-t4-text-transformation.md).

### <a name="example"></a>Örnek
 Bu örnek, kaynak C# MODELDEKI her UML sınıfı için bir sınıf oluşturur.

##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Bu örnek için bir Visual Studio çözümü ayarlamak için

1. Yeni bir çözümde modelleme projesinde UML sınıf diyagramı oluşturun.

   1. **Mimari** menüsünde **Yeni Diyagram**' a tıklayın.

   2. **UML sınıf diyagramını**seçin.

   3. Yeni bir çözüm ve modelleme projesi oluşturmak için istemleri izleyin.

   4. Araç kutusundan UML sınıf aracını sürükleyerek diyagrama bazı sınıflar ekleyin.

   5. Dosyayı kaydedin.

2. Aynı çözümde C# bir veya Visual Basic projesi oluşturun.

   - Çözüm Gezgini, çözüme sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın. **Yüklü şablonlar**altında **Visual Basic** veya  **C#görsel** ' e tıklayın ve ardından **konsol uygulaması**gibi bir proje türü seçin.

3. C# Veya Visual Basic projesine bir düz metin dosyası ekleyin. Bu dosya, çeşitli metin şablonları yazmak istiyorsanız paylaşılan kod içerir.

   - Çözüm Gezgini ' de projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın. **Metin dosyası**seçin.

     Aşağıdaki bölümde gösterilen metni ekleyin.

4. C# Veya Visual Basic projesine bir metin şablonu dosyası ekleyin.

   - Çözüm Gezgini ' de projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın. **Metin şablonu**seçin.

     Metin şablonu dosyasına aşağıdaki kodu ekleyin.

5. Metin şablonu dosyasını kaydedin.

6. Şube dosyasındaki kodu inceleyin. Modeldeki her UML sınıfı için bir sınıf içermelidir.

   1. Visual Basic projede, Çözüm Gezgini araç çubuğunda **tüm dosyaları göster** ' e tıklayın.

   2. Çözüm Gezgini şablon dosyası düğümünü genişletin.

#### <a name="content-of-the-shared-text-file"></a>Paylaşılan metin dosyasının içeriği
 Bu örnekte, dosya SharedTemplateCode. txt olarak adlandırılır ve metin şablonlarıyla aynı klasörde yer alabilir.

```
<# /* Common material for inclusion in my model templates */ #>
<# /* hostspecific allows access to the Visual Studio API */ #>
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>
<#+  // Note this is a Class Feature Block
///<summary>
/// Text templates are run in a common AppDomain, so
/// we can cache the model store that we find.
///</summary>
private IModelStore StoreCache
{
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }
}
private bool CacheIsOld()
{
    DateTime? dt = AppDomain.CurrentDomain
           .GetData("latestAccessTime") as DateTime?;
    DateTime t = dt.HasValue ? dt.Value : new DateTime();
    DateTime now = DateTime.Now;
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);
    return now.Subtract(t).Seconds > 3;
}

///<summary>
/// Find the UML modeling project in this solution,
/// and load the model.
///</summary>
private IModelStore ModelStore
{
  get
  {
    // Avoid loading the model for every template:
    if (StoreCache == null || CacheIsOld())
    {
      // Use Visual Studio API to find modeling project:
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
      EnvDTE.Project project = null;
      foreach (EnvDTE.Project p in dte.Solution.Projects)
      {
        if (p.FullName.EndsWith(".modelproj"))
        {
          project = p;
          break;
        }
      }
      if (project == null) return null;

      // Load UML model into this AppDomain
      // and access model store:
      IModelingProjectReader reader =
           ModelingProject.LoadReadOnly(project.FullName);
      StoreCache = reader.Store;
    }
    return StoreCache;
  }
}
#>
```

#### <a name="content-of-the-text-template-file"></a>Metin şablonu dosyasının içeriği
 Aşağıdaki metin **. tt** dosyasına yerleştirilir. Bu örnek, modeldeki UML sınıflarından C# bir dosyadaki sınıfları oluşturur. Ancak, herhangi bir türde dosya oluşturabilirsiniz. Oluşturulan dosyanın dili, metin şablonu kodunun yazıldığı dille ilişkili değildir.

```
<#@include file="SharedTemplateCode.txt"#>
<#@ output extension=".cs" #>
namespace Test{
<#
      foreach (IClass c in ModelStore.AllInstances<IClass>())
      {
#>
   public partial class <#=c.Name#>
   {   }
<#
      }
#>
}
```

## <a name="What"></a>Metin oluşturmayı kullanma
 Model oluşturmanın gerçek gücü, gereksinimler veya mimari düzeyinde tasarlamak için modeller kullandığınızda elde edilir. Üst düzey fikirleri koda dönüştürme işinin bazılarını yapmak için metin şablonlarını kullanabilirsiniz. Çoğu durumda bu, UML modellerindeki ve sınıflardaki öğeler ile program kodunun diğer kısımları arasında bire bir yazışmaya yol göstermez.

 Ayrıca, dönüştürme probleme etki alanına bağlıdır; modeller ve kod arasında evrensel eşleme yoktur.

 Modellerden kod oluşturmaya ilişkin bazı örnekler şunlardır:

- **Ürün hatları**. Fabrikam, Inc., Havaalanı Bagaj işleme sistemlerini oluşturur ve kurar. Yazılımın çoğu, bir yükleme ve bir sonraki arasında çok benzerdir, ancak yazılım yapılandırması, hangi paket işleme makinelerin yüklü olduğuna ve bu parçaların taşıyıcı beller tarafından nasıl birbirine bağlı olduğuna bağlıdır. Bir sözleşmenin başlangıcında fabrikam analistleri, Havaalanı yönetimiyle ilgili gereksinimleri tartışır ve bir UML etkinlik diyagramı kullanarak donanım planını yakalar. Bu modelden, geliştirme ekibi yapılandırma dosyaları, program kodu, planlar ve Kullanıcı belgeleri oluşturur. Bunlar, el ile yapılan eklemeler ve kod ayarlamaları ile çalışmayı tamamlarlar. Bir işten sonrakine bir deneyim elde ettikleri için, oluşturulan malzemenin kapsamını genişletir.

- **Desenler**. Contoso 'daki geliştiriciler, genellikle Web siteleri oluşturur ve UML sınıf diyagramlarını kullanarak gezinti şemasını tasarlayacaktır. Her Web sayfası bir sınıf tarafından temsil edilir ve ilişkilendirmeler gezinti bağlantılarını temsil eder. Geliştiriciler, modelden bir Web sitesi kodunun çoğunu oluşturur. Her Web sayfası, çeşitli sınıflara ve kaynak dosyası girişlerine karşılık gelir.  Bu yöntem, her sayfanın yapımını tek bir modele uygun hale getiren avantajlara sahiptir. Bu, el ile yazılmış koddan daha güvenilir ve esnek hale gelir. Model, değişken yönlerini yakalamak için kullanıldığı sırada oluşturma şablonlarıdır.

- **Şemaları**. İnsanlar sigortası dünya çapında binlerce sisteme sahiptir. Bu sistemler farklı veritabanları, diller ve arabirimler kullanır. Merkezi mimari ekibi, iş kavramlarının ve işlemlerin dahili modellerini yayınlar. Bu modellerden yerel takımlar, veritabanı ve değişim şemaları, Program kodundaki bildirimler vb. parçalarını oluşturur. Modellerin grafik sunumu, takımların teklifleri tartışmanıza yardımcı olur. Takımlar, farklı iş alanlarında uygulanan modelin alt kümelerini gösteren birden çok Diyagram oluşturur. Ayrıca, değişen alanların vurgulanmasını sağlamak için renk kullanır.

## <a name="important-techniques-for-generating-artifacts"></a>Yapıtlar oluşturmaya yönelik önemli teknikler
 Önceki örneklerde, modeller işe bağımlı farklı amaçlar için kullanılır ve sınıflar ve etkinlikler gibi modelleme öğelerinin yorumu bir uygulamadan diğerine farklılık gösterir. Modellerden yapılar oluştururken aşağıdaki teknikler yararlı olur.

- **Profiller**. Bir işletme alanı içinde bile, bir öğe türünün yorumu farklılık gösterebilir. Örneğin, bir Web sitesi diyagramında bazı sınıflar Web sayfalarını temsil edebilir ve diğerleri içerik bloklarını temsil eder. Kullanıcıların bu tahminleri kaydetmesini kolaylaştırmak için stereotipleri tanımlayın. Stereotipler Ayrıca, bu türden öğeler için uygulanan ek özellikler iliştirmeyi olanaklı kılar. Stereotipler profiller içinde paketlenmiştir. Daha fazla bilgi için bkz. [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).

     Şablon kodunda, bir nesne üzerinde tanımlanan stereotiplere erişmek kolaydır. Örneğin:

    ```
    public bool HasStereotype(IClass c, string profile, string stereo)
    { return c.AppliedStereotypes.Any
       (s => s.Profile == profile && s.Name == stereo ); }
    ```

- **Kısıtlanmış modeller**. Oluşturabileceğiniz modellerin hepsi her amaç için geçerli değildir. Örneğin, Fabrikam havaalanı bagaj modellerinde, giden taşıyıcı olmadan bir iade masasına sahip olmak yanlış olacaktır. Kullanıcılara bu kısıtlamaları gözlemlemeye yardımcı olan doğrulama işlevleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).

- **El ile yapılan değişiklikleri koru**. Bir modelden yalnızca bazı çözüm dosyaları oluşturulabilir. Çoğu durumda, oluşturulan içeriği el ile ekleyebilmeniz veya ayarlayabilmeniz gerekir. Ancak, şablon dönüştürmesi yeniden çalıştırıldığında bu el ile yapılan değişikliklerin korunması önemlidir.

     Şablonlarınızın [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] dillerde kod oluşturması durumunda, geliştiricilerin Yöntemler ve kod ekleyebilmeleri için kısmi sınıflar oluşturması gerekir. Her bir sınıfı bir çift olarak oluşturmak da yararlıdır: yöntemleri içeren soyut temel sınıf ve yalnızca oluşturucuyu içeren bir devralan sınıf. Bu, geliştiricilerin yöntemleri geçersiz kılmasına izin verir. Başlatmanın geçersiz kılınmasına izin vermek için, oluşturucular yerine ayrı bir yöntemde yapılır.

     Bir şablon XML ve diğer çıkış türlerini oluşturduğunda, el ile içeriğin oluşturulan içerikten ayrı tutulması daha zor olabilir. Bir yöntem, derleme işleminde iki dosyayı birleştiren bir görev oluşturmaktır. Diğer bir yöntem, geliştiricilerin oluşturulan şablonun yerel bir kopyasını ayarlamasına yöneliktir.

- **Kodu ayrı derlemelere taşıyın**. Şablonlarda büyük gövdeler yazmak önermiyoruz. Oluşturulan içeriğin hesaplamadan ayrı tutulması tercih edilir ve kod düzenlemede metin şablonları iyi desteklenmez.

     Bunun yerine, metin oluşturmak için önemli hesaplamalar yapmanız gerekiyorsa, bu işlevleri ayrı bir derlemede oluşturun ve kendi yöntemlerini şablondan çağırın.
