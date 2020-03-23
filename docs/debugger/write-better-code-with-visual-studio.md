---
title: Hata ayıklama teknikleri ve araçları
description: Özel durumları düzeltmek, hataları düzeltmek ve kodunuzu geliştirmek için Visual Studio'u kullanarak daha az hatayla daha iyi kod yazın
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302030"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Daha iyi kod yazmanıza yardımcı olacak hata ayıklama teknikleri ve araçları

Kodunuzdahataları ve hataları düzeltmek zaman alan ve bazen de sinir bozucu bir görev olabilir. Etkili bir şekilde hata ayıklama öğrenmek için zaman alır, ancak Visual Studio gibi güçlü bir IDE işinizi çok daha kolay hale getirebilir. Bir IDE hataları düzeltmek ve daha hızlı ve sadece bu değil, kod hata ayıklama yardımcı olabilir, ama aynı zamanda daha az hata ile daha iyi kod yazmanıza yardımcı olabilir. Bu makaledeki amacımız size "hata düzeltme" işleminin bütünsel bir görünümünü vermektir, böylece kod çözümleyicisini ne zaman kullanacağınızı, hata ayıklayıcıyı ne zaman kullanacağınızı, özel durumları nasıl düzelteceğinizi ve niyet için nasıl kod kullanılacağını bileceksiniz. Hata ayıklamayı kullanmanız gerektiğini zaten biliyorsanız, [hata ayıklamaya ilk bakışta](../debugger/debugger-feature-tour.md)bakın.

Bu makalede, kodlama oturumlarınızı daha verimli hale getirmek için IDE'den yararlanma hakkında konuşuyoruz. Çeşitli görevlere değiniyoruz, örneğin:

* IDE'nin kod çözümleyicisini yararlanarak hata ayıklama için kodunuzu hazırlayın

* Özel durumlar (çalışma zamanı hataları) nasıl düzeltilir?

* Amaç için kodlayarak hataları en aza indirme (assert kullanarak)

* Hata ayıklama ne zaman kullanılır?

Bu görevleri göstermek için, uygulamalarınızı hata ayıklamaya çalışırken karşılaşacağınız en yaygın hata ve hata türlerinden birkaçını gösteririz. Örnek kod C#olmasına rağmen, kavramsal bilgiler genellikle C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için de geçerlidir (not edilendurumlar hariç). Ekran görüntüleri C#'da.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Bazı hatalar ve hatalar içeren örnek bir uygulama oluşturma

Aşağıdaki kod, Visual Studio IDE'yi kullanarak düzeltebileceğiniz bazı hatalara sahiptir. Buradaki uygulama, json verilerini bazı işlemlerden almayı, verileri bir nesneye deserialize etmeyi ve yeni verilerle basit bir listeyi güncelleştirmeyi simüle eden basit bir uygulamadır.

Uygulamayı oluşturmak için:

1. Oluşturmak istediğiniz uygulama türüne bağlı olarak Visual Studio yüklü olmalı ve **.NET Core çapraz platform geliştirme** veya **.NET masaüstü geliştirme** iş yükü yüklü olmalıdır.

    Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'nuz varsa, **Araçlar** > **Araçları ve Özellikleri Al'ı**tıklatın. Visual Studio Installer başlattı. **.NET Core çapraz platform geliştirme** veya **.NET masaüstü geliştirme iş** yükünü seçin ve sonra **Değiştir'i**seçin.

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde yeni **bir proje oluştur'u**seçin. Arama kutusuna **konsol** yazın ve ardından **Konsol Uygulaması (.NET Core)** veya **Konsol Uygulaması 'nı (.NET Framework)** seçin. **İleri**’yi seçin. **Console_Parse_JSON** gibi bir proje adı yazın ve **Oluştur'u**tıklatın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında, **Konsol Uygulaması'nı**seçin ve orta bölmede Konsol **Uygulaması (.NET Core)** veya **Konsol Uygulaması (.NET Framework)** seçeneğini belirleyin. **Console_Parse_JSON** gibi bir ad yazın ve **Tamam'ı**tıklatın.
    ::: moniker-end

    **Konsol Uygulaması (.NET Core)** veya Console **App (.NET Framework)** proje şablonu görmüyorsanız, Visual Studio Installer'ı açan **Araçlar** > **Araçları ve Özellikleri Al'a**gidin. **.NET Core çapraz platform geliştirme** veya **.NET masaüstü geliştirme iş** yükünü seçin ve sonra **Değiştir'i**seçin.

    Visual Studio, sağ bölmede Solution Explorer'da görünen konsol projesini oluşturur.

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

