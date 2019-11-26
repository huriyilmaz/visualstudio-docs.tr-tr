---
title: .NET kullanarak 4.x Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: conceptual
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 01363ab1588507f31dc74800c85b159039c9bab6
ms.sourcegitcommit: 9c7d8693108ecd2042a70c04cebe3c44af657baf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74239429"
---
# <a name="using-net-4x-in-unity"></a>.NET kullanarak 4.x Unity

C# ve .NET, Unity betik, temel alınan teknoloji 2002'de, bunları başlangıçta Microsoft yayımlanan bu yana güncelleştirmeleri almaya devam etti. Ancak, Unity geliştiricilerinin .NET Framework ve C# dili için eklenen yeni özellikler gitmenize haberdar olmayabilir. Unity 2017.1 önce bir .NET yıl güncelleştirmelerin eksik 3.5 scripting çalışma zamanı, eşdeğer Unity kullanıyor olmasıdır.

Unity 2017.1 sürümünden, Unity, Deneysel bir C# 6 uyumlu sürümü, bir .NET 4.6 yükseltme komut dosyası, çalışma zamanı sürümü kullanıma sunuldu. Unity 2018.1 .NET 4.x eşdeğer çalışma zamanı artık eşdeğer çalışma zamanı artık eski bir sürüm olarak kabul edilir daha eski .NET 3.5 sırasında Deneysel olarak kabul edilir. Ve Unity 2018.3'ın yayınlanmasıyla birlikte, Unity yükseltilmiş bir komut dosyası çalışma zamanı varsayılan seçimi yapın ve hatta C# 7 daha fazla sınırlandıramazsınız güncelleştirmek için edeceğini öngörüyor. Bu yol haritasında daha fazla bilgi ve en son güncelleştirmeler için Unity 'nin [blog postasını](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) okuyun veya [deneysel betik önizlemeleri forumunu](https://forum.unity.com/forums/experimental-scripting-previews.107/)ziyaret edin. Bu sırada, aşağıdaki bölümlere .NET 4.x komut dosyası çalışma zamanıyla artık kullanılabilir yeni özellikler hakkında daha fazla bilgi için göz atın.

## <a name="prerequisites"></a>Önkoşullar

