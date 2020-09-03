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
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444915"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>ImmutableArray’ler için Roslyn Çözümleyicileri ve Kod Algılayan Kitaplık
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[.Net Compiler platform](https://github.com/dotnet/roslyn) ("Roslyn"), kod kullanan kitaplıklar oluşturmanıza yardımcı olur. Kod kullanan bir kitaplık, kitaplığı en iyi şekilde kullanmanıza veya hatalardan kaçınmak için kullanabileceğiniz ve araç (Roslyn çözümleyiciler) işlevlerini sağlar. Bu konuda, [nib: sabit koleksiyon](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet paketini kullanırken yaygın hataları yakalamak için gerçek bir dünya Roslyn Çözümleyicisinin nasıl oluşturulduğu gösterilmektedir. Örnek ayrıca, çözümleyici tarafından bulunan bir kod sorunu için nasıl kod düzeltildiğini gösterir. Kullanıcılar, Visual Studio Light ampul Kullanıcı arabirimindeki kod düzeltmelerini görür ve kod için otomatik olarak bir düzeltme uygulayabilir.

## <a name="getting-started"></a>Başlarken
Bu örneği derlemek için aşağıdakilere ihtiyacınız vardır:

- Visual Studio 2015 (Express Edition değil) veya sonraki bir sürüm. Ücretsiz [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs) 'ı kullanabilirsiniz

- [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Ayrıca, Visual Studio 'Yu yüklerken SDK 'yı aynı anda yüklemek için ortak araçların altındaki Visual Studio Genişletilebilirlik Araçları kontrol edebilirsiniz. Visual Studio 'Yu zaten yüklediyseniz, bu SDK 'yı Ayrıca ana menü **dosyasına &#124; yeni &#124;projesi...**' yi seçerek, sol gezinti bölmesinde C# ' ı ve ardından Genişletilebilirlik ' i seçerek de yükleyebilirsiniz. "**Visual Studio genişletilebilirlik Araçları**" içerik haritası proje şablonu ' nu seçtiğinizde, SDK 'yı indirip yüklemenizi ister.

- [.Net Compiler platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Bu SDK 'Yı Ayrıca, **yeni &#124; proje... &#124;**, sol gezinti bölmesinde **C#** ' ı ve sonra da **genişletilebilirlik**' i seçerek de yükleyebilirsiniz. "**.Net COMPILER Platform SDK 'Yı indir**" içerik haritası proje şablonu ' nu seçtiğinizde, SDK 'yı indirip yüklemenizi ister. Bu SDK, [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)içerir. Bu son derece faydalı araç, çözümleyicinizdeki için aramanız gereken kod modeli türlerini bulmanıza yardımcı olur. Çözümleyici altyapısı, belirli kod modeli türleri için kodunuzu çağırır, bu nedenle kodunuz yalnızca gerektiğinde yürütülür ve yalnızca ilgili kodu analiz etmeye odaklanabilir.

## <a name="whats-the-problem"></a>Sorun nedir?
ImmutableArray (örneğin,) desteğinin bulunduğu bir kitaplık sağladığınızı düşünelim <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> . C# geliştiricilerinin .NET dizileri ile çok sayıda deneyimi vardır. Ancak uygulamada kullanılan ımmutablearışın ve iyileştirme teknikleri doğası gereği, C# Geliştirici ıntuıtions, kitaplığınızın kullanıcılarının aşağıda açıklandığı gibi bozuk kod yazmasına neden olur. Ayrıca, kullanıcılar çalışma zamanına kadar kendi hatalarını görmez. Bu, .NET ile Visual Studio 'da kullanıldıkları kalite deneyimi değildir.

Kullanıcılar, aşağıdaki gibi kod yazmaya alışmış:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

Sonraki kod satırları ile doldurulacak boş diziler oluşturma ve koleksiyon başlatıcısı sözdiziminin kullanılması C# geliştiricilerine tanıdık gelecektir. Ancak, çalışma zamanında ImmutableArray kilitlenmeleri için aynı kodu yazma:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

İlk hata, ımutablearray uygulamasının temel alınan veri depolama alanını kaydırmak için bir struct kullanılarak kaynaklanmaktadır. `default(T)`Deyimlerin, tüm sıfır veya null üyelere sahip yapılar döndürebilmesi için parametresiz oluşturucuları olmalıdır. Kod eriştiğinde `b1.Length` , ImmutableArray yapısına temeldeki bir depolama dizisi bulunmadığından, çalışma zamanı null başvuru hatası vardır. Boş bir ImmutableArray oluşturmanın doğru yolu `ImmutableArray<int>.Empty` .

 Imutablearray. Add yöntemi her çağırdığınızda yeni örnekler döndürdüğünden, koleksiyon başlatıcılarla ilgili hata oluşur. Immutablearışın hiçbir zaman değişmediği için, yeni bir öğesi eklediğinizde yeni bir ımutablearray nesnesini geri alırsınız (Bu, daha önce varolan bir ImmutableArray ile performans nedenleriyle depolama alanını paylaşabilir). `b2`Beş kez çağrılmadan önce Ilk ImmutableArray 'e işaret ettiğinden `Add()` , `b2` varsayılan bir ImmutableArray olur. Aynı zamanda uzunluğu çağırma, null başvuru hatası ile kilitleniyor. Add, el ile çağrı yapmadan bir ImmutableArray başlatmanın doğru yolu kullanmaktır `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Çözümleyicinizi tetiklemek için Ilgili söz dizimi düğüm türlerini bulma
Çözümleyici 'yi oluşturmaya başlamak için önce aramanız gereken SyntaxNode türünü öğrenin.   **Diğer Windows &#124; Roslyn Syntax Visualizer &#124; menü görünümündeki**Syntax Visualizer başlatın.

Düzenleyicinin giriş işaretini, bildiren satıra yerleştirin `b1` . Syntax Visualizer, `LocalDeclarationStatement` söz dizimi ağacının bir düğümünde olduğunu gösterir. Bu düğüm, ' a sahip olan öğesine sahiptir ve bu da ' `VariableDeclaration` a sahiptir `VariableDeclarator` `EqualsValueClause` ve son olarak bir içerir `ObjectCreationExpression` . Düğümlerin Syntax Visualizer ağacına tıkladığınızda, düzenleyici penceresindeki sözdizimi bu düğüm tarafından temsil edilen kodu göstermek için vurgulanır. SyntaxNode Sub türlerinin adları, C# dilbilgisinde kullanılan adlarla eşleşir.

## <a name="creating-the-analyzer-project"></a>Çözümleyici projesi oluşturma
Ana menüden **dosya &#124; yeni &#124; proje...** öğesini seçin. **Yeni proje** iletişim kutusunda, sol gezinti çubuğundaki **C#** projeleri altında genişletilebilirlik ' i seçin ve sağ bölmedeki **kod düzeltmesini içeren çözümleyici** proje şablonu ' nu seçin. Bir ad girin ve iletişim kutusunu onaylayın.

Şablon bir DiagnosticAnalyzer.cs dosyası açar. Düzenleyici arabelleği sekmesini seçin. Bu dosya, `DiagnosticAnalyzer` (bir Roslyn API türü) öğesinden türetilen bir çözümleyici sınıfına (projeyi verdiğiniz adından oluşturulmuş) sahiptir. Yeni sınıfınız, `DiagnosticAnalyzerAttribute` çözümleyicinizin, çözümleyicinizi bulduğu ve yükleyeceği şekilde C# diliyle ilgili olduğunu belirten bir bildirim içerir.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# kodunu hedefleyen Visual Basic kullanarak bir çözümleyici uygulayabilir ve bunun tersini yapabilirsiniz. Bu, çözümleyicinizin bir dili mi yoksa her ikisini birden mi hedeflediğini belirlemek için Diagnosticanalizzerattribute içinde daha önemlidir. Dil için ayrıntılı modelleme gerektiren daha karmaşık çözümleyiciler yalnızca tek bir dili hedefleyebilir. Çözümleyici 'niz Örneğin, yalnızca tür adlarını veya ortak üye adlarını denetlediğinde, Visual Basic ve C# ' de ortak dil modeli Roslyn tekliflerini kullanmak mümkün olabilir. Örneğin, FxCop bir sınıfın uyguladığı <xref:System.Runtime.Serialization.ISerializable> , ancak sınıfın <xref:System.SerializableAttribute> özniteliğe dilden bağımsız olduğunu ve hem Visual Basic hem de C# kodu için çalışıp çalışmadığını uyarır.

## <a name="initalizing-the-analyzer"></a>Çözümleyici 'yi görselleştirme
Yöntemi görmek için, sınıfın bir kısmını aşağı kaydırın `DiagnosticAnalyzer` `Initialize` . Derleyici, bir çözümleyici etkinleştirirken bu yöntemi çağırır. Yöntemi, `AnalysisContext` çözümleyicinizi bağlam bilgilerine almasını ve analiz etmek istediğiniz kod türleri için olayların geri çağırmaları kaydetmenizi sağlayan bir nesne alır.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Bu yöntemde yeni bir satır açın ve "bağlam" yazın. IntelliSense tamamlanma listesini görmek için. Tamamlama listesinde, `Register…` çeşitli olay türlerini işlemek için birçok yöntem olduğunu görebilirsiniz. Örneğin, ilki, `RegisterCodeBlockAction` genellikle küme ayraçları arasında kod olan bir blok için kodunuzu geri çağırır. Bir blok için kaydolmak, bir alanın başlatıcısı için kodunuza geri çağrı, bir özniteliğe verilen değer ya da isteğe bağlı bir parametre değeri de çağırır.

Başka bir örnek olarak, `RegisterCompilationStartAction` bir derlemenin başlangıcında kodunuza geri çağrı yapılır, bu da birçok konuma durum toplamanız gerektiğinde yararlı olur. Kullanılan tüm sembolleri toplamak için bir veri yapısı oluşturabilir, her bir sözdizimi veya sembol için çözümleyicinizin her çağrılışında, veri yapınıza her bir konum hakkında bilgi kaydedebilirsiniz. Derleme sona ermek üzere geri çağırıldığında, örneğin, her bir deyimden kodun kullandığı sembolleri raporlamak için kaydettiğiniz tüm konumları analiz edebilirsiniz `using` .

**Syntax Visualizer**kullanarak, derleyici bir ObjectCreationExpression işlediğinde çağrılabilmesi istediğinizi öğrendiniz. Geri aramayı ayarlamak için bu kodu kullanın:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Bir sözdizimi düğümü için kayıt yaptırın ve yalnızca nesne oluşturma sözdizimi düğümleri için filtre uygulayın. Kurala göre, çözümleyici yazarları eylemleri kaydederken bir lambda kullanır ve bu da çözümleyiciler durum bilgisiz olamaz. Yöntemi oluşturmak için, kullanımdan Visual Studio özellik **Oluştur** ' da kullanabilirsiniz `AnalyzeObjectCreation` . Bu, sizin için doğru bağlam parametresi türünü oluşturur.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Çözümleyicinizi kullananlar için özellikleri ayarlama
Çözümleyicinizi Visual Studio Kullanıcı arabiriminde uygun şekilde göstermeleri için, çözümleyicinizi tanımlamak üzere aşağıdaki kod satırını bulup değiştirin:

```csharp
internal const string Category = "Naming";
```

`"Naming"`Olarak değiştirin `"API Guidance"` .

Daha sonra **Çözüm Gezgini**kullanarak projenizde resources. resx dosyasını bulun ve açın. Çözümleyici, başlık vb. için bir açıklama koyabilirsiniz. Bunların tümüne ilişkin değeri şimdilik ' de değiştirebilirsiniz `“Don’t use ImmutableArray<T> constructor”` . String biçimlendirme bağımsız değişkenlerini dizenizle ( {0} , {1} , vb.) koyabilirsiniz ve sonra çağırdığınızda `Diagnostic.Create()` , geçirilecek bağımsız değişkenlerin params dizisini sağlayabilirsiniz.

## <a name="analyzing-an-object-creation-expression"></a>Nesne oluşturma Ifadesi çözümleniyor
`AnalyzeObjectCreation`Yöntemi, Code Analyzer Framework tarafından sağlanan farklı bir bağlam türünü alır. Initialize yöntemi, `AnalysisContext` çözümleyicinizi ayarlamak için eylem geri çağırmaları kaydetmenizi sağlar. `SyntaxNodeAnalysisContext`Örneğin, `CancellationToken` içinde geçirebilmeniz için öğesine sahiptir. Kullanıcı düzenleyicide yazmaya başlarsa, Roslyn çalışmayı kaydetmek ve performansı artırmak için çalışan Çözümleyicileri iptal eder. Başka bir örnek olarak, bu bağlamın nesne oluşturma sözdizimi düğümünü döndüren bir Node özelliği vardır.

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

İle kod satırları `ImmutableArray` dalgalı çizgiler sahiptir çünkü sabit NuGet paketini almanız ve kodunuza bir ifade eklemeniz gerekir `using` . **Çözüm Gezgini** proje düğümünde sağ işaretçi düğmesine basın ve **NuGet Paketlerini Yönet...** seçeneğini belirleyin. NuGet Yöneticisi 'nde, arama kutusuna "sabit" yazın ve sol bölmede "System. Collections. sabit" öğesini seçin ("Microsoft. BCL. sabit" seçeneğini belirtmeyin) ve sağ bölmedeki Install düğmesine basın. Paketi yüklemek, proje başvurularınız için bir başvuru ekler.

Hala kırmızı dalgalı çizgiler görüyorsanız, giriş `ImmutableArray` işaretini bu tanımlayıcıya yerleştirip **CTRL +** tuşlarına basın. (Period) önerilen çözüm menüsünü getirip uygun ifadeyi eklemeyi seçin `using` .

Devam etmek için bir bütün olarak Visual Studio 'Yu **kaydedin ve** ikinci örneğini hemen kapatın.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Düzenle ve devam et kullanarak Çözümleyicisi bitiriliyor
Visual Studio 'nun ilk örneğinde, `AnalyzeObjectCreation` ilk satırda şapka işareti Ile **F9** tuşuna basarak yönteminizin başlangıcında bir kesme noktası ayarlayın.

**F5**ile çözümleyicinizi yeniden başlatın ve Visual Studio 'nun ikinci örneğinde, son kez oluşturduğunuz konsol uygulamanızı yeniden açın.

Roslyn derleyicisi bir nesne oluşturma ifadesi görtiğinden ve çözümleyicinizde çağırdığı için kesme noktasında Visual Studio 'nun ilk örneğine dönersiniz.

**Nesne oluşturma düğümünü alın.** İşaretçiyi `objectCreation` **F10**tuşuna basarak ayarlayan çizginin üzerinde Ilerleyin ve **komut penceresinde** ifadeyi değerlendirin `“objectCreation.ToString()”` . Değişkenin işaret ettiği söz dizimi düğümünün kodun olduğunu `"new ImmutableArray<int>()"` ve yalnızca aradığınızı görürsünüz.

**ImmutableArray \<T> türü nesnesini Al.** Oluşturulan türün ImmutableArray olup olmadığını kontrol etmeniz gerekir. İlk olarak, bu türü temsil eden nesneyi alırsınız. Doğru türe sahip olduğunuzdan emin olmak için, türleri anlam modeli kullanarak kontrol edersiniz ve dizeyi ToString () ile karşılaştırmayın. İşlevin sonuna aşağıdaki kod satırını girin:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

Genel türleri, geritekliflerle (') ve genel parametrelerin sayısıyla birlikte meta verilerde belirlersiniz. Bu nedenle "... Meta veri adında ImmutableArray \<T> ".

Anlam modeli, semboller, veri akışı, değişken ömür vb. hakkında sorular sormaya olanak tanıyan birçok yararlı şey içerir. Roslyn, çeşitli mühendislik nedenleri (performans, modelleme hatalı kodu vb.) için anlamsal modelden sözdizimi düğümlerini ayırır. Derleme modelinin, doğru karşılaştırma için başvurularda yer alan bilgileri araması istiyorsunuz.

Düzenleyici penceresinin sol tarafındaki Sarı yürütme işaretçisini sürükleyebilirsiniz. Bu öğeyi, `objectCreation` Yeni kod satırlarınızın **F10**kullanarak değişkenini ve adımını ayarlayan satıra sürükleyin. Fare işaretçisini değişkenin üzerine getirdiğinizde `immutableArrayOfType` anlamsal modelde tam türü bulduğumuz görürsünüz.

**Nesne oluşturma ifadesinin türünü alın.** "Tür" Bu makalede birkaç şekilde kullanılır, ancak bu, "yeni foo" ifadeniz varsa, foo modeli almanız gerektiği anlamına gelir. ImmutableArray türünde olup olmadığını görmek için nesne oluşturma ifadesinin türünü almanız gerekir \<T> . Nesne oluşturma ifadesinde tür sembolünün (ImmutableArray) sembol bilgisini almak için anlamsal modeli yeniden kullanın. İşlevin sonuna aşağıdaki kod satırını girin:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Çözümleyici 'nizin, düzenleyici arabelleklerinde tamamlanmamış veya hatalı kodu işlemesi gerektiğinden (örneğin, eksik bir `using` bildirim varsa), olduğunu denetlemeniz gerekir `symbolInfo` `null` . Çözümlemeyi bitirebilmeniz için sembol bilgisi nesnesinden adlandırılmış bir tür (INamedTypeSymbol) almanız gerekir.

**Türleri karşılaştırın.** Aradığımız açık genel bir T türü olduğundan ve koddaki tür somut genel bir tür olduğundan, türün oluşturulduğu öğe (açık genel bir tür) için simge bilgilerini sorgular ve bu sonucu ile karşılaştırın `immutableArrayOfTType` . Yönteminin sonuna şunu girin:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Tanılamayı bildirin.** Tanılamayı raporlama oldukça kolaydır. Başlangıç yönteminden önce tanımlanan proje şablonunda sizin için oluşturulan kuralı kullanırsınız. Koddaki bu durum bir hata olduğundan, başlatılan kuralı `DiagnosticSeverity.Warning` (yeşil dalgalı çizgi) ile değiştirecek şekilde `DiagnosticSeverity.Error` (kırmızı dalgalı çizgi) değiştirebilirsiniz. Kuralın geri kalanı, gözden geçirme başlangıcında düzenlediğiniz kaynaklardan başlatılır. Ayrıca, nesne oluşturma expressma 'nın tür belirtiminin konumu olan dalgalı çizgi için konumu rapor etmeniz gerekir. Bu kodu `if` bloğa girin:

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

Çözümleyicisi 'nin çalışmasını görebilmeniz için kesme noktasını kaldırın (ve Visual Studio 'nun ilk örneğine döndürmeyi durdurun). Yürütme işaretçisini yönteminizin başlangıcına sürükleyin ve yürütmeye devam etmek için **F5** tuşuna basın. Visual Studio 'nun ikinci örneğine geri döndüğünüzde, derleyici kodu yeniden incelemek üzere başlatılır ve çözümleyici 'ye çağrı yapar. Altında dalgalı bir çizgi görebilirsiniz `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Kod sorunu için "kod onarımı" ekleme
Başlamadan önce, Visual Studio 'nun ikinci örneğini kapatın ve Visual Studio 'nun ilk örneğindeki (çözümleyici 'yi geliştirdiğinizi) hata ayıklamayı durdurun.

**Yeni bir sınıf ekleyin.** Çözüm Gezgini proje düğümünüzde kısayol menüsünü (sağ işaretçi düğmesi) kullanın ve yeni bir öğe eklemeyi seçin. Adlı bir sınıf ekleyin `BuildCodeFixProvider` . Bu sınıfın ' den türetilmesi gerekir `CodeFixProvider` ve **CTRL +** kullanmanız gerekir. (Period) doğru ifadeyi ekleyen kod düzeltmesini çağırmak için `using` . Bu sınıfın Ayrıca özniteliğiyle açıklanması gerekir `ExportCodeFixProvider` ve `using` sabit listesini çözümlemek için bir ifade eklemeniz gerekir `LanguageNames` . Aşağıdaki kodu içeren bir sınıf dosyanız olmalıdır:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Türetilmiş üyeleri saplama.** Şimdi, düzenleyicinin giriş işaretini tanımlayıcıya yerleştirip `CodeFixProvider` **CTRL +** tuşlarına basın. (nokta) bu soyut temel sınıf için uygulamayı saplama. Bu, sizin için bir özellik ve bir yöntem oluşturur.

**Özelliğini uygulayın.** `FixableDiagnosticIds`Özelliğin `get` gövdesini aşağıdaki kodla doldur:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn, yalnızca dizeler olan bu tanımlayıcıları eşleştirerek tanılama ve düzeltmeleri birlikte getirir. Proje şablonu sizin için bir tanılama KIMLIĞI üretti ve bunu değiştirebilirsiniz. Özelliğindeki kod yalnızca çözümleyici sınıfından KIMLIĞI döndürür.

**RegisterCodeFixAsync yöntemi bir bağlam alır.** Bağlam önemlidir çünkü bir kod düzeltilmesi birden çok tanılamada uygulanabilir veya bir kod satırında birden fazla sorun olabilir. "Bağlam" yazın. yöntemin gövdesinde, IntelliSense tamamlanma listesi size bazı faydalı Üyeler gösterecektir. Bir şeyin bir şeyi iptal etmek isteyip istemediğine bakmak için kontrol edeceğiniz bir CancellationToken üyesi vardır. Çok sayıda faydalı üyeye sahip bir belge üyesi var ve proje ve çözüm modeli nesnelerine erişmenizi sağlar. Tanılamayı bildirdiğiniz sırada belirtilen kod konumunun başlangıcı ve bitişi olan bir span üyesi vardır.

**Yöntemi zaman uyumsuz olarak yapın.** Yapmanız gereken ilk şey, oluşturulan Yöntem bildirimini bir yöntem olacak şekilde düzeltemedi `async` . Bir soyut sınıfın uygulamasını kalıntıları oluşturuluyor için kod düzeltilme `async` yöntemi, yöntem bir döndürüyor olsa bile anahtar sözcüğünü içermez `Task` .

**Sözdizimi ağacının kökünü alın.** Kodu değiştirmek için, kod Düzeltmelerinizin yaptığı değişikliklerle yeni bir sözdizimi ağacı oluşturmanız gerekir. ' İ `Document` çağırmak için bağlamınızın olması gerekir `GetSyntaxRootAsync` . Bu, büyük olasılıkla dosyayı diskten alma, ayrıştırma ve için Roslyn kod modelini oluşturma dahil olmak üzere sözdizimi ağacını almak için bilinmeyen bir iş olduğundan zaman uyumsuz bir yöntemdir. Visual Studio Kullanıcı arabirimi bu süre boyunca yanıt vermesi gerekir, bu, tarafından `async` etkinleştirilir. Yöntemdeki kod satırını aşağıdaki gibi değiştirin:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Sorunu içeren düğümü bulun.** İçeriğin yayılma alanını geçirtirsiniz, ancak bulduğunuz düğüm değiştirmeniz istediğiniz kod olmayabilir. Bildirilen tanılama yalnızca tür tanımlayıcısı için (dalgalı çizgi 'nin ait olduğu) aralığı sağladıysa, ancak `new` sonundaki anahtar Woard ve sonda parantez dahil olmak üzere tüm nesne oluşturma ifadesini değiştirmeniz gerekir. Yöntemine aşağıdaki kodu ekleyin (ve **CTRL + kullanın.** `using`için bir ifade eklemek için `ObjectCreationExpressionSyntax` :

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Ampul Kullanıcı arabirimi için kod düzeltmeinizi kaydedin.** Kod düzeltmesini kaydettiğinizde, Roslyn, Visual Studio Light ampul Kullanıcı arabirimine otomatik olarak takılır. Son kullanıcılar, **CTRL + kullanabilirler.** (Period) Çözümleyicisi dalgalı çizgiler bir hatalı `ImmutableArray<T>` Oluşturucu kullanır. Kod onarma sağlayıcınız yalnızca bir sorun olduğunda yürütüldüğü için, Aradığınız nesne oluşturma ifadesine sahip olduğunu varsayabilirsiniz. Bağlam parametresinden, yönteminin sonuna aşağıdaki kodu ekleyerek yeni kod düzeltmesini kaydedebilirsiniz `RegisterCodeFixAsync` :

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Düzenleyicinin giriş işaretini tanımlayıcıya yerleştirmeniz ve `CodeAction` ardından **CTRL +** tuşlarını kullanmanız gerekir. (Period) `using` Bu tür için uygun deyimin eklenmesi.

Sonra, düzenleyicinin giriş işaretini `ChangeToImmutableArrayEmpty` tanımlayıcıya yerleştirip **CTRL +** tuşlarını kullanın. sizin için bu yöntem saplaması 'nı tekrar oluşturun.

Eklediğiniz bu son kod parçacığı, `CodeAction` bulunan sorun türü için bir ve tanılama kimliği geçirerek kod düzeltmesini kaydeder. Bu örnekte, bu kodun düzeltme sağladığı yalnızca bir tanılama KIMLIĞI vardır, bu yüzden yalnızca tanılama kimlikleri dizisinin ilk öğesini geçirebilirsiniz. `CodeAction`' I oluştururken, ampul Kullanıcı arabiriminin kod düzeltmesinin açıklaması olarak kullanması gereken metni geçirin. Ayrıca, CancellationToken alan ve yeni bir belge döndüren bir işlevi de geçitirsiniz. Yeni belge, çağıran kod eki eklenen kodunuzu içeren yeni bir sözdizimi ağacına sahiptir `ImmutableArray.Empty` . Bu kod parçacığı, Objectoluşturma düğümü ve bağlamın belgesi üzerinde kapatılabilir olması için bir lambda kullanır.

**Yeni sözdizimi ağacını oluşturun.** `ChangeToImmutableArrayEmpty`Daha önce oluşturduğunuz saplama yönteminde kod satırını girin: `ImmutableArray<int>.Empty;` . Syntax Visualizer araç penceresini yeniden görüntülediğinizde, bu söz dizimi bir Simplelememberaccessexpression düğümü olduğunu görebilirsiniz. Bu yöntem, bu yöntemin yeni bir belgeye oluşturulması ve döndürülmesi için gereken şeydir.

' A yapılan ilk değişiklik, kod oluşturanlar `ChangeToImmutableArrayEmpty` `async` `Task<Document>` yöntemin zaman uyumsuz olması gerektiğini varsayamadığı için önce eklemektir.

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

Düzenleyicinin giriş işaretini `SyntaxGenerator` tanımlayıcıda koymanız ve **CTRL +** tuşlarını kullanmanız gerekir. (Period) `using` Bu tür için uygun deyimin eklenmesi.

Bu kod `SyntaxGenerator` , yeni kod oluşturmak için çok faydalı bir tür olan kullanır. Kod sorunu olan belge için bir Oluşturucu aldıktan sonra, `ChangeToImmutableArrayEmpty` `MemberAccessExpression` erişim sağlamak istediğimiz üyeye sahip olan türü geçirerek bir dize olarak üyenin adını geçirerek.

Sonra, yöntemi belgenin kökünü getirir ve bu, genel durumda rastgele bir iş içerebileceği için, kod bu çağrıyı bekler ve iptal belirtecini geçirir. Roslyn kod modelleri, .NET dizesiyle çalışma gibi sabittir; dizeyi güncelleştirdiğinizde, dönerek yeni bir dize nesnesi alırsınız. `ReplaceNode`Öğesini çağırdığınızda yeni bir kök düğümü geri alırsınız. Sözdizimi ağacının çoğu paylaşılır (sabit olduğu için), ancak `objectCreation` düğüm, `memberAccess` sözdizimi ağaç köküne kadar olan tüm üst düğümleri ve düğüm ile değiştirilmiştir.

## <a name="trying-your-code-fix"></a>Kod Düzeltmeinizi deniyor
Şimdi, Visual Studio 'nun ikinci bir örneğinde Çözümleyicisi 'ni yürütmek için **F5** 'e basabilirsiniz. Daha önce kullandığınız konsol projesini açın. Şimdi yeni nesne oluşturma ifadeniz için olan ampul ' i görürsünüz `ImmutableArray<int>` . **CTRL +** tuşlarına basarsanız. (nokta), daha sonra kod düzeltmesini görürsünüz ve ampul Kullanıcı arabiriminde otomatik olarak oluşturulan bir kod farkı önizlemesi görürsünüz. Roslyn bunu sizin için oluşturur.

Pro Ipucu: Visual Studio 'nun ikinci örneğini başlatır ve kod düzeltmeinizle ampulü görmüyorsanız, Visual Studio bileşen önbelleğini temizlemeniz gerekebilir. Önbellek Temizleme, Visual Studio 'nun bileşenleri yeniden incelemesine zorlar, bu nedenle Visual Studio 'Nun en son bileşeninizi alması gerekir. İlk olarak, Visual Studio 'nun ikinci örneğini kapatın. Ardından Windows Gezgini 'nde Kullanıcı dizininize (c:\Users \\<UserID \> ) gidin ve AppData\Local\Microsoft\VisualStudio\14.0Roslyn bulun \\ . Bu dizinde, ComponentModelCache alt dizinini silin. "14" sürümü Visual Studio ile sürümü sürümüne dönüştürür.

## <a name="talk-video-and-finish-code-project"></a>Video ve son kod projesini konuşun
Bu örnekte geliştirilen ve daha ayrıntılı bilgi için bu [konuşmayı](https://channel9.msdn.com/events/Build/2015/3-725)görebilirsiniz. Konuş, çalışma çözümleyicisini gösterir ve bunu oluşturmak için size yol gösterir.

Tamamlanan tüm kodu [buradan](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)görebilirsiniz. Donotuseimmutablearraycollectionbaşlatıcısı ve DoNotUseImmutableArrayCtor alt klasörlerinin her biri, sorunları bulmak için bir C# dosyasına ve Visual Studio Light ampul Kullanıcı arabiriminde görünen kod düzeltmelerini uygulayan bir C# dosyasına sahiptir. Bu, tamamlanmış kodun, ImmutableArray türü nesnesini ve üzerine getirmeyi önlemek için biraz daha soyutlama olduğunu göz önüne alın \<T> . Tür nesnesini, alt eylemler (nesne oluşturmayı çözümle ve koleksiyon başlatmaları çözümle) yürütüher seferinde kullanılabilir bir bağlamda kaydetmek için iç içe kaydedilmiş eylemleri kullanır.

## <a name="see-also"></a>Ayrıca Bkz.
[ \\ \Build 2015](https://channel9.msdn.com/events/Build/2015/3-725)GitHub 'da 
 [Completed code on GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)  
 [birkaç örnek](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)içeren GitHub 'da, GitHub 'daki  
 [Other docs on the GitHub OSS site](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
 [Roslyn Çözümleyicileri ile uygulanan](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers) GitHub OSS site FxCop kuralları üzerinde gerçekleştirilen diğer docs
