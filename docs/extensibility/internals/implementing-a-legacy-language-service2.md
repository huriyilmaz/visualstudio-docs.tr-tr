---
title: Eski dil Service2 uygulama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 053ca367776c811dd1192814c5f928bb294eefb4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727236"
---
# <a name="implementing-a-legacy-language-service"></a>Eski dil hizmeti uygulama
Yönetilen paket çerçevesi 'ni (MPF) kullanarak bir dil hizmetini uygulamak için, <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfından bir sınıf türetmeniz ve aşağıdaki soyut yöntemleri ve özellikleri uygulamanız gerekir:

- @No__t_0 yöntemi

- @No__t_0 yöntemi

- @No__t_0 yöntemi

- @No__t_0 özelliği

  Bu yöntem ve özellikleri uygulamayla ilgili ayrıntılar için aşağıdaki ilgili bölümlere bakın.

  Ek özellikleri desteklemek için dil hizmetinizin MPF dil hizmeti sınıflarından birindeki bir sınıfı türetmeniz gerekebilir; Örneğin, ek menü komutlarını desteklemek için <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfından bir sınıf türetmeniz ve komut işleme yöntemlerinin birkaçını geçersiz kılmanız gerekir (Ayrıntılar için bkz. <xref:Microsoft.VisualStudio.Package.ViewFilter>). @No__t_0 sınıfı, çeşitli sınıfların yeni örneklerini oluşturmak için çağrılan ve sınıfınızın bir örneğini sağlamak için uygun oluşturma yöntemini geçersiz kıldığınız birkaç yöntem sağlar. Örneğin, kendi <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfınızın bir örneğini döndürmek için <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> yöntemini geçersiz kılmanız gerekir. Daha fazla ayrıntı için "özel sınıflar örneği oluşturma" bölümüne bakın.

  Dil hizmetiniz, birçok yerde kullanılan kendi simgelerini de sağlayabilir. Örneğin, bir IntelliSense tamamlanma listesi gösterildiğinde, listedeki her öğe kendisiyle ilişkili bir simgeye sahip olabilir, öğe bir yöntem, sınıf, ad alanı, özellik veya diliniz için gerekli herhangi bir şey olarak işaretleniyor. Bu simgeler tüm IntelliSense listelerinde, **Gezinti çubuğunda**ve **hata listesi** görev penceresinde kullanılır. Ayrıntılar için aşağıdaki "dil hizmeti görüntüleri" bölümüne bakın.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences Yöntemi
 @No__t_0 yöntemi her zaman aynı <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfının örneğini döndürür. Dil hizmetiniz için ek bir tercihlerinize gerek yoksa, temel <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfını kullanabilirsiniz. MPF dil hizmeti sınıfları, en azından temel <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfının varlığını varsayar.

### <a name="example"></a>Örnek
 Bu örnek <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> yönteminin tipik bir uygulamasını gösterir. Bu örnek, temel <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfını kullanır.

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

## <a name="getscanner-method"></a>GetScanner yöntemi
 Bu yöntem, belirteçleri ve bunların türlerini ve tetikleyicilerini elde etmek için kullanılan bir hat odaklı ayrıştırıcısı veya tarayıcıyı uygulayan <xref:Microsoft.VisualStudio.Package.IScanner> nesnesinin bir örneğini döndürür. Bu tarayıcı renklendirme için <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfında kullanılır, ancak tarayıcı belirteç türlerini ve Tetikleyicileri daha karmaşık bir ayrıştırma işlemine bir ön halde olarak almak için de kullanılabilir. @No__t_0 arabirimini uygulayan sınıfı sağlamanız gerekir ve <xref:Microsoft.VisualStudio.Package.IScanner> arabirimindeki tüm yöntemleri uygulamanız gerekir.

### <a name="example"></a>Örnek
 Bu örnek <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yönteminin tipik bir uygulamasını gösterir. @No__t_0 sınıfı <xref:Microsoft.VisualStudio.Package.IScanner> arabirimini uygular (gösterilmez).

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

## <a name="parsesource-method"></a>ParseSource yöntemi
 Kaynak dosyayı bir dizi farklı nedenden göre ayrıştırır. Bu yönteme, belirli bir ayrıştırma işleminden nelerin beklendiklerinizi açıklayan bir <xref:Microsoft.VisualStudio.Package.ParseRequest> nesnesi verilir. @No__t_0 yöntemi, belirteç işlevselliğini ve kapsamını belirleyen daha karmaşık bir Ayrıştırıcı çağırır. @No__t_0 yöntemi, IntelliSense işlemlerine yönelik desteğin yanı sıra küme ayracı eşleştirmesi de kullanılır. Bu tür gelişmiş işlemleri desteklemeseniz bile, yine de geçerli bir <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnesi döndürmelidir ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> arabirimini uygulayan ve bu arabirimdeki tüm yöntemleri uygulayan bir sınıf oluşturmanız gerekir. Tüm metotlardan null değerler döndürebilirsiniz, ancak <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnenin kendisi null bir değer olmamalıdır.

