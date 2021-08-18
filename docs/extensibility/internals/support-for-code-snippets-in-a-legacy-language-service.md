---
title: Eski Dil Hizmeti Hizmet Belgelerinde Kod Parçacıkları için destek | Microsoft Docs
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086618"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kod Parçacıkları için Destek
Kod parçacığı, kaynak dosyaya eklenen bir kod parçasıdır. Kod parçacığının kendisi, bir alan kümesine sahip XML tabanlı bir şablondur. Bu alanlar kod parçacığı eklendikten sonra vurgulanır ve kod parçacığının ekli olduğu bağlama bağlı olarak farklı değerlere sahip olabilir. Kod parçacığı eklendikten hemen sonra dil hizmeti kod parçacığını biçimlendirebilirsiniz.

 Kod parçacığı, sekme tuşu kullanılarak kod parçacığının alanlarında gezinmeye olanak sağlayan özel bir düzenleme moduna eklenir. Alanlar IntelliSense stili açılan menüleri destekleyene. Kullanıcı, ENTER veya ESC anahtarını yazarak kod parçacığını kaynak dosyaya işler. Kod parçacıkları hakkında daha fazla bilgi edinmek için bkz. [Kod Parçacıkları.](../../ide/code-snippets.md)

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [bkz. Adım adım kılavuz: Kod Parçacıklarını Uygulama.](../../extensibility/walkthrough-implementing-code-snippets.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="managed-package-framework-support-for-code-snippets"></a>Kod Parçacıkları için Yönetilen Paket Çerçevesi Desteği
 Yönetilen paket çerçevesi (MPF), şablonu okumaktan kod parçacığını eklemeye ve özel düzenleme modunu etkinleştirmeye kadar birçok kod parçacığı işlevini destekler. Destek sınıfı aracılığıyla <xref:Microsoft.VisualStudio.Package.ExpansionProvider> yönetilir.

 Sınıf örneği olduğunda, bir nesnesi almak için sınıfındaki yöntemi çağrılır (temel sınıfın her nesne için her zaman yeni bir <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> nesne <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> döndürse de <xref:Microsoft.VisualStudio.Package.Source> unutmayın).

 MPF genişletme işlevlerini desteklemez. Genişletme işlevi, bir kod parçacığı şablonuna eklenmiş ve bir alana yerleştirilmesi için bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Değerler dil hizmetinin kendisi tarafından bir nesnesi aracılığıyla <xref:Microsoft.VisualStudio.Package.ExpansionFunction> döndürülür. Genişletme <xref:Microsoft.VisualStudio.Package.ExpansionFunction> işlevlerini desteklemek için nesnesi dil hizmeti tarafından uygulanarak gerçekleştirilmesi gerekir.

## <a name="providing-support-for-code-snippets"></a>Kod Parçacıkları için Destek Sağlama
 Kod parçacıkları desteğini etkinleştirmek için kod parçacıklarını sağlamanız veya yüklemeniz ve kullanıcının bu kod parçacıklarını eklemesi için gerekli olan bir olanak sağlanız gerekir. Kod parçacıkları için desteği etkinleştirmenin üç adımı vardır:

1. Kod parçacığı dosyalarını yükleme.

2. Dil hizmetiniz için kod parçacıklarını etkinleştirme.

3. Nesnesinin <xref:Microsoft.VisualStudio.Package.ExpansionProvider> iptali.

### <a name="installing-the-snippet-files"></a>Kod Parçacığı Dosyalarını Yükleme
 Bir dil için tüm kod parçacıkları, genellikle dosya başına bir kod parçacığı şablonu olan XML dosyalarında şablon olarak depolanır. Kod parçacığı şablonları için kullanılan XML şemasıyla ilgili ayrıntılar için bkz. [Kod Parçacıkları Şema Başvurusu.](../../ide/code-snippets-schema-reference.md) Her kod parçacığı şablonu bir dil kimliğiyle tanımlanır. Bu dil kimliği kayıt defterinde belirtilir ve `Language` şablonda etiketin \<Code> özniteliğine girilmelidir.

 Genellikle kod parçacığı şablon dosyalarının depolandığı iki konum vardır: 1) dilinizin yüklandığı ve 2) kullanıcının klasöründe. Bu konumlar kayıt defterine eklenir, böylece Visual Studio Kod Parçacıkları **Yöneticisi** kod parçacıklarını bulabilir. Kullanıcının klasörü, kullanıcı tarafından oluşturulan kod parçacıklarının depolandığı klasördür.

 Yüklü kod parçacığı şablon dosyalarının tipik klasör düzeni şu şekilde görünür: *[InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets.

 *[InstallRoot],* dilinizin yüklü olduğu klasördür.

 *[TestLanguage],* klasör adı olarak dilinizin adıdır.

 *[LCID],* yerel kimliktir. Kod parçacıklarının yerelleştirilmiş sürümleri bu şekilde depolanır. Örneğin, İngilizce için yerel kimlik 1033'tir, bu nedenle *[LCID]* 1033 ile değiştirilir.

 Ek bir dosya sağlanmalıdır ve bu da genellikle SnippetsIndex.xml veya ExpansionsIndex.xml olarak adlandırılan bir dizin dosyasıdır (dosya adı ile biten herhangi bir geçerli dosya adını .xml). Bu dosya genellikle *[InstallRoot]* \\ *[TestLanguage]* klasöründe depolanır ve kod parçacıkları klasörünün tam konumunun yanı sıra kod parçacıklarını kullanan dil hizmetinin dil kimliğini ve GUID'lerini belirtir. Dizin dosyasının tam yolu, daha sonra "Kayıt Defteri Girdilerini Yükleme" makalesinde açıklandığı gibi kayıt defterine girebilirsiniz. Aşağıdaki örnek bir dosya SnippetsIndex.xml:

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

 Etiket, \<Language> dil kimliğini `Lang` (özniteliği) ve dil hizmeti GUID'lerini belirtir.

 Bu örnekte dil hizmetinizi Visual Studio yükleme klasörüne yüklemişsinizdir. %LCID% kullanıcı geçerli yerel kimliğiyle değiştirilir. Her \<SnippetDir> bir farklı dizin ve yerel değer için bir tane olmak için birden çok etiket eklenebilir. Ayrıca, bir kod parçacığı klasörü, her biri bir etikete eklenmiş etiketiyle dizin dosyasında tanımlanan \<SnippetSubDir> alt klasörler \<SnippetDir> içerebilir.

 Kullanıcılar ayrıca diliniz için kendi kod parçacıklarını da oluşturabilir. Bunlar genellikle kullanıcının ayarlar klasöründe depolanır, örneğin *[TestDocs]* \Kod Parçacıkları \\ *[TestLanguage]* \Test Kod Parçacıkları; burada *[TestDocs],* kullanıcının Visual Studio için ayarlar klasörünün konumudur.

 Aşağıdaki değiştirme öğeleri, dizin dosyasındaki etikette \<DirPath> depolanan yola yer olabilir.

|Öğe|Açıklama|
|-------------|-----------------|
|%LCID%|Yerel kimlik.|
|%InstallRoot%|Visual Studio için kök yükleme klasörü, örneğin, C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Geçerli projeyi içeren klasör.|
|%ProjItem%|Geçerli proje öğesini içeren klasör.|
|%TestDocs%|Kullanıcının ayarlar klasöründeki klasör, örneğin, C:\Documents ve \\ *Ayarlar [username]* \Belgelerim\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Dil Hizmetiniz için Kod Parçacıklarını Etkinleştirme
 VSPackage'nıza özniteliğini ekleyerek dil hizmetiniz için kod parçacıklarını etkinleştirebilirsiniz (ayrıntılar için bkz. Eski <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> [Dil Hizmeti](../../extensibility/internals/registering-a-legacy-language-service1.md) Kaydetme). ve parametreleri isteğe bağlıdır, ancak Kod Parçacıkları Yöneticisi'ne kod parçacıklarının konumunu bildirmek için adlandırılmış <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> `SearchPaths` parametreyi dahil etmek gerekir. 

 Aşağıda, bu özniteliğin nasıl kullanıla bir örneği ve ardından ve bir örnek ve ardından ve bir örnek ve ardından bu öznitelikler ve daha fazla bilgi

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Genişletme Sağlayıcısını Çağırma
 Dil hizmeti, herhangi bir kod parçacığının ekleme ve eklemenin çağrılma yolunu kontrol eder.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Kod Parçacıkları için Genişletme Sağlayıcısını Çağırma
 Genişletme sağlayıcısını çağırmanın iki yolu vardır: bir menü komutu veya tamamlama listesinden bir kısayol kullanarak.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Menü Komutu Kullanarak Kod Parçacığı Ekleme
 Kod parçacığı tarayıcısını görüntülemek üzere bir menü komutu kullanmak için bir menü komutu ekler ve ardından bu menü komutuna yanıt <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> olarak arabiriminde yöntemini çağırabilirsiniz.

1. .vsct dosyanıza bir komut ve düğme ekleyin. Bunu yapmaya ilişkin yönergeleri Menü [Komutuyla Uzantı Oluşturma içinde bulabilirsiniz.](../../extensibility/creating-an-extension-with-a-menu-command.md)

2. sınıfından bir sınıf <xref:Microsoft.VisualStudio.Package.ViewFilter> türetin ve yeni <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> menü komutu desteğini belirtmek için yöntemini geçersiz kılın. Bu örnek her zaman menü komutunu sağlar.

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

3. nesnesini <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> almak ve bu <xref:Microsoft.VisualStudio.Package.ViewFilter> nesnede yöntemini <xref:Microsoft.VisualStudio.Package.ExpansionProvider> çağırarak <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> sınıfındaki yöntemini geçersiz kılın.

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

     sınıfındaki aşağıdaki yöntemler, kod parçacığını Visual Studio sırasında verilen sırayla <xref:Microsoft.VisualStudio.Package.ExpansionProvider> çağrılır:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     yöntemi çağrıldıktan sonra kod parçacığı eklenir ve nesnesi yeni eklenen bir kod parçacığını değiştirmek için kullanılan <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> <xref:Microsoft.VisualStudio.Package.ExpansionProvider> özel bir düzenleme modundadır.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Kısayol kullanarak kod parçacığı ekleme
 Tamamlama listesinden kısayol uygulanması, menü komutu uygulamaktan çok daha fazlasıdır. Önce IntelliSense sözcük tamamlama listesine kod parçacığı kısayolları eklemeniz gerekir. Ardından, tamamlamanın sonucu olarak bir kod parçacığı kısayol adının ne zaman ekli olduğunu algılamanız gerekir. Son olarak, kısayol adını kullanarak kod parçacığı başlığını ve yolunu elde edin ve bu bilgileri <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> yönteminde yöntemine <xref:Microsoft.VisualStudio.Package.ExpansionProvider> iletirsiniz.

 Sözcük tamamlama listesine kod parçacığı kısayolları eklemek için bunları <xref:Microsoft.VisualStudio.Package.Declarations> sınıfınıza <xref:Microsoft.VisualStudio.Package.AuthoringScope> ekleyin. Kısayolu kod parçacığı adı olarak tanımlayalı olduğundan emin olun. Bir örnek için, [bkz. Walkthrough: Getting a List of Installed Code Snippets (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Kod parçacığı kısayolunu sınıfının yöntemine <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> <xref:Microsoft.VisualStudio.Package.Declarations> ekleyebilirsiniz. Kod parçacığı adı kaynak dosyaya zaten eklenmiş olduğundan, genişletme ekildiğinde kaldırılmalıdır. yöntemi, kod parçacığı için ekleme noktasını açıklayan bir aralık alır; yayma süresi kaynak dosyada kod parçacığının tamamını kapsıyorsa, bu ad kod <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> parçacığıyla değiştirilir.

 Aşağıda, bir kısayol adı <xref:Microsoft.VisualStudio.Package.Declarations> verilen kod parçacığı eklemeyi ele alan bir sınıf sürümü verilmiştir. Sınıftaki diğer <xref:Microsoft.VisualStudio.Package.Declarations> yöntemler netlik sağlamak için atlanmıştır. Bu sınıfın oluşturucusunu bir nesnesi <xref:Microsoft.VisualStudio.Package.LanguageService> alır. Bu, nesne sürümünüzden geçirebilirsiniz (örneğin, sınıf uygulamanız nesnesini kendi oluşturucus una alıp bu nesneyi sınıf <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.LanguageService> `TestDeclarations` oluşturucuya geçirebilirsiniz).

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

 Dil hizmeti kısayol adını geldiğinde, dosya adını ve kod parçacığı başlığını almak <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> için yöntemini çağırır. Dil hizmeti daha sonra kod <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> parçacığını eklemek <xref:Microsoft.VisualStudio.Package.ExpansionProvider> için sınıfındaki yöntemini çağırtır. Aşağıdaki yöntemler, kod parçacığını Visual Studio sırasında <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sınıfına verilen sırayla çağrılır:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Dil hizmetiniz için yüklü kod parçacıklarının listesini alma hakkında daha fazla bilgi için bkz. Kılavuz: Yüklü Kod Parçacıklarının Listesini Alma [(Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction Sınıfını Uygulama
 Genişletme işlevi, bir kod parçacığı şablonuna eklenmiş ve bir alana yerleştirilmesi için bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Dil hizmetinize genişletme işlevlerini desteklemek için sınıfından bir sınıf türetmeniz ve <xref:Microsoft.VisualStudio.Package.ExpansionFunction> yöntemini uygulamanız <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> gerekir. Ardından, sınıf sürümünüz için destekleyilen her genişletme işlevi için yeni bir örnekleme dönmek <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> üzere <xref:Microsoft.VisualStudio.Package.ExpansionFunction> sınıfındaki yöntemini geçersiz kılmanız gerekir. Genişletme işlevinden olası değerlerin listesini destekliyorsanız, bu değerlerin listesini geri dönmek <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> <xref:Microsoft.VisualStudio.Package.ExpansionFunction> için sınıfındaki yöntemini de geçersiz kılmalısınız.

 Bağımsız değişkenleri alan veya diğer alanlara erişmesi gereken bir genişletme işlevi düzenlenebilir bir alanla ilişkilendirilmesin çünkü genişletme sağlayıcısı genişletme işlevinin çağrıldı zamanı tarafından tam olarak başlatılmamış olabilir. Sonuç olarak genişletme işlevi bağımsız değişkenlerinin veya başka bir alanın değerini elde etmek mümkün değildir.

### <a name="example"></a>Örnek
 Burada adlı basit bir genişletme işlevinin nasıl uygulan `GetName` olabileceğine bir örnek vetir. Bu genişletme işlevi, genişletme işlevinin örneği her ildiğinde (ilişkili kod parçacığı her ekildiğinde buna karşılık gelen) temel sınıf adına bir sayı ekler.

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
