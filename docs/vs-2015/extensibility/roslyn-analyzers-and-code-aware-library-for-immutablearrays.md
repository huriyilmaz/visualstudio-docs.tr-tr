---
title: Immutablearışın için Roslyn Çözümleyicileri ve kod kullanan kitaplık | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fbba44ef5ac0e531198b3569008a260118aefcf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298370"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>ImmutableArray’ler için Roslyn Çözümleyicileri ve Kod Algılayan Kitaplık
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[.Net Compiler platform](https://github.com/dotnet/roslyn) ("Roslyn"), kod kullanan kitaplıklar oluşturmanıza yardımcı olur. Kod kullanan bir kitaplık, kitaplığı en iyi şekilde kullanmanıza veya hatalardan kaçınmak için kullanabileceğiniz ve araç (Roslyn çözümleyiciler) işlevlerini sağlar. Bu konuda, [nib: sabit koleksiyon](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet paketini kullanırken yaygın hataları yakalamak için gerçek bir dünya Roslyn Çözümleyicisinin nasıl oluşturulduğu gösterilmektedir. Örnek ayrıca, çözümleyici tarafından bulunan bir kod sorunu için nasıl kod düzeltildiğini gösterir. Kullanıcılar, Visual Studio Light ampul Kullanıcı arabirimindeki kod düzeltmelerini görür ve kod için otomatik olarak bir düzeltme uygulayabilir.

## <a name="getting-started"></a>Başlarken
Bu örneği derlemek için aşağıdakilere ihtiyacınız vardır:

- Visual Studio 2015 (Express Edition değil) veya sonraki bir sürüm. Ücretsiz [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs) 'ı kullanabilirsiniz

- [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Ayrıca, Visual Studio 'Yu yüklerken SDK 'yı aynı anda yüklemek için ortak araçların altındaki Visual Studio Genişletilebilirlik Araçları kontrol edebilirsiniz. Visual Studio 'Yu zaten yüklediyseniz, bu SDK 'yı Ayrıca ana menü **dosyasına &#124; yeni &#124;proje...** giderek, sol gezinti bölmesinde seçip C# genişletilebilirlik 'i seçerek de yükleyebilirsiniz. "**Visual Studio genişletilebilirlik Araçları**" içerik haritası proje şablonu ' nu seçtiğinizde, SDK 'yı indirip yüklemenizi ister.

- [.Net Compiler platform ("Roslyn") SDK](https://aka.ms/roslynsdktemplates). Bu SDK 'yı Ayrıca, ana menü **dosyasına &#124; yeni &#124; proje...** giderek, **C#** sol gezinti bölmesinde seçip **genişletilebilirlik**' i seçerek de yükleyebilirsiniz. " **.Net COMPILER Platform SDK 'Yı indir**" içerik haritası proje şablonu ' nu seçtiğinizde, SDK 'yı indirip yüklemenizi ister. Bu SDK, [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)içerir. Bu son derece faydalı araç, çözümleyicinizdeki için aramanız gereken kod modeli türlerini bulmanıza yardımcı olur. Çözümleyici altyapısı, belirli kod modeli türleri için kodunuzu çağırır, bu nedenle kodunuz yalnızca gerektiğinde yürütülür ve yalnızca ilgili kodu analiz etmeye odaklanabilir.

## <a name="whats-the-problem"></a>Sorun nedir?
ImmutableArray (örneğin, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) desteğini içeren bir kitaplık sağladığınızı düşünelim. C#geliştiricilere .NET dizileri ile çok fazla deneyim vardır. Ancak, uygulamada kullanılan ımmutablearışınlar ve iyileştirme teknikleri doğası nedeniyle, C# geliştirici kullanıcıları kitaplığınızın kullanıcılarının, aşağıda açıklandığı gibi bozuk kod yazmasına neden olur. Ayrıca, kullanıcılar çalışma zamanına kadar kendi hatalarını görmez. Bu, .NET ile Visual Studio 'da kullanıldıkları kalite deneyimi değildir.

Kullanıcılar, aşağıdaki gibi kod yazmaya alışmış:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Sonraki kod satırları ile doldurulacak boş diziler oluşturma ve koleksiyon başlatıcısı sözdiziminin kullanılması C# geliştiricilere çok tanıdık gelecektir. Ancak, çalışma zamanında ImmutableArray kilitlenmeleri için aynı kodu yazma:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

İlk hata, ımutablearray uygulamasının temel alınan veri depolama alanını kaydırmak için bir struct kullanılarak kaynaklanmaktadır. Yapılar, `default(T)` ifadelerin tüm sıfır veya null üyelere sahip yapılar döndürmesini sağlamak için parametresiz oluşturuculara sahip olmalıdır. Kod `b1.Length`eriştiğinde, ImmutableArray yapısına temeldeki bir depolama dizisi bulunmadığından, çalışma zamanı null başvuru hatası vardır. Boş bir ImmutableArray oluşturmanın doğru yolu `ImmutableArray<int>.Empty`.

 Imutablearray. Add yöntemi her çağırdığınızda yeni örnekler döndürdüğünden, koleksiyon başlatıcılarla ilgili hata oluşur. Immutablearışın hiçbir zaman değişmediği için, yeni bir öğesi eklediğinizde yeni bir ımutablearray nesnesini geri alırsınız (Bu, daha önce varolan bir ImmutableArray ile performans nedenleriyle depolama alanını paylaşabilir). `b2` beş kez `Add()` çağrılmadan önce ilk ImmutableArray 'e işaret ettiğinden, `b2` varsayılan bir ImmutableArray olur. Aynı zamanda uzunluğu çağırma, null başvuru hatası ile kilitleniyor. Add, el ile çağrılmadan bir ImmutableArray başlatmanın doğru yolu `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`kullanmaktır.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Çözümleyicinizi tetiklemek için Ilgili söz dizimi düğüm türlerini bulma
Çözümleyici 'yi oluşturmaya başlamak için önce aramanız gereken SyntaxNode türünü öğrenin.   **Diğer Windows &#124; &#124; Roslyn Syntax Visualizer menü görünümünden**Syntax Visualizer başlatın.

Düzenleyicinin giriş işaretini `b1`bildiren satıra yerleştirin. Syntax Visualizer, söz dizimi ağacının `LocalDeclarationStatement` bir düğümünde olduğunu görürsünüz. Bu düğüm bir `VariableDeclarator``VariableDeclaration`sahiptir ve bu, sırasıyla bir `EqualsValueClause`sahiptir ve son olarak bir `ObjectCreationExpression`vardır. Düğümlerin Syntax Visualizer ağacına tıkladığınızda, düzenleyici penceresindeki sözdizimi bu düğüm tarafından temsil edilen kodu göstermek için vurgulanır. SyntaxNode alt türlerin adları, C# dilbilgisinde kullanılan adlarla eşleşir.

## <a name="creating-the-analyzer-project"></a>Çözümleyici projesi oluşturma
Ana menüden **Dosya &#124; yeni &#124; proje...** öğesini seçin. **Yeni proje** iletişim kutusunda, sol gezinti **C#** çubuğundaki projeler altında genişletilebilirlik ' i seçin ve sağ bölmedeki **kod düzeltmesini içeren çözümleyici** proje şablonu ' nu seçin. Bir ad girin ve iletişim kutusunu onaylayın.

Şablon bir DiagnosticAnalyzer.cs dosyası açar. Düzenleyici arabelleği sekmesini seçin. Bu dosya, `DiagnosticAnalyzer` (bir Roslyn API türü) tarafından türetilen bir çözümleyici sınıfına (projeyi verdiğiniz ad tarafından oluşturulmuş) sahiptir. Yeni sınıfınız, çözümleyicinizin, çözümleyici 'yi keşfetmesinin ve yükleyeceği C# şekilde dile uygun olduğunu bildiren bir `DiagnosticAnalyzerAttribute` sahiptir.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Kodu hedefleyen C# Visual Basic kullanarak bir çözümleyici uygulayabilir ve bunun tersini yapabilirsiniz. Bu, çözümleyicinizin bir dili mi yoksa her ikisini birden mi hedeflediğini belirlemek için Diagnosticanalizzerattribute içinde daha önemlidir. Dil için ayrıntılı modelleme gerektiren daha karmaşık çözümleyiciler yalnızca tek bir dili hedefleyebilir. Örneğin, çözümleyici 'niz yalnızca tür adlarını veya ortak üye adlarını denetlediğinde, Visual Basic ve C#arasında ortak dil modeli Roslyn tekliflerini kullanmak mümkün olabilir. Örneğin, FxCop bir sınıfın <xref:System.Runtime.Serialization.ISerializable>uyguladığını, ancak sınıfın <xref:System.SerializableAttribute> özniteliği dilden bağımsız olduğunu ve hem Visual Basic hem C# de kod için çalışıp çalışmadığını uyarır.

## <a name="initalizing-the-analyzer"></a>Çözümleyici 'yi görselleştirme
`Initialize` yöntemini görmek için `DiagnosticAnalyzer` sınıfında biraz aşağı kaydırın. Derleyici, bir çözümleyici etkinleştirirken bu yöntemi çağırır. Yöntemi, Çözümleyicisinin bağlam bilgilerini almasına ve analiz etmek istediğiniz kod türleri için olayların geri çağırmaları kaydına izin veren bir `AnalysisContext` nesnesi alır.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Bu yöntemde yeni bir satır açın ve "bağlam" yazın. IntelliSense tamamlanma listesini görmek için. Tamamlama listesinde, çeşitli olay türlerini işlemek için pek çok `Register…` yöntemi olduğunu görebilirsiniz. Örneğin, ilk diğeri `RegisterCodeBlockAction`, genellikle küme ayraçları arasında kod olan bir blok için geri çağırır. Bir blok için kaydolmak, bir alanın başlatıcısı için kodunuza geri çağrı, bir özniteliğe verilen değer ya da isteğe bağlı bir parametre değeri de çağırır.

Diğer bir örnek olarak `RegisterCompilationStartAction`, bir derlemenin başlangıcında kodunuza geri çağrı yapılır, bu da çok sayıda konumda durum toplamanız gerektiğinde yararlı olur. Kullanılan tüm sembolleri toplamak için bir veri yapısı oluşturabilir, her bir sözdizimi veya sembol için çözümleyicinizin her çağrılışında, veri yapınıza her bir konum hakkında bilgi kaydedebilirsiniz. Derleme sona ermek üzere geri çağrıldığında, kaydettiğiniz tüm konumları analiz edebilirsiniz; Örneğin, her bir `using` deyimindeki kodun kullandığı sembolleri raporlamak için.

**Syntax Visualizer**kullanarak, derleyici bir ObjectCreationExpression işlediğinde çağrılabilmesi istediğinizi öğrendiniz. Geri aramayı ayarlamak için bu kodu kullanın:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Bir sözdizimi düğümü için kayıt yaptırın ve yalnızca nesne oluşturma sözdizimi düğümleri için filtre uygulayın. Kurala göre, çözümleyici yazarları eylemleri kaydederken bir lambda kullanır ve bu da çözümleyiciler durum bilgisiz olamaz. `AnalyzeObjectCreation` yöntemi oluşturmak için kullanımdan Visual Studio özellik **Oluştur** ' da kullanabilirsiniz. Bu, sizin için doğru bağlam parametresi türünü oluşturur.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Çözümleyicinizi kullananlar için özellikleri ayarlama
Çözümleyicinizi Visual Studio Kullanıcı arabiriminde uygun şekilde göstermeleri için, çözümleyicinizi tanımlamak üzere aşağıdaki kod satırını bulup değiştirin:

```csharp
internal const string Category = "Naming";
```

`"Naming"` `"API Guidance"`olarak değiştirin.

Daha sonra **Çözüm Gezgini**kullanarak projenizde resources. resx dosyasını bulun ve açın. Çözümleyici, başlık vb. için bir açıklama koyabilirsiniz. Bunların tümünün değerini şimdilik `“Don’t use ImmutableArray<T> constructor”` değiştirebilirsiniz. String biçimlendirme bağımsız değişkenlerini dizeniz ({0}, {1}, vb.) koyabilirsiniz ve daha sonra `Diagnostic.Create()`çağırdığınızda, geçirilecek bağımsız değişkenlerin params dizisini sağlayabilirsiniz.

## <a name="analyzing-an-object-creation-expression"></a>Nesne oluşturma Ifadesi çözümleniyor
`AnalyzeObjectCreation` yöntemi, Code Analyzer Framework tarafından sağlanan farklı bir bağlam türünü alır. Başlatma yönteminin `AnalysisContext`, çözümleyicinizi ayarlamak için eylem geri çağırmaları kaydetmenizi sağlar. Örneğin, `SyntaxNodeAnalysisContext`, geçirebilmeniz için `CancellationToken` vardır. Kullanıcı düzenleyicide yazmaya başlarsa, Roslyn çalışmayı kaydetmek ve performansı artırmak için çalışan Çözümleyicileri iptal eder. Başka bir örnek olarak, bu bağlamın nesne oluşturma sözdizimi düğümünü döndüren bir Node özelliği vardır.

Varsayabilirsiniz düğüm, söz dizimi düğümü eylemini filtreleyerek kullanabileceğiniz türdür:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Visual Studio 'Yu Çözümleyicinizi Ilk kez başlatma
Çözümleyicinizi oluşturup yürüterek Visual Studio 'Yu başlatın ( **F5**tuşuna basın). **Çözüm Gezgini** başlangıç projesi VSIX projesi olduğundan, kodunuzu çalıştırmak kodunuzu ve VSIX 'i oluşturur ve ardından Visual Studio 'YU bu VSIX yüklü olarak başlatır. Visual Studio 'Yu bu şekilde başlattığınızda, Visual Studio 'nun ana kullanabilmeniz, çözümleyiciler oluştururken test örneklerinizin etkilenmemesi için ayrı bir kayıt defteri Hive ile başlatılır. Bu şekilde ilk kez başlattığınızda, Visual Studio, yükledikten sonra Visual Studio 'Yu ilk kez başlattığınızda, benzer şekilde birkaç başlatma yapar.

 Konsol projesi oluşturun ve ardından konsol uygulamaları ana yöntemine dizi kodu girin:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Sabit NuGet paketini almanız ve kodunuza bir `using` açıklaması eklemeniz gerektiğinden `ImmutableArray` olan kod satırları dalgalı çizgiler sahiptir. **Çözüm Gezgini** proje düğümünde sağ işaretçi düğmesine basın ve **NuGet Paketlerini Yönet...** seçeneğini belirleyin. NuGet Yöneticisi 'nde, arama kutusuna "sabit" yazın ve sol bölmede "System. Collections. sabit" öğesini seçin ("Microsoft. BCL. sabit" seçeneğini belirtmeyin) ve sağ bölmedeki Install düğmesine basın. Paketi yüklemek, proje başvurularınız için bir başvuru ekler.

`ImmutableArray`altında kırmızı dalgalı çizgiler görmeye devam edersiniz, bu nedenle giriş işaretini bu tanımlayıcıya yerleştirin ve **CTRL +** tuşlarına basın. (Period) önerilen çözüm menüsünü getirip uygun `using` ifadesini eklemeyi seçin.

Devam etmek için bir bütün olarak Visual Studio 'Yu **kaydedin ve** ikinci örneğini hemen kapatın.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Düzenle ve devam et kullanarak Çözümleyicisi bitiriliyor
Visual Studio 'nun ilk örneğinde, ilk satırdaki şapka işareti ile **F9** tuşuna basarak `AnalyzeObjectCreation` yönteminizin başlangıcında bir kesme noktası ayarlayın.

**F5**ile çözümleyicinizi yeniden başlatın ve Visual Studio 'nun ikinci örneğinde, son kez oluşturduğunuz konsol uygulamanızı yeniden açın.

Roslyn derleyicisi bir nesne oluşturma ifadesi görtiğinden ve çözümleyicinizde çağırdığı için kesme noktasında Visual Studio 'nun ilk örneğine dönersiniz.

**Nesne oluşturma düğümünü alın.** `objectCreation` değişkenini, **F10**tuşuna basarak ayarlayan çizginin üzerinde Ilerleyin ve **komut penceresinde** ifade `“objectCreation.ToString()”`değerlendirin. Değişkenin işaret ettiği söz dizimi düğümünün kod `"new ImmutableArray<int>()"`olduğunu ve yalnızca aradığınızı görürsünüz.

**ImmutableArray\<T > Type nesnesi alın.** Oluşturulan türün ImmutableArray olup olmadığını kontrol etmeniz gerekir. İlk olarak, bu türü temsil eden nesneyi alırsınız. Doğru türe sahip olduğunuzdan emin olmak için, türleri anlam modeli kullanarak kontrol edersiniz ve dizeyi ToString () ile karşılaştırmayın. İşlevin sonuna aşağıdaki kod satırını girin:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Genel türleri, geritekliflerle (') ve genel parametrelerin sayısıyla birlikte meta verilerde belirlersiniz. Bu nedenle "... Meta veri adında ImmutableArray\<T > ".

Anlam modeli, semboller, veri akışı, değişken ömür vb. hakkında sorular sormaya olanak tanıyan birçok yararlı şey içerir. Roslyn, çeşitli mühendislik nedenleri (performans, modelleme hatalı kodu vb.) için anlamsal modelden sözdizimi düğümlerini ayırır. Derleme modelinin, doğru karşılaştırma için başvurularda yer alan bilgileri araması istiyorsunuz.

Düzenleyici penceresinin sol tarafındaki Sarı yürütme işaretçisini sürükleyebilirsiniz. `objectCreation` değişkenini ayarlayan satıra sürükleyin ve **F10**kullanarak yeni kod satırlarınızın üzerine adımlayın. Fare işaretçisini `immutableArrayOfType`değişkenin üzerine getirdiğinizde anlamsal modelde tam türü bulduğumuz görürsünüz.

**Nesne oluşturma ifadesinin türünü alın.** "Tür" Bu makalede birkaç şekilde kullanılır, ancak bu, "yeni foo" ifadeniz varsa, foo modeli almanız gerektiği anlamına gelir. Imutablearray\<T > türünde olup olmadığını görmek için nesne oluşturma ifadesinin türünü almanız gerekir. Nesne oluşturma ifadesinde tür sembolünün (ImmutableArray) sembol bilgisini almak için anlamsal modeli yeniden kullanın. İşlevin sonuna aşağıdaki kod satırını girin:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Çözümleyici 'nizin düzenleyici arabelleklerinde tamamlanmamış veya hatalı kodu işlemesi gerektiğinden (örneğin, eksik bir `using` deyimleri varsa) `symbolInfo` `null`denetlemeniz gerekir. Çözümlemeyi bitirebilmeniz için sembol bilgisi nesnesinden adlandırılmış bir tür (INamedTypeSymbol) almanız gerekir.

**Türleri karşılaştırın.** Aradığımız açık genel bir T türü olduğundan ve koddaki tür somut genel bir tür olduğundan, türün oluşturulduğu öğe (açık genel bir tür) için simge bilgilerini sorgular ve bu sonucu `immutableArrayOfTType`ile karşılaştırın. Yönteminin sonuna şunu girin:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Tanılamayı bildirin.** Tanılamayı raporlama oldukça kolaydır. Başlangıç yönteminden önce tanımlanan proje şablonunda sizin için oluşturulan kuralı kullanırsınız. Koddaki bu durum bir hata olduğundan, başlatılan kuralı `DiagnosticSeverity.Warning` (yeşil dalgalı çizgi) yerine `DiagnosticSeverity.Error` (kırmızı dalgalı çizgi) olacak şekilde değiştirebilirsiniz. Kuralın geri kalanı, gözden geçirme başlangıcında düzenlediğiniz kaynaklardan başlatılır. Ayrıca, nesne oluşturma expressma 'nın tür belirtiminin konumu olan dalgalı çizgi için konumu rapor etmeniz gerekir. `if` bloğunda bu kodu girin:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

İşleviniz şuna benzemelidir (Belki de farklı şekilde biçimlendirilir):

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

Çözümleyicisi 'nin çalışmasını görebilmeniz için kesme noktasını kaldırın (ve Visual Studio 'nun ilk örneğine döndürmeyi durdurun). Yürütme işaretçisini yönteminizin başlangıcına sürükleyin ve yürütmeye devam etmek için **F5** tuşuna basın. Visual Studio 'nun ikinci örneğine geri döndüğünüzde, derleyici kodu yeniden incelemek üzere başlatılır ve çözümleyici 'ye çağrı yapar. `ImmutableType<int>`altında dalgalı bir çizgi görebilirsiniz.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Kod sorunu için "kod onarımı" ekleme
Başlamadan önce, Visual Studio 'nun ikinci örneğini kapatın ve Visual Studio 'nun ilk örneğindeki (çözümleyici 'yi geliştirdiğinizi) hata ayıklamayı durdurun.

**Yeni bir sınıf ekleyin.** Çözüm Gezgini proje düğümünüzde kısayol menüsünü (sağ işaretçi düğmesi) kullanın ve yeni bir öğe eklemeyi seçin. `BuildCodeFixProvider`adlı bir sınıf ekleyin. Bu sınıfın `CodeFixProvider`türetilmesi gerekir ve **CTRL +** kullanmanız gerekir. (Period) doğru `using` ifadesini ekleyen kod düzeltmesini çağırmak için. Ayrıca, bu sınıfın `ExportCodeFixProvider` özniteliğiyle açıklanması gerekir ve `LanguageNames` numaralandırmasının çözümlenmesi için bir `using` bildirimi eklemeniz gerekir. Aşağıdaki kodu içeren bir sınıf dosyanız olmalıdır:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Türetilmiş üyeleri saplama.** Şimdi, düzenleyicinin giriş işaretini tanımlayıcı `CodeFixProvider` yerleştirip **CTRL +** tuşlarına basın. (nokta) bu soyut temel sınıf için uygulamayı saplama. Bu, sizin için bir özellik ve bir yöntem oluşturur.

**Özelliğini uygulayın.** `FixableDiagnosticIds` özelliğinin `get` gövdesini aşağıdaki kodla doldur:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn, yalnızca dizeler olan bu tanımlayıcıları eşleştirerek tanılama ve düzeltmeleri birlikte getirir. Proje şablonu sizin için bir tanılama KIMLIĞI üretti ve bunu değiştirebilirsiniz. Özelliğindeki kod yalnızca çözümleyici sınıfından KIMLIĞI döndürür.

**RegisterCodeFixAsync yöntemi bir bağlam alır.** Bağlam önemlidir çünkü bir kod düzeltilmesi birden çok tanılamada uygulanabilir veya bir kod satırında birden fazla sorun olabilir. "Bağlam" yazın. yöntemin gövdesinde, IntelliSense tamamlanma listesi size bazı faydalı Üyeler gösterecektir. Bir şeyin bir şeyi iptal etmek isteyip istemediğine bakmak için kontrol edeceğiniz bir CancellationToken üyesi vardır. Çok sayıda faydalı üyeye sahip bir belge üyesi var ve proje ve çözüm modeli nesnelerine erişmenizi sağlar. Tanılamayı bildirdiğiniz sırada belirtilen kod konumunun başlangıcı ve bitişi olan bir span üyesi vardır.

**Yöntemi zaman uyumsuz olarak yapın.** Yapmanız gereken ilk şey, üretilen Yöntem bildirimini bir `async` yöntemi olacak şekilde düzeltemedi. Bir soyut sınıf kalıntıları oluşturuluyor için kod düzeltilme, yöntem bir `Task`döndürse de `async` anahtar sözcüğünü içermez.

**Sözdizimi ağacının kökünü alın.** Kodu değiştirmek için, kod Düzeltmelerinizin yaptığı değişikliklerle yeni bir sözdizimi ağacı oluşturmanız gerekir. `GetSyntaxRootAsync`çağırmak için bağlamdan `Document` gerekir. Bu, büyük olasılıkla dosyayı diskten alma, ayrıştırma ve için Roslyn kod modelini oluşturma dahil olmak üzere sözdizimi ağacını almak için bilinmeyen bir iş olduğundan zaman uyumsuz bir yöntemdir. Visual Studio Kullanıcı arabirimi bu süre boyunca yanıt vermesi gerekir ve bu süre `async` tarafından etkinleştirilir. Yöntemdeki kod satırını aşağıdaki gibi değiştirin:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Sorunu içeren düğümü bulun.** İçeriğin yayılma alanını geçirtirsiniz, ancak bulduğunuz düğüm değiştirmeniz istediğiniz kod olmayabilir. Bildirilen tanılama yalnızca tür tanımlayıcısı için (dalgalı çizgi 'nin ait olduğu) aralığı sağladıysa, ancak başındaki `new` keywoard ve sonundaki parantez dahil olmak üzere nesne oluşturma ifadesinin tamamını değiştirmeniz gerekir. Yöntemine aşağıdaki kodu ekleyin (ve **CTRL + kullanın.** `ObjectCreationExpressionSyntax`için `using` bir ifade eklemek için:

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Ampul Kullanıcı arabirimi için kod düzeltmeinizi kaydedin.** Kod düzeltmesini kaydettiğinizde, Roslyn, Visual Studio Light ampul Kullanıcı arabirimine otomatik olarak takılır. Son kullanıcılar, **CTRL + kullanabilirler.** (Period) Çözümleyicisi dalgalı çizgiler kötü `ImmutableArray<T>` Oluşturucu kullanır. Kod onarma sağlayıcınız yalnızca bir sorun olduğunda yürütüldüğü için, Aradığınız nesne oluşturma ifadesine sahip olduğunu varsayabilirsiniz. Bağlam parametresinden, `RegisterCodeFixAsync` yönteminin sonuna aşağıdaki kodu ekleyerek yeni kod düzeltmesini kaydedebilirsiniz:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Düzenleyicinin giriş işaretini tanımlayıcıya yerleştirmeniz, `CodeAction`ve ardından **CTRL +** tuşlarını kullanmanız gerekir. (Period) bu tür için uygun `using` ifadesini eklemek için.

Sonra, düzenleyicinin giriş işaretini `ChangeToImmutableArrayEmpty` tanımlayıcısına yerleştirip **CTRL +** tuşlarını kullanın. sizin için bu yöntem saplaması 'nı tekrar oluşturun.

Eklediğiniz bu son kod parçacığı, bir `CodeAction` ve tanılama KIMLIĞINI bulunan sorun türüne geçirerek kod düzeltmesini kaydeder. Bu örnekte, bu kodun düzeltme sağladığı yalnızca bir tanılama KIMLIĞI vardır, bu yüzden yalnızca tanılama kimlikleri dizisinin ilk öğesini geçirebilirsiniz. `CodeAction`oluşturduğunuzda, ampul Kullanıcı arabiriminin kod düzeltmesinin bir açıklaması olarak kullanması gereken metni geçitirsiniz. Ayrıca, CancellationToken alan ve yeni bir belge döndüren bir işlevi de geçitirsiniz. Yeni belge, `ImmutableArray.Empty`çağıran düzeltme eki uygulanan kodunuzu içeren yeni bir sözdizimi ağacına sahiptir. Bu kod parçacığı, Objectoluşturma düğümü ve bağlamın belgesi üzerinde kapatılabilir olması için bir lambda kullanır.

**Yeni sözdizimi ağacını oluşturun.** Daha önce oluşturduğunuz saplama `ChangeToImmutableArrayEmpty` yönteminde, kod satırını girin: `ImmutableArray<int>.Empty;`. Syntax Visualizer araç penceresini yeniden görüntülediğinizde, bu söz dizimi bir Simplelememberaccessexpression düğümü olduğunu görebilirsiniz. Bu yöntem, bu yöntemin yeni bir belgeye oluşturulması ve döndürülmesi için gereken şeydir.

`ChangeToImmutableArrayEmpty` ilk değişikliği, kod oluşturucuları yöntemin zaman uyumsuz olması gerektiğini varsayamadığı için `Task<Document>` önce `async` eklemektir.

Aşağıdaki kodla birlikte metni doldurarak yönteminizin aşağıdakine benzer görünmesini sağlayın:

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

Düzenleyicinin giriş işaretini `SyntaxGenerator` tanımlayıcısına koymanız ve **CTRL +** tuşlarını kullanmanız gerekir. (Period) bu tür için uygun `using` ifadesini eklemek için.

Bu kod, yeni kod oluşturmak için çok faydalı bir tür olan `SyntaxGenerator`kullanır. Kod sorunu olan belge için bir Oluşturucu aldıktan sonra, `ChangeToImmutableArrayEmpty` `MemberAccessExpression`çağırır ve üyenin adını bir dize olarak geçirmek istiyoruz.

Sonra, yöntemi belgenin kökünü getirir ve bu, genel durumda rastgele bir iş içerebileceği için, kod bu çağrıyı bekler ve iptal belirtecini geçirir. Roslyn kod modelleri, .NET dizesiyle çalışma gibi sabittir; dizeyi güncelleştirdiğinizde, dönerek yeni bir dize nesnesi alırsınız. `ReplaceNode`çağırdığınızda, yeni bir kök düğümü geri alırsınız. Sözdizimi ağacının büyük bir çoğunluğu paylaşılır (sabit olduğu için), ancak `objectCreation` düğümü `memberAccess` düğümle ve sözdizimi ağacı köküne kadar olan tüm üst düğümlere değiştirilirler.

## <a name="trying-your-code-fix"></a>Kod Düzeltmeinizi deniyor
Şimdi, Visual Studio 'nun ikinci bir örneğinde Çözümleyicisi 'ni yürütmek için **F5** 'e basabilirsiniz. Daha önce kullandığınız konsol projesini açın. Şimdi yeni nesne oluşturma ifadeniz `ImmutableArray<int>`için olduğu ampul ' i görmeniz gerekir. **CTRL +** tuşlarına basarsanız. (nokta), daha sonra kod düzeltmesini görürsünüz ve ampul Kullanıcı arabiriminde otomatik olarak oluşturulan bir kod farkı önizlemesi görürsünüz. Roslyn bunu sizin için oluşturur.

Pro Ipucu: Visual Studio 'nun ikinci örneğini başlatır ve kod düzeltmeinizle ampulü görmüyorsanız, Visual Studio bileşen önbelleğini temizlemeniz gerekebilir. Önbellek Temizleme, Visual Studio 'nun bileşenleri yeniden incelemesine zorlar, bu nedenle Visual Studio 'Nun en son bileşeninizi alması gerekir. İlk olarak, Visual Studio 'nun ikinci örneğini kapatın. Ardından Windows Gezgini 'nde Kullanıcı dizininize (c:\Users\\< UserID\>) gidin ve AppData\Local\Microsoft\VisualStudio\14.0Roslyn\\bulun. Bu dizinde, ComponentModelCache alt dizinini silin. "14" sürümü Visual Studio ile sürümü sürümüne dönüştürür.

## <a name="talk-video-and-finish-code-project"></a>Video ve son kod projesini konuşun
Bu örnekte geliştirilen ve daha ayrıntılı bilgi için bu [konuşmayı](https://channel9.msdn.com/events/Build/2015/3-725)görebilirsiniz. Konuş, çalışma çözümleyicisini gösterir ve bunu oluşturmak için size yol gösterir.

Tamamlanan tüm kodu [buradan](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)görebilirsiniz. Donotuseimmutablearraycollectionbaşlatıcı ve DoNotUseImmutableArrayCtor alt klasörlerinin her biri, sorunları C# bulmaya yönelik bir dosya ve Visual C# Studio Light ampul Kullanıcı arabiriminde görünen kod düzeltmelerini uygulayan bir dosya vardır. Bu şekilde, tamamlanmış kodun, ImmutableArray\<T > Type nesnesinin üzerinde ve üzerinde oluşmasını önlemek için biraz daha soyutlama olduğunu göz önüne alın. Tür nesnesini, alt eylemler (nesne oluşturmayı çözümle ve koleksiyon başlatmaları çözümle) yürütüher seferinde kullanılabilir bir bağlamda kaydetmek için iç içe kaydedilmiş eylemleri kullanır.

## <a name="see-also"></a>Ayrıca Bkz.
[\\\Build 2015](https://channel9.msdn.com/events/Build/2015/3-725) , github 'Da
[tamamlanmış kod](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
github 'daki [birkaç örnek](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) 
GitHub 'Da, GitHub 'da [Roslyn çözümleyicileri Ile uygulanan](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop) GitHub 'daki [diğer docs](https://github.com/dotnet/roslyn/tree/master/docs/analyzers) 
FxCop kuralları
