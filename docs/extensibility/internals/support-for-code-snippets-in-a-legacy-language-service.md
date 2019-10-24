---
title: Eski dil hizmetindeki kod parçacıkları için destek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d771db166baa66426c7a6d03b344c4bc7b74b27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723106"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kod Parçacıkları için Destek
Kod parçacığı, kaynak dosyaya eklenen bir kod parçasıdır. Kod parçacığı, bir alan kümesi içeren XML tabanlı bir şablondur. Bu alanlar, kod parçacığı eklendikten sonra vurgulanır ve kod parçacığının eklendiği içeriğe bağlı olarak farklı değerlere sahip olabilir. Kod parçacığı eklendikten hemen sonra dil hizmeti kod parçacığını biçimlendirebilir.

 Kod parçacığı, kod parçacığının alanlarının TAB tuşu kullanılarak gezinilebilir olmasını sağlayan özel bir düzenleme moduna eklenir. Alanlar, IntelliSense stili açılan menüleri destekleyebilir. Kullanıcı, kod parçacığını, ENTER veya ESC tuşunu yazarak kaynak dosyasına kaydeder. Kod parçacıkları hakkında daha fazla bilgi edinmek için lütfen bkz. [kod parçacıkları](../../ide/code-snippets.md).

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [Izlenecek yol: kod parçacıkları uygulama](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="managed-package-framework-support-for-code-snippets"></a>Kod parçacıkları için yönetilen paket çerçevesi desteği
 Yönetilen paket çerçevesi (MPF), kod parçacığını eklemek ve özel düzenleme modunu etkinleştirmek için şablonu okumaktan birçok kod parçacığı işlevini destekler. Destek, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sınıfı aracılığıyla yönetilir.

 @No__t_0 sınıfı örneği oluşturulduğunda, bir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesnesi elde etmek için <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> yöntemi çağırılır (temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfının her bir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesnesi için her zaman yeni bir <xref:Microsoft.VisualStudio.Package.Source> nesne döndürdüğünden).

 MPF genişletme işlevlerini desteklemez. Genişletme işlevi, bir kod parçacığı şablonuna gömülü ve bir alana yerleştirilecek bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Değerler, bir <xref:Microsoft.VisualStudio.Package.ExpansionFunction> nesnesi aracılığıyla dil hizmetinin kendisi tarafından döndürülür. Genişletme işlevlerini desteklemek için <xref:Microsoft.VisualStudio.Package.ExpansionFunction> nesnesinin dil hizmeti tarafından uygulanması gerekir.

## <a name="providing-support-for-code-snippets"></a>Kod parçacıkları için destek sağlama
 Kod parçacıkları desteğini etkinleştirmek için, parçacıkları sağlamanız veya kurmanız gerekir ve kullanıcının bu kod parçacıklarını eklemesi için gereken araçları sağlamanız gerekir. Kod parçacıkları desteğini etkinleştirmenin üç adımı vardır:

1. Kod parçacığı dosyaları yükleniyor.

2. Dil hizmetiniz için kod parçacıkları etkinleştiriliyor.

3. @No__t_0 nesnesi çağrılıyor.

### <a name="installing-the-snippet-files"></a>Kod parçacığı dosyalarını yükleme
 Bir dilin tüm kod parçacıkları, genellikle her dosya için bir kod parçacığı şablonu olan XML dosyalarında şablon olarak depolanır. Kod parçacığı şablonları için kullanılan XML şeması hakkında daha fazla bilgi için bkz. [kod parçacıkları şema başvurusu](../../ide/code-snippets-schema-reference.md). Her kod parçacığı şablonu bir dil KIMLIĞIYLE tanımlanır. Bu dil KIMLIĞI kayıt defterinde belirtilir ve şablondaki \<Code > etiketinin `Language` özniteliğe konur.

 Genellikle kod parçacığı şablonu dosyalarının depolandığı iki konum vardır: 1) ve Kullanıcı klasöründe dilinizin yüklendiği 2). Bu konumlar kayıt defterine eklenerek, Visual Studio **kod parçacıkları yöneticisinin** kod parçacıklarını bulabilmesini sağlar. Kullanıcının klasörü, Kullanıcı tarafından oluşturulan kod parçacıklarının depolandığı yerdir.

 Yüklenen kod parçacığı şablon dosyaları için tipik klasör düzeni şuna benzer: *[InstallRoot]* \\ *[TestLanguage]* \Parçacıklar \\ *[LCID]* \Snippets.

 *[InstallRoot]* , dilinizin yüklendiği klasördür.

 *[TestLanguage]* , dilinizin bir klasör adı olarak adıdır.

 *[LCID]* , yerel ayar kimliğidir. Bu, kod parçacılarınızın yerelleştirilmiş sürümlerinin depolandığı bir şekilde yapılır. Örneğin, Ingilizce 'nin yerel ayar KIMLIĞI 1033, bu nedenle *[LCID]* 1033 ile değiştirilmiştir.

 Bir ek dosyanın sağlanması ve genellikle SnippetsIndex. xml veya ExpansionsIndex. xml olarak adlandırılan bir dizin dosyası olması gerekir (. xml dosyasında biten geçerli bir dosya adını kullanabilirsiniz). Bu dosya genellikle *[InstallRoot]* \\ *[TestLanguage]* klasöründe depolanır ve parçacıklar klasörünün tam konumunu ve kod parçacıklarını kullanan dil hizmetinin GUID kimliğini ve GUID 'sini belirtir. Dizin dosyasının tam yolu, daha sonra "kayıt defteri girdilerini yükleme" bölümünde açıklandığı gibi kayıt defterine konur. Bir SnippetsIndex. xml dosyası örneği aşağıda verilmiştir:

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 @No__t_0Language > etiketi, dil KIMLIĞINI (`Lang` özniteliğini) ve dil hizmeti GUID 'sini belirtir.

 Bu örnek, dil hizmetinizi Visual Studio yükleme klasörüne yüklediğinizi varsayar. % LCıD%, kullanıcının geçerli yerel ayar KIMLIĞIYLE değiştirilmiştir. Her farklı dizin ve yerel ayar için bir tane olmak üzere birden çok \<SnippetDir > etiketi eklenebilir. Ayrıca, bir kod parçacığı klasörü, her biri dizin dosyasında bir \<SnippetDir > etiketine gömülü \<SnippetSubDir > etiketiyle tanımlanan alt klasörleri içerebilir.

 Kullanıcılar, diliniz için kendi kod parçacıklarını da oluşturabilir. Bunlar genellikle kullanıcının ayarlar klasöründe depolanır *(örneğin,* [TestDocs] \Code parçacıklarında \\ *[TestLanguage]* \test kodu parçacıkları; burada *[TestDocs]* , kullanıcının Visual Studio 'nun ayarlar klasörü konumudur.

 Aşağıdaki değiştirme öğeleri, Dizin dosyasındaki \<DirPath > etiketinde depolanan yola yerleştirilebilir.

|Öğe|Açıklama|
|-------------|-----------------|
|IC|Yerel ayar KIMLIĞI.|
|InstallRoot|Visual Studio için kök yükleme klasörü, örneğin, C:\Program Files\Microsoft Visual Studio 8.|
|% ProjDir%|Geçerli projeyi içeren klasör.|
|% ProjItem%|Geçerli Proje öğesini içeren klasör.|
|% TestDocs%|Kullanıcının ayarlar klasöründeki klasör; Örneğin, C:\Documents and Settings \\ *[UserName]* \Bir Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Dil hizmetiniz için kod parçacıklarını etkinleştirme
 VSPackage 'a <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> özniteliğini ekleyerek dil hizmetiniz için kod parçacıklarını etkinleştirebilirsiniz (Ayrıntılar için [eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md) konusuna bakın). @No__t_0 ve <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametreler isteğe bağlıdır, ancak **kod parçacıkları yöneticisini kod parçacıkları yöneticisine** bilgilendirmek için `SearchPaths` adlı parametresi dahil etmelisiniz.

 Bu özniteliğin nasıl kullanılacağına ilişkin bir örnek aşağıda verilmiştir:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Genişletme sağlayıcısını çağırma
 Dil hizmeti, herhangi bir kod parçacığının eklenmesini ve eklemenin çağrılma şeklini denetler.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Kod parçacıkları için genişletme sağlayıcısını çağırma
 Genişletme sağlayıcısını çağırmak için iki yol vardır: bir menü komutu veya bir tamamlama listesinden kısayol kullanarak.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Bir menü komutu kullanarak kod parçacığı ekleme
 Kod parçacığı tarayıcısını göstermek üzere bir menü komutu kullanmak için, bir menü komutu ekler ve sonra bu menü komutuna yanıt olarak <xref:Microsoft.VisualStudio.Package.ExpansionProvider> arabirimindeki <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> yöntemi çağırın.

1. . Vsct dosyanıza bir komut ve düğme ekleyin. [Bir menü komutuyla bir uzantı oluşturmak](../../extensibility/creating-an-extension-with-a-menu-command.md)için yönergeler bulabilirsiniz.

2. @No__t_0 sınıfından bir sınıf türetirsiniz ve yeni menü komutuna yönelik desteği göstermek için <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> metodunu geçersiz kılın. Bu örnek, her zaman menü komutunu sunar.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. @No__t_2 nesnesini almak ve bu nesne üzerinde <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> yöntemini çağırmak için <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfındaki <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> yöntemi geçersiz kılın.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     @No__t_0 sınıfında aşağıdaki yöntemler, kod parçacığını ekleme işlemi sırasında verilen sırada Visual Studio tarafından çağırılır:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     @No__t_0 yöntemi çağrıldıktan sonra, kod parçacığı eklenmiştir ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesnesi, yeni eklenen bir kod parçacığını değiştirmek için kullanılan özel bir düzenleme modundadır.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Bir kısayol kullanarak kod parçacığı ekleme
 Bir tamamlama listesinden kısayol uygulaması, bir menü komutu uygulamaktan çok daha karmaşıktır. Önce IntelliSense sözcük tamamlama listesine kod parçacığı kısayolları eklemeniz gerekir. Daha sonra, bir kod parçacığı kısayol adının tamamlanma sonucu olarak ne zaman eklendiğini tespit etmeniz gerekir. Son olarak, kısayol adını kullanarak kod parçacığı başlığını ve yolunu edinmeniz ve bu bilgileri <xref:Microsoft.VisualStudio.Package.ExpansionProvider> yönteminde <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> yöntemine iletmeniz gerekir.

 Sözcük tamamlama listesine kod parçacığı kısayolları eklemek için, <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfınıza <xref:Microsoft.VisualStudio.Package.Declarations> nesnesine ekleyin. Kısayolu bir kod parçacığı adı olarak belirleyediğinizden emin olmanız gerekir. Bir örnek için bkz. [Izlenecek yol: yüklü kod parçacıklarının listesini alma (eski uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Kod parçacığı kısayolunun eklenmesini, <xref:Microsoft.VisualStudio.Package.Declarations> sınıfının <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metodunda tespit edebilirsiniz. Kod parçacığı adı kaynak dosyaya zaten eklenmiş olduğundan, genişletme eklendiğinde kaldırılmalıdır. @No__t_0 yöntemi, kod parçacığının ekleme noktasını açıklayan bir yayma alır; yayılma, kaynak dosyadaki tüm kod parçacığı adını içeriyorsa, bu ad kod parçacığına göre değişir.

 Bu, bir kısayol adı verilen kod parçacığı eklemeyi işleyen bir <xref:Microsoft.VisualStudio.Package.Declarations> sınıfının sürümüdür. @No__t_0 sınıfındaki diğer yöntemler açıklık için atlandı. Bu sınıfın oluşturucusunun <xref:Microsoft.VisualStudio.Package.LanguageService> nesne aldığını unutmayın. Bu, <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnesinin sürümünden geçirilebilir (örneğin, <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfının uygulamanız oluşturucusunda <xref:Microsoft.VisualStudio.Package.LanguageService> nesnesini alabilir ve bu nesneyi `TestDeclarations` sınıfı yapıcısına geçirebilir).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Dil hizmeti kısayol adını aldığında, dosya adını ve kod parçacığı başlığını almak için <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> yöntemini çağırır. Dil hizmeti daha sonra kod parçacığını eklemek için <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sınıfında <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> yöntemini çağırır. Aşağıdaki yöntemler Visual Studio tarafından, kod parçacığını ekleme işlemi sırasında <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sınıfında verilen sırada çağrılır:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Dil hizmetiniz için yüklü kod parçacıklarının listesini alma hakkında daha fazla bilgi için bkz. [Izlenecek yol: yüklü kod parçacıklarının listesini alma (eski uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction sınıfını uygulama
 Genişletme işlevi, bir kod parçacığı şablonuna gömülü ve bir alana yerleştirilecek bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Dil hizmetinizdeki genişletme işlevlerini desteklemek için <xref:Microsoft.VisualStudio.Package.ExpansionFunction> sınıfından bir sınıf türetmeniz ve <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> metodunu uygulamanız gerekir. Daha sonra, destekettiğiniz her bir genişletme işlevi için <xref:Microsoft.VisualStudio.Package.ExpansionFunction> sınıfının sürümünün yeni bir örneğini döndürmek üzere <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> yöntemini geçersiz kılmanız gerekir. Bir genişletme işlevinden olası değerler listesini destekediyorsanız, bu değerlerin bir listesini döndürmek için <xref:Microsoft.VisualStudio.Package.ExpansionFunction> sınıfındaki <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> yöntemini de geçersiz kılmanız gerekir.

 Genişletme sağlayıcısı, genişleme işlevinin çağrıldığı süre tarafından tam olarak başlatılamadığından, bağımsız değişkenler veya diğer alanlara erişmesi gereken bir genişletme işlevi, düzenlenebilir bir alanla ilişkilendirilmemelidir. Sonuç olarak, genişletme işlevi bağımsız değişkenlerinin veya başka bir alanın değerini elde edemeyebilir.

### <a name="example"></a>Örnek
 @No__t_0 bir basit genişletme işlevinin nasıl uygulanabileceğini gösteren bir örnek aşağıda verilmiştir. Bu genişletme işlevi, genişletme işlevi her başlatıldığında bir taban sınıf adına bir sayı ekler (ilişkili kod parçacığı eklendiği her seferinde buna karşılık gelir).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)
- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Kod Parçacıkları](../../ide/code-snippets.md)
- [İzlenecek Yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)