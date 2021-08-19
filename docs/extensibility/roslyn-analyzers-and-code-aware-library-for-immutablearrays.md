---
title: Roslyn çözümleyicileri ve ImmutableArrays için koda uygun kitaplıklar
description: System.Collections.Immutable veri paketi kullanılırken sık karşılaşılan hataları yakalamak için gerçek bir Roslyn çözümleyicisi NuGet öğrenin.
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
ms.openlocfilehash: ad08b0635e4c81fef4b1747f1b5da1e859977f65
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158366"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Roslyn çözümleyicileri ve ImmutableArrays için koda uygun kitaplık

Bu [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") koda sahip kitaplıklar derlemeye yardımcı olur. Kod kullanan bir kitaplık, kitaplığı en iyi şekilde kullanmanıza veya hataları önlemeye yardımcı olmak için kullanabileceğiniz işlevler ve araç (Roslyn çözümleyicileri) sağlar. Bu konuda, [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) veri paketi kullanılırken sık karşılaşılan hataları yakalamak için gerçek bir Roslyn çözümleyicisi oluşturma NuGet gösterilir. Örnek ayrıca çözümleyici tarafından bulunan bir kod sorunu için kod düzeltmesi sağlamayı da gösteriyor. Kullanıcılar ampul kullanıcı arabiriminde Visual Studio düzeltmeleri görebilir ve kod için otomatik olarak bir düzeltme uygulayabilir.

## <a name="get-started"></a>başlarken

Bu örneği oluşturmak için aşağıdakiler gerekir:

* Visual Studio 2015 (Express Edition değil) veya sonraki bir sürümü. Ücretsiz Visual Studio Community [Sürümünü kullanabilirsiniz](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK'sı.](../extensibility/visual-studio-sdk.md) Sdk'yı yüklerken Visual Studio **sdk'yı Visual Studio** Ortak Araçlar altında  Genişletilebilirlik Araçları'nda da kontrol edebilirsiniz. Visual Studio'yi zaten yüklemişsanız, ana menüye Gidip Dosya Yeni Project' menüsüne gidip sol gezinti bölmesinde C# öğesini ve ardından Genişletilebilirlik'i seçerek de bu SDK'yı  >    >   **yükleyebilirsiniz.**  " Install **the Visual Studio Genişletilebilirlik Araçları**" breadcrumb proje şablonunu seçerseniz, SDK'yı indirip yüklemenizi istenir.
* [.NET Compiler Platform ("Roslyn") SDK'sı](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Bu SDK'yı yüklemek için Dosya Yeni Giriş menüsüne Project, sol gezinti bölmesinde C# öğesini ve ardından  >    >   **Genişletilebilirlik'i seçebilirsiniz.**  " İndirme **sdk'sı" .NET Compiler Platform** proje şablonunu seçerseniz, SDK'yı indirip yüklemenizi istenir. Bu SDK, [Roslyn Syntax Visualizer.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md) Bu yararlı araç, çözümleyicinize hangi kod modeli türlerini bakmanız gerektiğini anlamanıza yardımcı olur. Çözümleyici altyapısı belirli kod modeli türleri için kodunuza çağrılar, bu nedenle kodunuz yalnızca gerektiğinde yürütülür ve yalnızca ilgili kodun analizine odaklanabilir.

## <a name="whats-the-problem"></a>Sorun nedir?

Imagine ImmutableArray (örneğin, ) desteği olan bir <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> kitaplık sağlar. C# geliştiricileri .NET dizileriyle ilgili birçok deneyime sahiptir. Ancak, uygulamada kullanılan ImmutableArrays ve iyileştirme tekniklerinin doğası gereği, C# geliştirici intuition'ları aşağıda açıklanan şekilde kitaplığınızı kullananların bozuk kod yazmasını sağlar. Ayrıca, kullanıcılar çalışma zamanlarına kadar hatalarını göremez. Bu, .NET ile çalışma sırasında Visual Studio deneyim değildir.

Kullanıcılar aşağıdaki gibi kod yazma hakkında bilgi sahibidir:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Sonraki kod satırlarıyla doldurmak için boş diziler oluşturmak ve koleksiyon başlatıcı söz dizimi kullanmak C# geliştiricilerine tanıdık geliyor. Ancak, ImmutableArray için aynı kodu yazmak çalışma zamanında kilitleniyor:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

İlk hata, ImmutableArray uygulamasının temel alınan veri depolama alanını sarmak için bir yapı kullanmasıdır. İfadelerin sıfır veya null üyelere sahip yapılar döndürebilecek şekilde, yapılarda `default(T)` parametresiz oluşturucular olmalıdır. Kod ' a erişse de, ImmutableArray yapıda temel alınan depolama dizisi olduğundan bir çalışma zamanı null başvuru `b1.Length` hatası vardır. Boş bir ImmutableArray oluşturmanın doğru yolu şu `ImmutableArray<int>.Empty` şekildedir: .

Koleksiyon başlatıcıları ile hatanın `ImmutableArray.Add` nedeni, yönteminin her çağıran yeni örnekleri döndüren olmasıdır. ImmutableArrays hiçbir zaman değişmeyce, yeni bir öğe eklerken yeni bir ImmutableArray nesnesi alırsınız (daha önce var olan bir ImmutableArray ile performans nedeniyle depolama alanını paylaşabilir). Beş `b2` kez çağırmadan önce ilk ImmutableArray değerine bakarak `Add()` varsayılan `b2` ImmutableArray değeridir. Üzerinde Length çağrısı da null başvuru hatasıyla kilitleniyor. Add'ı el ile çağırmadan ImmutableArray başlatmanın doğru yolu `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` kullanmaktır.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Çözümleyicinizi tetiklemek için ilgili söz dizimi düğümü türlerini bulma

 Çözümleyiciyi derlemeye başlamak için ilk olarak hangi SyntaxNode türünü aramalı olduğunu bulun. Roslyn **Syntax Visualizer** Diğer Öğeleri **Görüntüle**  >  **menüsünden**  >  **Windows Syntax Visualizer.**

Düzenleyicinin caret'ini bildiren satıra `b1` yer. Söz dizimi Syntax Visualizer düğümde olduğunu gösteren `LocalDeclarationStatement` komutlar olduğunu gösterir. Bu düğümde, sırasıyla , ve son olarak da olan bir `VariableDeclaration` `VariableDeclarator` `EqualsValueClause` `ObjectCreationExpression` vardır. Bir düğüm ağacına Syntax Visualizer, düzenleyici penceresindeki söz dizimi vurgulanır ve bu düğüm tarafından temsil edilen kodu gösterir. SyntaxNode alt türlerinin adları, C# dil bilgisinde kullanılan adlara eş.

## <a name="create-the-analyzer-project"></a>Çözümleyici projesini oluşturma

Ana menüden Dosya Yeni **Dosya'Project.**  >    >   Yeni uygulama **Project** iletişim kutusunun sol gezinti **çubuğundaki C#** projeleri altında Genişletilebilirlik'i seçin ve sağ bölmede Kod Düzeltmesi ile **Çözümleyici** proje şablonunu seçin. Bir ad girin ve iletişim kutusunu onaylayın.

Şablon bir *DiagnosticAnalyzer.cs dosyası* açar. Düzenleyici arabellek sekmesini seçin. Bu dosya, (Roslyn API türünden) türeten bir çözümleyici `DiagnosticAnalyzer` sınıfına (projeye verdiği addan oluşturulmuştur) içerir. Derleyicinin çözümleyicinizi bulması ve yüklemesi için yeni sınıfınız çözümleyicinizin C# diliyle ilgili `DiagnosticAnalyzerAttribute` olduğunu bildiren bir sınıfa sahip.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# kodunu hedef alan Visual Basic kullanarak çözümleyiciyi (veya tam tersi) gerçekleştirebilirsiniz. Çözümleyicinizin bir dili mi yoksa her ikisini birden mi hedefleyeceklerini seçmek DiagnosticAnalyzerAttribute'ta daha önemlidir. Dilin ayrıntılı modellemesini gerektiren daha gelişmiş çözümleyiciler yalnızca tek bir dili hedefleyene. Örneğin çözümleyiciniz yalnızca tür adlarını veya ortak üye adlarını denetlerse, Roslyn'in sunduğu ortak dil modelini Visual Basic ve C# arasında kullanabilirsiniz. Örneğin FxCop, bir sınıfın uygulaması konusunda uyarıyor ancak sınıfında özniteliği yok, dilden bağımsızdır ve hem Visual Basic <xref:System.Runtime.Serialization.ISerializable> <xref:System.SerializableAttribute> hem de C# kodu için çalışır.

## <a name="initialize-the-analyzer"></a>Çözümleyiciyi başlatma

 yöntemini görmek için `DiagnosticAnalyzer` sınıfında biraz aşağı `Initialize` kaydırın. Derleyici, çözümleyiciyi etkinleştirirken bu yöntemi çağırıyor. yöntemi, çözümleyicinizin bağlam bilgilerini almalarını ve analiz etmek istediğiniz kod türleri için olaylar için geri çağırmaları kaydetmelerini sağlayan `AnalysisContext` bir nesnesi alır.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Bu yöntemde yeni bir satır açın ve "bağlam" yazın. bir IntelliSense tamamlama listesi görmek için. Tamamlama listesinde, çeşitli türlerde olayları `Register...` işlemek için birçok yöntem olduğunu görüyorsunuz. Örneğin, ilki olan , genellikle küme ayraçları arasında kod olan bir blok için `RegisterCodeBlockAction` kodunuz için geri çağrır. Bir bloğuna kaydolmak ayrıca bir alanın başlatıcısı, bir özniteliğine verilen değer veya isteğe bağlı parametrenin değeri için kodunuz için geri çağrılar.

Başka bir örnek olarak, derlemenin başında kodunuz için geri çağrılar. Bu, birçok konumda durum `RegisterCompilationStartAction` toplamanız gereken durumlarda kullanışlıdır. Örneğin, kullanılan tüm sembolleri toplamak için bir veri yapısı oluşturabilir ve çözümleyiciniz söz dizimi veya sembol için her çağrıldında veri yapınıza ilişkin her konumla ilgili bilgileri kaydedebilirsiniz. Derlemenin bitimine bağlı olarak geri çağrıldıklarından, kodun her deyiminden hangi sembolleri kullandığını rapor etmek için, örneğin, kaydeden tüm konumları analiz `using` edersiniz.

Syntax Visualizer **kullanarak,** derleyici bir ObjectCreationExpression'ı işleyene kadar çağrılmalarını istediğinizi öğrendinsiniz. Bu kodu kullanarak geri çağırmayı ayarlayabilirsiniz:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Bir söz dizimi düğümüne kaydolarak yalnızca nesne oluşturma söz dizimi düğümlerini filtrelersiniz. Kural gereği çözümleyici yazarları eylemleri kaydettirerek çözümleyicileri durum bilgisiz tutmaya yardımcı olan bir lambda kullanır. Yöntemini oluşturmak için Visual Studio **Oluşturma özelliğini** `AnalyzeObjectCreation` kullanabilirsiniz. Bu, sizin için doğru bağlam parametresi türünü de üretir.

## <a name="set-properties-for-users-of-your-analyzer"></a>Çözümleyicinizin kullanıcıları için özellikleri ayarlama

Çözümleyicinizin kullanıcı arabiriminde uygun Visual Studio şekilde görünür, çözümleyicinizi tanımlamak için aşağıdaki kod satırına bakın ve bunu değiştirin:

```csharp
internal const string Category = "Naming";
```

olarak `"Naming"` `"API Guidance"` değişir.

Ardından projenizin *Resources.resx dosyasını* bulmak ve açmak için **Çözüm Gezgini.** Çözümleyiciniz, unvanınız vb. için bir açıklama koyabilirsiniz. Şimdilik bunların tüm değerini olarak `"Don't use ImmutableArray<T> constructor"` değiştirebilirsiniz. Dize biçimlendirme bağımsız değişkenlerini dizenize ( , vb.) ve daha sonra çağırarak geçireceğimiz bir bağımsız {0} {1} değişken dizisi `Diagnostic.Create()` `params` sebilirsiniz.

## <a name="analyze-an-object-creation-expression"></a>Nesne oluşturma ifadesini analiz etme

yöntemi, `AnalyzeObjectCreation` kod çözümleyicisi çerçevesi tarafından sağlanan farklı türde bir bağlam alır. yöntemi, `Initialize` `AnalysisContext` çözümleyicinizi ayarlamak için eylem geri çağırmalarını kaydetmenize olanak sağlar. Örneğin, `SyntaxNodeAnalysisContext` geçiş için `CancellationToken` bir var. Kullanıcı düzenleyicide yazmaya başlarsa Roslyn, çalışmadan tasarruf etmek ve performansı artırmak için çalışan çözümleyicileri iptal eder. Başka bir örnek olarak, bu bağlam nesne oluşturma söz dizimi düğümünü döndüren bir Node özelliğine sahip.

Söz dizimi düğümü eylemlerini filtreleyenin tür olduğunu varsayarak düğüme sahip olur:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Çözümleyicinizi Visual Studio kez başlatmak için

Çözümleyicinizi Visual Studio yürüterek uygulamayı çalıştırın **(F5 tuşuna basın).** **Çözüm Gezgini'daki** başlangıç projesi VSIX projesi olduğundan, kodunuzun ve VSIX'in çalışması kodunuzu ve vsIX'i Visual Studio VSIX yüklü olarak başlatıyor. Bu şekilde Visual Studio, ana Visual Studio çözümleyicileri hazırlarken test örneklerinden etkilenmeyecek şekilde ayrı bir kayıt defteri kovanı ile başlatıyor. Bu şekilde ilk kez Visual Studio, yüklemeden sonra ilk kez Visual Studio başlatmaları yapar.

Bir konsol projesi oluşturun ve dizi kodunu konsol uygulamalarınıza girin Main yöntemi:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

ile kod satırları, sabit bir NuGet paketi alıp kodunuz için bir deyimi eklemeniz gerektir olduğundan, `ImmutableArray` `using` çizgilere sahip olur. Dosyanın proje düğümünde sağ işaretçi düğmesine basın ve **Çözüm Gezgini** Yönet'i **NuGet seçin.** NuGet yöneticisinde, arama kutusuna "Sabit" yazın ve sol bölmede **System.Collections.Immutable** **(Microsoft.Bcl.Immutable'ı** seçme) öğesini seçin ve sağ bölmede **Yükle düğmesine** basın. Paketin yükleyerek proje başvurularınıza bir başvuru ekler.

Hala kırmızı dalgalı çizgiler görüyorsanız, giriş `ImmutableArray` işaretini bu tanımlayıcıya yerleştirip **CTRL** tuşuna basın + **.** (Period) önerilen çözüm menüsünü getirip uygun ifadeyi eklemeyi seçin `using` .

devam etmek için, **tümünü kaydedip** Visual Studio ikinci örneğini kapatın.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Düzenle ve devam et kullanarak çözümleyici 'yi tamamlama

ilk Visual Studio örneğinde, `AnalyzeObjectCreation` ilk satırdaki şapka işareti ile **F9** tuşuna basarak yönteminizin başlangıcında bir kesme noktası ayarlayın.

**F5** ile çözümleyicinizi yeniden başlatın ve Visual Studio ikinci örneğinde, son kez oluşturduğunuz konsol uygulamanızı yeniden açın.

roslyn derleyicisi bir nesne oluşturma ifadesi ve çözümleyicinizde çağırdığı için kesme noktasında Visual Studio ilk örneğine geri dönersiniz.

**Nesne oluşturma düğümünü alın.** İşaretçiyi `objectCreation` **F10** tuşuna basarak ayarlayan çizginin üzerinde Ilerleyin ve **komut penceresinde** ifadeyi değerlendirin `"objectCreation.ToString()"` . Değişkenin işaret ettiği söz dizimi düğümünün kodun olduğunu `"new ImmutableArray<int>()"` ve yalnızca aradığınızı görürsünüz.

**ImmutableArray<T \> türü nesnesi alın.** Oluşturulan türün ImmutableArray olup olmadığını kontrol etmeniz gerekir. İlk olarak, bu türü temsil eden nesneyi alırsınız. Doğru türe sahip olduğunuzdan emin olmak için türleri anlam modeli kullanarak kontrol edersiniz ve dizeyi ' den karşılaştırmayın `ToString()` . İşlevin sonuna aşağıdaki kod satırını girin:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Genel türleri, geri işaretleri (') ve genel parametre sayısı ile meta verilerde belirlersiniz. Bu nedenle "... Meta veri adında ImmutableArray \<T> ".

Anlam modeli, semboller, veri akışı, değişken ömür vb. hakkında sorular sormaya olanak tanıyan birçok yararlı şey içerir. Roslyn, çeşitli mühendislik nedenleri (performans, modelleme hatalı kodu vb.) için anlamsal modelden sözdizimi düğümlerini ayırır. Derleme modelinin, doğru karşılaştırma için başvurularda yer alan bilgileri araması istiyorsunuz.

Düzenleyici penceresinin sol tarafındaki Sarı yürütme işaretçisini sürükleyebilirsiniz. Bu öğeyi, `objectCreation` Yeni kod satırlarınızın **F10** kullanarak değişkenini ve adımını ayarlayan satıra sürükleyin. Fare işaretçisini değişkenin üzerine getirdiğinizde `immutableArrayOfType` anlamsal modelde tam türü bulduğumuz görürsünüz.

**Nesne oluşturma ifadesinin türünü alın.** "Tür" Bu makalede birkaç şekilde kullanılır, ancak bu, "yeni foo" ifadeniz varsa, foo modeli almanız gerektiği anlamına gelir. ImmutableArray türünde olup olmadığını görmek için nesne oluşturma ifadesinin türünü almanız gerekir \<T> . Nesne oluşturma ifadesinde tür sembolünün (ImmutableArray) sembol bilgisini almak için anlamsal modeli yeniden kullanın. İşlevin sonuna aşağıdaki kod satırını girin:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Çözümleyici 'nizin, düzenleyici arabelleklerinde tamamlanmamış veya hatalı kodu işlemesi gerektiğinden (örneğin, eksik bir `using` bildirim varsa), olduğunu denetlemeniz gerekir `symbolInfo` `null` . Çözümlemeyi bitirebilmeniz için sembol bilgisi nesnesinden adlandırılmış bir tür (INamedTypeSymbol) almanız gerekir.

**Türleri karşılaştırın.** Aradığımız açık genel bir T türü olduğundan ve koddaki tür somut genel bir tür olduğundan, türün oluşturulduğu öğe (açık genel bir tür) için simge bilgilerini sorgular ve bu sonucu ile karşılaştırın `immutableArrayOfTType` . Yönteminin sonuna şunu girin:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Tanılamayı bildirin.** Tanılamayı raporlama oldukça kolaydır. Başlangıç yönteminden önce tanımlanan proje şablonunda sizin için oluşturulan kuralı kullanırsınız. Koddaki bu durum bir hata olduğundan, başlatılan kuralı `DiagnosticSeverity.Warning` (yeşil dalgalı çizgi) ile değiştirecek şekilde `DiagnosticSeverity.Error` (kırmızı dalgalı çizgi) değiştirebilirsiniz. Kuralın geri kalanı, gözden geçirme başlangıcında düzenlediğiniz kaynaklardan başlatılır. Ayrıca, nesne oluşturma ifadesinin tür belirtiminin konumu olan dalgalı çizgi için konumu rapor etmeniz gerekir. Bu kodu `if` bloğa girin:

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

Çözümleyicisi 'nin çalışmasını görebilmeniz için kesme noktasını kaldırın (ve Visual Studio ilk örneğine döndürmeyi durdurabilirsiniz). Yürütme işaretçisini yönteminizin başlangıcına sürükleyin ve yürütmeye devam etmek için **F5** tuşuna basın. Visual Studio ikinci örneğine geri döndüğünüzde, derleyici kodu yeniden incelemek üzere başlatılır ve çözümleyici 'nize çağrı yapar. Altında dalgalı bir çizgi görebilirsiniz `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Kod sorunu için "kod onarımı" ekleme

başlamadan önce, Visual Studio ikinci örneğini kapatın ve Visual Studio ilk örneğindeki (çözümleyici 'yi geliştirdiğinizi) hata ayıklamayı durdurun.

**Yeni bir sınıf ekleyin.** **Çözüm Gezgini** proje düğümünüzde kısayol menüsünü (sağ işaretçi düğmesi) kullanın ve yeni bir öğe eklemeyi seçin. Adlı bir sınıf ekleyin `BuildCodeFixProvider` . Bu sınıfın ' den türetilmesi gerekir `CodeFixProvider` ve CTRL ' i kullanmanız gerekir  + **.** (Period) doğru ifadeyi ekleyen kod düzeltmesini çağırmak için `using` . Bu sınıfın Ayrıca özniteliğiyle açıklanması gerekir `ExportCodeFixProvider` ve `using` sabit listesini çözümlemek için bir ifade eklemeniz gerekir `LanguageNames` . Aşağıdaki kodu içeren bir sınıf dosyanız olmalıdır:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Türetilmiş üyeleri saplama.** Şimdi, düzenleyicinin giriş işaretini tanımlayıcıya yerleştirip `CodeFixProvider` **CTRL** tuşuna basın + **.** (nokta) bu soyut temel sınıf için uygulamayı saplama. Bu, sizin için bir özellik ve bir yöntem oluşturur.

**Özelliğini uygulayın.** `FixableDiagnosticIds`Özelliğin `get` gövdesini aşağıdaki kodla doldur:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn, yalnızca dizeler olan bu tanımlayıcıları eşleştirerek tanılama ve düzeltmeleri birlikte getirir. Proje şablonu sizin için bir tanılama KIMLIĞI üretti ve bunu değiştirebilirsiniz. Özelliğindeki kod yalnızca çözümleyici sınıfından KIMLIĞI döndürür.

**RegisterCodeFixAsync yöntemi bir bağlam alır.** Bağlam önemlidir çünkü bir kod düzeltilmesi birden çok tanılamada uygulanabilir veya bir kod satırında birden fazla sorun olabilir. "Bağlam" yazın. yöntemin gövdesinde, IntelliSense tamamlanma listesi size bazı faydalı Üyeler gösterecektir. Bir şeyin bir şeyi iptal etmek isteyip istemediğine bakmak için kontrol edeceğiniz bir CancellationToken üyesi vardır. Çok sayıda faydalı üyeye sahip bir belge üyesi var ve proje ve çözüm modeli nesnelerine erişmenizi sağlar. Tanılamayı bildirdiğiniz sırada belirtilen kod konumunun başlangıcı ve bitişi olan bir span üyesi vardır.

**Yöntemi zaman uyumsuz olarak yapın.** Yapmanız gereken ilk şey, oluşturulan Yöntem bildirimini bir yöntem olacak şekilde düzeltemedi `async` . Bir soyut sınıfın uygulamasını kalıntıları oluşturuluyor için kod düzeltilme `async` yöntemi, yöntem bir döndürüyor olsa bile anahtar sözcüğünü içermez `Task` .

**Sözdizimi ağacının kökünü alın.** Kodu değiştirmek için, kod Düzeltmelerinizin yaptığı değişikliklerle yeni bir sözdizimi ağacı oluşturmanız gerekir. ' İ `Document` çağırmak için bağlamınızın olması gerekir `GetSyntaxRootAsync` . Bu, büyük olasılıkla dosyayı diskten alma, ayrıştırma ve için Roslyn kod modelini oluşturma dahil olmak üzere sözdizimi ağacını almak için bilinmeyen bir iş olduğundan zaman uyumsuz bir yöntemdir. Visual Studio kullanıcı arabirimi bu süre boyunca yanıt vermesi gerekir, bu, tarafından `async` etkinleştirilir. Yöntemdeki kod satırını aşağıdaki gibi değiştirin:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Sorunu içeren düğümü bulun.** İçeriğin yayılma alanını geçirtirsiniz, ancak bulduğunuz düğüm değiştirmeniz istediğiniz kod olmayabilir. Bildirilen tanılama yalnızca tür tanımlayıcısı için (dalgalı çizgi 'nin ait olduğu) aralığı sağladıysa, ancak `new` başındaki anahtar sözcüğü ve sonundaki parantez dahil olmak üzere tüm nesne oluşturma ifadesini değiştirmeniz gerekir. Yöntemine aşağıdaki kodu ekleyin (ve **CTRL tuşunu** kullanın + **.** `using`için bir ifade eklemek için `ObjectCreationExpressionSyntax` :

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Ampul Kullanıcı arabirimi için kod düzeltmeinizi kaydedin.** kod düzeltmesini kaydettiğinizde, roslyn Visual Studio ampul kullanıcı arabirimine otomatik olarak takılır. Son kullanıcılar, **CTRL** kullanabilirler + **.** (Period) Çözümleyicisi dalgalı çizgiler bir hatalı `ImmutableArray<T>` Oluşturucu kullanır. Kod onarma sağlayıcınız yalnızca bir sorun olduğunda yürütüldüğü için, Aradığınız nesne oluşturma ifadesine sahip olduğunu varsayabilirsiniz. Bağlam parametresinden, yönteminin sonuna aşağıdaki kodu ekleyerek yeni kod düzeltmesini kaydedebilirsiniz `RegisterCodeFixAsync` :

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Düzenleyicinin giriş işaretini tanımlayıcıya yerleştirmeniz gerekir ve `CodeAction` ardından **CTRL tuşunu** kullanın + **.** (Period) `using` Bu tür için uygun deyimin eklenmesi.

Sonra, düzenleyicinin giriş işaretini `ChangeToImmutableArrayEmpty` tanımlayıcıya yerleştirip **CTRL** kullanın + **.** sizin için bu yöntem saplaması 'nı tekrar oluşturun.

Eklediğiniz bu son kod parçacığı, `CodeAction` bulunan sorun türü için bir ve tanılama kimliği geçirerek kod düzeltmesini kaydeder. Bu örnekte, bu kodun düzeltme sağladığı yalnızca bir tanılama KIMLIĞI vardır, bu yüzden yalnızca tanılama kimlikleri dizisinin ilk öğesini geçirebilirsiniz. `CodeAction`' I oluştururken, ampul Kullanıcı arabiriminin kod düzeltmesinin açıklaması olarak kullanması gereken metni geçirin. Ayrıca, CancellationToken alan ve yeni bir belge döndüren bir işlevi de geçitirsiniz. Yeni belge, çağıran kod eki eklenen kodunuzu içeren yeni bir sözdizimi ağacına sahiptir `ImmutableArray.Empty` . Bu kod parçacığı, Objectoluşturma düğümü ve bağlamın belgesi üzerinde kapatılabilir olması için bir lambda kullanır.

**Yeni sözdizimi ağacını oluşturun.** `ChangeToImmutableArrayEmpty`Daha önce oluşturduğunuz saplama yönteminde kod satırını girin: `ImmutableArray<int>.Empty;` . **Syntax Visualizer** araç penceresini yeniden görüntülediğinizde, bu söz dizimi bir Simplelememberaccessexpression düğümü olduğunu görebilirsiniz. Bu yöntem, bu yöntemin yeni bir belgeye oluşturulması ve döndürülmesi için gereken şeydir.

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

Düzenleyicinin giriş işaretini `SyntaxGenerator` tanımlayıcıda koymanız ve **CTRL**' i kullanmanız gerekir + **.** (Period) `using` Bu tür için uygun deyimin eklenmesi.

Bu kod `SyntaxGenerator` , yeni kod oluşturmak için kullanışlı bir tür olan kullanır. Kod sorunu olan belge için bir Oluşturucu aldıktan sonra, `ChangeToImmutableArrayEmpty` `MemberAccessExpression` erişim sağlamak istediğimiz üyeye sahip olan türü geçirerek bir dize olarak üyenin adını geçirerek.

Sonra, yöntemi belgenin kökünü getirir ve bu, genel durumda rastgele bir iş içerebileceği için, kod bu çağrıyı bekler ve iptal belirtecini geçirir. Roslyn kod modelleri, .NET dizesiyle çalışma gibi sabittir; dizeyi güncelleştirdiğinizde, dönerek yeni bir dize nesnesi alırsınız. `ReplaceNode`Öğesini çağırdığınızda yeni bir kök düğümü geri alırsınız. Sözdizimi ağacının çoğu paylaşılır (sabit olduğu için), ancak `objectCreation` düğüm, `memberAccess` sözdizimi ağaç köküne kadar olan tüm üst düğümleri ve düğüm ile değiştirilmiştir.

## <a name="try-your-code-fix"></a>Kod düzeltmesini deneyin

Artık **F5** 'e basarak Visual Studio ikinci bir örneğinde Çözümleyicisi gerçekleştirebilirsiniz. Daha önce kullandığınız konsol projesini açın. Şimdi yeni nesne oluşturma ifadeniz için olan ampul ' i görürsünüz `ImmutableArray<int>` . CTRL tuşuna basın  + **.** (nokta), daha sonra kod düzeltmesini görürsünüz ve ampul Kullanıcı arabiriminde otomatik olarak oluşturulan bir kod farkı önizlemesi görürsünüz. Roslyn bunu sizin için oluşturur.

**Pro ipucu:** Visual Studio ikinci örneğini başlatır ve kod düzeltmeinizle ampulü görmüyorsanız, Visual Studio bileşen önbelleğini temizlemeniz gerekebilir. önbelleğin temizlenmesi Visual Studio bileşenleri yeniden incelemek üzere zorlaştırılması için Visual Studio en son bileşeninizin olması gerekir. İlk olarak, Visual Studio ikinci örneğini kapatın. sonra, **Windows gezgini**' nde *%localappdata%\microsoft\visualstudio\16.0roslyn \\* dizinine gidin. ("16,0", sürümden sürüme Visual Studio olarak değişir.) *ComponentModelCache* alt dizinini silin.

## <a name="talk-video-and-finish-code-project"></a>Video ve son kod projesini konuşun

Bu örnekte geliştirilen ve daha ayrıntılı bilgi için bu [konuşmayı](https://channel9.msdn.com/events/Build/2015/3-725)görebilirsiniz. Konuş, çalışma çözümleyicisini gösterir ve bunu oluşturmak için size yol gösterir.

Tamamlanan tüm kodu [buradan](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)görebilirsiniz. *donotuseimmutablearraycollectionbaşlatıcısı* ve *donotuseimmutablearrayctor* alt klasörlerinin her biri, sorunları bulmak için bir c# dosyasına ve Visual Studio ampul kullanıcı arabiriminde görünen kod düzeltmelerini uygulayan bir c# dosyasına sahiptir. Bu, tamamlanmış kodun, ImmutableArray türü nesnesini ve üzerine getirmeyi önlemek için biraz daha soyutlama olduğunu göz önüne alın \<T> . Tür nesnesini, alt eylemler (nesne oluşturmayı çözümle ve koleksiyon başlatmaları çözümle) yürütüher seferinde kullanılabilir bir bağlamda kaydetmek için iç içe kaydedilmiş eylemleri kullanır.

## <a name="see-also"></a>Ayrıca bkz.

* [\\\Build 2015 Talk](https://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub tamamlanan kod](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [GitHub birçok örnek, üç tür çözümleyiciler halinde gruplandırılır](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS sitesindeki diğer belgeler](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [GitHub 'de Roslyn Çözümleyicileri ile uygulanan FxCop kuralları](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
