---
title: UML uzantılarında birim testlerini çalıştırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 745d74ae-e48c-4fd9-a755-4354b81b9f8a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f634f028dafea3260a69537893513f13cc0ebe83
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292542"
---
# <a name="run-unit-tests-on-uml-extensions"></a>UML genişletmelerinde birim testleri çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ardışık değişiklikler aracılığıyla kodunuzu kararlı tutmaya yardımcı olmak için birim testleri yazmanızı ve bunları düzenli bir yapı sürecinin bir parçası olarak gerçekleştirmenizi öneririz. Daha fazla bilgi için [Birim Test kodunuzu](../test/unit-test-your-code.md). Visual Studio modelleme uzantıları için testleri ayarlamak üzere bazı önemli bilgi parçalarına ihtiyacınız vardır. Özet:

- [VSıX uzantıları için birim testi ayarlama](#Host)

   VS IDE ana bilgisayar bağdaştırıcısıyla testleri çalıştırın. Her test yönteminin `[HostType("VS IDE")]`ön eki. Bu konak bağdaştırıcısı, testleriniz çalıştırıldığında [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlar.

- [DTE ve ModelStore 'a erişme](#DTE)

   Genellikle, bir modeli ve diyagramlarını açmanız ve test başlatılmasında `IModelStore` erişmeniz gerekir.

- [Model diyagramı açma](#Opening)

   `IDiagramContext``EnvDTE.ProjectItem` veya buradan çevirebilirsiniz.

- [UI Iş parçacığında değişiklikler gerçekleştiriliyor](#UiThread)

   Model deposunda değişiklik yapan testlerin Kullanıcı arabirimi iş parçacığında gerçekleştirilmesi gerekir. Bu, `Microsoft.VSSDK.Tools.VsIdeTesting.UIThreadInvoker` için kullanabilirsiniz.

- [Komutları, hareketleri ve diğer MEF bileşenlerini test etme](#MEF)

   MEF bileşenlerini test etmek için içe aktarılan özelliklerini açıkça değerlere bağlamanız gerekir.

  Bu noktalara aşağıdaki bölümlerde ayrıntılı.

## <a name="requirements"></a>Gereksinimler
 [Gereksinimlere](../modeling/extend-uml-models-and-diagrams.md#Requirements)bakın.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="Host"></a>VSıX uzantıları için birim testi ayarlama
 Modelleme uzantılarındaki yöntemler genellikle zaten açık olan bir diyagram ile çalışır. Yöntemler **IDiagramContext** ve **ılınkedundocontext**gibi MEF içeri aktarmaları kullanır. Testleri çalıştırmadan önce test ortamınızın bu bağlamı ayarlaması gerekir.

#### <a name="to-set-up-a-unit-test-that-executes-in-includevsprvsincludesvsprvs-mdmd"></a>[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] içinde yürütülen bir birim testi ayarlamak için

1. UML uzantı projesi ve birim testi projesi oluşturun.

    1. **UML uzantı projesi.** Genellikle bunu komutu, hareketi veya doğrulama projesi şablonlarını kullanarak oluşturursunuz. Örneğin, bkz. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

    2. **Bir birim test projesi.** Daha fazla bilgi için [Birim Test kodunuzu](../test/unit-test-your-code.md).

2. UML modelleme projesi içeren bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümü oluşturun. Bu çözümü testlerinizin ilk durumu olarak kullanacaksınız. UML uzantısını ve birim testlerini yazdığınız çözümden ayrı olmalıdır. Daha fazla bilgi için bkz. [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md).

3. **UML Uzantı projesinde**,. csproj dosyasını metin olarak düzenleyin ve aşağıdaki satırlarda `true`görüntülendiğinden emin olun:

    ```
    <CopyBuildOutputToOutputDirectory>true</CopyBuildOutputToOutputDirectory>
        <CopyOutputSymbolsToOutputDirectory>true</CopyOutputSymbolsToOutputDirectory>
    ```

     . Csproj dosyasını metin olarak düzenlemek için Çözüm Gezgini projedeki kısayol menüsünde **Projeyi Kaldır** ' ı seçin. Sonra **Düzenle.... csproj**öğesini seçin. Metni düzenledikten sonra **projeyi yeniden yükle**' yi seçin.

4. UML Uzantı projenizde, **Properties\AssemblyInfo.cs**'e aşağıdaki satırı ekleyin. Bu, birim testlerinin test etmek istediğiniz yöntemlere erişmesini sağlar:

    ```csharp
    [assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
    ```

5. **Birim testi projesinde**, aşağıdaki derleme başvurularını ekleyin:

    - *UML Uzantı projeniz*

    - **EnvDTE. dll**

    - **Microsoft. VisualStudio. mimari Turetools. Extensibility. dll**

    - **Microsoft.VisualStudio.ComponentModelHost.dll**

    - **Microsoft. VisualStudio. QualityTools. UnitTestFramework. dll**

    - **Microsoft. VisualStudio. Uml. Interfaces. dll**

    - **Microsoft.VSSDK.TestHostFramework.dll**

6. Başlangıç yöntemleri de dahil olmak üzere her test yöntemine `[HostType("VS IDE")]` özniteliği öneki.

     Bu, testin bir Visual Studio 'nun deneysel örneğinde çalışacağını güvence altına alacak.

## <a name="DTE"></a>DTE ve ModelStore 'a erişme
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]bir modelleme projesi açmak için bir yöntem yazın. Genellikle, her test çalıştırmasında bir çözümü yalnızca bir kez açmak istersiniz. Yöntemi yalnızca bir kez çalıştırmak için, metodu `[AssemblyInitialize]` özniteliğiyle önek yapın. Her test yönteminde [HostType ("VS IDE")] özniteliğine de ihtiyacınız olduğunu unutmayın.  Örneğin:

```csharp
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;

namespace UnitTests
{
  [TestClass]
  public static class TestSetup
  {

    // Location of a VS Solution that defines an initial state for your tests:
    private const string testSolutionFilePath = @"C:\MyTestFolder\TestModelSln\TestModel.sln";
    // Name of a modeling project within the test solution:
    private const string testModelingProjectName = "MyTestModel";

    // Make Solution and IModelStore available to test methods:
    public static Solution ModelSolution = null;
    public static IModelingProject ModelingProject = null;
    public static IModelStore ModelStore = null;

    // This method will be performed once to initialize tests for this assembly:
    [AssemblyInitialize]
    [HostType("VS IDE")]
    public static void OpenTestModelingProject(TestContext testContext)
    {
      // To make sure that we always start the tests in the same state,
      // copy the test solution from a read-only directory:
      // TODO: copy test solution folder.

      // Open a solution that is the initial state for your tests:
      ModelSolution = VsIdeTestHostContext.Dte.Solution;
      ModelSolution.Open(testSolutionFilePath);

      // Find the ModelingProject and IModelStore:
      foreach (Project project in ModelSolution.Projects)
      {
        // https://msdn.microsoft.com/library/ee791691.aspx
        ModelingProject = project as IModelingProject;
        if (ModelingProject != null)
        {
          // This is a modeling project.
          ModelStore = ModelingProject.Store;
          break;
        }
        // else this is another kind of project.
      }

      Assert.IsNotNull(ModelSolution, "VS solution not found");
      Assert.IsNotNull(ModelStore, "Modeling store not found");
    }
    [AssemblyCleanup]
    public static void RemoveTestSolution ()
    {
      // TODO: Remove copied test solution directory.
    }
  }
}

```

 Bir <xref:EnvDTE.Project?displayProperty=fullName> örneği bir modelleme projesini temsil ediyorsa, [IModelingProject](/previous-versions/ee789474(v=vs.140))'e ve öğesinden dönüştürebilirsiniz.

## <a name="Opening"></a>Model diyagramı açma
 Her test veya test sınıfı için, genellikle açık bir diyagram ile çalışmak istersiniz. Aşağıdaki örnek, bu test sınıfındaki diğer yöntemlerden önce bu yöntemi yürüten `[ClassInitialize]` özniteliğini kullanır. Ayrıca, her test yönteminde [HostType ("VS IDE")] özniteliğine de ihtiyacınız olduğunu unutmayın:

```csharp
//
private IDiagram diagram;
// This class contains unit tests:
[TestClass]
public class MyTestClass
{
  // Map filenames to open diagram files:
  private static Dictionary<string, IDiagram> diagrams = new Dictionary<string, IDiagram>();

  // This method will be called once for this test class:
  [ClassInitialize]
  [HostType("VS IDE")]
  public static void TestClassInitialize(TestContext testContext)
  {
    // Open all the diagrams in the model:
    foreach (ProjectItem item in (TestSetup.ModelingProject as Project).ProjectItems)
    {
      // Get the filename of the principal file (not the .layout subsidiary):
      string fileName = item.FileNames[0];
      // If this is a model diagram file, it can be cast to IDiagramContext:
      IDiagramContext modelingItem = item as IDiagramContext;
      if (modelingItem != null)
      {
        IDiagram diagram = modelingItem.CurrentDiagram;
        if (diagram == null)
        {
          // Diagram is closed. Open it:
          item.Open().Activate();
          diagram = modelingItem.CurrentDiagram;
        }
        diagrams[fileName] = diagram;
      }
      // else item is not a model diagram.
    }
    Assert.IsTrue(diagrams.Count>0, "UML diagram not found");
  }
// Insert test methods here ...
}

```

## <a name="UiThread"></a>Kullanıcı arabirimi Iş parçacığında model değişikliklerini gerçekleştirme
 Testleriniz veya test edilen Yöntemler, model deposunda değişiklik yaparsanız, bunları Kullanıcı arabirimi iş parçacığında yürütmeniz gerekir. Bunu yapmazsanız, bir `AccessViolationException`görebilirsiniz. Çağırmak için bir çağrıda test yönteminin kodunu Çevrele:

```
using System.Windows.Forms;
using Microsoft.VSSDK.Tools.VsIdeTesting;
 ...
    [TestMethod]
    [HostType("VS IDE")]
    public void MyTest1()
    {
      // Store operations must run in the UI thread:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        SetupTestState(TestSetup.ModelStore, diagram);
        ExecuteMethodUnderTest(TestSetup.ModelStore, diagram);
      });
    }
```

## <a name="MEF"></a>Komut, hareket ve diğer MEF bileşenlerini test etme
 MEF Bileşenleri, `[Import]` özniteliği olan ve değerleri ana bilgisayarları tarafından ayarlanan özellik bildirimlerini kullanır. Genellikle, bu tür özellikler IDiagramContext, SVsServiceProvider ve ılınkedundocontext ' i içerir. Bu özelliklerden herhangi birini kullanan bir yöntemi test ettiğinizde, test altındaki metodu yürütmeden önce değerlerini ayarlamanız gerekir. Örneğin, bu koda benzer bir komut uzantısı yazdıysanız:

```

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class MyCommand : ICommandExtension
  {
    [Import] IDiagramContext context { get; set; }
    [Import]
Microsoft.VisualStudio.Shell.SVsServiceProvider
serviceProvider {get;set;}
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }
    public void Execute(IMenuCommand command)
    {
      DoCommand();
    }
    private void DoCommand()
    {
      IDiagram diagram = context.CurrentDiagram;
      using (ILinkedUndoTransaction t = linkedUndoContext.BeginTransaction("go"))
      { ... }}}

```

 Ardından içeri aktarılan özellikleri aşağıdaki gibi ayarlayabilirsiniz:

```

using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ComponentModelHost;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.VSSDK.Tools.VsIdeTesting;
...
    [TestMethod]
    [HostType("VS IDE")]
    public void Test1()
    {
      // Create an instance of the class under test:
      MyCommand myCommand = new MyCommand();
      // Get the components service:
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
        .GetService(typeof(SComponentModel)) as IComponentModel;
      // Set the imported properties of the instance under test:
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(myCommand);
      // Call method(s) under test:
      UIThreadInvoker.Invoke((System.Action)delegate()
      {
        myCommand.DoCommand();
      });
...}
```

 İçeri aktarılan bir özelliği parametre olarak alan bir yöntemi test etmek istiyorsanız, özelliği test sınıfınıza aktarabilir ve test örneğine `SatisfyImportsOnce` uygulayabilirsiniz. Örneğin:

```

using System.ComponentModel.Composition;
...
  [TestClass]
  public class MyTestClass
  {
    [Import] ILinkedUndoContext linkedUndoContext { get; set; }

    // Called before each test method:
    [TestInitialize, HostType("VS IDE")]
    public void TestInitializer()
    {
      IComponentModel components = VsIdeTestHostContext.ServiceProvider
            .GetService(typeof(SComponentModel)) as IComponentModel;
      // Extension requires "using System.ComponentModel.Composition;" :
      components.DefaultCompositionService.SatisfyImportsOnce(this);
    }
    [TestMethod, HostType("VS IDE")]
    public void Test2()
    {
     UIThreadInvoker.Invoke((System.Action)delegate()
      {
      // Pass context items to class under test:
      Class1 item1 = new Class1(this.linkedUndoContext);
      item1.Method1(); // Can use linkedUndoContext
     });
   }
}

```

 Bu örnekte, her test yönteminin iki özniteliği tek bir satırda kolaylık sağlaması için birleştirilir.

## <a name="access-from-tests-to-private-methods-and-variables"></a>Testlerden özel yöntemlere ve değişkenlere erişim
 Bazen özel bir yöntemi test etmek veya test edilen bir yöntemi yürütmeden önce ve sonra özel bir alanın durumunu doğrulamak istiyorsanız. Bu, testler test kapsamındaki sınıflara ayrı bir derlemede olduğundan zorluk gösterir. Aşağıdakiler dahil olmak üzere göz önünde bulundurmanız gereken birkaç tacu vardır:

 Yalnızca ortak ve iç öğeleri kullanarak test yapmak, testlerinizi yalnızca ortak (veya iç) sınıflar ve Üyeler kullanacak şekilde yazar. Bu en iyi yaklaşımdır. Test edilen derlemenin iç uygulamasını yeniden düzenleme olsanız bile testleriniz çalışmaya devam edecektir. Değişikliklerden önce ve sonra aynı testleri uygulayarak, değişikliklerinizin derlemenin davranışını değiştirilmediğini emin olabilirsiniz.

 Bunu mümkün kılmak için kodunuzu yeniden yapılandırmak zorunda kalabilirsiniz. Örneğin, bazı yöntemleri başka bir sınıfa ayırmanız gerekebilir.

 Bu yaklaşıma dikkat etmeniz sayesinde, genellikle kodunuzun daha kolay okunması ve değiştirilmesini ve değişiklikler gerektiğinde hatalara karşı daha az olabileceğini fark edersiniz.

 Test derlemesinin, test edilecek projede **Properties\AssemblyInfo.cs** içinde bir öznitelik ekleyerek iç öğelere erişmesine izin verebilirsiniz:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Test arabirimini tanımlama, test edilecek bir sınıfın ortak üyelerini ve testlerin kullanmasını istediğiniz özel Üyeler için ek özellikleri ve yöntemleri içeren bir arabirim tanımlayın. Bu arabirimi test edilecek projeye ekleyin. Örneğin:

```csharp
internal interface MyClassTestInterface {
  void PublicMethod1();
  string PublicProperty1 { get; }
  string privateField1_Accessor { get; }
  int privateMethod1_Accessor (string p1);
 }
```

 Erişimci yöntemlerini açıkça uygulamak için test edilecek sınıfa Yöntemler ekleyin. Bu ek yöntemleri, ayrı bir dosyadaki kısmi bir sınıf tanımına yazarak ana sınıftan ayrı tutun. Örneğin:

```csharp
partial public class MyClass
{
  string MyClassTestInterface.privateField1_Accessor
  { get { return privateField1; } }
  int MyClassTestInterface.privateMethod1_Accessor (string p1)
  { return privateMethod1(p1); }
}

```

 Test derlemesinin test arabirimlerini bu özniteliği test ettiğiniz derlemeye ekleyerek bu özniteliği kullanmasına izin verin:

```csharp
[assembly:InternalsVisibleTo("MyUnitTests")] // Name of unit tests assembly.
```

 Birim testi yöntemlerinde, test arabirimini kullanın. Örneğin:

```csharp
MyClassTestInterface testInstance = new MyClass();
testInstance.PublicMethod1();
Assert.AreEqual("hello", testInstance.privateField1_Accessor);
```

 Yansımayı kullanarak erişimcileri tanımlayın Bu, en az önerdiğimiz yoldur. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] eski sürümleri, her özel yöntem için otomatik olarak bir erişimci yöntemi oluşturan bir yardımcı program sağladı. Bu kullanışlı olsa da, deneyimimiz, test ettikleri uygulamanın dahili yapısına çok sıkı bir şekilde bağlanmış birim testlerin oluşmasına neden olduğunu eğilimlidir. Bu, testlerin uygulamayla birlikte değiştirilmesi gerektiğinden, gereksinimler veya mimari değiştiğinde ek çalışmalarla sonuçlanır. Ayrıca, uygulamanın tasarımındaki hatalı varsayımlar, testlerin hata bulmaması için testler içinde de yerleşiktir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Birim testinin Anatomumu](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
