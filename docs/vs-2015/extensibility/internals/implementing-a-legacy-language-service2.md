---
title: Eski dil Service2 uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1a5f419b3b4c55538e8aa46d5aefb3f7e21369be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192706"
---
# <a name="implementing-a-legacy-language-service"></a>Eski Dil Hizmeti Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yönetilen paket çerçevesi 'ni (MPF) kullanarak bir dil hizmetini uygulamak için, sınıfından bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.LanguageService> ve aşağıdaki soyut yöntemleri ve özellikleri uygulamanız gerekir:  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>Yöntemi  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>Yöntemi  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Yöntemi  
  
- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>Özelliği  
  
  Bu yöntem ve özellikleri uygulamayla ilgili ayrıntılar için aşağıdaki ilgili bölümlere bakın.  
  
  Ek özellikleri desteklemek için dil hizmetinizin MPF dil hizmeti sınıflarından birindeki bir sınıfı türetmeniz gerekebilir; Örneğin, ek menü komutlarını desteklemek için, sınıfından bir sınıf türetmeniz <xref:Microsoft.VisualStudio.Package.ViewFilter> ve komut işleme yöntemlerinin birkaçını geçersiz kılmanız gerekir ( <xref:Microsoft.VisualStudio.Package.ViewFilter> Ayrıntılar için bkz.). <xref:Microsoft.VisualStudio.Package.LanguageService>Sınıfı, çeşitli sınıfların yeni örneklerini oluşturmak için çağrılan ve sınıfınızın bir örneğini sağlamak için uygun oluşturma yöntemini geçersiz kıldığınız birkaç yöntem sağlar. Örneğin, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> kendi sınıfınızın bir örneğini döndürmek için sınıfındaki yöntemini geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Package.ViewFilter> . Daha fazla ayrıntı için "özel sınıflar örneği oluşturma" bölümüne bakın.  
  
  Dil hizmetiniz, birçok yerde kullanılan kendi simgelerini de sağlayabilir. Örneğin, bir IntelliSense tamamlanma listesi gösterildiğinde, listedeki her öğe kendisiyle ilişkili bir simgeye sahip olabilir, öğe bir yöntem, sınıf, ad alanı, özellik veya diliniz için gerekli herhangi bir şey olarak işaretleniyor. Bu simgeler tüm IntelliSense listelerinde, **Gezinti çubuğunda**ve **hata listesi** görev penceresinde kullanılır. Ayrıntılar için aşağıdaki "dil hizmeti görüntüleri" bölümüne bakın.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences Yöntemi  
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>Yöntemi her zaman bir sınıfın örneğini döndürür <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . <xref:Microsoft.VisualStudio.Package.LanguagePreferences>Dil hizmetiniz için ek bir tercihlerinize gerek yoksa, temel sınıfı kullanabilirsiniz. MPF dil hizmeti sınıfları, en az temel sınıf olduğunu varsayar <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
### <a name="example"></a>Örnek  
 Bu örnek, yönteminin tipik bir uygulamasını gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> . Bu örnek, temel <xref:Microsoft.VisualStudio.Package.LanguagePreferences> sınıfını kullanır.  
  
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
 Bu yöntem, <xref:Microsoft.VisualStudio.Package.IScanner> belirteçleri ve bunların türlerini ve tetikleyicilerini elde etmek için kullanılan bir hat odaklı ayrıştırıcısı veya tarayıcıyı uygulayan bir nesnenin örneğini döndürür. <xref:Microsoft.VisualStudio.Package.Colorizer>Tarayıcı, belirteç türlerini ve tetiklerini daha karmaşık bir ayrıştırma işlemine bir ön halde olarak almak için de kullanılabilir olsa da, bu tarayıcı renklendirme sınıfında kullanılır. Arabirimi uygulayan sınıfı sağlamanız gerekir <xref:Microsoft.VisualStudio.Package.IScanner> ve arabirimdeki tüm yöntemleri uygulamalısınız <xref:Microsoft.VisualStudio.Package.IScanner> .  
  
