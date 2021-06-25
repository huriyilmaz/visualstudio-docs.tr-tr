---
title: Eski Dil Hizmeti2 Uygulama | Microsoft Docs
description: Yönetilen paket çerçevesini (MPF) kullanarak genişletilmiş dil hizmeti özelliklerini destekleyen eski bir dil hizmetinin nasıl uygulandığını öğrenin. Bölüm 2/2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca2548ddb0c8281241b14de0ec470cfe22db1a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900128"
---
# <a name="implementing-a-legacy-language-service-2"></a>Eski dil hizmetini uygulama 2
Yönetilen paket çerçevesini (MPF) kullanarak bir dil hizmeti uygulamak için sınıfından bir sınıf türetmeli ve aşağıdaki soyut yöntemleri <xref:Microsoft.VisualStudio.Package.LanguageService> ve özellikleri uygulamalısiniz:

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>yöntemi

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>yöntemi

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>yöntemi

- özelliği <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Bu yöntemleri ve özellikleri uygulama hakkında ayrıntılı bilgi için aşağıdaki uygun bölümlere bakın.

  Ek özellikleri desteklemek için, dil hizmetinizin MPF dil hizmeti sınıflarından bir sınıf türetmiş; Örneğin, ek menü komutlarını desteklemek için sınıfından bir sınıf türetmeli ve birkaç komut işleme yöntemini geçersiz <xref:Microsoft.VisualStudio.Package.ViewFilter> kılabilirsiniz (ayrıntılar <xref:Microsoft.VisualStudio.Package.ViewFilter> için bkz. ). sınıfı, çeşitli sınıfların yeni örneklerini oluşturmak için çağrılan bir dizi yöntem sağlar ve sınıfınıza bir örnek sağlamak için uygun oluşturma yöntemini <xref:Microsoft.VisualStudio.Package.LanguageService> geçersiz kılar. Örneğin, kendi sınıfınıza ait bir <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> örneği geri dönmek için <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki yöntemini geçersiz kılmanız <xref:Microsoft.VisualStudio.Package.ViewFilter> gerekir. Daha fazla ayrıntı için "Özel Sınıflar Örneği Oluşturma" bölümüne bakın.

  Dil hizmetiniz birçok yerde kullanılan kendi simgelerini de sağlar. Örneğin, bir IntelliSense tamamlama listesi gösterildiğinde, listede yer alan her öğeyle ilişkilendirilmiş bir simge olabilir, öğeyi yöntem, sınıf, ad alanı, özellik veya diliniz için gereken her şey olarak işaretleyerek. Bu simgeler tüm IntelliSense listelerinde, **Gezinti çubuğunda ve** Hata Listesi görev **penceresinde** kullanılır. Ayrıntılar için aşağıdaki "Dil Hizmeti Görüntüleri" bölümüne bakın.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences Yöntemi
 yöntemi <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> her zaman bir sınıfın aynı örneğini <xref:Microsoft.VisualStudio.Package.LanguagePreferences> döndürür. Dil hizmetiniz için <xref:Microsoft.VisualStudio.Package.LanguagePreferences> ek tercihlere ihtiyacınız yoksa temel sınıfı kullanabilirsiniz. MPF dil hizmeti sınıfları en azından temel sınıfın varlığını <xref:Microsoft.VisualStudio.Package.LanguagePreferences> varsayıyor.

### <a name="example"></a>Örnek
 Bu örnek, yönteminin tipik bir uygulamasını <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> gösterir. Bu örnek temel sınıfı <xref:Microsoft.VisualStudio.Package.LanguagePreferences> kullanır.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>GetScanner Yöntemi
 Bu yöntem, belirteçleri ve bunların türlerini ve tetikleyicilerini almak için kullanılan satır odaklı ayrıştırıcı veya tarayıcı uygulayan <xref:Microsoft.VisualStudio.Package.IScanner> bir nesnenin örneğini döndürür. Bu tarayıcı renklendirme için sınıfında kullanılır, ancak tarayıcı daha karmaşık bir ayrıştırma işlemi için belirteç türlerini ve tetikleyicileri önceden almak için de <xref:Microsoft.VisualStudio.Package.Colorizer> kullanılabilir. Arabirimi uygulayan sınıfını ve <xref:Microsoft.VisualStudio.Package.IScanner> arabirimde tüm yöntemleri uygulamalısiniz. <xref:Microsoft.VisualStudio.Package.IScanner>