## <a name="find-the-red-and-green-squiggles"></a>Kırmızı ve yeşil dalgalı bul!

Örnek uygulamayı başlatmayı ve hata ayıklayıcıyı çalıştırmayı denemeden önce, kod düzenleyicisindeki kırmızı ve yeşil dalgalı squiggles kodunu kontrol edin. Bunlar, IDE'nin kod çözümleyicisi tarafından tanımlanan hataları ve uyarıları temsil eder. Kırmızı dalgalı, kodu çalıştırmadan önce düzeltmeniz gereken derleme zamanı hatalarıdır. Yeşil dalgalı lar uyarılardır. Uyarılarınızı düzeltmeden uygulamanızı sık sık çalıştırabiliyor olsanız da, bunlar hata kaynağı olabilir ve bunları araştırarak sık sık kendinize zaman ve sorun dan tasarruf emebilirsiniz. Bu uyarılar ve hatalar, liste görünümünü tercih ederseniz **Hata Listesi** penceresinde de gösterir.

Örnek uygulamada, düzeltmeniz gereken birkaç kırmızı dalgalı ve baktığınız bir yeşil dalgalı madde görürsünüz. İşte ilk hata.

![Kırmızı dalgalı olarak gösterilen hata](../debugger/media/write-better-code-red-squiggle.png)

Bu hatayı gidermek için, Ampul simgesi tarafından temsil edilen IDE'nin başka bir özelliğine bakacaksınız.

## <a name="check-the-light-bulb"></a>Ampulü kontrol et!

İlk kırmızı dalgalı bir derleme zamanı hatasını temsil eder. Üzerine oturun ve mesajı ```The name `Encoding` does not exist in the current context```görüyorsunuz.

Bu hatanın sol altta bir ampul simgesi gösterdiğine dikkat edin. Tornavida ![simgesi tornavida](../ide/media/screwdriver-icon.png)simgesi ile ![birlikte,](../ide/media/light-bulb-icon.png) ampul simgesi ampul ampul simgesi düzeltmek veya kod satırında yeniden faktör yardımcı olabilir Hızlı Eylemler temsil eder. Ampul, düzeltmeniz *gereken* sorunları temsil eder. Tornavida, düzeltmeyi seçebileceğiniz sorunlar içindir. Soldaki **System.Text'i kullanarak** bu hatayı gidermek için önerilen ilk düzeltmeyi kullanın.

![Kodu düzeltmek için ampulü kullanın](../debugger/media/write-better-code-missing-include.png)

Bu öğeyi tıklattığınızda, `using System.Text` Visual Studio *Program.cs* dosyasının üst kısmındaki deyimi ekler ve kırmızı dalgalı kaybolur. (Önerilen düzeltmenin ne yapacağından emin değilseniz, düzeltmeyi uygulamadan önce sağdaki **Önizleme değişiklikleri** bağlantısını seçin.)

Önceki hata, genellikle kodunuza yeni `using` bir deyim ekleyerek düzeltirdiğiniz yaygın bir hatadır. Bu tür hatalar gibi ```The type or namespace `Name` cannot be found.``` bu hatalar için birkaç yaygın, benzer hatalar eksik bir derleme başvurusu gösterebilir (projeyi sağ tıklatın,**Başvuru** **Ekle'yi** > seçin), yanlış yazılmış bir ad veya eklemeniz gereken eksik bir kitaplık (C#için, projeyi sağ tıklatın ve **NuGet Paketlerini Yönet'i**seçin).

## <a name="fix-the-remaining-errors-and-warnings"></a>Kalan hataları ve uyarıları düzeltme

Bu kodda bakmak için birkaç dalgalı vardır. Burada, yaygın bir tür dönüştürme hatası görürsünüz. Dalgalı üzerinde gezinirken, kodun bir dizeyi bir int'e dönüştürmeye çalıştığını görürsünüz ve dönüştürme yapmak için açık kod eklemediğiniz sürece desteklenmez.

![Tür dönüştürme hatası](../debugger/media/write-better-code-conversion-error.png)

Kod çözümleyicisi niyetinizi tahmin edemediği için, bu sefer size yardımcı olacak ampul ler yok. Bu hatayı gidermek için kodun amacını bilmeniz gerekir. Bu örnekte, `points` `points` `totalpoints`'ye eklemeye çalıştığınız için sayısal (tamsayı) değeri olması gerektiğini görmek çok zor değildir.

Bu hatayı düzeltmek için `points` sınıfın `User` üyesini aşağıdakilerden değiştirin:

```csharp
[DataMember]
internal string points;
```

şu şekilde:

```csharp
[DataMember]
internal int points;
```

Kod düzenleyicisindeki kırmızı kıvrımlı çizgiler yok.

Daha sonra, `points` veri üyesinin bildiriminde yeşil dalgalı üzerinde gezinmek. Kod çözümleyicisi, değişkene hiçbir zaman bir değer atanmadı.

![Atanmamış değişken için uyarı iletisi](../debugger/media/write-better-code-warning-message.png)

Genellikle, bu düzeltilmesi gereken bir sorunu temsil eder. Ancak, örnek uygulamada aslında deserialization işlemi `points` sırasında değişkende veri depolama ve daha sonra `totalpoints` veri üyesi için bu değeri ekleyerek. Bu örnekte, kodun amacını biliyorsunuz ve uyarıyı güvenle yok sayabilirsiniz. Ancak, uyarıyı ortadan kaldırmak istiyorsanız, aşağıdaki kodu değiştirebilirsiniz:

```csharp
item.totalpoints = users[i].points;
```

şununla değiştirin:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Yeşil dalgalı gidiyor.

## <a name="fix-an-exception"></a>Özel durumu düzeltme

Tüm kırmızı dalgalı sabit ve çözüldü - ya da en azından araştırılmış - tüm yeşil squiggles, hata ayıklayıcı başlatmak ve uygulamayı çalıştırmak için hazır.

**Hata** Ayıklama > Hata**Ayıklama'ya**veya Hata **Ayıklama** Başlat düğmesine basın Hata Ayıklama araç çubuğunda Hata ![Ayıklama](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklama'yı Başlatma") başlat.

Bu noktada, örnek uygulama bir `SerializationException` özel durum (çalışma zamanı hatası) atar. Diğer bir de, uygulama seri hale getirmeye çalıştığı verilerle boğulur. Uygulamayı hata ayıklama modunda başlattığınız (hata ayıklayıcı ekli) için hata ayıklayıcının Özel Durum Yardımcısı sizi özel durum atan koda götürür ve size yararlı bir hata iletisi verir.

![Serileştirme Özel Durum oluşur](../debugger/media/write-better-code-serialization-exception.png)

Hata iletisi, değerin `4o` bir sonda olarak ayrıştılamayacağını bildirir. Yani, bu örnekte, veri kötü `4o` olduğunu `40`biliyorum: olmalıdır. Ancak, gerçek bir senaryoda verilerin denetiminde değilseniz (bir web hizmetinden aldığınızı varsayalım), bu konuda ne yaparsınız? Bunu nasıl düzeltebiliyorsun?

Bir özel durum vurduğunuzda, birkaç soru sormanız (ve yanıtlamanız) gerekir:

* Bu özel durum sadece düzeltebileceğiniz bir hata mı? Veya

* Bu özel durum, kullanıcılarınızın karşılaşabileceği bir durum mudur?

Eğer eskiyse, hatayı düzelt. (Örnek uygulamada, bu kötü verileri düzeltmek anlamına gelir.) Ikincisi ise, bir `try/catch` blok kullanarak kodunuzda özel durum işlemek gerekebilir (sonraki bölümde diğer olası stratejiler bakmak). Örnek uygulamada aşağıdaki kodu değiştirin:

```csharp
users = ser.ReadObject(ms) as User[];
```

bu kod ile:

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

Bir `try/catch` bloğun bazı performans maliyeti vardır, bu nedenle bunları yalnızca gerçekten ihtiyacınız olduğunda, yani (a) uygulamanın sürüm sürümünde nerede oluşabilecekleri ve (b) yönteme ilişkin belgelerin özel durumu denetlemeniz gerektiğini gösterdiği durumlarda (belgelerin tamamlandığı varsayarak!) kullanmak istersiniz. Çoğu durumda, bir özel durumu uygun şekilde işleyebilirsiniz ve kullanıcının bu konuda bilmesi gerekmez.

Özel durum işleme için birkaç önemli ipucu aşağıda verilmiştir:

* Bir hatayı ortaya çıkarmak `catch (Exception) {}`veya işlemek için uygun eylemi yapmayan boş bir catch bloğu kullanmaktan kaçının. Boş veya bilgilendirici olmayan bir catch bloğu özel durumları gizleyebilir ve kodunuzu hata ayıklamayı kolaylaştırmak yerine daha zor hale getirebilir.

