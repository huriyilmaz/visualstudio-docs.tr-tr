---
title: Immutablearışınlar için Roslyn Çözümleyicileri ve kod kullanan kitaplıklar
description: System. Collections. sabit NuGet paketini kullanırken yaygın hataları yakalamak için gerçek bir world roslyn çözümleyicisi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c430bc041e5212cd67aaf0801d58581b251c7770
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517638"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Immutablearışın için Roslyn Çözümleyicileri ve kod duyarlı kitaplık

[.NET Compiler Platform](https://github.com/dotnet/roslyn) ("roslyn"), kod kullanan kitaplıklar oluşturmanıza yardımcı olur. Kod kullanan bir kitaplık, kitaplığı en iyi şekilde kullanmanıza veya hatalardan kaçınmak için kullanabileceğiniz ve araç (Roslyn çözümleyiciler) işlevlerini sağlar. bu konuda, [System. Collections. sabit](https://www.nuget.org/packages/System.Collections.Immutable) NuGet paketini kullanırken yaygın hataları yakalamak için gerçek bir dünya roslyn çözümleyicisinin nasıl oluşturulduğu gösterilmektedir. Örnek ayrıca, çözümleyici tarafından bulunan bir kod sorunu için nasıl kod düzeltildiğini gösterir. kullanıcılar Visual Studio ampul kullanıcı arabirimindeki kod düzeltmelerini görür ve kod için otomatik olarak bir düzeltme uygulayabilir.

## <a name="get-started"></a>başlarken

Bu örneği derlemek için aşağıdakilere ihtiyacınız vardır:

* Visual Studio 2015 (Express Edition değil) veya sonraki bir sürüm. ücretsiz [Visual Studio Community sürümünü](https://visualstudio.microsoft.com/vs/community/) kullanabilirsiniz
* [SDK Visual Studio](../extensibility/visual-studio-sdk.md). ayrıca, Visual Studio yüklenirken SDK 'yı aynı anda yüklemek için **ortak araçlar** altında **Visual Studio genişletilebilirlik araçları** ' nı kontrol edebilirsiniz. Visual Studio zaten yüklediyseniz, bu SDK 'yı yeni Project ana menü **dosyasına giderek**  >    >  , sol gezinti bölmesinde **C#** ' ı seçip, ardından **genişletilebilirlik**' i seçerek de yükleyebilirsiniz. "**Visual Studio genişletilebilirlik araçları**" içerik haritası proje şablonu ' nu seçtiğinizde, SDK 'yı indirip yüklemenizi ister.
* [.NET Compiler Platform ("roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). bu SDK 'yı ayrıca, yeni Project ana menü **dosyasına** giderek  >    >  , sol gezinti bölmesinde **C#** ' ı seçip **genişletilebilirlik**' i seçerek de yükleyebilirsiniz. "**.NET Compiler Platform sdk 'yı indir**" içerik haritası proje şablonu ' nu seçtiğinizde, sdk 'yı indirip yüklemenizi ister. Bu SDK, [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md)içerir. Bu faydalı araç, çözümleyicinizdeki için aramanız gereken kod modeli türlerini bulmanıza yardımcı olur. Çözümleyici altyapısı, belirli kod modeli türleri için kodunuzu çağırır, bu nedenle kodunuz yalnızca gerektiğinde yürütülür ve yalnızca ilgili kodu analiz etmeye odaklanabilir.

## <a name="whats-the-problem"></a>Sorun nedir?

Imagine, ımmutablearray (örneğin,) desteğiyle bir kitaplık sağlarsınız <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> . C# geliştiricilerinin .NET dizileri ile çok sayıda deneyimi vardır. Ancak uygulamada kullanılan ımmutablearışın ve iyileştirme teknikleri doğası gereği, C# Geliştirici ıntuıtions, kitaplığınızın kullanıcılarının aşağıda açıklandığı gibi bozuk kod yazmasına neden olur. ayrıca, kullanıcılar çalışma zamanına kadar kendi hatalarını görmez, bu da .net ile Visual Studio için kullanıldıkları kalite deneyimi değildir.

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

İlk hata, ımutablearray uygulamasının temel alınan veri depolama alanını kaydırmak için bir struct kullanılarak kaynaklanmaktadır. Yapılar, `default(T)` tüm sıfır veya null üyelere sahip yapılar döndürebilmesi için parametre-daha az oluşturuculara sahip olmalıdır. Kod eriştiğinde `b1.Length` , ImmutableArray yapısına temeldeki bir depolama dizisi bulunmadığından, çalışma zamanı null başvuru hatası vardır. Boş bir ImmutableArray oluşturmanın doğru yolu `ImmutableArray<int>.Empty` .

Koleksiyon başlatıcılarla ilgili hata, `ImmutableArray.Add` Yöntem her çağırdığınızda yeni örnekler döndürdüğünden oluşur. Immutablearışın hiçbir zaman değişmediği için, yeni bir öğesi eklediğinizde yeni bir ımutablearray nesnesini geri alırsınız (Bu, daha önce varolan bir ImmutableArray ile performans nedenleriyle depolama alanını paylaşabilir). `b2`Beş kez çağrılmadan önce Ilk ImmutableArray 'e işaret ettiğinden `Add()` , `b2` varsayılan bir ImmutableArray olur. Aynı zamanda uzunluğu çağırma, null başvuru hatası ile kilitleniyor. Add, el ile çağrı yapmadan bir ImmutableArray başlatmanın doğru yolu kullanmaktır `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Çözümleyicinizi tetiklemek için ilgili söz dizimi düğüm türlerini bulun

 Çözümleyici 'yi oluşturmaya başlamak için önce aramanız gereken SyntaxNode türünü öğrenin.    >  **diğer Windows**  >  **roslyn Syntax Visualizer** menü görünümünden Syntax Visualizer başlatın.

Düzenleyicinin giriş işaretini, bildiren satıra yerleştirin `b1` . Syntax Visualizer, `LocalDeclarationStatement` söz dizimi ağacının bir düğümünde olduğunu gösterir. Bu düğüm, ' a sahip olan öğesine sahiptir ve bu da ' `VariableDeclaration` a sahiptir `VariableDeclarator` `EqualsValueClause` ve son olarak bir içerir `ObjectCreationExpression` . Düğümlerin Syntax Visualizer ağacına tıkladığınızda, düzenleyici penceresindeki sözdizimi bu düğüm tarafından temsil edilen kodu göstermek için vurgulanır. SyntaxNode Sub türlerinin adları, C# dilbilgisinde kullanılan adlarla eşleşir.

## <a name="create-the-analyzer-project"></a>Çözümleyici projesi oluşturma

ana menüden **dosya**  >  **yeni**  >  **Project**' yi seçin. **yeni Project** iletişim kutusunda, sol gezinti çubuğunda bulunan **C#** projeleri altında, **genişletilebilirlik**' i seçin ve sağ bölmedeki **kod düzeltmesini içeren çözümleyici** proje şablonu ' nu seçin. Bir ad girin ve iletişim kutusunu onaylayın.

Şablon bir *Diagnosticanalyzer. cs* dosyası açar. Düzenleyici arabelleği sekmesini seçin. Bu dosya, `DiagnosticAnalyzer` (bir Roslyn API türü) öğesinden türetilen bir çözümleyici sınıfına (projeyi verdiğiniz adından oluşturulmuş) sahiptir. Yeni sınıfınız, `DiagnosticAnalyzerAttribute` çözümleyicinizin, çözümleyicinizi bulduğu ve yükleyeceği şekilde C# diliyle ilgili olduğunu belirten bir bildirim içerir.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# kodunu hedefleyen Visual Basic kullanarak bir çözümleyici uygulayabilir ve bunun tersini yapabilirsiniz. Bu, çözümleyicinizin bir dili mi yoksa her ikisini birden mi hedeflediğini belirlemek için Diagnosticanalizzerattribute içinde daha önemlidir. Dil için ayrıntılı modelleme gerektiren daha karmaşık çözümleyiciler yalnızca tek bir dili hedefleyebilir. çözümleyici 'niz örneğin, yalnızca tür adlarını veya ortak üye adlarını denetlediğinde, Visual Basic ve C# ' de ortak dil modeli roslyn tekliflerini kullanmak mümkün olabilir. örneğin, FxCop bir sınıfın uyguladığı <xref:System.Runtime.Serialization.ISerializable> , ancak sınıfın <xref:System.SerializableAttribute> özniteliğe dilden bağımsız olduğunu ve hem Visual Basic hem de C# kodu için çalışıp çalışmadığını uyarır.

## <a name="initialize-the-analyzer"></a>Çözümleyici 'yi başlatma

 Yöntemi görmek için, sınıfın bir kısmını aşağı kaydırın `DiagnosticAnalyzer` `Initialize` . Derleyici, bir çözümleyici etkinleştirirken bu yöntemi çağırır. Yöntemi, `AnalysisContext` çözümleyicinizi bağlam bilgilerine almasını ve analiz etmek istediğiniz kod türleri için olayların geri çağırmaları kaydetmenizi sağlayan bir nesne alır.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Bu yöntemde yeni bir satır açın ve "bağlam" yazın. IntelliSense tamamlanma listesini görmek için. Tamamlama listesinde, `Register...` çeşitli olay türlerini işlemek için birçok yöntem olduğunu görebilirsiniz. Örneğin, ilki, `RegisterCodeBlockAction` genellikle küme ayraçları arasında kod olan bir blok için kodunuzu geri çağırır. Bir blok için kaydolmak, bir alanın başlatıcısı için kodunuza geri çağrı, bir özniteliğe verilen değer ya da isteğe bağlı bir parametre değeri de çağırır.

Başka bir örnek olarak, `RegisterCompilationStartAction` bir derlemenin başlangıcında kodunuza geri çağrı yapılır, bu da birçok konuma durum toplamanız gerektiğinde yararlı olur. Kullanılan tüm sembolleri toplamak için bir veri yapısı oluşturabilir, her bir sözdizimi veya sembol için çözümleyicinizin her çağrılışında, veri yapınıza her bir konum hakkında bilgi kaydedebilirsiniz. Derleme sona ermek üzere geri çağırıldığında, örneğin, her bir deyimden kodun kullandığı sembolleri raporlamak için kaydettiğiniz tüm konumları analiz edebilirsiniz `using` .

**Syntax Visualizer** kullanarak, derleyici bir ObjectCreationExpression işlediğinde çağrılabilmesi istediğinizi öğrendiniz. Geri aramayı ayarlamak için bu kodu kullanın:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Bir sözdizimi düğümü için kayıt yaptırın ve yalnızca nesne oluşturma sözdizimi düğümleri için filtre uygulayın. Kurala göre, çözümleyici yazarları eylemleri kaydederken bir lambda kullanır ve bu da çözümleyiciler durum bilgisiz olamaz. yöntemi oluşturmak için kullanımdan Visual Studio özelliği **oluştur** ' a yararlanabilirsiniz `AnalyzeObjectCreation` . Bu, sizin için doğru bağlam parametresi türünü oluşturur.

## <a name="set-properties-for-users-of-your-analyzer"></a>Çözümleyicinizi kullananlar için özellikleri ayarlayın

çözümleyici 'nizin Visual Studio kullanıcı arabirimine uygun şekilde görünmesi için, çözümleyicinizi tanımlamak üzere aşağıdaki kod satırını arayın ve değiştirin:

```csharp
internal const string Category = "Naming";
```

`"Naming"`Olarak değiştirin `"API Guidance"` .

Daha sonra **Çözüm Gezgini** kullanarak projenizde *Resources. resx* dosyasını bulun ve açın. Çözümleyici, başlık vb. için bir açıklama koyabilirsiniz. Bunların tümüne ilişkin değeri şimdilik ' de değiştirebilirsiniz `"Don't use ImmutableArray<T> constructor"` . String biçimlendirme bağımsız değişkenlerini dizenizle ( {0} , {1} , vb.) koyabilirsiniz ve sonra çağırdığınızda `Diagnostic.Create()` , `params` geçirilecek bir bağımsız değişken dizisi sağlayabilirsiniz.

## <a name="analyze-an-object-creation-expression"></a>Nesne oluşturma ifadesini çözümleme

`AnalyzeObjectCreation`Yöntemi, Code Analyzer Framework tarafından sağlanan farklı bir bağlam türünü alır. `Initialize`Yöntemi, `AnalysisContext` çözümleyicinizi ayarlamak için eylem geri çağırmaları kaydetmenizi sağlar. `SyntaxNodeAnalysisContext`Örneğin, `CancellationToken` içinde geçirebilmeniz için öğesine sahiptir. Kullanıcı düzenleyicide yazmaya başlarsa, Roslyn çalışmayı kaydetmek ve performansı artırmak için çalışan Çözümleyicileri iptal eder. Başka bir örnek olarak, bu bağlamın nesne oluşturma sözdizimi düğümünü döndüren bir Node özelliği vardır.

Varsayabilirsiniz düğüm, söz dizimi düğümü eylemini filtreleyerek kullanabileceğiniz türdür:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>çözümleyici 'yi ilk kez Visual Studio başlatın

çözümleyicinizi oluşturup yürüterek Visual Studio başlatın ( **F5** tuşuna basın). **Çözüm Gezgini** başlangıç projesi vsıx projem olduğundan, kodunuzu çalıştırmak kodunuzu ve vsıx 'i oluşturur ve sonra bu vsıx yüklü Visual Studio başlatır. Visual Studio bu şekilde başlattığınızda, Visual Studio ana kullanmanın, çözümleyiciler oluştururken test örneklerinizin etkilenmemesi için ayrı bir kayıt defteri hive ile başlatılır. bu şekilde ilk kez başladığınızda Visual Studio, yükleme sonrasında Visual Studio ilk kez başlatıldığında benzer şekilde birkaç başlatma yapmaz.

Konsol projesi oluşturun ve ardından konsol uygulamaları ana yöntemine dizi kodu girin:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

`ImmutableArray`sabit NuGet paketini almanız ve kodunuza bir ifade eklemeniz gerektiğinden, kod satırları dalgalı çizgiler sahiptir `using` . **Çözüm Gezgini** proje düğümünde sağ işaretçi düğmesine basın ve **NuGet paketlerini yönet**' i seçin. NuGet yöneticisi 'nde, arama kutusuna "sabit" yazın ve sol bölmedeki **System. Collections. sabit** öğesini seçin ( **Microsoft. Bcl. sabit**' i belirtmeyin) ve sağ bölmedeki **Install** düğmesine basın. Paketi yüklemek, proje başvurularınız için bir başvuru ekler.

altında kırmızı geçişler görmeye devam ediyor, bu nedenle dikkati bu tanımlayıcıya bırakın ve `ImmutableArray` **Ctrl tuşuna** + **basın.** (dönem) seçeneğini belirleyin ve önerilen düzeltme menüsünü açın ve uygun deyimi `using` ekleyin.

**Devam etmek için sizi** temiz bir Visual Studio durumuna koymak için şimdilik Tüm'leri Kaydet ve kapat'ın ikinci örneğini kapatın.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Düzenle ve devam etmek için çözümleyiciyi bitirme

İlk örnek Visual Studio F9 tuşuna basarak yönteminizin başında bir kesme noktası `AnalyzeObjectCreation` ayarlayın. 

**Çözümleyicinizi F5 ile** yeniden başlatın ve uygulamanın ikinci örneğinde Visual Studio oluşturduğunuz konsol uygulamasını yeniden açın.

Roslyn derleyicisi bir Nesne oluşturma ifadesi gördüğü ve çözümleyicinize çağırarak kesme Visual Studio ilk örneğine dönersiniz.

**Nesne oluşturma düğümünü al.** F10 tuşuna basarak değişkeni ayar eden satırın üzerinden `objectCreation` **geçin** ve Anında **Pencere'de ifadesini** `"objectCreation.ToString()"` değerlendirin. Değişkenin hangi söz dizimi düğümüne bakarak koda `"new ImmutableArray<int>()"` bakabilirsiniz?

**T Türü nesnesine ImmutableArray<\> yazın.** Oluşturulan türün ImmutableArray olup olduğunu denetlemelisiniz. İlk olarak, bu türü temsil eden nesnesini elde edersiniz. Tam olarak doğru türe sahip olduğundan emin olmak için semantik modeli kullanarak türleri kontrol edin ve dizesini ile `ToString()` karşılaştırmazsanız. İşlevin sonuna aşağıdaki kod satırı girin:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Meta verilerde genel türleri backticks (') ve genel parametre sayısı ile belirtirsiniz. Bu nedenle "... Meta veri adlarında ImmutableArray \<T> " .

Semantik modelde semboller, veri akışı, değişken yaşam süresi vb. hakkında soru sormanın pek çok yararlı şeyi vardır. Roslyn, söz dizimi düğümlerini çeşitli mühendislik nedenleriyle (performans, hatalı kod modelleme vb.) semantik modelden ayırmıştır. Derleme modelinin doğru karşılaştırma için başvurularda yer alan bilgileri toplaması gerekir.

Sarı yürütme işaretçisini düzenleyici penceresinin sol tarafına sürükleyebilirsiniz. Değişkeni ayar alan satıra kadar sürükleyin ve F10 kullanarak yeni kod `objectCreation` satırınıza **geçin.** Fare işaretçisini değişkeninin üzerine `immutableArrayOfType` gösterirsanız, semantik modelde tam türü bulduğumuza bakın.

**Nesne oluşturma ifadesinin türünü elde eder.** Bu makalede "Tür" birkaç şekilde kullanılır, ancak "yeni Foo" ifadesiniz varsa Foo modeline ihtiyacınız olduğu anlamına gelir. Bunun ImmutableArray türü olup olduğunu görmek için nesne oluşturma ifadesinin türünü \<T> alasiniz. Nesne oluşturma ifadesinde tür sembolüne (ImmutableArray) ilişkin sembol bilgilerini almak için semantik modeli yeniden kullanın. İşlevin sonuna aşağıdaki kod satırı girin:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Çözümleyicinizin düzenleyici arabellekleri içinde eksik veya yanlış kodu işlemesi gerektiği için (örneğin, eksik bir deyim `using` vardır) olup denetlemeniz `symbolInfo` `null` gerekir. Analizi tamamlamak için sembol bilgi nesnesinden adlandırılmış bir tür (INamedTypeSymbol) alasiniz.

**Türler'i karşılaştırın.** T'nin açık bir genel türü olduğundan ve kodda yer alan tür somut bir genel tür olduğundan, türün hangi türden (açık bir genel tür) oluşturulmuş olduğu için sembol bilgilerini sorgular ve sonucu ile `immutableArrayOfTType` karşılaştırabilirsiniz. Yönteminin sonuna aşağıdakini girin:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Tanılama'yı raporla.** Tanılamayı raporlamak oldukça kolaydır. Proje şablonunda sizin için oluşturulan Ve Initialize yöntemi öncesinde tanımlanan Kuralı kullanırsınız. Kodda bu durum bir hata olduğundan, Kural'ı başlatan satırı `DiagnosticSeverity.Warning` (yeşil geçiş) ile (kırmızı geçiş) değiştirecek `DiagnosticSeverity.Error` şekilde değiştirebilirsiniz. Kural'ın geri kalanı, gözden geçirmenin başlangıcına yakın bir yerde düzenley istediğiniz kaynaklardan başlatılır. Ayrıca, nesne oluşturma ifadesinin tür belirtimlerinin konumu olan iki durumlu düğmenin konumunu da bildirmelisiniz. Bloğuna şu kodu `if` girin:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

İşlevin şöyle olması gerekir (belki de farklı biçimlendirildi):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Çözümleyicinizin çalıştığını görmek için kesme noktası kaldırın (ve çözümleyicinizin ilk örneğine geri Visual Studio). Yürütme işaretçisini yönteminizin başına sürükleyin ve yürütmeye devam etmek **için F5** tuşuna basın. Uygulamanın ikinci örneğine geri Visual Studio, derleyici kodu yeniden incelemeye başlar ve çözümleyicinize çağrır. altında bir geçiş `ImmutableType<int>` görüyorsunuz.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Kod Sorunu için "Kod Düzeltmesi" Ekleme

Başlamadan önce, Visual Studio örneğinin ikinci örneğini kapatın ve Visual Studio (çözümleyiciyi geliştirdiğinizi) ilk örneğinde hata ayıklamayı durdurun.

**Yeni bir sınıf ekleyin.** Proje düğümünde kısayol menüsünü (sağ işaretçi düğmesi) **Çözüm Gezgini** yeni bir öğe eklemeyi seçin. adlı bir sınıf `BuildCodeFixProvider` ekleyin. Bu sınıfın ' sınıfından `CodeFixProvider` türetmiş olması ve Ctrl tuşunu **kullanmamız** + **gerekir.** (nokta) doğru deyimi ekleyen kod düzeltmesi çağırmak `using` için. Bu sınıfın ayrıca özniteliğiyle açıklama eklemesi `ExportCodeFixProvider` gerekir ve enum çözümlemek için `using` bir deyimi eklemeniz `LanguageNames` gerekir. Içinde aşağıdaki kodun yer alan bir sınıf dosyası olması gerekir:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Türetilmiş üyeleri saplama.** Şimdi düzenleyicinin caret'ini tanımlayıcıya yer ve `CodeFixProvider` **Ctrl tuşlarına** + **basın.** (dönem) bu soyut temel sınıf için uygulamanın saplama. Bu, sizin için bir özellik ve yöntem üretir.

**özelliğini uygulama.** Özelliğin `FixableDiagnosticIds` gövdesinde `get` aşağıdaki kodu girin:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn, yalnızca dizeler olan bu tanımlayıcıları eşleştirerek tanılama ve düzeltmeleri bir araya getirir. Proje şablonu sizin için bir tanılama kimliği oluştursa da bunu değiştirebilirsiniz. özelliğinde kod yalnızca çözümleyici sınıfından kimliği döndürür.

**RegisterCodeFixAsync yöntemi bir bağlam alır.** Kod düzeltmesi birden çok tanılama için geçerli olduğundan veya bir kod satırı üzerinde birden fazla sorun olduğu için bağlam önemlidir. "Context" (bağlam) yazın. yönteminin gövdesinde IntelliSense tamamlama listesinde bazı yararlı üyeler görüntülenir. Bir şeyin düzeltmeyi iptal etmek istediğini görmek için kontrol etmeniz gereken bir CancellationToken üyesi vardır. Çok sayıda yararlı üyeye sahip olan ve proje ve çözüm modeli nesnelerine inmanizi sağlayan bir Belge üyesi vardır. Tanılamayı rapor ettiyseniz belirtilen kod konumunun başlangıcı ve bitişi olan bir Span üyesi vardır.

**Yönteminin zaman uyumsuz olması.** İlk olarak, oluşturulan yöntem bildirimini bir yöntem olacak şekilde düzeltmeniz `async` gerekir. Soyut bir sınıfın uygulamasını saptamaya yönelik kod düzeltmesi, yöntem bir döndürse `async` bile anahtar sözcüğünü içermez. `Task`

**Söz dizimi ağacının kökünü al.** Kodu değiştirmek için, kod düzeltmenizin değişikliklerini kullanarak yeni bir söz dizimi ağacı üretmeniz gerekir. çağrısı için `Document` bağlamdan `GetSyntaxRootAsync` gerekir. Bu zaman uyumsuz bir yöntemdir çünkü söz dizimi ağacını almak için bilinmeyen bir çalışma vardır; örneğin dosyayı diskten alma, ayrıştırma ve bunun için Roslyn kod modelini oluşturma da buna dahil olabilir. Kullanıcı Visual Studio kullanıcı arabiriminin bu süre boyunca yanıt vermesi gerekir ve bu da kullanılarak `async` olanak sağlar. yönteminde kod satırı aşağıdakiyle değiştirin:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Sorunu olan düğümü bulun.** Bağlamın zaman dilimini geçersiniz, ancak bulmanız gereken düğüm, değiştirmek zorunda olmadığınız kod olabilir. Bildirilen tanılama yalnızca tür tanımlayıcısı için aralığı sağladı (iki durumlu düğmenin ait olduğu yer), ancak başındaki anahtar sözcüğü ve sonundaki parantezler de dahil olmak üzere nesne oluşturma ifadesinin tamamını `new` değiştirmeniz gerekir. Aşağıdaki kodu yönteminize ekleyin (ve **Ctrl tuşunu** + **kullanın).** için deyimi `using` eklemek `ObjectCreationExpressionSyntax` için:

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Ampul kullanıcı arabirimi için kod düzeltmenizi kaydetme.** Kod düzeltmenizi kaydeden Roslyn, otomatik olarak Visual Studio kullanıcı arabirimine takıyor. Son kullanıcılar Ctrl tuşlarını **kullanabileceğini** + **görebilir.** (dönem) çözümleyiciniz hatalı bir oluşturucu kullanımında geçiş `ImmutableArray<T>` yaptı. Kod düzeltme sağlayıcınız yalnızca bir sorun olduğunda yürütülür, çünkü istediğiniz nesne oluşturma ifadesine sahip olduğunu varsayabilirsiniz. Bağlam parametresinden, yönteminin sonuna aşağıdaki kodu ekleyerek yeni kod düzeltmesi `RegisterCodeFixAsync` kaydedebilirsiniz:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Düzenleyicinin caret'ini tanımlayıcıya ( ) ve ardından `CodeAction` **Ctrl** tuşunu + **kullanın.** (period) yazarak bu tür `using` için uygun deyimi ekleyin.

Ardından düzenleyicinin caret'ini tanımlayıcıya `ChangeToImmutableArrayEmpty` yer açın ve **Ctrl tuşunu** + **kullanın.** bu yöntem saplamayı sizin için oluşturmak için yeniden kullanın.

Eklenen son kod parçacığı, bulunan soruna ilişkin tanılama kimliğini ve bir kodunu geçerek `CodeAction` kod düzeltmeyi kaydedmektedir. Bu örnekte, bu kodun düzeltme sağladığı tek bir tanılama kimliği vardır, bu nedenle tanılama kimlikleri dizisinin ilk öğesini yalnızca geçebilirsiniz. 0000000000000000000000000000000000000000000000000000000000000000000000000000 `CodeAction` Ayrıca CancellationToken alan ve yeni bir Belge döndüren bir işlev de iletirsiniz. Yeni Belge, çağıran düzeltme eki uygulamalı kodunuzu içeren yeni bir söz dizimi ağacına `ImmutableArray.Empty` sahip. Bu kod parçacığı, objectCreation düğümünün ve bağlamın Belge'sinde kapatılaya kadar bir lambda kullanır.

**Yeni söz dizimi ağacını oluşturun.** `ChangeToImmutableArrayEmpty`Saplamayı daha önce oluşturan yöntemine şu kod satırı girin: `ImmutableArray<int>.Empty;` . Araç penceresini yeniden **Syntax Visualizer,** bu sözdiziminin SimpleMemberAccessExpression düğümü olduğunu görebilirsiniz. Bu yöntemin yeni bir Belge oluşturmak ve geri dönmek için ihtiyacı olan şey bu.

kod oluşturucuları `ChangeToImmutableArrayEmpty` yöntemin zaman `async` uyumsuz olması gerektiğini `Task<Document>` varsayamayay olduğundan, ilk değişikliği önce eklemektir.

Yönteminizin aşağıdakine benzer şekilde göründüğünü için gövdeyi aşağıdaki kodla doldurun:

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

Düzenleyicinin caret'ini tanımlayıcıya koymalı ve `SyntaxGenerator` **Ctrl tuşunu kullanabilirsiniz.** +  (period) yazarak bu tür `using` için uygun deyimi ekleyin.

Bu kod, `SyntaxGenerator` yeni kod oluşturmak için kullanışlı bir tür olan kullanır. Kod sorunu olan belge için bir oluşturucu alır, erişmek istediğiniz üyenin türünü iletir ve üyenin adını dize `ChangeToImmutableArrayEmpty` `MemberAccessExpression` olarak iletir.

Daha sonra, yöntemi belgenin kökünü getirir ve bu genel durumda rastgele bir iş içeriyor olabilir çünkü kod bu çağrıyı bekler ve iptal belirteci iletir. Roslyn kod modelleri bir .NET dizesiyle çalışma gibi sabittir; dizesini güncelleştirin, karşılığında yeni bir dize nesnesi alır. `ReplaceNode`çağrısında, yeni bir kök düğüm geri dönersiniz. Söz dizimi ağacının çoğu paylaşılır (sabit olduğundan), ancak düğüm düğümle ve söz dizimi ağacı köküne kadar olan tüm üst `objectCreation` `memberAccess` düğümlerle değiştirilir.

## <a name="try-your-code-fix"></a>Kod düzeltmenizi deneyin

Artık çözümleyicinizi **sorgu analizinin** ikinci bir örneğinde yürütmek için F5 tuşuna Visual Studio. Daha önce kullanılan konsol projesini açın. Şimdi yeni nesne oluşturma ifadenizin için olduğu yerde ampulün görünmesi `ImmutableArray<int>` gerekir. **Ctrl** tuşuna + **basın.** (dönem) sonra kod düzeltmenizi ve ampul kullanıcı arabiriminde otomatik olarak oluşturulan bir kod farkı önizlemesini görebilirsiniz. Roslyn bunu sizin için oluşturur.

**Pro İpucu:** Visual Studio'nin ikinci örneğini başlattıysanız ve kod düzeltmeniz ile ampulü görmüyorsanız, Visual Studio bileşeni önbelleğini temizlemeniz gerekir. Önbelleğin temizlendiğinde Visual Studio yeniden incelenmesi gerekir, bu Visual Studio en son bileşeninizi toplamanız gerekir. İlk olarak, uygulamanın ikinci örneğini Visual Studio. Ardından, **Windows 'de** *%LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn dizinine gidin. \\* ("16.0" sürümü, Visual Studio.) *ComponentModelCache alt dizinini silin.*

## <a name="talk-video-and-finish-code-project"></a>Videodan bahsedin ve kod projesini bitirin

Tüm bitmiş kodu burada [görüyorsunuz.](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) *DoNotUseImmutableArrayCollectionInitializer* ve *DoNotUseImmutableArrayCtor* alt klasörlerinin her biri sorunları bulmak için bir C# dosyasına ve Visual Studio ampul kullanıcı arabiriminde bulunan kod düzeltmelerini uygulayan bir C# dosyasına sahip olur. Bitmiş kodun ImmutableArray türü nesnesini tekrar tekrar getirmesini önlemek için biraz daha \<T> soyutlama olduğunu unutmayın. İç içe kayıtlı eylemleri, tür nesnesini alt eylemlerin (nesne oluşturma analizi ve koleksiyon başlatmalarını analiz etme) her yürütülürken kullanılabilen bir bağlamda kaydetmek için kullanır.

## <a name="see-also"></a>Ayrıca bkz.

* \\\Build 2015 konuşma
* [GitHub'de tamamlanan kod](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Üç çözümleyici GitHub gruplara göre kümeler hakkında birkaç örnek](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS sitesinde diğer belgeler](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [GitHub'da Roslyn çözümleyicileri ile uygulanan FxCop GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
