---
title: Unity’de .NET 4.x kullanma
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: conceptual
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 5fb521ff1769f1d742dc1ce67080e98aecb417ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75944232"
---
# <a name="using-net-4x-in-unity"></a>Unity’de .NET 4.x kullanma

Unity komut dosyasının altında yatan teknolojiler olan C# ve .NET, Microsoft'un bunları ilk olarak 2002'de yayımladığından beri güncelleştirmeleri almaya devam etti. Ancak Unity geliştiricileri, C# dili ve .NET Framework'e eklenen yeni özelliklerin sürekli akışının farkında olmayabilir. Bunun nedeni, Unity 2017.1'den önce Unity'nin .NET 3,5 eşdeğer komut dosyası çalışma zamanı, eksik yıllar güncelleştirmeleri kullanmasıdır.

Unity 2017.1'in yayınlanmasıyla birlikte Unity, komut dosyası çalışma zamanının deneysel bir sürümünü .NET 4.6, C# 6 uyumlu bir sürüme yükseltti. Unity 2018.1'de .NET 4.x eşdeğer çalışma süresi artık deneysel olarak kabul edilmezken, eski .NET 3.5 eşdeğer çalışma süresi artık eski sürüm olarak kabul edilir. Unity 2018.3'ün yayınlanmasıyla birlikte Unity, yükseltilmiş komut dosyası çalışma süresini varsayılan seçim haline getirmeyi ve C# 7'ye daha da güncelleştirilmelerini hedefliyor. Daha fazla bilgi ve bu yol haritasındaki en son güncellemeler için Unity'nin [blog gönderisini](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) okuyun veya [Deneysel Komut Dosyası Önizlemeleri forumunu](https://forum.unity.com/forums/experimental-scripting-previews.107/)ziyaret edin. Bu arada, .NET 4.x komut dosyası çalışma süresi ile şimdi mevcut yeni özellikler hakkında daha fazla bilgi edinmek için aşağıdaki bölümlere göz atın.

## <a name="prerequisites"></a>Önkoşullar