### <a name="example"></a>Örnek
 Bu örnek, yönteminin tipik bir uygulamasını <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> gösterir. sınıfı `TestScanner` arabirimini <xref:Microsoft.VisualStudio.Package.IScanner> (gösterilmez) uygulamaya alır.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>ParseSource Yöntemi
 Kaynak dosyayı birkaç farklı nedene göre ayrıştırır. Bu yönteme, <xref:Microsoft.VisualStudio.Package.ParseRequest> belirli bir ayrıştırma işlemi tarafından bekleneni açıklayan bir nesne verilir. yöntemi, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> belirteç işlevselliğini ve kapsamını belirleyen daha karmaşık bir ayrıştırıcı çağırır. yöntemi, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> IntelliSense işlemlerinin yanı sıra küme ayracı eşleştirme desteğinde kullanılır. Bu tür gelişmiş işlemleri desteklemese bile, yine de geçerli bir nesne dönmeniz gerekir ve bu da arabirimi uygulayan ve bu arabirimde tüm yöntemleri uygulayan bir <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıf oluşturmanızı gerektirir. Tüm yöntemlerden null değerler döndürebilirsiniz, <xref:Microsoft.VisualStudio.Package.AuthoringScope> ancak nesnenin kendisi null değer olmamalıdır.

### <a name="example"></a>Örnek
 Bu örnekte yöntemin ve sınıfının en düşük düzeyde uygulanması, dil hizmetinin daha gelişmiş özelliklerden herhangi birini desteklemeden derleyeme ve işleve <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> izin verecek kadar yeterli olduğunu <xref:Microsoft.VisualStudio.Package.AuthoringScope> gösterir.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Name Özelliği
 Bu özellik dil hizmetinin adını döndürür. Bu, dil hizmeti kaydedilirken verilen adla aynı adla aynı olması gerekir. Bu ad, kayıt defterine erişmek için kullanılan sınıf olan en belirgin olan <xref:Microsoft.VisualStudio.Package.LanguagePreferences> birkaç yerde kullanılır. Kayıt defteri girdisi ve anahtar adları için kayıt defterinde kullanılan ad, bu özellik tarafından döndürülen adın yerelleştirilmiş olması gerekmez.

### <a name="example"></a>Örnek
 Bu örnekte özelliğin olası bir uygulaması <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> yer almaktadır. Buradaki adın sabit kodlu olduğunu unutmayın: Gerçek ad bir kaynak dosyasından alınarak dil hizmetinin kaydında kullanılabilir [(bkz.](../../extensibility/internals/registering-a-legacy-language-service1.md)Eski Dil Hizmeti Kaydetme).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Özel Sınıflar Örneği Oluşturma
 Belirtilen sınıflarda aşağıdaki yöntemler, her sınıfın kendi sürümlerinin örneklerini sağlamak için geçersiz kılınabilir.

### <a name="in-the-languageservice-class"></a>LanguageService Sınıfında

