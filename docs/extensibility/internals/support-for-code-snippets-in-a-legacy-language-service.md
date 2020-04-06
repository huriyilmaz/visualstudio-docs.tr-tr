---
title: Eski Dil Hizmetinde Kod Parçacıkları Desteği | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704909"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Kod Parçacıkları için Destek
Kod parçacığı, kaynak dosyaya eklenen bir kod parçasıdır. Parçacık kendisi, bir alan kümesine sahip XML tabanlı bir şablondur. Bu alanlar, parçacık eklendikten sonra vurgulanır ve snippet'in eklendiği bağlama bağlı olarak farklı değerlere sahip olabilir. Parçacık takıldıktan hemen sonra, dil hizmeti snippet'i biçimlendirebilir.

 Parçacık, SEKME tuşu kullanılarak snippet alanlarının gezinmesini sağlayan özel bir düzenleme moduna eklenir. Alanlar IntelliSense tarzı açılır menüleri destekleyebilir. Kullanıcı, ENTER veya ESC tuşunu yazarak snippet'i kaynak dosyaya adar. Parçacıklar hakkında daha fazla bilgi edinmek için lütfen [Kod Parçacıkları'na](../../ide/code-snippets.md)bakın.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [Walkthrough: Code Snippets uygulama](../../extensibility/walkthrough-implementing-code-snippets.md)' ya bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="managed-package-framework-support-for-code-snippets"></a>Kod Parçacıkları için Yönetilen Paket Çerçeve Desteği
 Yönetilen paket çerçevesi (MPF), şablonu okumaktan snippet'i eklemeye ve özel düzeltme modunu etkinleştirmeye kadar çoğu parçacık işlevini destekler. Destek <xref:Microsoft.VisualStudio.Package.ExpansionProvider> sınıf aracılığıyla yönetilir.

 <xref:Microsoft.VisualStudio.Package.Source> Sınıf <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> anında olduğunda, <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfdaki yöntem bir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesne elde etmek için çağrılır <xref:Microsoft.VisualStudio.Package.LanguageService> (taban sınıfın <xref:Microsoft.VisualStudio.Package.ExpansionProvider> her <xref:Microsoft.VisualStudio.Package.Source> nesne için her zaman yeni bir nesne döndürür).

 MPF genişletme işlevlerini desteklemez. Genişletme işlevi, bir parçacık şablonuna katıştırılmış ve bir alana yerleştirilecek bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Değerler, dil hizmetinin kendisi tarafından <xref:Microsoft.VisualStudio.Package.ExpansionFunction> bir nesne aracılığıyla döndürülür. Nesne <xref:Microsoft.VisualStudio.Package.ExpansionFunction> genişletme işlevlerini desteklemek için dil hizmeti tarafından uygulanmalıdır.

## <a name="providing-support-for-code-snippets"></a>Kod Parçacıkları için Destek Sağlama
 Kod parçacıkları için destek sağlamak için, parçacıkları sağlamanız veya yüklemeniz ve kullanıcının bu parçacıkları eklemesi için gereken araçları sağlamanız gerekir. Kod parçacıkları için desteği etkinleştirmek için üç adım vardır:

1. Parçacık dosyalarını yükleme.

2. Dil hizmetiniz için kod parçacıklarını etkinleştirme.

3. Nesneyi <xref:Microsoft.VisualStudio.Package.ExpansionProvider> çağırmak.

