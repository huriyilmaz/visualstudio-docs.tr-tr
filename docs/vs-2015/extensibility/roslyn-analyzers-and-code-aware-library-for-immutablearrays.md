---
title: ImmutableArrays için Roslyn Analizörler ve Kod-aware Kütüphane | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444915"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>ImmutableArray’ler için Roslyn Çözümleyicileri ve Kod Algılayan Kitaplık
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[.NET Derleyici Platformu](https://github.com/dotnet/roslyn) ("Roslyn"), kod alabilen kitaplıklar oluşturmanıza yardımcı olur. Kod alabilen kitaplık, kitaplığı en iyi şekilde kullanmanıza veya hataları önlemenize yardımcı olmak için kullanabileceğiniz işlevsellik ve takım (Roslyn çözümleyicileri) sağlar. Bu konu, [NIB: Değişmez Koleksiyonlar](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet paketini kullanırken sık karşılaşılan hataları yakalamak için gerçek bir Roslyn çözümleyicisinin nasıl oluşturabileceğinizi gösterir. Örnek, çözümleyici tarafından bulunan bir kod sorunu için kod düzeltmesinin nasıl sağverilebildiğini de gösterir. Kullanıcılar Visual Studio ampul UI'de kod düzeltmeleri görür ler ve kod için otomatik olarak düzeltme uygulayabilirler.

## <a name="getting-started"></a>Başlarken
Bu örneği oluşturmak için aşağıdakilere ihtiyacınız var:

- Visual Studio 2015 (Express Edition değil) veya daha sonraki bir sürüm. Ücretsiz [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs) kullanabilirsiniz

- [Görsel Stüdyo SDK](../extensibility/visual-studio-sdk.md). Ayrıca, Visual Studio'yu yüklerken, SDK'yı aynı anda yüklemek için Ortak Araçlar altında Visual Studio Genişletilebilirlik Araçlarını da kontrol edebilirsiniz. Visual Studio'yu zaten yüklediyseniz, bu SDK'yı, **Yeni &#124;Projesi &#124;** ana menüye giderek de yükleyebilirsiniz... sol navigasyon bölmesinde C# seçerek ve ardından Genişletilebilirliği seçerek. "**Visual Studio Genişletilebilirlik Araçlarını Yükle**" kırıntısı proje şablonunu seçtiğinizde, SDK'yı indirmenizi ve yüklemenizi ister.

- [.NET Derleyici Platformu ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Ayrıca yeni **&#124; Projesi &#124;** ana menü Dosya giderek bu SDK yükleyebilirsiniz ... , sol navigasyon bölmesinde C **#** seçerek, ve sonra **Genişletilebilirlik**seçerek . "**.NET Derleyici Platformu SDK'yı indirin**" kırıntı sıyrık proje şablonunu seçtiğinizde, SDK'yı indirip yüklemenizi ister. Bu SDK [Roslyn Sözdizimi Görselleştirici](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)içerir. Bu son derece kullanışlı araç, çözümleyicinizde hangi kod modeli türlerini aramanız gerektiğini anlamanıza yardımcı olur. Çözümleyici altyapısı belirli kod modeli türleri için kodunuza çağrı yapar, bu nedenle kodunuz yalnızca gerektiğinde yürütür ve yalnızca ilgili kodu çözümlemeye odaklanabilir.

## <a name="whats-the-problem"></a>Sorun nedir?
ImmutableArray (örneğin, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) desteği ile bir kitaplık sağladığınızı düşünün. C# geliştiricileri .NET dizileri ile ilgili çok fazla deneyime sahiptir. Ancak, ImmutableArrays ve uygulamada kullanılan optimizasyon teknikleri doğası nedeniyle, C# geliştirici sezgileri kitaplığınızı kullanıcıları nın aşağıda açıklandığı gibi bozuk kod yazmak için neden olur. Ayrıca, kullanıcılar .NET ile Visual Studio'da alışık oldukları kalite deneyimi olmayan çalışma süresine kadar hatalarını görmezler.

Kullanıcılar aşağıdaki gibi kod yazmaya aşinadır:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Sonraki kod satırlarıyla doldurmak için boş diziler oluşturmak ve koleksiyon başharfi sözdizimini kullanmak C# geliştiricileri için çok tanıdık. Ancak, çalışma zamanında bir DeğişmezDizi çöküyor için aynı kodu yazma:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

İlk hata, ImmutableArray uygulamasının altta yatan veri depolamasını sarmak için bir yapı kullanmasıdır. İfadelerin tüm sıfır veya null üyeleri ile `default(T)` yapıları döndürebilmek için yapıları parametresiz oluşturucular olmalıdır. Kod erişildiğinde, `b1.Length`ImmutableArray struct'ta altta yatan depolama dizisi olmadığından, bir çalışma süresi null dereference hatası vardır. Boş bir Değişmez Dizi oluşturmak için `ImmutableArray<int>.Empty`doğru yolu.

 ImmutableArray.Add yöntemi her çağrıda yeni örnekleri döndürür çünkü toplama başlatılması ile hata olur. Değişmez Diziler hiçbir zaman değişmediği için, yeni bir öğe eklediğinizde, yeni bir DeğişmezDizi nesnesini geri alırsınız (daha önce varolan bir ImmutableArray ile performans nedenleriyle depolama alanını paylaşabilir). Beş `b2` kez aramadan `Add()` önce ilk ImmutableArray noktaları, varsayılan ImmutableArray `b2` olduğundan. Üzerinde Arama Uzunluğu da null dereference hatası ile çöker. El ile Add'i aramadan Bir ImmutableArray'i `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`başlatmanın doğru yolu.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Çözümleyicinizi Tetiklemek Için İlgili Sözdizimi Düğümü Türlerini Bulma
Çözümleyiciyi oluşturmaya başlamak için, önce ne tür bir Sözdizimi aramanız gerektiğini öğrenin.   Sözdizimi Görselleştiricisini Diğer **Windows &#124; &#124;** Görünüm menüsünden başlatın.

Editörün caret'ini bildiren satıra `b1`yerleştirin. Sözdizimi Görselleştiricisinin sözdizimi ağacının `LocalDeclarationStatement` düğümünde olduğunuzu gösterdiğini görürsünüz. Bu düğüm bir `VariableDeclaration`vardır , sırayla bir `VariableDeclarator`vardır `EqualsValueClause`, hangi sırayla `ObjectCreationExpression`bir vardır , ve nihayet bir . Düğümlerin Sözdizimi Görselleştiricisi ağacını tıklattığınızda, düzenleyici penceresindeki sözdizimi, bu düğümün temsil ettiği kodu göstermek için vurgular. SözdizimiNode alt türlerinin adları C# dilbilgisinde kullanılan adlarıyla eşleşir.

## <a name="creating-the-analyzer-project"></a>Çözümleyici Projesi Oluşturma
Ana menüden **Yeni &#124; Projesi &#124; Dosya**seçin ... . Yeni **Proje** iletişim kutusunda, sol gezinti çubuğundaki **C#** projeleri altında Genişletilebilirliği seçin ve sağ bölmede Kod Düzeltme proje şablonuna **sahip Çözümleyici'yi** seçin. Bir ad girin ve iletişim kutusunu onaylayın.

Şablon bir DiagnosticAnalyzer.cs dosyasını açar. Bu düzenleyici arabellek sekmesini seçin. Bu dosyada (Roslyn API türünden) türeyen bir `DiagnosticAnalyzer` çözümleyici sınıfı (projeyi vermiş olduğunuz addan oluşturulmuş) vardır. Yeni sınıfınızda `DiagnosticAnalyzerAttribute` çözümleyicinizin C# diliyle alakalı olduğu belirtilir, böylece derleyici çözümleyicinizi keşfeder ve yükler.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Visual Basic kullanarak C# kodunu hedefleyen bir çözümleyici uygulayabilirsiniz ve bunun tersi de olabilir. AnalyzerAttribute'da çözümleyicinizin bir dili mi yoksa her ikisini birden mi hedeflediğini seçmek daha önemlidir. Dilin ayrıntılı modellemesini gerektiren daha gelişmiş çözümleyiciler yalnızca tek bir dili hedefleyebilir. Örneğin çözümleyiciniz yalnızca tür adlarını veya ortak üye adlarını denetlerse, Visual Basic ve C# genelinde Roslyn'in sunduğu ortak dil modelini kullanmak mümkün olabilir. Örneğin, FxCop bir sınıfın uyguladığı <xref:System.Runtime.Serialization.ISerializable>, ancak sınıfın dilden bağımsız özniteliği olmadığı <xref:System.SerializableAttribute> ve hem Visual Basic hem de C# kodu için çalıştığı konusunda uyarır.

## <a name="initalizing-the-analyzer"></a>Çözümleyicinin Initalizing
Yöntemi görmek için `DiagnosticAnalyzer` sınıfta biraz `Initialize` aşağı kaydırın. Derleyici, bir çözümleyiciyi etkinleştirirken bu yöntemi çağırır. Yöntem, çözümleyicinizin bağlam bilgilerine ulaşmasını ve çözümlemek istediğiniz kod türlerine yönelik olaylar için geri aramaları kaydetmesini sağlayan bir `AnalysisContext` nesne alır.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Bu yöntemde yeni bir satır açın ve "bağlam" yazın. Intellisense tamamlama listesini görmek için. Tamamlama listesinde çeşitli olayları işlemek `Register…` için birçok yöntem olduğunu görebilirsiniz. Örneğin, ilki, `RegisterCodeBlockAction`genellikle kıvırcık ayraçlar arasında kod olan bir blok için kodunuzu geri çağırır. Bir blok için kaydolmak, bir alanın baş harflerini, özniteliğe verilen değeri veya isteğe bağlı bir parametrenin değeri için kodunuza geri çağırır.

Başka bir `RegisterCompilationStartAction`örnek olarak, derlemenin başlangıcında kodunuza geri çağrıda bulunur ve bu da birçok konum üzerinde durum toplamanız gerektiğinde yararlıdır. Kullanılan tüm simgeleri toplamak için bir veri yapısı oluşturabilirsiniz ve çözümleyiciniz bazı sözdizimi veya sembol için her çağrıldığınızda, veri yapınızdaki her konum la ilgili bilgileri kaydedebilirsiniz. Derleme bitişi nedeniyle geri çağrıldığınızda, kaydettiğiniz tüm konumları çözümleyebilir, örneğin, kodun her `using` ekstreden hangi sembolleri kullandığını bildirebilirsiniz.

**Sözdizimi Görselleştiricisi'ni**kullanarak, derleyici objectcreationexpression'yı işlerken çağrılmak istediğinizi öğrendiniz. Geri aramayı ayarlamak için bu kodu kullanırsınız:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Sözdizimi düğümü için kaydolur ve yalnızca nesne oluşturma sözdizimi düğümleri için filtre. Kural olarak, çözümleyici yazarlar analizörler için vatansız tutmak için yardımcı olan eylemleri kaydederken bir lambda kullanırlar. Yöntemi oluşturmak için Visual Studio'nun **Kullanımdan Oluştur** özelliğini `AnalyzeObjectCreation` kullanabilirsiniz. Bu sizin için de doğru türbağlam parametresi oluşturur.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Çözümleyicinizin Kullanıcıları için Özellikleri Ayarlama
Analyzer'ınızın Visual Studio UI'da uygun bir şekilde görünmesi için çözümleyicinizi tanımlamak için aşağıdaki kod satırını arayın ve değiştirin:

```csharp
internal const string Category = "Naming";
```

'ye `"API Guidance"`değiştirin. `"Naming"`

Sonraki bul ve **Çözüm Gezgini**kullanarak projenizdeki Resources.resx dosyasını açın. Analyzer, başlık, vb için bir açıklama koyabilirsiniz Şimdilik tüm bunların `“Don’t use ImmutableArray<T> constructor”` değerini değiştirebilirsiniz. Dizenizde dize biçimlendirme bağımsız{0} {1}değişkenleri (, , vb.) koyabilirsiniz ve daha sonra aradığınızda, `Diagnostic.Create()`geçirilecek bir param dizi bağımsız değişkeni sağlayabilirsiniz.

## <a name="analyzing-an-object-creation-expression"></a>Nesne Oluşturma İfadesi Çözümleme
Yöntem, `AnalyzeObjectCreation` kod çözümleyicisi çerçevesi tarafından sağlanan farklı bir bağlam türünü alır. Initialize yöntemi, `AnalysisContext` çözümleyicinizi kurmak için eylem geri aramalarını kaydetmenize olanak tanır. Örneğin, `SyntaxNodeAnalysisContext`etrafında geçirebilirsiniz `CancellationToken` bir vardır. Bir kullanıcı düzenleyicide yazmaya başlarsa, Roslyn işi kaydetmek ve performansı artırmak için çözümleyicileri çalıştırmayı iptal eder. Başka bir örnek olarak, bu bağlamda nesne oluşturma sözdizimi düğümü döndüren bir Düğüm özelliği vardır.

Sözdizimi düğümü eylemini filtrelediğiniz tür olduğunu varsayabileceğiniz düğümü alın:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Analyzer'ınızla Visual Studio'yu İlk Kez Başlatmak
Analizörünüzü oluşturarak ve çalıştırarak Visual Studio'yı başlatın **(F5 tuşuna**basın). **Solution Explorer'daki** başlangıç projesi VSIX projesi olduğundan, kodunuzu çalıştırarak kodunuzu ve VSIX'i oluşturur ve ardından Bu VSIX yüklü Visual Studio'yu başlatır. Visual Studio'u bu şekilde başlattığınızda, visual studio'nun ana kullanımının analizörler inşa ederken test örneklerinizden etkilenmemesi için ayrı bir kayıt defteri kovanı ile başlatılır. Bu şekilde ilk başlattığınızda, Visual Studio, Visual Studio'yu yükledikten sonra ilk kez başlattığınızdakine benzer birkaç başlatma yapar.

 Bir konsol projesi oluşturun ve ardından dizi kodunu konsol uygulamalarınıza girin Ana yöntem:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Değişmez NuGet `ImmutableArray` paketini almanız ve kodunuza bir `using` ifade eklemeniz gerektiğinden, kod satırları nın dalgalı çizgileri vardır. **Çözüm Gezgini'ndeki** proje düğümünde sağ işaretçi düğmesine basın ve **NuGet Paketlerini Yönet'i seçin...**. NuGet yöneticisinde, arama kutusuna "Değişmez" yazın ve sol bölmede "System.Collections.Immutable" ("Microsoft.Bcl.Immutable") öğesini seçin ve sağ bölmedeki Yükle düğmesine basın. Paketi yüklemek, proje referanslarınıza bir başvuru ekler.

Hala altında `ImmutableArray`kırmızı squiggles görmek , bu yüzden bu tanımlayıcı ve **CTRL +** tuşuna caret yerleştirin. (dönem) önerilen düzeltme menüsünü getirmek ve uygun `using` deyimi eklemeyi seçmek için.

**Tümler kaydedin ve** şimdilik Visual Studio'nun ikinci örneğini kapatın ve sizi devam etmek için temiz bir duruma sokun.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Çözümleyiciyi Edit'i Kullanarak Bitirme ve Devam
Visual Studio'nun ilk örneğinde, ilk satırdaki `AnalyzeObjectCreation` özenli **F9** tuşuna basarak yönteminizin başında bir kesme noktası ayarlayın.

Analizcinizi **F5**ile yeniden başlatın ve Visual Studio'nun ikinci örneğinde, son kez oluşturduğunuz konsol uygulamanızı yeniden açın.

Kırılma noktasında Visual Studio'nun ilk örneğine geri dönersiniz, çünkü Roslyn derleyicisi bir Nesne oluşturma ifadesi gördü ve çözümleyicinize çağırdı.

**Nesne oluşturma düğümalın.** **F10**tuşuna `objectCreation` basarak değişkeni ayarlayan çizginin üzerine çıkın `“objectCreation.ToString()”`ve Hemen **Pencere'de** ifadeyi değerlendirin. Değişken noktalarının sözdizimi düğümünün kod `"new ImmutableArray<int>()"`olduğunu görürsünüz, tam da aradığınız koddur.

**DeğişmezArray\<T> Type nesnesini alın.** Oluşturulan türün DeğişmezDizi olup olmadığını denetlemeniz gerekir. İlk olarak, bu türü temsil eden nesneyi alırsınız. Tam olarak doğru türe sahip olduğundan emin olmak için semantik modeli kullanarak türleri denetlersiniz ve ToString() dizesini karşılaştırmazsınız. İşlevin sonuna aşağıdaki kod satırını girin:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Meta verilerde genel türleri tırnak işaretleri (') ve genel parametrelerin sayısıyla belirlersiniz. Bu yüzden görmüyorum "... DeğişmezArray\<T>" meta veri adı.

Anlamsal model semboller, veri akışı, değişken yaşam süresi, vb hakkında sorular sormak izin üzerinde birçok yararlı şeyler vardır. Roslyn sözdizimi düğümlerini çeşitli mühendislik nedenleriyle (performans, hatalı kodu modelleme, vb.) semantik modelden ayırır. Derleme modelinin doğru karşılaştırma için başvurularda yer alan bilgileri aramasını istiyorsunuz.

Düzenleyici penceresinin sol tarafındaki sarı yürütme işaretçisini sürükleyebilirsiniz. `objectCreation` Değişkeni ayarlayan satıra sürükleyin ve **F10**kullanarak yeni kod satırınızın üzerine çıkın. Fare işaretçisini değişkenin `immutableArrayOfType`üzerine bırakırsanız, semantik modelde tam türünü bulduğumuzu görürsünüz.

**Nesne oluşturma ifadesinin türünü alın.** "Türü" bu makalede birkaç şekilde kullanılır, ancak bu "yeni Foo" ifadesi varsa, Foo bir model almak gerekir anlamına gelir. DeğişmezArray\<T> türü olup olmadığını görmek için nesne oluşturma ifadesinin türünü almanız gerekir. Nesne oluşturma ifadesinde tür sembolü (ImmutableArray) için sembol bilgilerini almak için semantik modeli yeniden kullanın. İşlevin sonuna aşağıdaki kod satırını girin:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Çözümleyicinizin düzenleyici arabelleklerinde eksik veya yanlış kodu işlemesi gerektiğinden (örneğin, eksik `using` bir deyim var), `symbolInfo` '. `null` Çözümlemesi tamamlamak için sembol bilgi nesnesinden adlandırılmış bir tür (INamedTypeSymbol) almanız gerekir.

**Türleri karşılaştırın.** Aradığımız açık genel bir T türü olduğundan ve koddaki tür somut bir genel tür olduğundan, simge bilgilerini türün (açık genel tür) oluşturulduğu `immutableArrayOfTType`na göre sorgular sınız ve bu sonucu . Yöntemin sonunda aşağıdakileri girin:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Teşhis'i bildirin.** Teşhisi bildirmek oldukça kolay. İlkbaşlatma yönteminden önce tanımlanan proje şablonunda sizin için oluşturulan Kuralı kullanırsınız. Koddaki bu durum bir hata olduğundan, Kuralı (yeşil dalgalı) ile `DiagnosticSeverity.Warning` `DiagnosticSeverity.Error` (kırmızı dalgalı) değiştirmek için başlattığı satırı değiştirebilirsiniz. Kuralın geri kalanı, gözden geçirme nin başlangıcına yakın düzenlediğiniz kaynaklardan başlar. Ayrıca, nesne oluşturma özelliğinin konumu olan dalgalı geçişin konumunu da bildirmeniz gerekir. Bu kodu bloka `if` girin:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Işleviniz bu gibi görünmelidir (belki farklı biçimlendirilmiş):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

Çözümleyicinizin çalıştığını görebilmeniz için kesme noktasını kaldırın (ve Visual Studio'nun ilk örneğine dönmeyi durdurun). Yürütme işaretçisini yönteminizin başına sürükleyin ve yürütmeye devam etmek için **F5** tuşuna basın. Visual Studio'nun ikinci örneğine geri döndüğünüzde, derleyici kodu yeniden incelemeye başlar ve çözümleyicinize çağırır. Altında bir kıvrım `ImmutableType<int>`görebilirsiniz.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Kod Sorunu için "Kod Düzeltme" ekleme
Başlamadan önce Visual Studio'nun ikinci örneğini kapatın ve Visual Studio'nun ilk örneğinde hata ayıklamayı durdurun (çözümleyiciyi geliştirdiğiniz yer).

**Yeni bir sınıf ekleyin.** Çözüm Gezgini'ndeki proje düğümünüzün kısayol menüsünü (sağ işaretçi düğmesi) kullanın ve yeni bir öğe eklemeyi seçin. 'li bir `BuildCodeFixProvider`sınıf ekle adlı. Bu sınıfın türetini `CodeFixProvider`yapması gerekir ve **CTRL+'ı** kullanmanız gerekir. (dönem) doğru `using` deyimi ekleyen kod düzeltmesini çağırmak için. Bu sınıfın da öznitelik ile `ExportCodeFixProvider` açıklamalı olması gerekir ve `using` `LanguageNames` enum çözmek için bir deyim eklemeniz gerekir. Içinde aşağıdaki kodun bulunan bir sınıf dosyası olmalıdır:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Türetilmiş üyeleri sapla.** Şimdi, editörün atağını tanımlayıcıya yerleştirin `CodeFixProvider` ve **CTRL+'ye basın.** (dönem) bu soyut taban sınıf için uygulama saplamak için. Bu sizin için bir özellik ve bir yöntem oluşturur.

**Özelliği uygulayın.** Tesisin `FixableDiagnosticIds` `get` gövdesini aşağıdaki kodla doldurun:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn, sadece dizeleri olan bu tanımlayıcıları eşleştirerek tanılama ve düzeltmeleri bir araya getirir. Proje şablonu sizin için bir tanıkimliği oluşturdu ve bunu değiştirmekte özgürsunuz. Özellikteki kod, çözümleyici sınıfından kimliği döndürür.

**RegisterCodeFixAsync yöntemi bir bağlam alır.** Bir kod düzeltmesi birden çok tanılama için geçerli olabilir, çünkü bağlam önemlidir, ya da bir kod satırında birden fazla sorun olabilir. "Bağlam" yazarsanız. yöntemin gövdesinde, Intellisense tamamlama listesi bazı yararlı üyeleri gösterecektir. Bir iptal token üyesi bir şey düzeltme iptal etmek istiyor olup olmadığını kontrol edebilirsiniz. Çok sayıda kullanışlı üyesi olan ve proje ve çözüm modeli nesnelerine girmenizi sağlayan bir Belge üyesi vardır. Tanılamayı bildirdiğinizde belirtilen kod konumunun başlangıcı ve sonu olan bir Span üyesi vardır.

**Yöntemin uyumlu olmasını sağla.** Yapmanız gereken ilk şey, oluşturulan yöntem bildirimini `async` bir yöntem olarak düzeltmektir. Soyut bir sınıfın uygulanmasını saptamaya yönelik kod düzeltmesi, yöntem bir `async` `Task`. döndürse bile anahtar sözcüğü içermez.

**Sözdizimi ağacının kökünü alın.** Kodu değiştirmek için, kod düzeltmenizin yaptığı değişikliklerle birlikte yeni bir sözdizimi ağacı oluşturmanız gerekir. Aramak için `Document` bağlamından. `GetSyntaxRootAsync` Sözdizimi ağacını almak için bilinmeyen bir çalışma olduğundan, dosyayı diskten almak, ayrıştırmak ve roslyn kod modelini oluşturmak da dahil olmak üzere bu bir async yöntemidir. Visual Studio UI bu süre içinde duyarlı `async` olmalıdır, hangi kullanırken sağlar. Yöntemdeki kod satırını aşağıdakilerle değiştirin:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Sorunla birlikte düğümü bulun.** Bağlamın açıklığından geçersiniz, ancak bulduğunuz düğüm değiştirmeniz gereken kod olmayabilir. Bildirilen tanılama yalnızca tür tanımlayıcısı (dalgalı nın ait olduğu yer) için açıklık sağladı, ancak başlangıçtaki `new` keywoard ve sonundaki parantezler de dahil olmak üzere tüm nesne oluşturma ifadesini değiştirmeniz gerekir. Yönteminize aşağıdaki kodu ekleyin **(ve CTRL+'ı kullanın.** için bir `using` deyim `ObjectCreationExpressionSyntax`eklemek için):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Ampul UI için kod düzeltme kaydedin.** Kod düzeltmenizi kaydettiğinizde, Roslyn Visual Studio ampul ui'sine otomatik olarak takılır. Son kullanıcılar **CTRL+** kullanabileceklerini görürler. (nokta) analizör kötü `ImmutableArray<T>` bir yapıcı kullanımı squiggles zaman. Kod düzeltme sağlayıcınız yalnızca bir sorun olduğunda yürütüldettiğinden, aradığınız nesne oluşturma ifadesine sahip olduğunuzu varsayabilirsiniz. Bağlam parametresinden, yöntemin sonuna aşağıdaki kodu ekleyerek yeni kod `RegisterCodeFixAsync` düzeltmesini kaydedebilirsiniz:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Editörün bakımını tanımlayıcıya `CodeAction`yerleştirmeniz, ardından **CTRL+** kullanmanız gerekir. (dönem) bu tür `using` için uygun deyimi eklemek için.

Daha sonra editörün bakımını `ChangeToImmutableArrayEmpty` tanımlayıcıya yerleştirin ve **CTRL+'ı kullanın.** yine sizin için bu yöntem saplama oluşturmak için.

Eklediğiniz bu son kod parçacığı, bulunan sorun türü `CodeAction` için a ve tanılama kimliğini geçirerek kod düzeltmesini kaydeder. Bu örnekte, bu kodun düzeltmeler sağladığı tek bir tanılama kimliği vardır, bu nedenle tanılama kimlikleri dizisinin ilk öğesini geçirebilirsiniz. `CodeAction`Oluşturduğunuzda, ampul Kullanıcı Gİyi'nin kod düzeltmesinin açıklaması olarak kullanması gereken metinden geçersiniz. Ayrıca, İptal Token'i alan ve yeni bir Belge döndüren bir işlev de geçersiniz. Yeni Belge, yamalı kodunuzu içeren ve `ImmutableArray.Empty`.. Bu kod snippet, objectCreation düğümü ve bağlamın Belgesi üzerinde kapanabilmesi için bir lambda kullanır.

**Yeni sözdizimi ağacını oluştur.** Daha `ChangeToImmutableArrayEmpty` önce oluşturduğunuz saplama yönteminde kod satırını girin: `ImmutableArray<int>.Empty;`. Sözdizimi Görselleştirici araç penceresini yeniden görüntülerseniz, bu sözdizimini basit bir BasitÜye Erişim İfade düğümü olarak görebilirsiniz. Bu yöntemin yeni bir Belge'de oluşturmak ve döndürmek için gereken budur.

Kod üreteçleri `async` yöntemin async olması gerektiğini varsayamaz çünkü ilk değişiklik önce `Task<Document>` `ChangeToImmutableArrayEmpty` eklemektir.

Yönteminiz aşağıdakilere benzer şekilde gövdeyi aşağıdaki kodla doldurun:

```csharp

private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Editörün bakımını `SyntaxGenerator` tanımlayıcıya koymanız ve **CTRL+'ı** kullanmanız gerekir. (dönem) bu tür `using` için uygun deyimi eklemek için.

Bu `SyntaxGenerator`kod, yeni kod oluşturmak için çok yararlı bir tür olan kullanır. Kod sorunu olan belge için bir jeneratör `ChangeToImmutableArrayEmpty` `MemberAccessExpression`aldıktan sonra, aramalar , erişmek istediğimiz üye türü geçen ve bir dize olarak üyenin adını geçen.

Ardından, yöntem belgenin kökünü getirir ve bu genel durumda rasgele çalışma içerebileceğinden, kod bu çağrıyı bekler ve iptal belirteci geçer. Roslyn kod modelleri değişmez, bir .NET dize ile çalışma gibi; dizeyi güncelleştirdiğinizde, karşılığında yeni bir dize nesnesi elde elabilirsiniz. `ReplaceNode`Aradiğinizde, yeni bir kök düğüm geri alırsınız. Sözdizimi ağacının çoğu paylaşılır (çünkü değişmez, `objectCreation` ancak düğüm `memberAccess` düğümle ve sözdizimi ağacı köküne kadar olan tüm üst düğümlerle değiştirilir.

## <a name="trying-your-code-fix"></a>Kod Düzeltmenizi Deneme
Artık Visual Studio'nun ikinci bir örneğinde analizcünüzü çalıştırmak için **F5** tuşuna basabilirsiniz. Daha önce kullandığınız konsol projesini açın. Şimdi ampulün yeni nesne oluşturma ifadenizin olduğu `ImmutableArray<int>`yerde göründüğünü görmeniz gerekir. **CTRL+** tuşuna baslarsanız. (dönem), daha sonra kod düzeltme görürsünüz ve ampul UI otomatik olarak oluşturulan kod farkı önizleme göreceksiniz. Roslyn bunu senin için yaratıyor.

Pro İpucu: Visual Studio'nun ikinci örneğini başlattıysanız ve ampulü kod düzeltmenizle göremiyorsanız, Visual Studio bileşen önbelleğini temizlemeniz gerekebilir. Önbelleği temizlemek Visual Studio'yu bileşenleri yeniden incelemeye zorlar, bu nedenle Visual Studio en son bileşeninizi almalıdır. İlk olarak, Visual Studio ikinci örneği kapatın. Daha sonra Windows Gezgini'nde, kullanıcı dizininize\\ gidin\>(c:\users<userid) ve AppData\Local\Microsoft\VisualStudio\14.0Roslyn'i\\bulun. Bu dizinde, BileşenModelÖnbellek alt dizinini silin. "14", Visual Studio ile sürümü değiştirir.

## <a name="talk-video-and-finish-code-project"></a>Konuşma Video ve Bitiş Kodu Projesi
Bu örnek geliştirilen ve [bu konuşmada](https://channel9.msdn.com/events/Build/2015/3-725)daha fazla tartışıldı görebilirsiniz. Konuşma çalışan analizör gösterir ve onu inşa boyunca size yol gösterir.

[Burada](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)tüm bitmiş kodu görebilirsiniz. Alt klasörler DoNotUseImmutableArrayCollectionInitializer ve DoNotUseImmutableArrayCtor her sorunları bulmak için bir C # dosyası ve Visual Studio ampul UI göstermek kod düzeltmeleri uygulayan bir C # dosyası var. Not, bitmiş kod immutableArray\<T> türü nesneyi tekrar tekrar alma önlemek için biraz daha soyutlama vardır. Alt eylemler (nesne oluşturma yı çözümle ve toplama başlatmaları çözümle) yürütüldüğünde kullanılabilir bir bağlamda tür nesnesini kaydetmek için iç içe kayıtlı eylemleri kullanır.

## <a name="see-also"></a>Ayrıca Bkz.
[\\\Build 2015 talk](https://channel9.msdn.com/events/Build/2015/3-725)
[GitHub'da](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
tamamlanmış kod[GitHub'daki birkaç örnek,](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) 
GitHub'da[Roslyn analizörleri ile uygulanan](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers) [GitHub OSS sitesi](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
FxCop kurallarındaki üç tür analizöre ayrılmıştır
