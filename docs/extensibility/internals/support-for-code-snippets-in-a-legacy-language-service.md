---
title: Eski dil hizmetindeki kod parçacıkları için destek | Microsoft Docs
description: Eski dil hizmetinin kod parçacıklarını nasıl desteklediğini öğrenin. Kod parçacığı, kaynak dosyaya eklenen bir kod parçasıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 71d12bb0bd80c10140aaaa6f276cf772397d699f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634545"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kod Parçacıkları için Destek
Kod parçacığı, kaynak dosyaya eklenen bir kod parçasıdır. Kod parçacığı, bir alan kümesi içeren XML tabanlı bir şablondur. Bu alanlar, kod parçacığı eklendikten sonra vurgulanır ve kod parçacığının eklendiği içeriğe bağlı olarak farklı değerlere sahip olabilir. Kod parçacığı eklendikten hemen sonra dil hizmeti kod parçacığını biçimlendirebilir.

 Kod parçacığı, kod parçacığının alanlarının TAB tuşu kullanılarak gezinilebilir olmasını sağlayan özel bir düzenleme moduna eklenir. Alanlar, IntelliSense stili açılan menüleri destekleyebilir. Kullanıcı, kod parçacığını, ENTER veya ESC tuşunu yazarak kaynak dosyasına kaydeder. Kod parçacıkları hakkında daha fazla bilgi edinmek için lütfen bkz. [kod parçacıkları](../../ide/code-snippets.md).

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [Izlenecek yol: kod parçacıkları uygulama](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="managed-package-framework-support-for-code-snippets"></a>Kod parçacıkları için yönetilen paket çerçevesi desteği
 Yönetilen paket çerçevesi (MPF), kod parçacığını eklemek ve özel düzenleme modunu etkinleştirmek için şablonu okumaktan birçok kod parçacığı işlevini destekler. Destek, sınıfı aracılığıyla yönetilir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> .

 <xref:Microsoft.VisualStudio.Package.Source>Sınıf örneği oluşturulduğunda, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki yöntemi bir nesnesi elde etmek için çağrılır <xref:Microsoft.VisualStudio.Package.ExpansionProvider> (temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfın her bir nesne için her zaman yeni bir nesne döndürdüğünü unutmayın <xref:Microsoft.VisualStudio.Package.ExpansionProvider> <xref:Microsoft.VisualStudio.Package.Source> ).

 MPF genişletme işlevlerini desteklemez. Genişletme işlevi, bir kod parçacığı şablonuna gömülü ve bir alana yerleştirilecek bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Değerler bir nesne aracılığıyla dil hizmetinin kendisi tarafından döndürülür <xref:Microsoft.VisualStudio.Package.ExpansionFunction> . <xref:Microsoft.VisualStudio.Package.ExpansionFunction>Genişleme işlevlerini desteklemek için nesnenin dil hizmeti tarafından uygulanması gerekir.

## <a name="providing-support-for-code-snippets"></a>Kod parçacıkları için destek sağlama
 Kod parçacıkları desteğini etkinleştirmek için, parçacıkları sağlamanız veya kurmanız gerekir ve kullanıcının bu kod parçacıklarını eklemesi için gereken araçları sağlamanız gerekir. Kod parçacıkları desteğini etkinleştirmenin üç adımı vardır:

1. Kod parçacığı dosyaları yükleniyor.

2. Dil hizmetiniz için kod parçacıkları etkinleştiriliyor.

3. Nesnesi çağrılıyor <xref:Microsoft.VisualStudio.Package.ExpansionProvider> .

### <a name="installing-the-snippet-files"></a>Kod parçacığı dosyalarını yükleme
 Bir dilin tüm kod parçacıkları, genellikle her dosya için bir kod parçacığı şablonu olan XML dosyalarında şablon olarak depolanır. Kod parçacığı şablonları için kullanılan XML şeması hakkında daha fazla bilgi için bkz. [kod parçacıkları şema başvurusu](../../ide/code-snippets-schema-reference.md). Her kod parçacığı şablonu bir dil KIMLIĞIYLE tanımlanır. Bu dil KIMLIĞI kayıt defterinde belirtilir ve `Language` \<Code> şablondaki etiketin özniteliğine konur.

 Genellikle kod parçacığı şablonu dosyalarının depolandığı iki konum vardır: 1) ve Kullanıcı klasöründe dilinizin yüklendiği 2). bu konumlar kayıt defterine eklenerek Visual Studio **kod parçacıkları yöneticisinin** parçacıkları bulabilmesini sağlar. Kullanıcının klasörü, Kullanıcı tarafından oluşturulan kod parçacıklarının depolandığı yerdir.

 Yüklenen kod parçacığı şablon dosyaları için tipik klasör düzeni şuna benzer: *[InstallRoot]* \\ *[TestLanguage]* \parçacıklar \\ *[LCID]* \Snippets.

 *[InstallRoot]* , dilinizin yüklendiği klasördür.

 *[TestLanguage]* , dilinizin bir klasör adı olarak adıdır.

 *[LCID]* , yerel ayar kimliğidir. Bu, kod parçacılarınızın yerelleştirilmiş sürümlerinin depolandığı bir şekilde yapılır. Örneğin, Ingilizce 'nin yerel ayar KIMLIĞI 1033, bu nedenle *[LCID]* 1033 ile değiştirilmiştir.

 Bir ek dosyanın sağlanması ve genellikle SnippetsIndex.xml veya ExpansionsIndex.xml olarak adlandırılan bir dizin dosyası olması gerekir (.xml biten geçerli bir dosya adını kullanabilirsiniz). Bu dosya genellikle *[InstallRoot]* \\ *[TestLanguage]* klasöründe depolanır ve kod parçacıkları klasörünün tam konumunu ve kod parçacıklarını kullanan dil hizmetinin GUID kimliğini ve GUID 'sini belirtir. Dizin dosyasının tam yolu, daha sonra "kayıt defteri girdilerini yükleme" bölümünde açıklandığı gibi kayıt defterine konur. Bir SnippetsIndex.xml dosyasına bir örnek aşağıda verilmiştir:

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

 \<Language>Etiket, DIL kimliğini ( `Lang` özniteliği) ve DIL hizmeti GUID 'sini belirtir.

 bu örnek, dil hizmetinizi Visual Studio yükleme klasörüne yüklediğinizi varsayar. % LCıD%, kullanıcının geçerli yerel ayar KIMLIĞIYLE değiştirilmiştir. \<SnippetDir>Her farklı dizin ve yerel ayar için bir tane olmak üzere birden çok etiket eklenebilir. Buna ek olarak, bir kod parçacığı klasörü, her biri dizin dosyasında bir etikete gömülü olan etiketi ile tanımlanan alt klasörleri içerebilir \<SnippetSubDir> \<SnippetDir> .

 Kullanıcılar, diliniz için kendi kod parçacıklarını da oluşturabilir. Bunlar genellikle kullanıcının ayarlar klasöründe depolanır (örneğin, [TestDocs *]* \Code parçacıklarında \\ *[TestLanguage]* \test kodu parçacıkları; burada *[TestDocs]* Visual Studio için kullanıcının ayarlar klasörünün konumudur.

 Aşağıdaki değiştirme öğeleri, \<DirPath> Dizin dosyasındaki etiketinde saklanan yola yerleştirilebilir.

|Öğe|Açıklama|
|-------------|-----------------|
|IC|Yerel ayar KIMLIĞI.|
|InstallRoot|Visual Studio için kök yükleme klasörü; örneğin, C:\Program Files \ Microsoft Visual Studio 8.|
|% ProjDir%|Geçerli projeyi içeren klasör.|
|% ProjItem%|Geçerli Proje öğesini içeren klasör.|
|% TestDocs%|kullanıcının ayarlar klasöründeki klasör, örneğin, C:\Documents and Ayarlar \\ *[username]* \documents \ Visual Studio \ 8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Dil hizmetiniz için kod parçacıklarını etkinleştirme
 Özelliği VSPackage 'a ekleyerek dil hizmetiniz için kod parçacıklarını etkinleştirebilirsiniz <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> (Ayrıntılar Için [eski dil hizmeti kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md) konusuna bakın). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A>Ve <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametreleri isteğe bağlıdır, ancak `SearchPaths` **kod parçacıkları yöneticisini kod parçacığı yöneticisine** bilgilendirmek için adlandırılmış parametreyi dahil etmelisiniz.

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
 Kod parçacığı tarayıcısını göstermek üzere bir menü komutu kullanmak için, bir menü komutu ekler ve sonra <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Bu menü komutuna yanıt olarak arabirimindeki yöntemi çağırın.

1. . Vsct dosyanıza bir komut ve düğme ekleyin. [Bir menü komutuyla bir uzantı oluşturmak](../../extensibility/creating-an-extension-with-a-menu-command.md)için yönergeler bulabilirsiniz.

2. Sınıfından bir sınıf türetirsiniz <xref:Microsoft.VisualStudio.Package.ViewFilter> ve <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> yeni menü komutu için desteği göstermek üzere yöntemi geçersiz kılar. Bu örnek, her zaman menü komutunu sunar.

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

3. <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> <xref:Microsoft.VisualStudio.Package.ViewFilter> Nesneyi almak için sınıfındaki yöntemini geçersiz kılın <xref:Microsoft.VisualStudio.Package.ExpansionProvider> ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> yöntemi bu nesnede çağırın.

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

     sınıfındaki aşağıdaki yöntemler, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> kod parçacığını ekleme işlemi sırasında verilen sırada Visual Studio tarafından çağırılır:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>Yöntemi çağrıldıktan sonra, kod parçacığı eklenmiştir ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesne, yeni eklenen bir kod parçacığını değiştirmek için kullanılan özel bir düzenleme modundadır.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Bir kısayol kullanarak kod parçacığı ekleme
 Bir tamamlama listesinden kısayol uygulaması, bir menü komutu uygulamaktan çok daha karmaşıktır. Önce IntelliSense sözcük tamamlama listesine kod parçacığı kısayolları eklemeniz gerekir. Daha sonra, bir kod parçacığı kısayol adının tamamlanma sonucu olarak ne zaman eklendiğini tespit etmeniz gerekir. Son olarak, kısayol adını kullanarak kod parçacığı başlığını ve yolunu edinmeniz ve bu bilgileri yöntemdeki yönteme iletmeniz gerekir <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> .

 Sözcük tamamlama listesine kod parçacığı kısayolları eklemek için bunları <xref:Microsoft.VisualStudio.Package.Declarations> <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfınıza nesnesine ekleyin. Kısayolu bir kod parçacığı adı olarak belirleyediğinizden emin olmanız gerekir. Bir örnek için bkz. [Izlenecek yol: yüklü kod parçacıklarının listesini alma (eski uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Sınıfın yönteminde kod parçacığı kısayolunun eklenmesini tespit edebilirsiniz <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> <xref:Microsoft.VisualStudio.Package.Declarations> . Kod parçacığı adı kaynak dosyaya zaten eklenmiş olduğundan, genişletme eklendiğinde kaldırılmalıdır. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A>Yöntemi, kod parçacığı için ekleme noktasını açıklayan bir yayma alır; yayılma alanı kaynak dosyadaki tüm kod parçacığı adını içeriyorsa, bu ad kod parçacığına göre değişir.

 Bir <xref:Microsoft.VisualStudio.Package.Declarations> kısayol adı verilen kod parçacığı eklemeyi işleyen bir sınıfın sürümü aşağıda verilmiştir. Sınıftaki diğer yöntemler <xref:Microsoft.VisualStudio.Package.Declarations> netme için atlandı. Bu sınıfın oluşturucusunun bir nesne aldığını unutmayın <xref:Microsoft.VisualStudio.Package.LanguageService> . Bu, nesne sürüminizden geçirilebilir <xref:Microsoft.VisualStudio.Package.AuthoringScope> (örneğin, <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfının uygulamanız <xref:Microsoft.VisualStudio.Package.LanguageService> nesneyi oluşturucuda alabilir ve bu nesneyi `TestDeclarations` sınıf yapıcısına geçirebilir).

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

 Dil hizmeti kısayol adını aldığında, <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> dosya adını ve kod parçacığı başlığını almak için yöntemini çağırır. Dil hizmeti daha sonra <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> kod parçacığını eklemek için sınıfındaki yöntemini çağırır. aşağıdaki yöntemler, <xref:Microsoft.VisualStudio.Package.ExpansionProvider> kod parçacığını ekleme işlemi sırasında sınıfında verilen sırada Visual Studio tarafından çağırılır:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Dil hizmetiniz için yüklü kod parçacıklarının listesini alma hakkında daha fazla bilgi için bkz. [Izlenecek yol: yüklü kod parçacıklarının listesini alma (eski uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction sınıfını uygulama
 Genişletme işlevi, bir kod parçacığı şablonuna gömülü ve bir alana yerleştirilecek bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Dil hizmetinizdeki genişletme işlevlerini desteklemek için, sınıfından bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.ExpansionFunction> ve metodunu uygulamanız gerekir <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> . Daha sonra <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> , <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionFunction> destekettiğiniz her genişletme işlevi için sınıfının yeni bir örneğini döndürmek üzere sınıfındaki yöntemini geçersiz kılmanız gerekir. Bir genişletme işlevinden olası değerler listesini destekediyorsanız, <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Bu değerlerin bir listesini döndürmek için sınıfındaki metodunu da geçersiz kılmanız gerekir.

 Genişletme sağlayıcısı, genişleme işlevinin çağrıldığı süre tarafından tam olarak başlatılamadığından, bağımsız değişkenler veya diğer alanlara erişmesi gereken bir genişletme işlevi, düzenlenebilir bir alanla ilişkilendirilmemelidir. Sonuç olarak, genişletme işlevi bağımsız değişkenlerinin veya başka bir alanın değerini elde edemeyebilir.

### <a name="example"></a>Örnek
 Aşağıda, bir basit genişletme işlevinin nasıl uygulanabileceğini gösteren bir örnek verilmiştir `GetName` . Bu genişletme işlevi, genişletme işlevi her başlatıldığında bir taban sınıf adına bir sayı ekler (ilişkili kod parçacığı eklendiği her seferinde buna karşılık gelir).

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
- [İzlenecek yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)