### <a name="installing-the-snippet-files"></a>Parçacık Dosyalarını Yükleme
 Bir dilin tüm parçacıkları, genellikle dosya başına bir parçacık şablonu olan XML dosyalarında şablon olarak depolanır. Kod snippet şablonları için kullanılan XML şeması yla ilgili ayrıntılar için [Kod Parçacıkları Şeması Başvurusu'na](../../ide/code-snippets-schema-reference.md)bakın. Her parçacık şablonu bir dil kimliğiyle tanımlanır. Bu dil kimliği kayıt defterinde belirtilir ve `Language` şablondaki \<Kod> etiketinin özniteliğine konur.

 Genellikle snippet şablon dosyalarının depolandığı iki konum vardır: 1) dilinizin yüklendiği yer ve 2) kullanıcının klasöründe. Bu konumlar, Visual Studio **Code Snippets Manager'ın** parçacıkları bulabilmeleri için kayıt defterine eklenir. Kullanıcının klasörü, kullanıcı tarafından oluşturulan parçacıkların depolandığı yerdir.

 Yüklü snippet şablon dosyaları için tipik klasör düzeni şuna benzer: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.

 *[InstallRoot]* dilinizin yüklü olduğu klasördür.

 *[TestLanguage]* klasör adı olarak dilinizin adıdır.

 *[LCID]* yerel kimliktir. Parçacıklarınızın yerelleştirilmiş sürümleri bu şekilde depolanır. Örneğin, İngilizce için yerel kimlik 1033 olduğundan *[LCID]* 1033 ile değiştirilir.

 Bir ek dosya sağlanmalıdır ve bu genellikle SnippetsIndex.xml veya ExpansionsIndex.xml (.xml ile biten geçerli bir dosya adı kullanabilirsiniz) olarak adlandırılan bir dizin dosyasıdır. Bu dosya genellikle *[InstallRoot]*\\ *[TestLanguage]* klasöründe depolanır ve parçacıklar klasörünün tam konumunun yanı sıra parçacıkları kullanan dil hizmetinin dil kimliğini ve GUID'i belirtir. Dizin dosyasının tam yolu daha sonra "Kayıt Defteri Girişlerini Yükleme"de açıklandığı şekilde kayıt defterine konur. Burada bir SnippetsIndex.xml dosyasının bir örneğidir:

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

 Dil \<> etiketinde dil kimliği `Lang` (öznitelik) ve dil hizmeti GUID belirtilir.

 Bu örnek, dil hizmetinizi Visual Studio yükleme klasörüne yüklediğinizi varsayar. %LCID% kullanıcının geçerli yerel kimliği ile değiştirilir. Birden \<çok SnippetDir> etiketleri, her farklı dizin ve yerel için bir eklenebilir. Buna ek olarak, bir snippet klasörü, her biri dizin dosyasında SnippetDir> etiketi \<yle \<tanımlanan ve Bir SnippetDir> etiketine katıştırılmış alt klasörler içerebilir.

 Kullanıcılar ayrıca diliniz için kendi parçacıklarını oluşturabilir. Bunlar genellikle kullanıcının ayarlar klasöründe depolanır, örneğin *[TestDocs]* \Code\\Snippets *[TestLanguage]* \Test Kodu Parçacıkları, *[TestDocs]* Visual Studio için kullanıcının ayarlar klasörünün konumudur.

 Aşağıdaki ikame öğeleri, dizin dosyasındaki \<DirPath> etiketinde depolanan yola yerleştirilebilir.

|Öğe|Açıklama|
|-------------|-----------------|
|%LCID%|Yerel kimlik.|
|%InstallRoot%|Visual Studio için kök yükleme klasörü, örneğin, C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Geçerli projeyi içeren klasör.|
|%ProjItem%|Geçerli proje öğesini içeren klasör.|
|%TestDocs%|Kullanıcının ayarlar klasöründeki klasör, örneğin, C:\Belgeler ve Ayarlar\\ *[kullanıcı adı]* \Belgelerim\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Dil Hizmetiniz için Kod Parçacıklarını Etkinleştirme
 VSPackage'ınıza özniteliği ekleyerek <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> dil hizmetinizin kod parçacıklarını etkinleştirebilirsiniz (ayrıntılar için Eski Dil Hizmeti [Kaydetme'ye](../../extensibility/internals/registering-a-legacy-language-service1.md) bakın). Ve <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametreler isteğe bağlıdır, ancak `SearchPaths` **kod** parçacıkları yöneticisini parçacıklarınızın konumunu bildirmek için adlandırılmış parametreyi eklemeniz gerekir.

 Bu özniteliğin nasıl kullanılacağına bir örnek aşağıda verilmiştir:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Genişletme Sağlayıcısını Arama
 Dil hizmeti, herhangi bir kod parçacığının eklenmesini ve eklemenin çağrılma şeklini denetler.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Kod Parçacıkları için Genişletme Sağlayıcısını Arama
 Genişletme sağlayıcısını çağırmanın iki yolu vardır: menü komutunu kullanarak veya tamamlama listesinden kısayol kullanarak.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Menü Komutu kullanarak Kod Snippet ekleme
 Snippet tarayıcısını görüntülemek için bir menü komutu kullanmak için, <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> bir <xref:Microsoft.VisualStudio.Package.ExpansionProvider> menü komutu ekleyin ve ardından bu menü komutuna yanıt olarak arabirimdeki yöntemi ararsınız.