* Özel `try/catch` durumu (örnek uygulamada)`ReadObject`atan belirli bir işlevin etrafındaki bloğu kullanın. Daha büyük bir kod yığınıetrafında kullanırsanız, hatanın konumunu gizlersiniz. Örneğin, burada gösterilen üst `try/catch` işleviçin `ReadToObject`çağrı etrafında blok kullanmayın, ya da özel durum oluştu tam olarak bilemezsin.

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

* Uygulamanıza eklediğiniz yabancı işlevler, özellikle dış verilerle (web isteği gibi) etkileşimde bulunanlar için, işlevin hangi özel durumları ortaya atmasını sağlayacaklarını görmek için belgeleri denetleyin. Bu, doğru hata işleme ve uygulamanızın hata ayıklama için kritik bilgiler olabilir.

Örnek uygulama için, `SerializationException` `GetJsonData` 'ye değiştirerek `4o` `40`yöntemdeki düzeltme

## <a name="clarify-your-code-intent-by-using-assert"></a>Assert'ı kullanarak kod amacınızı netleştirin

Hata Ayıklama Araç Çubuğu'ndaki **(Ctrl** + **Shift** + **F5)** Uygulamayı Yeniden **Başlat** ![Restart App](../debugger/media/dbg-tour-restart.png "Yeniden BaşlatApp") düğmesini tıklatın. Bu, uygulamayı daha az adımda yeniden başlatır. Konsol penceresinde aşağıdaki çıktıyı görürsünüz.

![Çıktıdaki null değeri](../debugger/media/write-better-code-using-assert-null-output.png)

Bu çıktıda doğru olmayan bir şey görebilirsiniz. **üçüncü** kaydın adı ve **soyadı** boş!

Bu yararlı bir kodlama uygulaması hakkında konuşmak için iyi bir zaman, `assert` genellikle az kullanılan, hangi işlevleri ifadeleri kullanmaktır. Aşağıdaki kodu ekleyerek, emin `firstname` olmak için bir çalışma `lastname` zamanı `null`denetimi eklersiniz ve değil. Yöntemde aşağıdaki kodu `UpdateRecords` değiştirin:

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

Geliştirme `assert` işlemi sırasında işlevlerinize bu gibi ifadeler ekleyerek, kodunuzu belirlemenize yardımcı olabilirsiniz. Önceki örnekte, aşağıdakileri belirtiriz:

* İlk ad için geçerli bir dize gereklidir
* Soyadı için geçerli bir dize gereklidir

Bu şekilde niyet belirterek, gereksinimlerinizi uygularsınız. Bu, geliştirme sırasında hataları yüzeye çıkarmak için kullanabileceğiniz basit ve kullanışlı bir yöntemdir. (`assert` ifadeler birim testlerinde ana unsur olarak da kullanılır.)

Hata Ayıklama Araç Çubuğu'ndaki **(Ctrl** + **Shift** + **F5)** Uygulamayı Yeniden **Başlat** ![Restart App](../debugger/media/dbg-tour-restart.png "Yeniden BaşlatApp") düğmesini tıklatın.

> [!NOTE]
> Kod `assert` yalnızca Hata Ayıklama yapısında etkindir.

Yeniden başlattığınızda, hata ayıklama `assert` deyimi duraklar, çünkü `users[i].firstname != null` ifade `false` yerine `true`.