### <a name="example"></a>Örnek  
 Bu örnek, yönteminin tipik bir uygulamasını gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> . `TestScanner`Sınıfı <xref:Microsoft.VisualStudio.Package.IScanner> arabirimini uygular (gösterilmez).  
  
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
 Kaynak dosyayı bir dizi farklı nedenden göre ayrıştırır. Bu yönteme, belirli bir <xref:Microsoft.VisualStudio.Package.ParseRequest> ayrıştırma işleminden nelerin beklendiklerin açıklandığı bir nesne verilir. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Yöntemi, belirteç işlevselliğini ve kapsamını belirleyen daha karmaşık bir Ayrıştırıcı çağırır. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Yöntemi, IntelliSense işlemlerine yönelik desteğin yanı sıra parantez eşleştirme için de kullanılır. Bu gibi gelişmiş işlemleri desteklemeseniz bile, yine de geçerli bir <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesne döndürmelidir ve <xref:Microsoft.VisualStudio.Package.AuthoringScope> arabirimi uygulayan ve bu arabirimdeki tüm yöntemleri uygulayan bir sınıf oluşturmanız gerekir. Tüm yöntemlerin null değerlerini döndürebilirsiniz, ancak <xref:Microsoft.VisualStudio.Package.AuthoringScope> nesnenin kendisi bir null değer olmamalıdır.  
  
### <a name="example"></a>Örnek  
 Bu örnek, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> dil hizmetinin daha gelişmiş özelliklerden herhangi birini desteklemeyerek derlenmesi ve işlevi yapmasına izin vermek için, yönteminin ve sınıfının en az bir uygulamasını gösterir.  
  
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
 Bu özellik, dil hizmetinin adını döndürür. Bu, dil hizmeti kaydedildiğinde verilen ad ile aynı olmalıdır. Bu ad, bir dizi yerde kullanılır, en belirgin bir deyişle, <xref:Microsoft.VisualStudio.Package.LanguagePreferences> kayıt defterine erişmek için adının kullanıldığı sınıftır. Kayıt defteri girdisi ve anahtar adları için kayıt defterinde kullanıldığından, bu özellik tarafından döndürülen ad yerelleştirilemez olmalıdır.  
  
