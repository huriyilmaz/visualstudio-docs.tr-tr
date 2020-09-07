---
title: Unity’de .NET 4.x kullanma
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 9a53db2d7cb73fbbb8ea694386dbada3186957ee
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508983"
---
# <a name="using-net-4x-in-unity"></a>Unity’de .NET 4.x kullanma

Unity betiği temel alan teknolojiler olan C# ve .NET, Microsoft tarafından ilk olarak 2002 içinde piyasaya sürülmesinden beri güncelleştirmeleri almaya devam etti. Ancak Unity geliştiricileri, C# diline eklenen yeni özelliklerin sürekli akışını bilmeyebilir ve .NET Framework. Bunun nedeni, Unity 2017,1 ' den önce Unity 'nin bir .NET 3,5 eşdeğer betik çalışma zamanı (eksik güncelleştirme) kullandığından dolayı.

Unity 2017,1 sürümü ile Unity, betik çalışma zamanının bir .NET 4,6, C# 6 uyumlu sürümüne yükseltildiğini deneysel bir sürümünü sunmuştur. Unity 2018,1 ' de, .NET 4. x eşdeğeri çalışma zamanı artık deneysel olarak değerlendirilmez, ancak eski .NET 3,5 denk çalışma zamanı artık eski sürüm olarak kabul edilir. Unity 2018,3 sürümü sayesinde Unity, yükseltilen betik çalışma zamanını varsayılan seçimi yapmak ve C# 7 ' ye daha da sonra güncelleştirmek için yansıtılacak. Bu yol haritasında daha fazla bilgi ve en son güncelleştirmeler için Unity 'nin [blog postasını](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) okuyun veya [deneysel betik önizlemeleri forumunu](https://forum.unity.com/forums/experimental-scripting-previews.107/)ziyaret edin. Bu sırada, artık .NET 4. x Scripting Runtime ile kullanılabilen yeni özellikler hakkında daha fazla bilgi edinmek için aşağıdaki bölümlere göz atın.

## <a name="prerequisites"></a>Ön koşullar