* [Unity 2017,1 veya üzeri](https://unity3d.com/) (2018,2 önerilir)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>.NET 4.x komut dosyası çalışma zamanı Unity etkinleştirme

.NET 4.x komut dosyası çalışma zamanı'nı etkinleştirmek için aşağıdaki adımları uygulayın:

1. **> proje ayarlarını düzenle > oynatıcı**' yı seçerek Unity denetçisinde playersettings ' i açın.

1. **Yapılandırma** başlığı altında, **komut dosyası çalışma zamanı sürüm** açılan listesine tıklayın ve **.NET 4. x eşdeğerini**seçin. Unity yeniden başlatmanız istenir.

![.NET 4.x eşdeğer seçin](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Seçme arasında .NET 4.x ve .NET Standard 2.0 profilleri

.NET 4. x eşdeğer betik çalışma zamanına geçiş yaptıktan sonra, PlayerSettings ( **> proje ayarlarını düzenle > Player**) açılır menüsünü kullanarak **API uyumluluk düzeyini** belirtebilirsiniz. İki seçenek vardır:

* **.NET Standard 2,0**. Bu profil, .NET Foundation tarafından yayımlanan [.NET Standard 2,0 profiliyle](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) eşleşir. Unity için yeni projeler .NET Standard 2.0 önerir. .NET küçük olan 4.x, boyutu kısıtlı platformlar için avantajlıdır. Ayrıca, bu profili destek Unity destekleyen tüm platformlarda Unity kaydoldu.

* **.NET 4. x**. Bu profil en son .NET 4 API'sine erişim sağlar. .NET Framework sınıf kitaplıkları tüm mevcut kodlar içerir ve .NET Standard 2.0 profillerini destekler. .NET Standard 2.0 profile dahil edilmemiş API parçası, projenizin gerektirdiği .NET 4.x profili kullanın. Ancak, bu API bazı bölümlerini tüm platformlarda Unity'nın desteklenmiyor olabilir.

Bu seçenekler hakkında daha fazla bilgi için Unity 'nin [Blog](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)gönderisine erişebilirsiniz.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>.NET kullanarak derleme başvurularını eklemeyi 4.x API uyumluluk düzeyi

**API Uyumluluk düzeyi** açılan menüsünde .NET Standard 2,0 ayarını KULLANıRKEN, API profilindeki tüm derlemelere başvurulur ve kullanılabilir. Ancak, daha büyük bir .NET 4.x profil kullanılırken, Unity ile birlikte gelen derlemelerden bazıları varsayılan olarak başvurulan değildir. Bu API'leri kullanmak için elle bir bütünleştirilmiş kod başvurusu eklemeniz gerekir. Unity 'nin birlikte bulunan derlemelerini, Unity Düzenleyicisi yüklemenizin **MonoBleedingEdge/lib/mono** dizininde görüntüleyebilirsiniz:

![MonoBleedingEdge dizini](media/vstu_monobleedingedge.png)

Örneğin, .NET 4. x profilini kullanıyorsanız ve `HttpClient`kullanmak istiyorsanız, System. net. http. dll için bir derleme başvurusu eklemeniz gerekir. Bu olmadan, derleyici bir bütünleştirilmiş kod başvurusu eksik Şikayet:

![Eksik derleme başvurusu](media/vstu_missing-reference.png)

Visual Studio Unity projeleri için .csproj ve .sln dosyaları, açtığınız her durumda yeniden oluşturur. Sonuç olarak, projeyi yeniden açmayı üzerine kayıp çünkü, doğrudan Visual Studio'da derleme başvurularını ekleyemezsiniz. Bunun yerine, **MCS. rsp** adlı özel bir metin dosyası kullanılmalıdır:

1. Unity projenizin kök **varlıklar** dizininde **MCS. rsp** adlı yeni bir metin dosyası oluşturun.

1. Boş metin dosyasının ilk satırında, şunu girin: `-r:System.Net.Http.dll` ve ardından dosyayı kaydedin. Dahil edilen derlemeler ile bir başvuru eksik olabilir, "System.Net.Http.dll" değiştirebilirsiniz.

1. Unity Düzenleyicisi'ni yeniden başlatın.

## <a name="taking-advantage-of-net-compatibility"></a>.NET uyumluluğu yararlanma

Yeni C# sözdizimi ve dil özelliklerin yanı sıra .NET 4.x komut dosyası çalışma zamanı Unity kullanıcılar eski .NET 3.5 komut dosyası çalışma zamanı ile uyumsuz .NET paket çok büyük bir kitaplık erişmenizi sağlar.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Paketleri Nuget'ten Unity projeye ekleyin.

[NuGet](https://www.nuget.org/) , .NET için paket yöneticisidir. NuGet, Visual Studio'da tümleşiktir. Ancak, Unity projeleri NuGet paketleri eklemek için özel bir işlem gerektirir. Unity içinde bir proje açtığınızda Visual Studio Proje dosyalarının yeniden oluşturulur, gerekli yapılandırmaları geri alma olmasıdır. Bir paket, Unity projesi için aşağıdakileri yapın Nuget'ten eklemek için:

1. NuGet, eklemek istediğiniz uyumlu bir paketi bulmak için Gözat (.NET Standard 2.0 ya da .NET 4.x). Bu örnek, .NET Standard 2,0 projesine JSON ile çalışmaya yönelik popüler bir paket olan [JSON.net](https://www.nuget.org/packages/Newtonsoft.Json/)eklemeyi gösterir.

1. **İndir** düğmesine tıklayın:

    ![indir düğmesi](media/vstu_nuget-download.png)

1. İndirilen dosyayı bulun ve uzantıyı **. nupkg** konumundan **. zip**olarak değiştirin.

1. ZIP dosyası içinde **lib/Netstandard 2.0** dizinine gidin ve **Newtonsoft. JSON. dll** dosyasını kopyalayın.

1. Unity projenizin kök **varlıklar** klasöründe, **Eklentiler**adlı yeni bir klasör oluşturun. Eklentiler bir Unity özel klasör addır. Daha fazla bilgi için [Unity belgelerine](https://docs.unity3d.com/Manual/Plugins.html) bakın.

1. **Newtonsoft. JSON. dll** dosyasını Unity projenizin **Eklentiler** dizinine yapıştırın.

1. Unity projenizin **varlıklar** dizininde **Link. xml** adlı bir dosya oluşturun ve aşağıdaki XML 'i ekleyin.  Bu, Unity'nın bayt şeridi oluşturma işlemi bir ıl2cpp platformu verirken gerekli verileri kaldırmaz garanti eder.  Bu adım bu kitaplığın belirli olsa da, yansıma benzer şekillerde kullandığınız diğer kitaplıklarla sorunlar çalıştırabilirsiniz.  Daha fazla bilgi için lütfen bu konudaki [Unity 'nin docs](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) bölümüne bakın.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Olan her şeyi yerinde, artık Json.NET paketini kullanabilirsiniz.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Bu, bağımlılıkları olan bir kitaplık kullanılarak, basit bir örnektir. NuGet paketleri kullanan diğer NuGet paketleri, bu bağımlılıkları el ile indirin ve aynı şekilde projeye eklemek gerekir.

## <a name="new-syntax-and-language-features"></a>Yeni söz dizimi ve dil özellikleri

Güncelleştirilmiş komut dosyası çalışma zamanı'nı kullanarak C# 6 ve çok sayıda yeni dil özellikleri ve söz dizimi için Unity geliştiricileri erişmenizi sağlar.

### <a name="auto-property-initializers"></a>Otomatik-özellik başlatıcıları

Unity'nın .NET 3.5 komut dosyası çalışma zamanı, otomatik özelliği söz dizimi başlatılmamış özelliklere hızlıca tanımlamak kolaylaştırır, ancak başlatma betiğinizde başka bir yerde olması gerekir. Artık .NET 4.x çalışma zamanı ile aynı satırda otomatik özelliklerde başlatmak mümkündür:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Dize ilişkilendirme

Eski .NET 3.5 çalışma zamanı ile dize birleştirme garip sözdizimi gereklidir. Artık .NET 4. x çalışma zamanı ile [`$` dize ilişkilendirme](https://docs.microsoft.com/dotnet/csharp/language-reference/tokens/interpolated) özelliği, ifadelerin daha doğrudan ve okunabilir bir sözdiziminde dizelere eklenmesine izin verir:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>İfade gövdeli üyeler

.NET 4. C# x çalışma zamanı 'nda daha yeni sözdizimi bulunan [lambda ifadeleri](https://docs.microsoft.com/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) , işlevlerin gövdesini daha kısa yapmak için değiştirebilir:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

İfade gövdeli üyeler salt okunur özellikler de kullanabilirsiniz:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Görev Tabanlı Zaman Uyumsuz Desen (TAP)

Zaman [uyumsuz programlama](https://docs.microsoft.com/dotnet/csharp/async) , uygulamanızın yanıt vermemesine neden olmadan zaman alma işlemlerinin gerçekleşmesini sağlar. Bu işlev, bu işlemlerin sonuçlarına bağlı olan kod devam etmeden önce tamamlanması uzun süren işlemleri için beklenecek kodunuzu de sağlar. Örneğin, bir dosyaya yük ya da bir ağ işlemin tamamlanmasını bekleyebilir.

Unity 'de, zaman uyumsuz programlama genellikle [eş](https://docs.unity3d.com/Manual/Coroutines.html)yordamlar ile gerçekleştirilir. Ancak, 5 C# ' den itibaren, .net geliştirmede zaman uyumsuz programlama için tercih edilen yöntem, [System. Threading. Task](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task)ile `async` ve `await` anahtar sözcüklerini kullanarak [görev tabanlı zaman uyumsuz bir modeldir (dokunun)](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) . Özet ' te, bir `async` işlevinde, uygulamanızın geri kalanını güncelleştirmeden önce bir görevin tamamlanmasını `await`:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

DOKUNUN karmaşık bir konu, geliştiricilerin düşünmelisiniz Unity özgü farklılıklarına sahip olur. Sonuç olarak, DOKUNUN Unity oluşturucuda Evrensel bir ardılı değildir; Ancak, yararlanarak başka bir araçtır. Bu özelliğin kapsamı dışında bu makalede, ancak bazı genel en iyi uygulamalar ve ipuçları aşağıda verilmiştir.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Unity DOKUNARAK için başlatılan bir başvuru alma

Bu ipuçlarını Unity TAP kullanmaya başlamanıza yardımcı olabilir:

* Beklenmeye yönelik olarak beklenen zaman uyumsuz işlevlerin dönüş türü [`Task`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task) veya [`Task<TResult>`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task-1)olmalıdır.
* Bir görevi döndüren zaman uyumsuz işlevlerin adlarına **"Async"** soneki eklenmiş olması gerekir. "Async" soneki yardımcı olan bir işlev her zaman beklenmesini gösterir.
* Yalnızca geleneksel zaman uyumlu koddan zaman uyumsuz işlevleri harekete geçirme işlevleri için `async void` dönüş türünü kullanın. Bu tür işlevleri kendilerini beklenemez ve "Async" soneki adlarında olmamalıdır.
* Unity UnitySynchronizationContext zaman uyumsuz işlevleri, varsayılan olarak ana iş parçacığında çalışır emin olmak için kullanır. Unity API ana iş parçacığı dışında erişilebilir değildir.
* [`Task.Run`](https://msdn.microsoft.com/library/hh195051.aspx) ve [`Task.ConfigureAwait(false)`](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx)gibi yöntemlerle arka plan iş parçacıklarında görevler çalıştırmak mümkündür. Bu ana iş parçacığından performansı artırmak için pahalı işlemler boşaltılması için kullanışlı bir tekniktir. Ancak, arka plan iş parçacıklarını kullanmak, [yarış durumları](https://wikipedia.org/wiki/Race_condition)gibi hata ayıklama zor olan sorunlara yol açabilir.
* Unity API ana iş parçacığı dışında erişilebilir değildir.
* Kullanım iş parçacıkları üzerinde Unity WebGL desteklenmeyen görevleri oluşturur.

#### <a name="differences-between-coroutines-and-tap"></a>Eş yordamlar DOKUNUN arasındaki farklar

Eş yordamlar ve DOKUNUN arasında bazı önemli farklar vardır / async-await:

* Coroutines değer döndüremez, ancak `Task<TResult>` olabilir.
* Try-catch ifadesine bir `yield` koyamazsınız, bu işlem, eş yordamlar ile hata işleme zorlaştırılması gerekir. Ancak, try-catch DOKUNARAK çalışır.
* MonoBehaviour türetilen olmayan sınıflarda Unity'nın eş yordam özelliği kullanılamaz. DOKUNUN, zaman uyumsuz programlama bu tür sınıflar için mükemmeldir.
* Bu noktada, Unity DOKUNUN önermek ve bu da bir eş yordamlar toptan yerine değil. Profil oluşturma ve diğer herhangi bir proje için bir yaklaşım belirli sonuçları bilmek tek yoludur.

> [!NOTE]
> Unity 2018,2 itibariyle, kesme noktaları ile zaman uyumsuz yöntemlerin hata ayıklaması tam olarak desteklenmez; Ancak, [Bu Işlevsellik Unity 2018,3 ' de beklenmektedir](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof işleci

`nameof` işleci bir değişkenin, türün veya üyenin dize adını alır. `nameof` yararlı olan bazı durumlar, günlüğe kaydetme hatalarından oluşur ve bir sabit listesinin dize adını alma:

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Arayan bilgileri öznitelikleri

[Çağıran bilgi öznitelikleri](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/caller-information) bir yöntemin çağıranı hakkında bilgi sağlar. Çağıran bilgisi özniteliği ile kullanmak istediğiniz her parametre için varsayılan bir değer sağlamanız gerekir:

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>' Using static

[Statik kullanmak](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/using-static) , sınıf adını yazmadan statik işlevleri kullanmanıza olanak sağlar. Aynı sınıftaki statik çeşitli işlevler kullanmanız gerekirse statik kullanarak, alan ve zaman kaydedebilirsiniz:

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Il2cpp konuları

Oyununuzu iOS gibi platformlarda verirken, Unity kendi ıl2cpp altyapısına "derleyin" IL ardından hedef platformu yerel derleyiciyi kullanarak derlenmiş C++ kodu için kullanır. Bu senaryoda, yansıma parçaları ve `dynamic` anahtar sözcüğünün kullanımı gibi desteklenmeyen çeşitli .NET özellikleri vardır. Kendi kodunuzda bu özellikleri kullanmaya kontrol edebilirsiniz, ancak sorunlar ıl2cpp ve Unity ile göz önünde 3. parti DLL'ler ve değil yazılan SDK'ları kullanarak çalıştırabilirsiniz. Bu konu hakkında daha fazla bilgi için lütfen Unity 'nin sitesindeki [betik kısıtlamaları](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) belgelerine bakın.

Ayrıca, yukarıdaki Json.NET örnekte belirtildiği gibi Unity kullanılmayan kodu ıl2cpp dışarı aktarma işlemi sırasında Şerit dener.  Bu genellikle bir sorun olmasa da, yansıma kullanan kitaplıklar sayesinde, yanlışlıkla dışa aktarma zamanında belirlenemeyecek çalışma zamanında çağrılacak özellikleri veya yöntemleri açabilir.  Bu sorunları gidermek için, projenize, ortaya çıkan işlemi çalıştırmayan derlemelerin ve ad alanlarının bir listesini içeren bir **Link. xml** dosyası ekleyin.  Tam Ayrıntılar için lütfen bkz. [Unity 'nin belge bytecode üzerinde çaba](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html)

## <a name="net-4x-sample-unity-project"></a>.NET 4.x örnek Unity projesi

Örnek, çeşitli .NET 4.x özellikleri örnekleri içerir. Projeyi indirebilir veya [GitHub](https://github.com/Microsoft/unity-scripting-upgrade)'da kaynak kodu görüntüleyebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

* [Unity blog-betik oluşturma çalışma zamanı geliştirmeleri 2018,2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [GeçmişiC#](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-version-history)
* [6 ' daki C# yenilikler](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-6)
* [Unity 'de eş zamanlı olmayan programlama, Coroutine ve TAP 'ı kullanma](https://blogs.msdn.microsoft.com/appconsult/2017/09/01/unity-coroutine-tap)
* [Unity 2017 ' de eş zamanlı olmayan-await](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Unity Forumu-deneysel betik önizlemeleri](https://forum.unity.com/forums/experimental-scripting-previews.107/)