|Yöntem|Döndürülen Sınıf|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Metin görünümüne özel eklemeleri desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Özel belge özelliklerini desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Gezinti çubuğunu **desteklemek için.**|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Kod parçacığı şablonlarındaki işlevleri desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Kod parçacıklarını desteklemek için (bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Yapı özelleştirmeyi <xref:Microsoft.VisualStudio.Package.ParseRequest> desteklemek için (bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Kaynak kodunu biçimlendirmeyi, açıklama karakterlerini belirtmeyi ve yöntem imzalarını özelleştirmeyi desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Ek menü komutlarını desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Söz dizimi vurgulamayı desteklemek için (bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Dil tercihlerine erişimi desteklemek için. Bu yöntemin uygulanması gerekir, ancak temel sınıfın bir örneğini dönüş olabilir.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Bir satırda belirteç türlerini tanımlamak için kullanılan bir ayrıştırıcı sağlamak için. Bu yöntemin uygulanması ve <xref:Microsoft.VisualStudio.Package.IScanner> türetilen olması gerekir.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Kaynak dosyanın tamamına işlev ve kapsam tanımlamak için kullanılan ayrıştırıcı sağlamak için. Bu yöntem uygulanmalı ve sınıfının sürümünün bir örneğini <xref:Microsoft.VisualStudio.Package.AuthoringScope> getirsin. Tek desteklemek istediğiniz söz dizimi vurgulaması ise (yönteminden döndürülen ayrıştırıcıyı gerektirir), yöntemleri null değerler döndüren sınıfın bir sürümünün döndürülme dışında bu yöntemde hiçbir şey <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> yapmayamazsınız.|

### <a name="in-the-source-class"></a>Kaynak Sınıfında

|Yöntem|Döndürülen Sınıf|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|IntelliSense tamamlama listelerinin görüntülemesini özelleştirmek için (bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Hata Listesi görev listesinde işaretçileri desteklemek için; özellikle, dosyayı açmanın ve hataya neden olan satıra atlayarak ötesine geçilen özellikler için destek.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense Parametre Bilgisi Araç İpucu'larının display'ini özelleştirmek için.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Kod açıklamalarını desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Ayrıştırma işlemi sırasında bilgi toplamak için.|

### <a name="in-the-authoringscope-class"></a>AuthoringScope Sınıfında

|Yöntem|Döndürülen Sınıf|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Üyeler veya türler gibi bildirimlerin listesini sağlar. Bu yöntemin uygulanması gerekir, ancak null değer döndürebilirsiniz. Bu yöntem geçerli bir nesne döndürürse, nesne sınıf sürümünün bir örneği <xref:Microsoft.VisualStudio.Package.Declarations> olmalıdır.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Belirli bir bağlam için yöntem imzalarının listesini sağlar. Bu yöntemin uygulanması gerekir, ancak null değer döndürebilirsiniz. Bu yöntem geçerli bir nesne döndürürse, nesne sınıf sürümünün bir örneği <xref:Microsoft.VisualStudio.Package.Methods> olmalıdır.|

## <a name="language-service-images"></a>Dil Hizmeti Görüntüleri
 Dil hizmeti boyunca kullanılacak simgelerin bir listesini sağlamak için sınıfındaki yöntemini geçersiz <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> kılın ve simgeleri içeren bir <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:System.Windows.Forms.ImageList> dönüş. Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıf, varsayılan bir simge kümesi yükler. Simgelere ihtiyaç olan yerlerde tam görüntü dizinini belirttiğinizden, kendi görüntü listenizi düzenlemeniz tamamen size göre olur.

### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense tamamlama listelerinde kullanılan görüntüler
 IntelliSense tamamlama listeleri için, görüntü dizini sınıfın yönteminde her öğe için belirtilir ve bir görüntü dizini sağlamak için bunu <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> geçersiz kılmalısiniz. yönteminden döndürülen değer, sınıf oluşturucusu için sağlanan görüntü listesine bir dizindir ve sınıfındaki yönteminden döndürülen görüntü listesiyle aynı <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> olandır (farklı <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> <xref:Microsoft.VisualStudio.Package.Source> bir görüntü listesi sağlamak için sınıfındaki yöntemini geçersiz kılarsanız için hangi görüntü listesinin kullanacağız?

### <a name="images-used-in-the-navigation-bar"></a>Gezinti Çubuğunda Kullanılan Görüntüler
 Gezinti **çubuğunda tür** ve üye listeleri görüntülenir ve hızlı gezinti için kullanılan simgeler gösterebilirsiniz. Bu simgeler sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminden elde edilir ve Gezinti çubuğu için özel olarak geçersiz <xref:Microsoft.VisualStudio.Package.LanguageService> **kılınamaz.** Birleşik giriş kutularındaki her öğe için kullanılan dizinler, Birleşik giriş kutularını temsil eden listeler, sınıfındaki yönteminde doldurulduğu zaman belirtilir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (bkz. [eski dil hizmetindeki gezinti çubuğu için destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Bu görüntü dizinleri, genellikle kendi sınıfınızın sürümü aracılığıyla Ayrıştırıcıdan bir şekilde alınır <xref:Microsoft.VisualStudio.Package.Declarations> . Dizinler nasıl alınır?

### <a name="images-used-in-the-error-list-task-window"></a>Hata Listesi görev penceresinde kullanılan görüntüler
 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Yöntem ayrıştırıcısı (bkz. [eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) bir hatayla karşılaştığında ve bu hatayı sınıftaki yönteme geçirdiğinde <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> , hata **hata listesi** görev penceresinde raporlanır. Bir simge, görev penceresinde görüntülenen her öğeyle ilişkilendirilebilir ve bu simge, sınıftaki yöntemden döndürülen görüntü listesinden gelir <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> . MPF sınıflarının varsayılan davranışı hata iletisiyle bir görüntü göstermemelidir. Ancak, sınıfından bir sınıf türeterek <xref:Microsoft.VisualStudio.Package.Source> ve yöntemi geçersiz kılarak bu davranışı geçersiz kılabilirsiniz <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> . Bu yöntemde yeni bir <xref:Microsoft.VisualStudio.Package.DocumentTask> nesne oluşturacaksınız. Nesneyi döndürmeden önce, <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> <xref:Microsoft.VisualStudio.Package.DocumentTask> görüntü dizinini ayarlamak için nesnesi üzerinde özelliğini kullanabilirsiniz. Bu, aşağıdaki örneğe benzer bir şekilde görünür. `TestIconImageIndex`Tüm simgeleri listeleyen ve bu örneğe özgü olan bir sabit listesi olduğunu unutmayın. Dil hizmetinizdeki simgeleri tanımlamaya yönelik farklı bir yönteme sahip olabilirsiniz.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>Dil hizmeti için varsayılan görüntü listesi
 Temel MPF dil hizmeti sınıflarıyla sağlanan varsayılan görüntü listesi, daha yaygın dil öğeleriyle ilişkili bir dizi simge içerir. Bu simgelerin toplu kümesi, genel, dahili, arkadaş, korunan, özel ve kısayol 'un erişim kavramlarına karşılık gelen altı çeşitteki kümeler halinde düzenlenir. Örneğin, genel, korumalı veya özel olmasına bağlı olarak bir yöntem için farklı simgelere sahip olabilirsiniz.

 Aşağıdaki sabit listesi her bir simge kümesi için tipik adları belirtir ve ilişkili dizini belirtir. Örneğin, sabit listesine bağlı olarak, korumalı bir yöntemin görüntü dizinini olarak belirtebilirsiniz `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . Bu Numaralandırmadaki adları istediğiniz gibi değiştirebilirsiniz.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)
- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