![Assert false'a çözüm gösterir](../debugger/media/write-better-code-using-assert.png)

Hata, `assert` araştırmanız gereken bir sorun olduğunu gösterir. `assert`bir özel durum görmemeniz gereken birçok senaryoyu kapsayabilir. Bu örnekte, kullanıcı bir özel durum görmez `null` ve bir `firstname` değer kayıt listenizdeki gibi eklenir. Bu, daha sonra sorunlara neden olabilir (konsol çıkışında gördüğünüz gibi) ve hata ayıklama daha zor olabilir.

> [!NOTE]
> `null` Değer üzerinde bir yöntem çağırdığınız senaryolarda, sonuç. `NullReferenceException` Normalde genel bir özel `try/catch` durum için bir blok kullanmaktan kaçınmak istersiniz, yani belirli kitaplık işlevine bağlı olmayan bir özel durum. Herhangi bir nesne `NullReferenceException`bir . Emin değilseniz kitaplık işlevi için belgeleri denetleyin.

Hata ayıklama işlemi sırasında, gerçek bir kod `assert` düzeltmesi ile değiştirmeniz gerektiğini bilene kadar belirli bir ifadeyi tutmak iyidir. Kullanıcının uygulamanın bir sürüm yapısında özel durumla karşılaşabiliyor sayılacağına karar verdiğinizi varsayalım. Bu durumda, uygulamanızın önemli bir özel durum ortaya çıkarmadığından veya başka bir hataya yol açmadığından emin olmak için kodu yeniden düzenlemeniz gerekir. Bu nedenle, bu kodu düzeltmek için aşağıdaki kodu değiştirin:

```csharp
if (existingUser == false)
{
    User user = new User();
```

bu kod ile:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Bu kodu kullanarak, kod gereksinimlerinizi karşılar ve verilere `firstname` `lastname` bir `null` veya değeri olan bir kaydın eklenmediğinden emin olun.

Bu örnekte, iki `assert` ifadeyi bir döngünün içine ekledik. Genellikle, kullanırken, `assert`bir işlevin `assert` veya yöntemin giriş noktasında (başlangıçta) deyimeklemek en iyisidir. Şu anda örnek `UpdateRecords` uygulamadaki yönteme bakıyorsunuz. Bu yöntemde, yöntem bağımsız değişkenlerinden biri varsa, `null`sorun olduğunuzu biliyorsunuz, `assert` bu nedenle her ikisini de işlevin giriş noktasında bir deyimle denetleyin.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Önceki ifadeler için, amacınız varolan verileri`db`yüklemek ( )`users`ve yeni veri almak ( ) bir şey güncelleştirmeden önce.

Çözülen `assert` her türlü ifadeyi `true` kullanabilirsiniz. `false` Örneğin, bunun gibi bir `assert` ifade ekleyebilirsiniz.

```csharp
Debug.Assert(users[0].points > 0);
```

Aşağıdaki amacı belirtmek isterseniz, önceki kod yararlıdır: kullanıcının kaydını güncelleştirmek için sıfırdan (0) büyük yeni bir nokta değeri gereklidir.

## <a name="inspect-your-code-in-the-debugger"></a>Hata ayıklayıcıda kodunuzu inceleyin

Tamam, artık örnek uygulama ile yanlış her şeyi kritik sabit ettik, diğer önemli şeyler üzerine taşıyabilirsiniz!

Hata ayıklayıcının Özel Durum Yardımcısı'nı gösterdik, ancak hata ayıklayıcı, kodunuzda adım atma ve değişkenlerini inceleme gibi diğer şeyleri de yapmanızı sağlayan çok daha güçlü bir araçtır. Bu daha güçlü yetenekler birçok senaryoda, özellikle de aşağıdakidurumlarda yararlıdır:

* Kodunuzda bir çalışma zamanı hatasını yalıtmaya çalışıyorsunuz, ancak bunu daha önce tartışılan yöntemler ve araçları kullanarak yapamıyorsunuz.

* Kodunuzu doğrulamak, diğer bir deyişle, beklediğiniz şekilde davrandığından ve istediğinizi yaptığından emin olmak için çalışırken izleyin.

    Kodunuzu çalışırken izlemek öğreticidir. Kodunuz hakkında bu şekilde daha fazla bilgi edinebilir ve hataları belirgin belirtiler ortaya çıkmadan önce genellikle tanımlayabilirsiniz.

Hata ayıklamanın temel özelliklerini nasıl kullanacağınızı öğrenmek [için, mutlak yeni başlayanlar için Hata Ayıklama bölümüne](../debugger/debugging-absolute-beginners.md)bakın.

## <a name="fix-performance-issues"></a>Performans sorunlarını düzeltme

Başka bir tür hata, uygulamanızın yavaş çalışmasına veya çok fazla bellek kullanmasına neden olan verimsiz kodiçerir. Genellikle, performansı en iyi duruma etmek daha sonra uygulama geliştirmenizde yaptığınız bir şeydir. Ancak, performans sorunlarıyla erken karşılaşabilirsiniz (örneğin, uygulamanızın bir kısmının yavaş çalıştığını görürsünüz) ve uygulamanızı profil oluşturma araçlarıyla erkenden test etmeniz gerekebilir. CPU Kullanım aracı ve Memory Analyzer gibi profil oluşturma araçları hakkında daha fazla bilgi için [profil oluşturma araçlarına ilk bakışta](../profiling/profiling-feature-tour.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, kodunuzda ki birçok yaygın hatadan kaçınmayı ve düzeltmeyi ve hata ayıklayıcıyı ne zaman kullanacağınızı öğrendiniz. Ardından, hataları düzeltmek için Visual Studio hata ayıklama sını kullanma hakkında daha fazla bilgi edinin.

> [!div class="nextstepaction"]
> [Başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)