1. .vsct dosyanıza bir komut ve bir düğme ekleyin. [Menü Komutu ile Uzantı Oluşturma'da](../../extensibility/creating-an-extension-with-a-menu-command.md)bunu yapmak için yönergeleri bulabilirsiniz.

2. Sınıftan <xref:Microsoft.VisualStudio.Package.ViewFilter> bir sınıf türetin <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> ve yeni menü komutunu desteklemek için yöntemi geçersiz kılın. Bu örnek her zaman menü komutunu etkinleştirir.

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

3. Nesneyi <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> elde etmek <xref:Microsoft.VisualStudio.Package.ViewFilter> için sınıftaki yöntemi <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> geçersiz kılın ve bu nesneüzerindeki yöntemi çağırın. <xref:Microsoft.VisualStudio.Package.ExpansionProvider>

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

     <xref:Microsoft.VisualStudio.Package.ExpansionProvider> Sınıftaki aşağıdaki yöntemler, snippet'in eklenmesi sırasında verilen sırada Visual Studio tarafından çağrılır:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> Yöntem çağrıldıktan sonra, parçacık eklenmiş ve <xref:Microsoft.VisualStudio.Package.ExpansionProvider> nesne yeni eklenmiş bir snippet değiştirmek için kullanılan özel bir edit modunda.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Kısayol kullanarak kod parçacığı ekleme
 Bir tamamlama listesinden kısayol uygulaması, bir menü komutunu uygulamaktan çok daha fazla ilgilidir. Öncelikle IntelliSense sözcük tamamlama listesine snippet kısayolları eklemeniz gerekir. Daha sonra tamamlanması sonucunda bir snippet kısayol adı eklendiğinde algılamanız gerekir. Son olarak, kısayol adını kullanarak snippet başlığı nı ve yolunu <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> edinmeniz <xref:Microsoft.VisualStudio.Package.ExpansionProvider> ve bu bilgileri yöntemdeki yönteme aktarmanız gerekir.

 Sözcük tamamlama listesine snippet kısayolları eklemek <xref:Microsoft.VisualStudio.Package.Declarations> için bunları <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfınızdaki nesneye ekleyin. Kısayolu bir parçacık adı olarak tanımlayabildiğinizden emin olmalısınız. Örneğin, [Bkz. Walkthrough: Yüklü Kod Parçacıkları Listesi Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 <xref:Microsoft.VisualStudio.Package.Declarations> Sınıfın <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> yönteminde kod snippet kısayolu ekleme algılayabilirsiniz. Parçacık adı zaten kaynak dosyaya eklenmiş olduğundan, genişletme eklendiğinde kaldırılması gerekir. Yöntem, <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> parçacık için ekleme noktasını açıklayan bir yayılma alanı alır; açıklık kaynak dosyadaki tüm parçacık adını içeriyorsa, bu ad parçacıkla değiştirilir.

 Burada bir kısayol <xref:Microsoft.VisualStudio.Package.Declarations> adı verilen snippet ekleme işleyen bir sınıfın bir sürümüdür. Sınıftaki <xref:Microsoft.VisualStudio.Package.Declarations> diğer yöntemler netlik için atlanmıştır. Bu sınıfın oluşturucusu bir <xref:Microsoft.VisualStudio.Package.LanguageService> nesne alır unutmayın. Bu, <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnenin sizin sürümünüzden geçirilebilir (örneğin, <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfın uygulamanız <xref:Microsoft.VisualStudio.Package.LanguageService> nesneyi oluşturucusundaki alabilir ve `TestDeclarations` bu nesneyi sınıf oluşturucunuza geçirebilir).

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

 Dil hizmeti kısayol adını aldığında, dosya <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> adı ve kod snippet başlığı almak için yöntemi çağırır. Dil hizmeti daha <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> sonra kod <xref:Microsoft.VisualStudio.Package.ExpansionProvider> snippet eklemek için sınıfta yöntem çağırır. Aşağıdaki yöntemler Visual Studio tarafından <xref:Microsoft.VisualStudio.Package.ExpansionProvider> snippet ekleme işlemi sırasında sınıfta verilen sırada çağrılır:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Dil hizmetiniz için yüklü kod parçacıklarının listesini alma hakkında daha fazla bilgi için [Walkthrough: Installed Code Snippets (Eski Uygulama) listesi ne rendelene](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)bakın.

## <a name="implementing-the-expansionfunction-class"></a>ExpansionFunction Sınıfının Uygulanması
 Genişletme işlevi, bir parçacık şablonuna katıştırılmış ve bir alana yerleştirilecek bir veya daha fazla değer döndüren adlandırılmış bir işlevdir. Dil hizmetinizdeki genişletme işlevlerini desteklemek <xref:Microsoft.VisualStudio.Package.ExpansionFunction> için, sınıftan bir sınıf türetmeniz ve <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> yöntemi uygulamanız gerekir. Daha sonra, desteklediğiniz her <xref:Microsoft.VisualStudio.Package.LanguageService> genişletme işlevi için <xref:Microsoft.VisualStudio.Package.ExpansionFunction> sınıfın sürümünün yeni bir anlık halini döndürmek için sınıftaki <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> yöntemi geçersiz kılmanız gerekir. Genişletme işlevinden olası değerlerin listesini destekliyorsanız, bu değerlerin <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> listesini döndürmek <xref:Microsoft.VisualStudio.Package.ExpansionFunction> için sınıftaki yöntemi de geçersiz kılmanız gerekir.

 Genişletme sağlayıcısı genişletme işlevi çağrıldığında tam olarak başlatılan olmayabilir gibi, bağımsız değişkenler alır veya diğer alanlara erişmek için gereken bir genişletme işlevi, erişilebilir bir alan ile ilişkili olmamalıdır. Sonuç olarak, genişletme işlevi bağımsız değişkenlerinin veya başka bir alanın değerini elde etmek mümkün değildir.

### <a name="example"></a>Örnek
 Burada, adlı `GetName` basit bir genişletme işlevinin nasıl uygulanabildiğini bir örnek verilmiştir. Bu genişletme işlevi, genişletme işlevi her anında olduğunda (ilişkili kod parçacığı nın her eklenmesine karşılık gelen) bir sayıyı taban sınıf adına ekler.

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
