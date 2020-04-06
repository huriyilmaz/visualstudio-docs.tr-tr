---
title: Eski Dil Hizmetinin Uygulanması2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707672"
---
# <a name="implementing-a-legacy-language-service"></a>Eski Dil Hizmeti Uygulama
Yönetilen paket çerçevesini (MPF) kullanarak bir dil hizmeti uygulamak <xref:Microsoft.VisualStudio.Package.LanguageService> için, sınıftan bir sınıf türetmeniz ve aşağıdaki soyut yöntemleri ve özellikleri uygulamanız gerekir:

- Yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Özellik <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Bu yöntem ve özellikleriuygulama hakkında ayrıntılar için aşağıdaki uygun bölümlere bakın.

  Ek özellikleri desteklemek için, dil hizmetinizin MPF dil hizmeti sınıflarından birinden bir sınıf türetmesi gerekebilir; örneğin, ek menü komutlarını desteklemek için <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıftan bir sınıf türetmeniz ve komut işleme <xref:Microsoft.VisualStudio.Package.ViewFilter> yöntemlerinden birkaçını geçersiz kılmanız gerekir (ayrıntılar için bkz. Sınıf, <xref:Microsoft.VisualStudio.Package.LanguageService> çeşitli sınıfların yeni örnekleri oluşturmak için çağrılan bir dizi yöntem sağlar ve sınıfınızın bir örneğini sağlamak için uygun oluşturma yöntemini geçersiz kılarsınız. Örneğin, kendi <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> <xref:Microsoft.VisualStudio.Package.ViewFilter> sınıfınızdan bir örneği <xref:Microsoft.VisualStudio.Package.LanguageService> döndürmek için sınıftaki yöntemi geçersiz kılmanız gerekir. Daha fazla bilgi için "Özel Sınıfları Anında Alma" bölümüne bakın.

  Dil hizmetiniz, birçok yerde kullanılan kendi simgelerini de sağlayabilir. Örneğin, bir IntelliSense tamamlama listesi gösterildiğinde, listedeki her öğenin bir simgesi olabilir ve bu simge, öğeyi yöntem, sınıf, ad alanı, özellik veya diliniz için ne gerekiyorsa olarak işaretleyebilir. Bu simgeler tüm IntelliSense listelerinde, **Gezinti çubuğunda**ve **Hata Listesi** görev penceresinde kullanılır. Ayrıntılar için aşağıdaki "Dil Hizmeti Resimleri" bölümüne bakın.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences Yöntemi
 Yöntem <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> her zaman aynı <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıf örneğini döndürür. Dil hizmetiniz <xref:Microsoft.VisualStudio.Package.LanguagePreferences> için ek tercihe ihtiyacınız yoksa taban sınıfını kullanabilirsiniz. MPF dil hizmeti sınıfları en az <xref:Microsoft.VisualStudio.Package.LanguagePreferences> taban sınıfın varlığını varsayar.

### <a name="example"></a>Örnek
 Bu örnek, yöntemin <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> tipik bir uygulamasını gösterir. Bu örnek, <xref:Microsoft.VisualStudio.Package.LanguagePreferences> taban sınıfı kullanır.

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
 Bu yöntem, belirteçleri ve türleri ve tetikleyicileri elde etmek için kullanılan satır yönelimli parer veya tarayıcı uygulayan bir <xref:Microsoft.VisualStudio.Package.IScanner> nesnenin bir örneği döndürür. Tarayıcı da belirteç türleri almak için kullanılabilir ve daha karmaşık bir ayrıştırma işlemi için bir prelüd olarak tetikler rağmen bu tarayıcı renklendirme için <xref:Microsoft.VisualStudio.Package.Colorizer> sınıfta kullanılır. <xref:Microsoft.VisualStudio.Package.IScanner> Arabirimi uygulayan sınıfı sağlamanız ve <xref:Microsoft.VisualStudio.Package.IScanner> arabirimdeki tüm yöntemleri uygulamanız gerekir.

### <a name="example"></a>Örnek
 Bu örnek, yöntemin <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> tipik bir uygulamasını gösterir. Sınıf `TestScanner` <xref:Microsoft.VisualStudio.Package.IScanner> arabirimi uygular (gösterilmez).

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
 Kaynak dosyayı çeşitli nedenlerle parses. Bu yöntem, <xref:Microsoft.VisualStudio.Package.ParseRequest> belirli bir ayrıştırma işleminden beklenenleri açıklayan bir nesne verilir. Yöntem, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> belirteç işlevselliğini ve kapsamını belirleyen daha karmaşık bir ayrıştırıcı çağırır. Yöntem, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> IntelliSense işlemlerinin yanı sıra ayraç eşleştirmesini desteklemek için de kullanılır. Bu tür gelişmiş işlemleri desteklemeseniz bile, yine <xref:Microsoft.VisualStudio.Package.AuthoringScope> de geçerli bir nesne döndürmeniz gerekir <xref:Microsoft.VisualStudio.Package.AuthoringScope> ve bu da arabirimi uygulayan bir sınıf oluşturmanızı ve bu arabirimdeki tüm yöntemleri uygulamanızı gerektirir. Tüm yöntemlerden null değerleri döndürebilirsiniz, ancak nesnenin <xref:Microsoft.VisualStudio.Package.AuthoringScope> kendisi null değeri olmamalıdır.

### <a name="example"></a>Örnek
 Bu örnek, dil hizmetinin <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> daha <xref:Microsoft.VisualStudio.Package.AuthoringScope> gelişmiş özelliklerden herhangi birini desteklemeden derlemesine ve çalışmasına izin vermek için yeterli olan yöntemin ve sınıfın en az uygulamasını gösterir.

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
 Bu özellik, dil hizmetinin adını döndürür. Bu, dil hizmeti kaydedildiğinde verilen adla aynı olmalıdır. Bu ad, en belirgin olan, kayıt defterine <xref:Microsoft.VisualStudio.Package.LanguagePreferences> erişmek için adın kullanıldığı sınıf olan birkaç yerde kullanılır. Kayıt defterinde kayıt defterinde ve anahtar adlarında kullanıldığından, bu özellik tarafından döndürülen ad yerelleştirilmemelidir.

### <a name="example"></a>Örnek
 Bu örnek, özelliğin <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> olası bir uygulamasını gösterir. Buradaki adın sabit kodlanmış olduğunu unutmayın: bir dil hizmetinin kaydedilmesinde kullanılabilmesi için gerçek ad bir kaynak dosyasından alınmalıdır (bkz. [Eski Dil Hizmeti Kaydolma).](../../extensibility/internals/registering-a-legacy-language-service1.md)

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

## <a name="instantiating-custom-classes"></a>Özel Sınıfları Anında
 Belirtilen sınıflarda aşağıdaki yöntemler, her sınıfın kendi sürümleriörnekleri sağlamak için geçersiz kılınabilir.

### <a name="in-the-languageservice-class"></a>DilHizmet Sınıfında

|Yöntem|Sınıf İade|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Metin görünümüne özel eklemeleri desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Özel belge özelliklerini desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|**Gezinti çubuğunu**desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Kod parçacıkları şablonlarında işlevleri desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Kod parçacıklarını desteklemek için (bu yöntem genellikle geçersiz kılınmadı).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Yapının <xref:Microsoft.VisualStudio.Package.ParseRequest> özelleştirmesini desteklemek için (bu yöntem genellikle geçersiz kılınmadı).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Kaynak kodu biçimlendirmeyi, yorum karakterlerini belirtmeyi ve yöntem imzalarını özelleştirmeyi desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Ek menü komutlarını desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Sözdizimi vurgulamayı desteklemek için (bu yöntem genellikle geçersiz kılınmadı).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Dil tercihlerine erişimi desteklemek için. Bu yöntem uygulanmalıdır, ancak taban sınıfın bir örneğini döndürebilir.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Bir satırdaki belirteç türlerini tanımlamak için kullanılan bir araç. Bu yöntem uygulanmalı <xref:Microsoft.VisualStudio.Package.IScanner> ve türetilmelidir.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Tüm kaynak dosyası boyunca işlevselliği ve kapsamı tanımlamak için kullanılan bir araç ışığı sağlamak için. Bu yöntem uygulanmalıdır ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> sınıfın sürümünün bir örneğini döndürmelidir. Desteklemek istediğiniz tek şey sözdizimi vurgulamaysa <xref:Microsoft.VisualStudio.Package.IScanner> (bu yöntemden <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> döndürülen parleyici gerektirir), bu yöntemde yöntemleri <xref:Microsoft.VisualStudio.Package.AuthoringScope> tüm null değerlerini döndüren sınıfın bir sürümünü döndürmek dışında hiçbir şey yapamazsınız.|

### <a name="in-the-source-class"></a>Kaynak Sınıfta

|Yöntem|Sınıf İade|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|IntelliSense tamamlama listelerinin ekranını özelleştirmek için (bu yöntem genellikle geçersiz kılınmaz).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Hata Listesi görev listesindeki işaretçileri desteklemek için; özellikle, dosyayı açmanın ve hataya neden olan satıra atlamanın ötesindeki özellikler için destek.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|IntelliSense Parametre Bilgi ToolTips ekran özelleştirme için.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Yorum kodunu desteklemek için.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Ayrışdırış işlemi sırasında bilgi toplamak için.|

### <a name="in-the-authoringscope-class"></a>AuthoringScope Sınıfında

|Yöntem|Sınıf İade|Açıklama|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Üyeler veya türler gibi bildirimlerin bir listesini sağlar. Bu yöntem uygulanmalıdır, ancak null bir değer döndürebilir. Bu yöntem geçerli bir nesne döndürürse, nesne <xref:Microsoft.VisualStudio.Package.Declarations> sınıfın sürümünüzün bir örneği olmalıdır.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Belirli bir bağlam için yöntem imzalarının listesini sağlar. Bu yöntem uygulanmalıdır, ancak null bir değer döndürebilir. Bu yöntem geçerli bir nesne döndürürse, nesne <xref:Microsoft.VisualStudio.Package.Methods> sınıfın sürümünüzün bir örneği olmalıdır.|

## <a name="language-service-images"></a>Dil Hizmeti Resimleri
 Dil hizmeti boyunca kullanılacak simgelerin listesini sağlamak <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> için, sınıftaki yöntemi geçersiz kılın <xref:System.Windows.Forms.ImageList> ve simgeleri içeren bir simge döndürün. Taban <xref:Microsoft.VisualStudio.Package.LanguageService> sınıf varsayılan bir simge kümesi yükler. Simgelere ihtiyaç duyan yerlerde tam görüntü dizini belirttiğinizden, kendi resim listenizi nasıl düzenleyebilirsiniz tamamen size aittir.

### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense Tamamlama Listelerinde Kullanılan Görseller
 IntelliSense tamamlama listeleri için, görüntü dizini, <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> bir görüntü <xref:Microsoft.VisualStudio.Package.Declarations> dizini sağlamak istiyorsanız geçersiz kılmanız gereken sınıfın yöntemindeki her öğe için görüntü dizini belirtilir. <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> Yöntemden döndürülen değer, <xref:Microsoft.VisualStudio.Package.CompletionSet> sınıf oluşturucuya verilen görüntü listesine bir dizindir ve <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıftaki yöntemden döndürülen aynı görüntü listesidir <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.Source> (farklı bir <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> görüntü listesi sağlamak için sınıftaki yöntemi geçersiz kılarsanız hangi resim listesini kullanacağınızı değiştirebilirsiniz).

### <a name="images-used-in-the-navigation-bar"></a>Gezinti Çubuğunda Kullanılan Görüntüler
 **Gezinti çubuğu** türlerin ve üyelerin listelerini görüntüler ve hızlı gezinme için kullanılan simgeleri gösterebilir. Bu simgeler sınıftaki <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> yöntemden elde edilir ve **gezinti çubuğu**için özel olarak geçersiz kılınmaz. Açılan kutulardaki her öğe için kullanılan endeksler, açılan kutuları temsil eden listeler <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> sınıftaki yöntemde doldurulduğunda belirtilir (bkz. Eski Dil [Hizmetinde Gezinti Çubuğu Desteği).](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) Bu görüntü endeksleri bir şekilde ayrıştırıcıdan, genellikle <xref:Microsoft.VisualStudio.Package.Declarations> sınıfın sizin sürümünüzden elde edilir. Endekslerin nasıl elde edilir tamamen size kalmış.

### <a name="images-used-in-the-error-list-task-window"></a>Hata Listesi Görev Penceresinde Kullanılan Görüntüler
 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Yöntem arayıcı [(bkz. Eski Dil Hizmeti Parser ve Scanner)](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)bir <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> hatayla <xref:Microsoft.VisualStudio.Package.AuthoringSink> karşılaştığında ve bu hatayı sınıftaki yönteme ilettiğinde, hata **Hata Listesi** görev penceresinde bildirilir. Bir simge, görev penceresinde görünen her öğeyle ilişkilendirilebilir ve bu simge <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> sınıftaki yöntemden döndürülen aynı resim listesinden gelir. MPF sınıflarının varsayılan davranışı hata iletisi ile bir görüntü göstermemektir. Ancak, <xref:Microsoft.VisualStudio.Package.Source> sınıftan bir sınıf türeterek ve <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> yöntemi geçersiz kılarak bu davranışı geçersiz kılabilirsiniz. Bu yöntemde, yeni <xref:Microsoft.VisualStudio.Package.DocumentTask> bir nesne oluşturursunuz. Bu nesneyi döndürmeden önce, <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> görüntü <xref:Microsoft.VisualStudio.Package.DocumentTask> dizini ayarlamak için nesneüzerindeki özelliği kullanabilirsiniz. Bu aşağıdaki örnek gibi bir şey görünür. Tüm `TestIconImageIndex` simgeleri listeleyen ve bu örneğe özgü bir numaralandırma olduğunu unutmayın. Dil hizmetinizde simgeleri tanımlamanın farklı bir yolu olabilir.

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

## <a name="the-default-image-list-for-a-language-service"></a>Dil Hizmeti için Varsayılan Resim Listesi
 Temel MPF dil hizmeti sınıflarıyla birlikte verilen varsayılan resim listesi, daha yaygın dil öğeleriyle ilişkili bir dizi simge içerir. Bu simgelerin büyük kısmı, genel, dahili, arkadaş, korumalı, özel ve kısayol erişim kavramlarına karşılık gelen altı varyasyondan oluşan kümeler halinde düzenlenir. Örneğin, bir yöntemin ortak, korumalı veya özel olmasına bağlı olarak farklı simgelere sahip olabilirsiniz.

 Aşağıdaki numaralandırma, her simge kümesi için tipik adları belirtir ve ilişkili dizini belirtir. Örneğin, numaralandırmaya bağlı olarak, korumalı bir yöntem için görüntü `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`dizini ' ni . Bu numaralandırmadaki adları istediğiniz gibi değiştirebilirsiniz.

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