### <a name="example"></a>Örnek  
 Bu örnek, özelliğinin olası bir uygulamasını gösterir <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> . Buradaki adın sabit kodlanmış olduğunu unutmayın: bir kaynak dosyasından gerçek adın alınması gerekir, böylece bir dil hizmeti kaydı için kullanılabilir (bkz. [eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
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
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Yapının özelleştirmesini desteklemek için <xref:Microsoft.VisualStudio.Package.ParseRequest> (Bu yöntem genellikle geçersiz kılınmaz).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Kaynak kodu biçimlendirmeyi desteklemek, açıklama karakterlerini belirtmek ve Yöntem imzalarını özelleştirmek için.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Ek menü komutlarını desteklemek için.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Söz dizimi vurgulamasını desteklemek için (Bu yöntem genellikle geçersiz kılınmaz).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Dil tercihlerine erişimi desteklemek için. Bu yöntem uygulanmalıdır, ancak temel sınıfın bir örneğini döndürebilir.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Bir satırdaki belirteçlerin türlerini tanımlamak için kullanılan bir Ayrıştırıcı sağlamak için. Bu yöntem uygulanmalıdır ve <xref:Microsoft.VisualStudio.Package.IScanner> öğesinden türetilmelidir.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Tüm kaynak dosya genelinde işlevselliği ve kapsamı tanımlamak için kullanılan bir Ayrıştırıcı sağlamak için. Bu yöntem uygulanmalıdır ve sınıf sürümünüzün bir örneğini döndürmelidir <xref:Microsoft.VisualStudio.Package.AuthoringScope> . ' I desteklemek istiyorsanız, söz dizimi vurgulaması varsa (Bu, <xref:Microsoft.VisualStudio.Package.IScanner> yöntemden döndürülen ayrıştırıcı gerektirir <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> ), bu yöntemde, <xref:Microsoft.VisualStudio.Package.AuthoringScope> yöntemlerinin hepsi null değer döndüren sınıfın bir sürümünü döndürenden başka hiçbir şey yapabilirsiniz.|  
  
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
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Üyeler veya türler gibi bildirimlerin bir listesini sağlar. Bu yöntemin uygulanması gerekir, ancak null bir değer döndürebilir. Bu yöntem geçerli bir nesne döndürürse, nesne sınıfının sürümünün bir örneği olmalıdır <xref:Microsoft.VisualStudio.Package.Declarations> .|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Belirli bir bağlam için yöntem imzalarının bir listesini sağlar. Bu yöntemin uygulanması gerekir, ancak null bir değer döndürebilir. Bu yöntem geçerli bir nesne döndürürse, nesne sınıfının sürümünün bir örneği olmalıdır <xref:Microsoft.VisualStudio.Package.Methods> .|  
  
## <a name="language-service-images"></a>Dil hizmeti görüntüleri  
 Dil hizmeti genelinde kullanılacak simgelerin bir listesini sağlamak için, <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> sınıfındaki yöntemini geçersiz kılın <xref:Microsoft.VisualStudio.Package.LanguageService> ve <xref:System.Windows.Forms.ImageList> simgeleri içeren bir simge döndürün. Temel <xref:Microsoft.VisualStudio.Package.LanguageService> sınıf varsayılan bir simge kümesi yükler. Bu konumlarda simge gerektiren tam görüntü dizinini belirttiğinizden, kendi görüntü listenizi düzenleme işlemi tamamen size aittir.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>IntelliSense tamamlanma listelerinde kullanılan görüntüler  
 IntelliSense tamamlanma listeleri için görüntü dizini, sınıf yöntemindeki her öğe için belirtilir <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> , bu da bir görüntü dizini sağlamak istiyorsanız geçersiz kılmanız gerekir. Yönteminden döndürülen değer, <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> sınıf oluşturucusuna sağlanan görüntü listesinin bir dizinidir <xref:Microsoft.VisualStudio.Package.CompletionSet> ve sınıftaki yöntemden döndürülen aynı görüntü listesidir <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> ( <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> <xref:Microsoft.VisualStudio.Package.Source> farklı bir görüntü listesi sağlamak için sınıfında yöntemini geçersiz kılarsınız, için kullanılacak görüntü listesini değiştirebilirsiniz).  
  
### <a name="images-used-in-the-navigation-bar"></a>Gezinti çubuğunda kullanılan görüntüler  
 **Gezinti çubuğu** , türlerin ve üyelerin listelerini görüntüler ve hızlı gezinme için kullanılan simgeleri gösterebilir. Bu simgeler, <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> sınıfındaki yönteminden alınır <xref:Microsoft.VisualStudio.Package.LanguageService> ve özellikle **Gezinti çubuğu**için geçersiz kılınamaz. Birleşik giriş kutularındaki her öğe için kullanılan dizinler, Birleşik giriş kutularını temsil eden listeler, sınıfındaki yönteminde doldurulduğu zaman belirtilir <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (bkz. [eski dil hizmetindeki gezinti çubuğu için destek](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Bu görüntü dizinleri, genellikle kendi sınıfınızın sürümü aracılığıyla Ayrıştırıcıdan bir şekilde alınır <xref:Microsoft.VisualStudio.Package.Declarations> . Dizinler nasıl alınır?  
  
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
            TastPriority      priority,  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski dil hizmeti uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Eski dil hizmetine genel bakış](../../extensibility/internals/legacy-language-service-overview.md)   
 [Eski dil hizmetini kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