* [Unity 2017,1 veya üzeri](https://unity3d.com/) (2018,2 önerilir)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Unity 'de .NET 4. x Scripting çalışma zamanını etkinleştirme

.NET 4. x Scripting çalışma zamanını etkinleştirmek için aşağıdaki adımları uygulayın:

1. **> proje ayarlarını düzenle > oynatıcı**' yı seçerek Unity denetçisinde playersettings ' i açın.

1. **Yapılandırma** başlığı altında, **komut dosyası çalışma zamanı sürüm** açılan listesine tıklayın ve **.NET 4. x eşdeğerini**seçin. Unity 'yi yeniden başlatmanız istenir.

![.NET 4. x eşdeğerini seçin](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>.NET 4. x ve .NET Standard 2,0 profillerinin arasından seçim yapma

.NET 4. x eşdeğer betik çalışma zamanına geçiş yaptıktan sonra, PlayerSettings (**> proje ayarlarını düzenle > Player**) açılır menüsünü kullanarak **API uyumluluk düzeyini** belirtebilirsiniz. İki seçenek vardır:

* **.NET Standard 2,0**. Bu profil, .NET Foundation tarafından yayımlanan [.NET Standard 2,0 profiliyle](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) eşleşir. Unity yeni projeler için .NET Standard 2,0 önerir. Boyut kısıtlı platformlar için avantajlı olan .NET 4. x 'ten daha küçüktür. Ayrıca Unity, Unity 'nin desteklediği tüm platformlarda bu profili desteklemeye kararlıdır.

* **.NET 4. x**. Bu profil, en son .NET 4 API 'sine erişim sağlar. .NET Framework sınıfı kitaplıklarında bulunan tüm kodu içerir ve .NET Standard 2,0 profillerini de destekler. Projeniz .NET Standard 2,0 profilinde bulunmayan API 'nin bir parçasını gerektiriyorsa .NET 4. x profilini kullanın. Ancak, bu API 'nin bazı bölümleri Unity 'nin tüm platformlarında desteklenmeyebilir.

Bu seçenekler hakkında daha fazla bilgi için Unity 'nin [Blog](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)gönderisine erişebilirsiniz.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>.NET 4. x API Uyumluluk düzeyi kullanılırken derleme başvuruları ekleme

**API Uyumluluk düzeyi** açılan menüsünde .NET Standard 2,0 ayarını KULLANıRKEN, API profilindeki tüm derlemelere başvurulur ve kullanılabilir. Ancak, daha büyük .NET 4. x profilini kullanırken, Unity 'nin birlikte geldiği derlemelerin bazılarına varsayılan olarak başvurulmuyor. Bu API 'Leri kullanmak için el ile bir derleme başvurusu eklemeniz gerekir. Unity 'nin birlikte bulunan derlemelerini, Unity Düzenleyicisi yüklemenizin **MonoBleedingEdge/lib/mono** dizininde görüntüleyebilirsiniz:

![MonoBleedingEdge dizini](media/vstu_monobleedingedge.png)

Örneğin, .NET 4. x profilini kullanıyorsanız ve kullanmak istiyorsanız `HttpClient` , System.Net.Http.dll için bir derleme başvurusu eklemeniz gerekir. Bu olmadan derleyici, bir derleme başvurunuz eksik olduğunu şikayet eder:

![eksik bütünleştirilmiş kod başvurusu](media/vstu_missing-reference.png)

Visual Studio her açılışında Unity projeleri için. csproj ve. sln dosyalarını yeniden oluşturur. Sonuç olarak, proje yeniden alındıktan sonra kaybolabilecek olduğundan doğrudan Visual Studio 'da derleme başvuruları ekleyemezsiniz. Bunun yerine, **MCS. rsp** adlı özel bir metin dosyası kullanılmalıdır:

1. Unity projenizin kök **varlıklar** dizininde **MCS. rsp** adlı yeni bir metin dosyası oluşturun.

1. Boş metin dosyasının ilk satırında, şunu girin: `-r:System.Net.Http.dll` ve sonra dosyayı kaydedin. "System.Net.Http.dll" öğesini bir başvuru eksik olabilecek herhangi bir dahil edilen derlemeyle değiştirebilirsiniz.

1. Unity düzenleyicisini yeniden başlatın.

## <a name="taking-advantage-of-net-compatibility"></a>.NET uyumluluğundan yararlanın

Yeni C# sözdizimi ve dil özelliklerine ek olarak, .NET 4. x Scripting Runtime, Unity kullanıcılarına eski .NET 3,5 komut dosyası çalışma zamanı ile uyumlu olmayan çok sayıda .NET paketi kitaplığı erişimi sağlar.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>NuGet 'ten bir Unity projesine paket ekleme

[NuGet](https://www.nuget.org/) , .NET için paket yöneticisidir. NuGet, Visual Studio ile tümleşiktir. Ancak Unity projeleri, NuGet paketleri eklemek için özel bir işlem gerektirir. Bunun nedeni, Unity 'de bir proje açtığınızda, Visual Studio proje dosyalarının yeniden oluşturulması ve gerekli yapılandırmaların geri alınması nedeniyle oluşur. NuGet 'den Unity projenize bir paket eklemek için aşağıdakileri yapın:

1. Eklemek istediğiniz uyumlu bir paketi bulmak için NuGet 'e gözatıp (.NET Standard 2,0 veya .NET 4. x). Bu örnek, .NET Standard 2,0 projesine JSON ile çalışmaya yönelik popüler bir paket olan [JSON.net](https://www.nuget.org/packages/Newtonsoft.Json/)eklemeyi gösterir.

1. **İndir** düğmesine tıklayın:

    ![İndir düğmesi](media/vstu_nuget-download.png)

1. İndirilen dosyayı bulun ve uzantıyı **. nupkg** konumundan **. zip**olarak değiştirin.

1. ZIP dosyası içinde **lib/Netstandard 2.0** dizinine gidin ve **Newtonsoft.Json.dll** dosyasını kopyalayın.

1. Unity projenizin kök **varlıklar** klasöründe, **Eklentiler**adlı yeni bir klasör oluşturun. Eklentiler, Unity 'de özel bir klasör adıdır. Daha fazla bilgi için [Unity belgelerine](https://docs.unity3d.com/Manual/Plugins.html) bakın.

1. **Newtonsoft.Json.dll** dosyasını Unity projenizin **Eklentiler** dizinine yapıştırın.

1. Unity projenizin **varlıklar** dizininde **link.xml** adlı bir dosya oluşturun ve aşağıdaki XML 'i ekleyin.  Bu, Unity 'nin bytecode 'un bir IL2CPP platformuna aktarılırken gerekli verileri kaldırmadığından emin olmanızı sağlar.  Bu adım bu kitaplığa özel olmakla birlikte, yansıma kullanan diğer kitaplıklarla benzer yollarla sorun yaşayabilirsiniz.  Daha fazla bilgi için lütfen bu konudaki [Unity 'nin docs](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) bölümüne bakın.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Her şey olduğunda, artık Json.NET paketini kullanabilirsiniz.

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

Bu, bağımlılığı olmayan bir kitaplığın kullanılmasına ilişkin basit bir örnektir. NuGet paketleri diğer NuGet paketlerine güvendiğinizde, bu bağımlılıkları el ile indirmeniz ve aynı şekilde projeye eklemeniz gerekir.

## <a name="new-syntax-and-language-features"></a>Yeni sözdizimi ve dil özellikleri

Güncelleştirilmiş betik çalışma zamanının kullanılması, Unity geliştiricilerine C# 6 ve yeni dil özellikleri ve söz dizimi için erişim sağlar.

### <a name="auto-property-initializers"></a>Otomatik Özellik başlatıcıları

Unity 'nin .NET 3,5 Scripting Runtime sürümünde, Auto-property sözdizimi, başlatılmamış özellikleri hızlı bir şekilde tanımlamanızı kolaylaştırır, ancak başlatma işlemi betiğinizdeki başka bir yerde gerçekleşecektir. Artık .NET 4. x çalışma zamanı ile, otomatik özellikleri aynı satırda başlatmak mümkündür:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Dize ilişkilendirme

Eski .NET 3,5 çalışma zamanı ile dize birleştirme gereken garip söz dizimi. Artık .NET 4. x çalışma zamanı ile [ `$` dize ilişkilendirme](/dotnet/csharp/language-reference/tokens/interpolated) özelliği, ifadelerin daha doğrudan ve okunabilir bir sözdiziminde dizelere eklenmesine izin verir:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>İfade gövdeli üyeler

.NET 4. x çalışma zamanı 'nda bulunan daha yeni C# sözdizimi ile, [lambda ifadeleri](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) daha kısa yapmak için işlevlerin gövdesini değiştirebilir:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Ayrıca, salt okuma özelliklerinde ifade-Bodied Üyeler de kullanabilirsiniz:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Görev Tabanlı Zaman Uyumsuz Desen (TAP)

Zaman [uyumsuz programlama](/dotnet/csharp/async) , uygulamanızın yanıt vermemesine neden olmadan zaman alma işlemlerinin gerçekleşmesini sağlar. Bu işlevsellik Ayrıca, bu işlemlerin sonuçlarına bağlı olan koda devam etmeden önce kodunuzun zaman tüketen işlemlerin bitmesini beklemesini sağlar. Örneğin, bir dosyanın yüklenmesini veya bir ağ işleminin tamamlanmasını bekleyebilirsiniz.

Unity 'de, zaman uyumsuz programlama genellikle [eş](https://docs.unity3d.com/Manual/Coroutines.html)yordamlar ile gerçekleştirilir. Ancak, C# 5 ' de, .NET geliştirmede zaman uyumsuz programlama için tercih edilen yöntem, [Task-based Asynchronous Pattern (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) `async` `await` [System. Threading. Task](/dotnet/api/system.threading.tasks.task)ile ve anahtar sözcüklerini kullanarak görev tabanlı zaman uyumsuz bir modeldir (TAP). Özet ' de bir `async` işlevde, `await` uygulamanızın geri kalanını güncelleştirmeden önce bir görevin tamamlanması gerekir:

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

DOKUNUN, Unity 'ye özgü nuslar geliştiricilerin göz önünde bulundurulması gereken karmaşık bir konudur. Sonuç olarak, Unity 'de eş olmayan bir evrensel değişiklik değildir seçeneğine dokunun. Ancak, daha fazla yararlanmak için başka bir araçtır. Bu özelliğin kapsamı Bu makalenin dışındadır, ancak bazı genel en iyi uygulamalar ve ipuçları aşağıda verilmiştir.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Unity ile dokunma için Başlarken başvurusu

Bu ipuçları Unity 'de dokunarak çalışmaya başlamanıza yardımcı olabilir:

* Beklenmeye yönelik olarak beklenen zaman uyumsuz işlevlerin dönüş türü veya olmalıdır [`Task`](/dotnet/api/system.threading.tasks.task) [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1) .
* Bir görevi döndüren zaman uyumsuz işlevlerin adlarına **"Async"** soneki eklenmiş olması gerekir. "Async" soneki, bir işlevin her zaman beklenmiş olması gerektiğini belirtmenize yardımcı olur.
* Yalnızca `async void` geleneksel zaman uyumlu koddan zaman uyumsuz işlevleri çalıştıran işlevler için dönüş türünü kullanın. Bu işlevlerin kendisi beklenmez ve adlarında "Async" sonekine sahip olmamalıdır.
* Unity, zaman uyumsuz işlevlerin varsayılan olarak ana iş parçacığında çalışmasını sağlamak için UnitySynchronizationContext kullanır. Unity API 'SI ana iş parçacığı dışında erişilebilir değildir.
* Görevleri, ve gibi yöntemlerle arka plan iş parçacıklarında çalıştırmak mümkündür [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait) . Bu teknik, performansı geliştirmek için ana iş parçacığından pahalı işlemleri devrederde yararlıdır. Ancak, arka plan iş parçacıklarını kullanmak, [yarış durumları](https://wikipedia.org/wiki/Race_condition)gibi hata ayıklama zor olan sorunlara yol açabilir.
* Unity API 'SI ana iş parçacığı dışında erişilebilir değildir.
* İş parçacıklarını kullanan görevler Unity WebGL Derlemeleriyle desteklenmez.

#### <a name="differences-between-coroutines-and-tap"></a>Eş yordam ve dokunma arasındaki farklılıklar

Eş yordam ve TAP/Async-Await arasında bazı önemli farklılıklar vardır:

* Coroutines değer döndüremez, ancak bu `Task<TResult>` olabilir.
* Bir `yield` try-catch ifadesine ekleyemezsiniz ve bunlarla hata işlemenin zor olmasını sağlayabilirsiniz. Ancak, try-catch, dokunarak çalışır.
* Unity 'nin eş yordam olamaz özelliği monodavranış sınıfından türemeyen sınıflarda kullanılamaz. TAP, bu tür sınıflarda zaman uyumsuz programlama için harika.
* Bu noktada Unity, eş yordamın toptan yerini alacak şekilde dokunma önerisinde yoktur. Profil oluşturma, belirli bir proje için bir yaklaşımdan kaynaklanan belirli sonuçları öğrenmenin tek yoludur.

> [!NOTE]
> Unity 2018,2 itibariyle, kesme noktaları ile zaman uyumsuz yöntemlerin hata ayıklaması tam olarak desteklenmez; Ancak, [Bu Işlevsellik Unity 2018,3 ' de beklenmektedir](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof işleci

`nameof`İşleci bir değişkenin, türün veya üyenin dize adını alır. `nameof`Yararlı olarak verilen bazı durumlar, hataları günlüğe kaydetme ve bir sabit listesinin dize adını alma:

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

[Çağıran bilgi öznitelikleri](/dotnet/csharp/programming-guide/concepts/caller-information) bir yöntemin çağıranı hakkında bilgi sağlar. Bir arayan bilgileri özniteliğiyle kullanmak istediğiniz her parametre için bir varsayılan değer sağlamalısınız:

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

[Statik kullanmak](/dotnet/csharp/language-reference/keywords/using-static) , sınıf adını yazmadan statik işlevleri kullanmanıza olanak sağlar. Statik kullanarak, aynı sınıftan birkaç statik işlev kullanmanız gerekiyorsa, boşluk ve zaman kazanabilirsiniz:

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

## <a name="il2cpp-considerations"></a>IL2CPP konuları

Oyununuzu iOS gibi platformlarda dışa aktarırken, Unity, IL2CPP altyapısını, daha sonra hedef platformun yerel derleyicisi kullanılarak derlenen C++ koduna "derleyin" olarak kullanır. Bu senaryoda, yansıma parçaları ve anahtar sözcüğünün kullanımı gibi desteklenmeyen bazı .NET özellikleri vardır `dynamic` . Bu özellikleri kendi kodunuzda kullanarak denetleyebilirken, Unity ve IL2CPP ile yazılmayan 3. taraf dll 'Leri ve SDK 'Ları kullanarak sorunlar yaşayabilirsiniz. Bu konu hakkında daha fazla bilgi için lütfen Unity 'nin sitesindeki [betik kısıtlamaları](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) belgelerine bakın.

Ayrıca, yukarıdaki Json.NET örneğinde belirtildiği gibi Unity, IL2CPP dışa aktarma işlemi sırasında kullanılmayan kodu kullanıma açmaya çalışır.  Bu genellikle bir sorun olmasa da, yansıma kullanan kitaplıklar sayesinde, yanlışlıkla dışa aktarma zamanında belirlenemeyecek çalışma zamanında çağrılacak özellikleri veya yöntemleri açabilir.  Bu sorunları gidermek için, projenize, ortaya çıkan işlemi çalıştırmayan derlemelerin ve ad alanlarının listesini içeren bir **link.xml** dosyası ekleyin.  Tam Ayrıntılar için lütfen bkz. [Unity 'nin belge bytecode üzerinde çaba](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html)

## <a name="net-4x-sample-unity-project"></a>.NET 4. x örnek Unity projesi

Örnek, çeşitli .NET 4. x özelliklerine örnek içerir. Projeyi indirebilir veya [GitHub](https://github.com/Microsoft/unity-scripting-upgrade)'da kaynak kodu görüntüleyebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

* [Unity blog-betik oluşturma çalışma zamanı geliştirmeleri 2018,2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [C geçmişi #](/dotnet/csharp/whats-new/csharp-version-history)
* [C# 6 ' daki yenilikler](/dotnet/csharp/whats-new/csharp-6)
* [Unity 'de eş zamanlı olmayan programlama, Coroutine ve TAP 'ı kullanma](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Unity 2017 ' de eş zamanlı olmayan-await](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Unity Forumu-deneysel betik önizlemeleri](https://forum.unity.com/forums/experimental-scripting-previews.107/)