### <a name="example"></a>Örnek
 Bu örnek, dil hizmetinin daha gelişmiş özelliklerden herhangi birini desteklemeyerek derlenmesi ve işlevi yapmasına izin vermek için yeterli <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> yönteminin ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfının en az bir uygulamasını gösterir.

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

## <a name="name-property"></a>Name özelliği
 Bu özellik, dil hizmetinin adını döndürür. Bu, dil hizmeti kaydedildiğinde verilen ad ile aynı olmalıdır. Bu ad, bir dizi yerde kullanılır, en belirgin değer, kayıt defterine erişmek için adının kullanıldığı <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfıdır. Kayıt defteri girdisi ve anahtar adları için kayıt defterinde kullanıldığından, bu özellik tarafından döndürülen ad yerelleştirilemez olmalıdır.

### <a name="example"></a>Örnek
 Bu örnek <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> özelliğinin olası bir uygulamasını gösterir. Buradaki adın sabit kodlanmış olduğunu unutmayın: bir kaynak dosyasından gerçek adın alınması gerekir, böylece bir dil hizmeti kaydı için kullanılabilir (bkz. [eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Özel sınıfları örnekleme
 Belirtilen sınıflarda bulunan aşağıdaki yöntemler, her sınıfın kendi sürümlerinizin örneklerini sağlamak için geçersiz kılınabilir.

### <a name="in-the-languageservice-class"></a>LanguageService sınıfında

|Yöntem|Döndürülen sınıf|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Metin görünümüne özel eklemeleri desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Özel belge özelliklerini desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|**Gezinti çubuğunu**desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Kod parçacığı şablonlarındaki işlevleri desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Kod parçacıklarını desteklemek için (Bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|@No__t_0 yapısının özelleştirmesini desteklemek için (Bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Kaynak kodu biçimlendirmeyi desteklemek, açıklama karakterlerini belirtmek ve Yöntem imzalarını özelleştirmek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Ek menü komutlarını desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Söz dizimi vurgulamasını desteklemek için (Bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Dil tercihlerine erişimi desteklemek için. Bu yöntem uygulanmalıdır, ancak temel sınıfın bir örneğini döndürebilir.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Bir satırdaki belirteçlerin türlerini tanımlamak için kullanılan bir Ayrıştırıcı sağlamak için. Bu yöntem uygulanmalıdır ve <xref:Microsoft.VisualStudio.Package.IScanner> türetilmelidir.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Tüm kaynak dosya genelinde işlevselliği ve kapsamı tanımlamak için kullanılan bir Ayrıştırıcı sağlamak için. Bu yöntem uygulanmalıdır ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfının sürümünün bir örneğini döndürmelidir. ' I desteklemek istiyorsanız, sözdizimi vurgulaması (<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> yönteminden döndürülen <xref:Microsoft.VisualStudio.Package.IScanner> ayrıştırıcısı gerektiriyorsa), bu yöntemde, yöntemlerinin hepsi null değerler döndüren <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfının bir sürümünü döndürenden başka hiçbir şey yapabilirsiniz.|

### <a name="in-the-source-class"></a>Kaynak sınıfta

|Yöntem|Döndürülen sınıf|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|IntelliSense tamamlanma listelerinin görüntülenmesini özelleştirmek için (Bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Hata Listesi görev listesinde destekleyici işaretçiler için; Özellikle, dosyayı açan ve hataya neden olan satıra atlama özellikleri için destek.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense parametre bilgisi araç Ipuçlarının görüntülenmesini özelleştirmek için.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Açıklama kodunu desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Ayrıştırma işlemi sırasında bilgi toplamak için.|

### <a name="in-the-authoringscope-class"></a>AuthoringScope sınıfında

|Yöntem|Döndürülen sınıf|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Üyeler veya türler gibi bildirimlerin bir listesini sağlar. Bu yöntemin uygulanması gerekir, ancak null bir değer döndürebilir. Bu yöntem geçerli bir nesne döndürürse, nesne <xref:Microsoft.VisualStudio.Package.Declarations> sınıf sürümünüzün bir örneği olmalıdır.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Belirli bir bağlam için yöntem imzalarının bir listesini sağlar. Bu yöntemin uygulanması gerekir, ancak null bir değer döndürebilir. Bu yöntem geçerli bir nesne döndürürse, nesne <xref:Microsoft.VisualStudio.Package.Methods> sınıf sürümünüzün bir örneği olmalıdır.|

## <a name="language-service-images"></a>Dil hizmeti görüntüleri
 Dil hizmeti genelinde kullanılacak simgelerin listesini sağlamak için <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yöntemi geçersiz kılın ve simgeleri içeren bir <xref:System.Windows.Forms.ImageList> döndürün. Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfı varsayılan simge kümesini yükler. Bu konumlarda simge gerektiren tam görüntü dizinini belirttiğinizden, kendi görüntü listenizi düzenleme işlemi tamamen size aittir.

### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense tamamlanma listelerinde kullanılan görüntüler
 IntelliSense tamamlama listelerinde, bir görüntü dizini sağlamak istiyorsanız, geçersiz kılmanız gereken <xref:Microsoft.VisualStudio.Package.Declarations> sınıfının <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> yöntemindeki her öğe için görüntü dizini belirtilir. @No__t_0 yönteminden döndürülen değer, <xref:Microsoft.VisualStudio.Package.CompletionSet> sınıf oluşturucusuna sağlanan görüntü listesinin bir dizinidir ve <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminden döndürülen görüntü listesidir (@no__ için kullanılacak görüntü listesini değiştirebilirsiniz farklı bir görüntü listesi sağlamak için <xref:Microsoft.VisualStudio.Package.Source> sınıfında <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> yöntemini geçersiz kılarsınız.

### <a name="images-used-in-the-navigation-bar"></a>Gezinti çubuğunda kullanılan görüntüler
 **Gezinti çubuğu** , türlerin ve üyelerin listelerini görüntüler ve hızlı gezinme için kullanılan simgeleri gösterebilir. Bu simgeler <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminden alınır ve özellikle **Gezinti çubuğu**için geçersiz kılınamaz. Birleşik giriş kutularındaki her öğe için kullanılan dizinler, Birleşik giriş kutularını temsil eden listeler <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> sınıfındaki <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> yönteminde doldurulduğu zaman belirtilir (bkz. [eski dil hizmetindeki gezinti çubuğu Için destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Bu görüntü dizinleri, genellikle <xref:Microsoft.VisualStudio.Package.Declarations> sınıfının sürümünüz aracılığıyla Ayrıştırıcıdan bir şekilde alınır. Dizinler nasıl alınır?

### <a name="images-used-in-the-error-list-task-window"></a>Hata Listesi görev penceresinde kullanılan görüntüler
 @No__t_0 yöntemi ayrıştırıcısı (bkz. [eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) bir hatayla karşılaştığında ve bu hatayı <xref:Microsoft.VisualStudio.Package.AuthoringSink> sınıfındaki <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> yöntemine geçirdiğinde, hata **hata listesi** görev penceresinde raporlanır. Bir simge, görev penceresinde görüntülenen her öğeyle ilişkilendirilebilir ve bu simgenin <xref:Microsoft.VisualStudio.Package.LanguageService> sınıfındaki <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> yönteminden döndürülen aynı görüntü listesinden gelir. MPF sınıflarının varsayılan davranışı hata iletisiyle bir görüntü göstermemelidir. Ancak, <xref:Microsoft.VisualStudio.Package.Source> sınıfından bir sınıf türeterek ve <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> yöntemini geçersiz kılarak bu davranışı geçersiz kılabilirsiniz. Bu yöntemde yeni bir <xref:Microsoft.VisualStudio.Package.DocumentTask> nesnesi oluşturursunuz. Bu nesneyi döndürmeden önce, görüntü dizinini ayarlamak için <xref:Microsoft.VisualStudio.Package.DocumentTask> nesnesindeki <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> özelliğini kullanabilirsiniz. Bu, aşağıdaki örneğe benzer bir şekilde görünür. @No__t_0 tüm simgeleri listeleyen ve bu örneğe özgü bir sabit listesi olduğunu unutmayın. Dil hizmetinizdeki simgeleri tanımlamaya yönelik farklı bir yönteme sahip olabilirsiniz.

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

 Aşağıdaki sabit listesi her bir simge kümesi için tipik adları belirtir ve ilişkili dizini belirtir. Örneğin, sabit listesine bağlı olarak, korumalı bir yöntemin görüntü dizinini `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` olarak belirtebilirsiniz. Bu Numaralandırmadaki adları istediğiniz gibi değiştirebilirsiniz.

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