* [Birlik 2017.1 ve üzeri](https://unity3d.com/) (2018.2 önerilir)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Unity'de .NET 4.x komut dosyası çalışma süresini etkinleştirme

.NET 4.x komut dosyası çalışma süresini etkinleştirmek için aşağıdaki adımları izleyin:

1. Oyuncu > > **Proje Ayarlarını Edit'i**seçerek Birlik Denetçisi'nde PlayerSettings'i açın.

1. **Yapılandırma** başlığı altında, **Komut Dosyası Çalışma Zamanı Sürümü** açılır dosyasını tıklatın ve **.NET 4.x Equivalent'yi**seçin. Birlik'i yeniden başlatmanız istenir.

![.NET 4.x eşdeğerini seçin](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>.NET 4.x ve .NET Standart 2.0 profilleri arasında seçim

.NET 4.x eşdeğer komut dosyası çalışma süresine geçtikten sonra, Player Settings **(> Proje Ayarlarını > Player)** açılır menüsünü kullanarak **Api Uyumluluk Düzeyini** belirtebilirsiniz. İki seçenek vardır:

* **.NET Standart 2.0**. Bu profil, .NET Foundation tarafından yayınlanan [.NET Standart 2.0 profiliyle](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) eşleşir. Unity, yeni projeler için .NET Standard 2.0 önerir. Boyut kısıtlamalı platformlar için avantajlı olan .NET 4.x'ten daha küçüktür. Ayrıca, Unity, Bu profili Birliğin desteklediği tüm platformlarda desteklemeyi taahhüt etmiştir.

* **.NET 4.x**. Bu profil en son .NET 4 API'sine erişim sağlar. .NET Framework sınıf kitaplıklarında bulunan tüm kodu içerir ve .NET Standart 2.0 profillerini de destekler. Projeniz .NET Standart 2.0 profilinde yer almayan API'nin bir parçasını gerektiriyorsa .NET 4.x profilini kullanın. Ancak, bu API'nin bazı bölümleri Birlik'in tüm platformlarında desteklenmeyebilir.

Unity'nin [blog gönderisinde](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)bu seçenekler hakkında daha fazla bilgi edinebilirsiniz.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>.NET 4.x Api Uyumluluk Düzeyini kullanırken montaj başvuruları ekleme

**Api Uyumluluk Düzeyi** açılır sayısındaki .NET Standart 2.0 ayarını kullanırken, API profilindeki tüm derlemeler başvurulur ve kullanılabilir. Ancak, daha büyük .NET 4.x profilini kullanırken, Unity gemilerinin bulunduğu bazı derlemeler varsayılan olarak başvurulmaz. Bu API'leri kullanmak için, bir derleme başvurusu el ile eklemeniz gerekir. Unity editör kurulumunuzun **MonoBleedingEdge/lib/mono** dizininde Unity gemi derlemelerini görüntüleyebilirsiniz:

![MonoBleedingEdge dizini](media/vstu_monobleedingedge.png)

Örneğin, .NET 4.x profilini kullanıyorsanız ve kullanmak `HttpClient`istiyorsanız System.Net.Http.dll için bir montaj başvurusu eklemeniz gerekir. Onsuz, derleyici bir derleme başvurusu eksik şikayet edecektir:

![eksik montaj başvurusu](media/vstu_missing-reference.png)

Visual Studio, her açıldığında Unity projeleri için .csproj ve .sln dosyalarını yeniler. Sonuç olarak, doğrudan Visual Studio'ya montaj başvuruları ekleyemezsiniz, çünkü projeyi yeniden açtıktan sonra kaybolurlar. Bunun yerine, **mcs.rsp** adlı özel bir metin dosyası kullanılmalıdır:

1. Unity projenizin kök **Varlıklar** dizininde **mcs.rsp** adlı yeni bir metin dosyası oluşturun.

1. Boş metin dosyasındaki ilk satıra `-r:System.Net.Http.dll` girin: ve sonra dosyayı kaydedin. "System.Net.Http.dll"i, bir başvuru eksik olabilecek herhangi bir dahil derlemeyle değiştirebilirsiniz.

1. Unity düzenleyicisini yeniden başlatın.

## <a name="taking-advantage-of-net-compatibility"></a>.NET uyumluluğundan yararlanma

Yeni C# sözdizimi ve dil özelliklerine ek olarak, .NET 4.x komut dosyası oluşturma çalışma süresi, Unity kullanıcılarına eski .NET 3.5 komut dosyası çalışma süresiyle uyumsuz olan büyük bir .NET paketleri kitaplığına erişim sağlar.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>NuGet'den Bir Birlik projesine paket ekleme

[NuGet](https://www.nuget.org/) ,NET'in paket yöneticisidir. NuGet Visual Studio entegre edilmiştir. Ancak, Unity projeleri NuGet paketleri eklemek için özel bir işlem gerektirir. Bunun nedeni, Unity'de bir proje açtığınızda, Visual Studio proje dosyalarının yeniden oluşturulması ve gerekli yapılandırmaların geri alınmasıdır. NuGet'den Birlik projenize bir paket eklemek için aşağıdakileri yapın:

1. Eklemek istediğiniz uyumlu bir paketi bulmak için NuGet'e göz atın (.NET Standart 2.0 veya .NET 4.x). Bu örnek, JSON ile çalışmak için popüler bir paket olan [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/).NET Standart 2.0 projesine eklemeyi gösterir.

1. **İndir** düğmesine tıklayın:

    ![indirme düğmesi](media/vstu_nuget-download.png)

1. İndirilen dosyayı bulun ve uzantıyı **.nupkg'dan** **.zip'e**değiştirin.

1. Zip dosyası içinde, **lib/netstandard2.0** dizinine gidin ve **Newtonsoft.Json.dll** dosyasını kopyalayın.

1. Unity projenizin kök **Varlıklar** klasöründe **Eklentiler**adlı yeni bir klasör oluşturun. Eklentiler Unity'de özel bir klasör adıdır. Daha fazla bilgi için [Birlik belgelerine](https://docs.unity3d.com/Manual/Plugins.html) bakın.

1. **Newtonsoft.Json.dll** dosyasını Unity projenizin **Eklentileri** dizinine yapıştırın.

1. Unity projenizin **Varlıklar** dizininde **link.xml** adlı bir dosya oluşturun ve aşağıdaki XML'yi ekleyin.  Bu, Unity'nin bytecode sıyırma işleminin il2CPP platformuna dışa aktarırken gerekli verileri kaldırmamasını sağlar.  Bu adım bu kitaplığa özgü olsa da, Yansıma'yı benzer şekillerde kullanan diğer kitaplıklarla ilgili sorunlarla karşılaşabilirsiniz.  Daha fazla bilgi için lütfen bu konuda [Birlik'in dokümanlarına](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) bakın.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Her şey yerinde, artık Json.NET paketi kullanabilirsiniz.

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

Bu, bağımlılıkları olmayan bir kitaplık kullanmanın basit bir örneğidir. NuGet paketleri diğer NuGet paketlerine güvendiğinde, bu bağımlılıkları el ile indirmeniz ve projeye aynı şekilde eklemeniz gerekir.

## <a name="new-syntax-and-language-features"></a>Yeni sözdizimi ve dil özellikleri

Güncelleştirilmiş komut dosyası çalışma süresini kullanmak, Unity geliştiricilerinc# 6'ya ve bir dizi yeni dil özelliğine ve sözdizimine erişmelerini sağlar.

### <a name="auto-property-initializers"></a>Otomatik özellik başlangıç layıcıları

Unity'nin .NET 3.5 komut dosyası çalışma zamanında, otomatik özellik sözdizimi başharfe sahip olmayan özellikleri hızlı bir şekilde tanımlamayı kolaylaştırır, ancak başlatma komut dosyanızın başka bir yerinde gerçekleşmesi zorunludur. Şimdi .NET 4.x çalışma süresi ile, otomatik özellikleri aynı satırda başlatma mümkündür:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Dize ilişkilendirme

Eski .NET 3.5 çalışma süresi ile, dize concatenation garip sözdizimi gerekli. Şimdi .NET 4.x çalışma süresi ile, [ `$` string enterpolasyon](/dotnet/csharp/language-reference/tokens/interpolated) özelliği ifadeler daha doğrudan ve okunabilir sözdizimi dizeleri içine eklenmesini sağlar:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>İfade gövdeli üyeler

.NET 4.x çalışma zamanında bulunan yeni C# sözdizimi ile [lambda ifadeleri](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) işlevlerin gövdesini değiştirerek daha kısa bir şekilde kullanabilir:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

İfade gövdeli üyeleri salt okunur özelliklerde de kullanabilirsiniz:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Görev Tabanlı Zaman Uyumsuz Desen (TAP)

[Eş zamanlı programlama,](/dotnet/csharp/async) uygulamanızın yanıt vermemesine neden olmadan zaman alıcı işlemlerin gerçekleşmesini sağlar. Bu işlevsellik, kodun uzun süren işlemlerin tamamlanmasını beklemesine de olanak tanır ve bu işlemlerin sonuçlarına bağlı olarak kodla devam eder. Örneğin, bir dosyanın yüklenmesini veya ağ işleminin tamamlanmasını bekleyebilirsiniz.

Unity'de, asynchronous programlama genellikle [ortak yordamlarla](https://docs.unity3d.com/Manual/Coroutines.html)gerçekleştirilir. Ancak C# 5'ten bu yana .NET geliştirmede tercih edilen eşzamanlı programlama yöntemi [System.Threading.Task](/dotnet/api/system.threading.tasks.task)ile `async` `await` birlikte Görev [Tabanlı Asynchronous Pattern (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) ve anahtar kelimeler olmuştur. Özetle, bir `async` işlevde `await` uygulamanızın geri kalanının güncellenmesini engellemeden görevin tamamlanmasını sağlayabilirsiniz:

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

TAP karmaşık bir konudur, Birlik özgü nüansları geliştiriciler dikkate almalıdır. Sonuç olarak, TAP Birlik'teki ortak yordamların evrensel bir yerine değildir; ancak, kaldıraç için başka bir araçtır. Bu özelliğin kapsamı bu makalenin ötesindedir, ancak bazı genel en iyi uygulamalar ve ipuçları aşağıda verilmiştir.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Unity ile TAP için referans almaya başlama

Bu ipuçları, TAP in Unity ile başlamanıza yardımcı olabilir:

* Beklenen asenkron fonksiyonlar dönüş türüne [`Task`](/dotnet/api/system.threading.tasks.task) veya [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1).
* Bir görevi döndüren eşendin işlevleri, adlarına **"Async"** sonekini eklemelidir. "Async" soneki, bir işlevin her zaman beklenen olması gerektiğini gösterir yardımcı olur.
* Yalnızca geleneksel `async void` senkron koddan async işlevlerini ateşleyen işlevler için dönüş türünü kullanın. Bu tür işlevler kendilerini bekleyemez ve adlarında "Async" soneki olmamalıdır.
* Unity, async işlevlerinin varsayılan olarak ana iş parçacığı üzerinde çalışmasını sağlamak için UnitySynchronizationContext'ı kullanır. Unity API'ye ana iş parçacığı nın dışında erişilemez.
* Arka plan iş parçacıklarındaki görevleri gibi [`Task.Run`](https://msdn.microsoft.com/library/hh195051.aspx) yöntemlerle [`Task.ConfigureAwait(false)`](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx)çalıştırmak mümkündür. Bu teknik, performansı artırmak için ana iş parçacığından pahalı işlemleri boşaltmak için yararlıdır. Ancak, arka plan iş parçacığı [kullanmak, hata](https://wikipedia.org/wiki/Race_condition)ayıklamanın zor olduğu, yarış koşulları gibi sorunlara yol açabilir.
* Unity API'ye ana iş parçacığı dışında erişilemez.
* İş parçacığı kullanan görevler Unity WebGL oluşturur desteklenmez.

#### <a name="differences-between-coroutines-and-tap"></a>Ortak yordamlar ve TAP arasındaki farklar

Coroutines ve TAP / async-await arasında bazı önemli farklılıklar vardır:

* Eş yordamlar değerleri döndüremez, ancak `Task<TResult>` döndürebilir.
* Bir try-catch deyimi `yield` koyarak, ortak yordamlarla hata işlemeyi zorlaştıramazsınız. Ancak, try-catch TAP ile çalışır.
* Unity'nin ortak yordam özelliği, MonoBehaviour'tan türeyen sınıflarda kullanılamaz. TAP bu tür sınıflarda eşzamanlı programlama için harika.
* Bu noktada, Unity, TAP'ın ortak yordamların toptan yerine değiştirilmesini önermez. Profil oluşturma, belirli bir proje için bir yaklaşımın belirli sonuçlarını diğerine karşı bilmenin tek yoludur.

> [!NOTE]
> Unity 2018.2 itibariyle, mola noktaları ile async yöntemleri hata ayıklama tam olarak desteklenmez; ancak [bu işlevselliğin Unity 2018.3'te olması beklenmektedir.](https://twitter.com/jbevain/status/900043560665235456)

### <a name="nameof-operator"></a>nameof işleci

İşleç, `nameof` bir değişkenin, yazın veya üyenin dize adını alır. Kullanışlı olduğu `nameof` bazı durumlarda günlük hataları ve bir enum dize adını almak vardır:

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

### <a name="caller-info-attributes"></a>Arayan bilgi öznitelikleri

[Arayan bilgi öznitelikleri,](/dotnet/csharp/programming-guide/concepts/caller-information) bir yöntemin arayanı çağıran hakkında bilgi sağlar. Arayan Bilgileri özniteliği yle kullanmak istediğiniz her parametre için varsayılan değer sağlamanız gerekir:

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

### <a name="using-static"></a>Statik kullanma

[Statik kullanarak](/dotnet/csharp/language-reference/keywords/using-static) sınıf adını yazmadan statik işlevleri kullanmanıza olanak sağlar. Statik kullanarak, aynı sınıftan birkaç statik işlev kullanmanız gerekiyorsa, zaman ve zaman tasarrufu yapabilirsiniz:

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

## <a name="il2cpp-considerations"></a>IL2CPP Hususlar

Oyununuzu iOS gibi platformlara dışa aktarırken, Unity IL2CPP motorunu kullanarak IL2CPP motorunu kullanarak IL'den C++ koduna "transpile" ve daha sonra hedef platformun yerel derleyicisi kullanılarak derlenir. Bu senaryoda, Yansıma'nın bölümleri ve `dynamic` anahtar kelimenin kullanımı gibi desteklenmeyen birkaç .NET özelliği vardır. Bu özellikleri kendi kodunuzda kullanarak kontrol edebilirsiniz, ancak akılda Birlik ve IL2CPP ile yazılmış değildi 3 parti DLs ve SDK'lar kullanarak sorunlarla karşılaşabilirsiniz. Bu konu hakkında daha fazla bilgi için lütfen Unity'nin sitesindeki [Komut Dosyası Kısıtlamaları](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) dokümanlarına bakın.

Ayrıca, yukarıdaki Json.NET örnekte belirtildiği gibi, Unity IL2CPP dışa aktarma işlemi sırasında kullanılmayan kodu sökmeye çalışır.  Bu genellikle bir sorun olmasa da, Yansıma kullanan kitaplıklar ile yanlışlıkla dışa aktarma zamanında belirlenemeyen çalışma zamanında çağrılacak özellikleri veya yöntemleri şeritleyebilir.  Bu sorunları gidermek için, ekleme işlemini çalıştırmamak için derlemelerin ve ad alanlarının listesini içeren bir **link.xml** dosyasını projenize ekleyin.  Tüm ayrıntılar için lütfen [Unity'nin bytecode sıyırma ile ilgili dokümanlarına](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html)bakın.

## <a name="net-4x-sample-unity-project"></a>.NET 4.x Örnek Birlik Projesi

Örnek birkaç .NET 4.x özelliğinden örnekler içerir. Projeyi karşıdan yükleyebilir veya Kaynak Kodu [GitHub'da](https://github.com/Microsoft/unity-scripting-upgrade)görüntüleyebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

* [Unity Blog - Unity 2018.2'de Çalışma Zamanı İyileştirmeleri Yazma](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [C Tarihi #](/dotnet/csharp/whats-new/csharp-version-history)
* [C# 6'daki Yenilikler](/dotnet/csharp/whats-new/csharp-6)
* [Unity'de asynchronous programlama, Coroutine ve TAP kullanma](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Unity 2017'de Coroutines Yerine Async-Await](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Birlik Forumu - Deneysel Scripting Önizlemeler](https://forum.unity.com/forums/experimental-scripting-previews.107/)
