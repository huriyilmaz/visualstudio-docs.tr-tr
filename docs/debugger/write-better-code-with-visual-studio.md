---
title: Hata ayıklama teknikleri ve araçları
description: Özel durumları düzeltmek, hataları düzeltmek ve kodunuzu geliştirmek için Visual Studio kullanarak daha az hatayla daha iyi kod yazma
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ea1c016caed0071e1a63ea9e21e33047a32cdb82
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635912"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Daha iyi kod yazmanıza yardımcı olacak hata ayıklama teknikleri ve araçları

Kodundaki hataları ve hataları düzeltmek zaman alan ve bazen can sıkıcı bir görev olabilir. Hata ayıklamayı etkili bir şekilde öğrenmek zaman alır, ancak Visual Studio gibi güçlü bir IDE, işinizi çok daha kolay hale getirir. IDE yalnızca bu değil, hataları düzeltmenize ve kodunuzun hatalarını daha hızlı ayıklamanıza yardımcı olabilir, ancak daha az hatayla daha iyi kod yazmanıza da yardımcı olabilir. Bu makaledeki hedefimiz size "hata düzeltme" işleminin bütünsel bir görünümünü vermektir. Böylece kod çözümleyiciyi ne zaman, hata ayıklayıcıyı ne zaman kullanabileceğinizi, özel durumları düzeltmeyi ve amaç için kod kullanmayı bilirsiniz. Hata ayıklayıcısını kullanmak zorunda olduğunu zaten biliyorsanız [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

Bu makalede, kodlama oturumlarınızı daha üretken hale getirirken IDE'den yararlanarak bahsedacağız. Çeşitli görevlere dokunuruz, örneğin:

* IDE'nin kod çözümleyiciden yararlanarak kodunuzu hata ayıklama için hazırlama

* Özel durumları düzeltme (çalışma zamanı hataları)

* Amaç için kodlama (onay kullanarak) hataları en aza indirme

* Hata ayıklayıcının ne zaman kullanımı gerekir?

Bu görevleri göstermek için uygulamalarınızı hata ayıklamaya çalışırken karşılaşacakları en yaygın hata ve hata türlerinden birkaçını gösteriyoruz. Örnek kod C# olsa da kavramsal bilgiler genellikle C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (not alınarak hariç). Ekran görüntüleri C# içindedir.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Bazı hatalar ve hatalar olan bir örnek uygulama oluşturma

Aşağıdaki kodda, IDE kullanarak düzeltebilirsiniz bazı Visual Studio vardır. Buradaki uygulama, JSON verilerini bir işlemden alma, verileri bir nesneye alma ve basit bir listeyi yeni verilerle güncelleştirme simülasyonu yapmak için basit bir uygulamadır.

Uygulamayı oluşturmak için:

1. .NET Core Visual Studio iş yükünü yüklemiş ve **.NET Core'da yüklü** olması gerekir.

    Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz yükleyin.

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları **ve** Özellikleri  >  **Al'a tıklayın.** Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.** Arama **kutusuna** console yazın ve ardından .NET Core **için Konsol Uygulaması'dan** birini seçin. **İleri**’yi seçin. Console_Parse_JSON gibi **bir proje adı yazın** ve Ardından **veya** **Oluştur'a** tıklayın .

    .NET Core için önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından Oluştur'a **seçin.**

    .NET Core için  Konsol Uygulaması proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al'a gidin ve bu  >  işlem Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** altında Konsol Uygulaması'nu seçin ve orta bölmede Konsol Uygulaması  **(.NET Core) öğesini seçin.** Console_Parse_JSON gibi **bir ad yazın ve** Tamam'a **tıklayın.**

    Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al'a gidin ve bu işlem  >  Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
    ::: moniker-end

    Visual Studio, sağ bölmede görünen Çözüm Gezgini konsol projesini oluşturur.

1. Projenin *Program.cs* dosyasındaki varsayılan kodu aşağıdaki örnek kodla değiştirin.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Kırmızı ve yeşil geçişleri bulun!

Örnek uygulamayı başlatmayı ve hata ayıklayıcıyı çalıştırmayı denemeden önce, kod düzenleyicisinde kırmızı ve yeşil geçişler olup o kodu kontrol edin. Bunlar, IDE'nin kod çözümleyicisi tarafından tanımlanan hataları ve uyarıları temsil eder. Kırmızı geçişler, kodu çalıştırmadan önce düzeltmesi gereken derleme zamanı hatalarıdır. Yeşil geçişler uyarıdır. Genellikle uyarıları düzeltmeden uygulama çalıştırabilirsiniz ancak bunlar bir hata kaynağı olabilir ve bunları araştırarak zaman ve sorundan tasarruf sağlarsınız. Liste görünümünü tercih ediyorsanız, bu **uyarılar ve** hatalar Hata Listesi penceresinde de gösterilir.

Örnek uygulamada düzeltmesi gereken birkaç kırmızı çizgi ve bakacağız yeşil bir tane var. İlk hata şu şekildedir.

![Kırmızı çizgi olarak gösterilen hata](../debugger/media/write-better-code-red-squiggle.png)

Bu hatayı düzeltmek için IDE'nin ampul simgesiyle temsil edilen başka bir özelliğine bakabilirsiniz.

## <a name="check-the-light-bulb"></a>Ampulü kontrol edin!

İlk kırmızı geçiş, derleme zamanı hatasını temsil eder. Üzerine gelin ve iletiyi ```The name `Encoding` does not exist in the current context``` alırsınız.

Bu hatanın sol altta bir ampul simgesi gösterir. Tornavida simgesi ile birlikte, ampul simgesi ampul simgesi satır içi kodu düzeltmeye veya yeniden düzenlemeye yardımcı olan Hızlı ![ ](../ide/media/screwdriver-icon.png) ![ ](../ide/media/light-bulb-icon.png) Eylemler'i temsil eder. Ampul, düzeltmesi gereken sorunları *temsil* eder. Tornavida, düzeltmeyi seçebilirsiniz sorunlar için. Önerilen ilk düzeltmeyi kullanarak sol tarafta **System.Text'i kullanarak bu** hatayı düzeltin.

![Kodu düzeltmek için ampulü kullanma](../debugger/media/write-better-code-missing-include.png)

Bu öğeye tıklarsanız Visual Studio Program.cs dosyasının en üstüne deyimini ekler ve kırmızı `using System.Text` çizgi kaybolur.  (Önerilen bir düzeltmenin ne yapar emin değilken **düzeltmeyi** uygulamadan önce sağdan Değişiklikleri önizle bağlantısını seçin.)

Yukarıdaki hata, genellikle kodunuza yeni bir deyim ekleyerek `using` düzeltilen yaygın bir hatadır. Bu tür hatalar eksik derleme başvurusuna işaret ediyor olabilir (projeye sağ tıklayın, Başvuru Ekle'yi seçin), yanlış yazılmış bir ad veya eklemeniz gereken eksik bir kitaplık gibi çeşitli yaygın hatalar vardır (C# için projeye sağ tıklayın ve NuGet Paketlerini ```The type or namespace `Name` cannot be found.``` Yönet'i   >  seçin). 

## <a name="fix-the-remaining-errors-and-warnings"></a>Kalan hataları ve uyarıları düzeltme

Bu kodda göz atmak için birkaç geçiş daha vardır. Burada yaygın bir tür dönüştürme hatası görüyorsunuz. Geçişin üzerine gelindiğinde, kodun bir dizeyi int'e dönüştürmeye çalıştığını görüyorsunuz. Dönüştürmeyi yapmak için açık kod eklemedikçe bu desteklenmiyor.

![Tür dönüştürme hatası](../debugger/media/write-better-code-conversion-error.png)

Kod çözümleyicisi amacınızı tahmin edebilirim, bu kez size yardımcı olacak ampuller yoktur. Bu hatayı düzeltmek için kodun amacını biliyor gerekir. Bu örnekte, 'a eklemeye çalıştığınıza göre sayısal `points` (tamsayı) bir değer olması gerektiğini görmek çok zor `points` `totalpoints` değildir.

Bu hatayı düzeltmek için sınıfın `points` üyesini `User` bundan değiştirebilirsiniz:

```csharp
[DataMember]
internal string points;
```

şu şekilde:

```csharp
[DataMember]
internal int points;
```

Kod düzenleyicisinde kırmızı çizgiler gider.

Ardından, veri üyesinin bildiriminde yeşil geçişin `points` üzerine gelin. Kod çözümleyicisi değişkenine hiçbir zaman değer atanmamış olduğunu söyler.

![Atanmamış değişken için uyarı iletisi](../debugger/media/write-better-code-warning-message.png)

Genellikle bu, düzeltilecek bir sorunu temsil eder. Ancak örnek uygulamada, verileri aslında, verileri, veri üyesine ekleme işlemi sırasında, deserialization işlemi sırasında değişkende depolar ve bu `points` `totalpoints` değeri eklersiniz. Bu örnekte, kodun amacını biliyorsunuz ve uyarıyı güvenle yoksayabilirsiniz. Ancak uyarıyı ortadan kaldırmak için aşağıdaki kodu değiştirebilirsiniz:

```csharp
item.totalpoints = users[i].points;
```

şununla değiştirin:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Yeşil geçiş gider.

## <a name="fix-an-exception"></a>Özel durumu düzeltme

Tüm kırmızı geçişleri düzelttiy ve çözdüymüş ya da en azından araştırılan tüm yeşil geçişleri düzelttiyebilirsiniz. Hata ayıklayıcıyı başlatmaya ve uygulamayı çalıştırmaya hazır olursanız.

**F5** (**Hata Ayıklama > Başlat**) veya Hata ![](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") Ayıklama araç çubuğunda Hata Ayıklamayı Başlat düğmesine basın. 

Bu noktada örnek uygulama bir özel durum `SerializationException` (çalışma zamanı hatası) oluşturur. Başka bir ifadeyle, uygulama serileştirmeye çalıştığı veriler üzerinde çalışıyor. Uygulamayı hata ayıklama modunda (hata ayıklayıcısı ekli) başlattınız, hata ayıklayıcının Özel Durum Yardımcısı sizi özel durumu veren koda doğru alır ve size yararlı bir hata iletisi verir.

![SerializationException oluşur](../debugger/media/write-better-code-serialization-exception.png)

Hata iletisi, değerin tamsayı `4o` olarak ayrıştırılamaması talimatını verir. Bu örnekte verilerin kötü olduğunu biliyorsunuz: `4o` olması `40` gerekir. Ancak, gerçek bir senaryoda verilerin denetiminde değilken (bir web hizmetten alıyorsanız) bu konuda ne yapacaksınız? Bunu nasıl düzeltin?

Bir özel durumla karşılasanız birkaç soru sormalı (ve yanıtla) gerekir:

* Bu özel durum yalnızca düzeltebilir bir hata mı? Veya

* Bu özel durum, kullanıcılarının karşılaş olabileceği bir durum mu?

Bu eski ise hatayı düzeltin. (Örnek uygulamada bu, hatalı verileri düzeltme anlamına gelir.) bu ikinci ise, kodda özel durumu bir blok kullanarak işlemeniz gerekir (sonraki bölümde diğer olası `try/catch` stratejilere göz atacağız). Örnek uygulamada aşağıdaki kodu değiştirin:

```csharp
users = ser.ReadObject(ms) as User[];
```

yerine şu kodu yazın:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Bir bloğun performans maliyeti vardır. Bu nedenle, bunları yalnızca gerçekten ihtiyacınız olduğunda , yani (a) uygulamanın yayın sürümünde oluşabilirler ve nerede (b) yöntemine ilişkin belgeler özel durumu denetlemeniz gerektiğini gösterir (belgelerin tamamlandıktan sonra!) kullanmak istemeniz `try/catch` gerekir. Çoğu durumda, bir özel durumu uygun şekilde işleye bilirsiniz ve kullanıcının bu konuda hiçbir zaman bilgisi olmaz.

Özel durum işleme için birkaç önemli ipucu:

* Bir hatayı ortaya çıkarmak veya işlemek için uygun eylemde bulunan gibi boş bir yakalama `catch (Exception) {}` bloğu kullanmaktan kaçının. Boş veya bilgilendirici olmayan bir catch bloğu özel durumları gizleyebilirsiniz ve kodunuzun hata ayıklamayı kolaylaştırmak yerine daha zor hale getirir.

* Örnek `try/catch` uygulamada özel durum ( , ) oluşturur belirli `ReadObject` bir işlevin çevresindeki bloğu kullanın. Bunu daha büyük bir kod öbbsinde kullanırsanız, hatanın konumunu gizlersiniz. Örneğin, burada gösterilen üst işlev çağrısının çevresindeki bloğu kullanmayın, yoksa özel durumun tam olarak nerede `try/catch` `ReadToObject` olduğunu bilesiniz.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* Uygulamanıza dahil edersiniz, özellikle de dış verilerle (web isteği gibi) etkileşimde bulunanlar için, işlevin atma olasılığı olan özel durumları görmek için belgeleri inceleyin. Bu, doğru hata işleme ve uygulama hata ayıklama için kritik bilgiler olabilir.

Örnek uygulama için yöntemini olarak `SerializationException` `GetJsonData` değiştirerek `4o` `40` düzeltin.

## <a name="clarify-your-code-intent-by-using-assert"></a>assert kullanarak kod amacınızı netleştirme

Hata Ayıklama **Araç Çubuğunda** ![Uygulamayı](../debugger/media/dbg-tour-restart.png "RestartApp") Yeniden Başlat düğmesine tıklayın (**Ctrl**  +  **Shift**  +  **F5**). Bu, uygulamayı daha az adımda yeniden başlatıyor. Konsol penceresinde aşağıdaki çıkışı görebilirsiniz.

![Çıktıda null değer](../debugger/media/write-better-code-using-assert-null-output.png)

Bu çıkışta doğru bir şey göresiniz. **üçüncü** **kaydın adı** ve soyadı boş!

Bu, işlevlerinize deyimleri kullanmak için olan ve genellikle az kullanımlı olan yararlı bir kodlama uygulaması `assert` hakkında konuşmak için iyi bir zaman. Aşağıdaki kodu ekleyerek, ve 'nin olduğundan emin olmak için bir çalışma zamanı `firstname` denetimi `lastname` `null` eklersiniz. yönteminde aşağıdaki kodu `UpdateRecords` değiştirin:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

şununla değiştirin:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Geliştirme `assert` işlemi sırasında işlevlerinize bunun gibi deyimler ekleyerek kodunuzun amacını belirtmenize yardımcı olabilir. Yukarıdaki örnekte, şunları belirtiriz:

* Ad için geçerli bir dize gereklidir
* Soyadı için geçerli bir dize gereklidir

Amaç bu şekilde belirterek gereksinimlerinizi zorunlu kılın. Bu, geliştirme sırasında hataları ortaya çıkararak kullanabileceğiniz basit ve kullanışlı bir yöntemdir. ( `assert` deyimleri birim testlerinde ana öğe olarak da kullanılır.)

Hata Ayıklama **Araç Çubuğunda** ![Uygulamayı](../debugger/media/dbg-tour-restart.png "RestartApp") Yeniden Başlat düğmesine tıklayın (**Ctrl**  +  **Shift**  +  **F5**).

> [!NOTE]
> Kod `assert` yalnızca hata ayıklama derlemesinde etkindir.

Yeniden başlatıldığında, ifade yerine olarak değerlendirilene kadar `assert` hata ayıklayıcısı `users[i].firstname != null` deyimi üzerinde `false` `true` duraklatılır.

![Onay false olarak çözümle](../debugger/media/write-better-code-using-assert.png)

Bu `assert` hata, araştırmamız gereken bir sorun olduğunu gösterir. `assert` bir özel durum görmey üstünüz olan birçok senaryoyu kapsıyor olabilir. Bu örnekte kullanıcı bir özel durum görmez ve kayıt `null` listeniz gibi `firstname` bir değer eklenir. Bu, daha sonra (konsol çıkışında gördüğünüz gibi) sorunlara neden olabilir ve hata ayıklaması daha zor olabilir.

> [!NOTE]
> Değeri üzerinde bir yöntem çağıran `null` senaryolarda, bir `NullReferenceException` sonuç. Normalde genel bir özel durum için, yani belirli kitaplık işlevine bağlı bir özel durum için `try/catch` blok kullanmaktan kaçınmak istersiniz. Herhangi bir nesne bir `NullReferenceException` oluşturur. Emin değilken kitaplık işlevinin belgelerine bakın.

Hata ayıklama işlemi sırasında, belirli bir deyimi gerçek bir kod düzeltmesi ile değiştirmeniz gerektirinceye `assert` kadar tutmak iyi olur. Kullanıcının uygulamanın yayın derlemesinde özel durumla karşılaşabilirsiniz. Bu durumda, uygulamanın önemli bir özel durum veya başka bir hatayla sonuçlanmayacak şekilde çalışmay olduğundan emin olmak için kodu yeniden düzenlemeniz gerekir. Bu nedenle, bu kodu düzeltmek için aşağıdaki kodu değiştirin:

```csharp
if (existingUser == false)
{
    User user = new User();
```

yerine şu kodu yazın:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Bu kodu kullanarak kod gereksinimlerinizi karşılar ve veya değerine sahip bir kaydın verilere `firstname` `lastname` `null` eklenmeyebilirsiniz.

Bu örnekte, bir döngüye `assert` iki deyimi ekledik. Genellikle kullanırken, bir işlevin veya yöntemin giriş noktasına `assert` `assert` (başlangıcı) deyimleri eklemek en iyisidir. Şu anda örnek uygulamada `UpdateRecords` yöntemine bakabilirsiniz. Bu yöntemde, yöntem bağımsız değişkenlerden biri ise sorun içinde olduğunu biliyorsunuz, bu nedenle her ikisini de işlevin giriş noktasında bir `null` `assert` deyimiyle kontrol edin.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Yukarıdaki deyimler için amacınız, herhangi bir şeyi güncelleştirmeden önce var olan verileri ( ) yüklemek `db` ve yeni verileri ( ) `users` almaktır.

veya olarak `assert` çözümlene herhangi bir ifade ile `true` `false` kullanabilirsiniz. Bu nedenle, örneğin, bunun gibi bir `assert` deyimi eklemek için.

```csharp
Debug.Assert(users[0].points > 0);
```

Yukarıdaki kod, aşağıdaki amacı belirtmek için kullanışlıdır: kullanıcının kaydını güncelleştirmek için sıfırdan (0) büyük yeni bir nokta değeri gerekir.

## <a name="inspect-your-code-in-the-debugger"></a>Hata ayıklayıcıda kodunuzu inceleme

Artık örnek uygulamada yanlış olan kritik öneme sahip olan her şeyi düzelttiyebilirsiniz. Başka önemli işlere geçebilirsiniz!

Hata ayıklayıcının Özel Durum Yardımcısını gösterdik, ancak hata ayıklayıcı, kodunuzu adım adım inceleme ve değişkenlerini inceleme gibi başka şeyler de yapmanızı sağlayan çok daha güçlü bir araçtır. Bu daha güçlü özellikler, özellikle de aşağıdakiler olmak üzere birçok senaryoda yararlıdır:

* Kodunda bir çalışma zamanı hatasını yalıtmaya çalışıyorsanız, ancak daha önce tartışılan yöntemleri ve araçları kullanarak bunu yapamazsanız.

* Kodunuzu doğrulamak, yani beklediğiniz gibi olduğundan ve istediğiniz şekilde olduğundan emin olmak için çalışırken izleyin.

    Çalışırken kodunuzu izlemenizi sağlar. Kodunuz hakkında bu şekilde daha fazla bilgi edinmek ve genellikle belirgin belirtiler ortaya çıkarmadan önce hataları tanımlayabilirsiniz.

Hata ayıklayıcının temel özelliklerini kullanmayı öğrenmek için bkz. Mutlak yeni [başlayanlar için hata ayıklama.](../debugger/debugging-absolute-beginners.md)

## <a name="fix-performance-issues"></a>Performans sorunlarını çözme

Başka bir tür hata, uygulamanın yavaş çalışmasına veya çok fazla bellek kullanmalarına neden olan verimsiz kod içerir. Genellikle performansı en iyi duruma getirme, uygulama geliştirme aşamasında daha sonra yapacaklarınızı ifade etmektir. Ancak, performans sorunlarıyla erkenden (örneğin, uygulamanın bir kısmının yavaş çalışıyor olduğunu görüyorsunuz) ve profil oluşturma araçlarıyla uygulamayı erkenden test etmek zorundayabilirsiniz. CPU Kullanımı aracı ve Bellek Çözümleyicisi gibi profil oluşturma araçları hakkında daha fazla bilgi için bkz. Profil oluşturma [araçlarına ilk bakış.](../profiling/profiling-feature-tour.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, kodunda birçok yaygın hatayı önlemeyi ve düzeltmeyi ve hata ayıklayıcıyı ne zaman kullanabileceğinizi öğrendiniz. Ardından, hataları düzeltmek için Visual Studio hakkında daha fazla bilgi edinmek için.

> [!div class="nextstepaction"]
> [Başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)
