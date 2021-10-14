---
title: Hata ayıklama teknikleri ve araçları
description: Özel durumları düzeltmek, hataları düzeltmek ve kodunuzu geliştirmek için Visual Studio kullanarak daha az hatayla daha iyi kod yazma
ms.custom:
- debug-experiment
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
ms.openlocfilehash: 58f60e6c63057e115342e91e3ee50c880411e793
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972498"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Daha iyi kod yazmanıza yardımcı olacak hata ayıklama teknikleri ve araçları

Kodundaki hataları ve hataları düzeltmek zaman alan ve bazen can sıkıcı bir görev olabilir. Hata ayıklamayı etkili bir şekilde öğrenmek zaman alır, ancak Visual Studio gibi güçlü bir IDE, işinizi çok daha kolay hale getirir. IDE yalnızca bu değil, hataları düzeltmenize ve kodunuzun hatalarını daha hızlı ayıklamanıza yardımcı olabilir, ancak daha az hatayla daha iyi kod yazmanıza da yardımcı olabilir. Bu makaledeki hedefimiz size "hata düzeltme" işleminin bütünsel bir görünümünü vermektir. Böylece kod çözümleyiciyi ne zaman, hata ayıklayıcıyı ne zaman kullanabileceğinizi, özel durumları düzeltmeyi ve amaç için kod kullanmayı bilirsiniz. Hata ayıklayıcısını kullanmak zorunda olduğunu zaten biliyorsanız [bkz. İlk olarak hata ayıklayıcısına bakın.](../debugger/debugger-feature-tour.md)

Bu makalede, kodlama oturumlarınızı daha üretken hale getirirken IDE'den yararlanarak bahsedacağız. Çeşitli görevlere dokunuruz, örneğin:

* IDE'nin kod çözümleyiciden yararlanarak kodunuzu hata ayıklama için hazırlama

* Özel durumları düzeltme (çalışma zamanı hataları)

* Amaç için kodlama (onay kullanarak) hataları en aza indirme

* Hata ayıklayıcının ne zaman kullanımı gerekir?

Bu görevleri göstermek için uygulamalarınızı hata ayıklamaya çalışırken karşılaşacakları en yaygın hata ve hata türlerinden birkaçını gösteririz. Örnek kod C# olsa da kavramsal bilgiler genellikle C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (not alınarak hariç). Ekran görüntüleri C# içindedir.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Bazı hatalar ve hatalar olan bir örnek uygulama oluşturma

Aşağıdaki kodda, IDE'leri kullanarak düzeltebilirsiniz Visual Studio vardır. Buradaki uygulama, JSON verilerini bir işlemden alma, verileri bir nesneye alma ve basit bir listeyi yeni verilerle güncelleştirme simülasyonu yapmak için basit bir uygulamadır.

Uygulamayı oluşturmak için:

1. .NET Core Visual Studio ve .NET Core platformlar arası geliştirme **iş yükünün yüklü** olması gerekir.

    Henüz yüklemedıysanız, Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve **Özellikleri**  >  **Al'a tıklayın.** Uygulama Visual Studio Yükleyicisi başlatıyor. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.** Arama **kutusuna** console yazın ve ardından .NET Core **için Konsol Uygulaması'dan** birini seçin. **İleri**’yi seçin. Console_Parse_JSON gibi **bir proje adı yazın** ve Ardından **veya** **Oluştur**'a (varsa) tıklayın.

    .NET Core için önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından Oluştur'a **seçin.**

    .NET Core için Konsol **Uygulaması** proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al'a gidin ve bu  >  işlem Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** altında Konsol Uygulaması'nu seçin ve orta bölmede Konsol Uygulaması  **(.NET Core) öğesini seçin.** Console_Parse_JSON gibi **bir ad yazın ve** Tamam'a **tıklayın.**

    Konsol Uygulaması **(.NET Core)** proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al'a gidin ve  >  bu işlem Visual Studio Yükleyicisi. **.NET Core platformlar arası geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**
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

Örnek uygulamayı başlatmayı ve hata ayıklayıcıyı çalıştırmayı denemeden önce, kod düzenleyicisinde kırmızı ve yeşil geçişler olup o kodu kontrol edin. Bunlar, IDE'nin kod çözümleyicisi tarafından tanımlanan hataları ve uyarıları temsil eder. Kırmızı geçişler, kodu çalıştırmadan önce düzeltmesi gereken derleme zamanı hatalarıdır. Yeşil geçişler uyarıdır. Genellikle uyarıları düzeltmeden uygulama çalıştırabilirsiniz, ancak bunlar bir hata kaynağı olabilir ve bunları araştırarak zaman ve sorundan tasarruf sağlarsınız. Liste görünümünü tercih ediyorsanız, bu **uyarılar ve** hatalar Hata Listesi penceresinde de gösterilir.

Örnek uygulamada düzeltmesi gereken birkaç kırmızı çizgi ve bakacağız yeşil bir tane var. İlk hata şu şekildedir.

![Kırmızı geçiş olarak gösterilen hata](../debugger/media/write-better-code-red-squiggle.png)

Bu hatayı düzeltmek için IDE'nin ampul simgesiyle temsil edilen başka bir özelliğine bakabilirsiniz.

## <a name="check-the-light-bulb"></a>Ampulü kontrol edin!

İlk kırmızı geçiş, derleme zamanı hatasını temsil eder. Üzerine gelin ve iletiyi ```The name `Encoding` does not exist in the current context``` alırsınız.

Bu hatanın sol altta bir ampul simgesi gösterir. Tornavida simgesi tornavida simgesiyle birlikte ampul simgesi ampul simgesi satır içi kodu düzeltmeye veya yeniden düzenlemeye yardımcı olan Hızlı ![ ](../ide/media/screwdriver-icon.png) ![ ](../ide/media/light-bulb-icon.png) Eylemler'i temsil eder. Ampul, düzeltmesi gereken sorunları *temsil* eder. Tornavida, düzeltmeyi seçebilirsiniz sorunlar için. Önerilen ilk düzeltmeyi kullanarak sol tarafta **System.Text'i kullanarak bu** hatayı düzeltin.

![Kodu düzeltmek için ampulü kullanma](../debugger/media/write-better-code-missing-include.png)

Bu öğeye tıklarsanız Visual Studio Program.cs dosyasının en üstüne deyimini ekler ve kırmızı `using System.Text` çizgi kaybolur.  (Önerilen bir düzeltmenin ne yapar emin değilken **düzeltmeyi** uygulamadan önce sağdan Değişiklikleri önizle bağlantısını seçin.)

Yukarıdaki hata, genellikle kodunuza yeni bir deyim ekleyerek düzeltilen `using` yaygın bir hatadır. Bu tür hatalar eksik derleme başvurusuna işaret ediyor olabilir (projeye sağ tıklayın, Başvuru Ekle'yi seçin), yanlış yazılmış bir ad veya eklemeniz gereken eksik bir kitaplık gibi çeşitli yaygın hatalar vardır (C# için projeye sağ tıklayın ve NuGet Paketlerini ```The type or namespace `Name` cannot be found.``` Yönet'i   >  seçin). 

## <a name="fix-the-remaining-errors-and-warnings"></a>Kalan hataları ve uyarıları düzeltme

Bu kodda birkaç tane daha göz atabilirsiniz. Burada yaygın bir tür dönüştürme hatası görüyorsunuz. Geçişin üzerine gelindiğinde, kodun bir dizeyi int'e dönüştürmeye çalıştığını görüyorsunuz. Dönüştürmeyi yapmak için açık kod eklemedikçe bu desteklenmiyor.

![Tür dönüştürme hatası](../debugger/media/write-better-code-conversion-error.png)

Kod çözümleyicisi amacınızı tahmin edebilirim, bu kez size yardımcı olacak ampuller yoktur. Bu hatayı düzeltmek için kodun amacını biliyor gerekir. Bu örnekte, 'a eklemeye çalıştığınıza göre sayısal `points` (tamsayı) bir değer olması gerektiğini görmek çok zor `points` `totalpoints` değildir.

Bu hatayı düzeltmek için sınıfın `points` üyesini `User` şu şekilde değiştirebilirsiniz:

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

**F5** (**Hata Ayıklama > Başlat**) veya Hata Ayıklama ![](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") araç çubuğunda Hata Ayıklamayı Başlat düğmesine basın. 

Bu noktada örnek uygulama bir özel durum `SerializationException` (çalışma zamanı hatası) oluşturur. Başka bir ifadeyle, uygulama serileştirmeye çalıştığı veriler üzerinde çalışıyor. Uygulamayı hata ayıklama modunda (hata ayıklayıcı ekli) başlattınız, hata ayıklayıcının Özel Durum Yardımcısı sizi özel durumu veren koda doğru alır ve size yararlı bir hata iletisi verir.

![SerializationException oluşur](../debugger/media/write-better-code-serialization-exception.png)

Hata iletisi, değerin tamsayı `4o` olarak ayrıştırılanamaması talimatını verir. Bu örnekte verilerin kötü olduğunu biliyorsunuz: `4o` olması `40` gerekir. Ancak, gerçek bir senaryoda verilerin denetiminde değilken (bir web hizmetten alıyorsanız) bu konuda ne yapacaksınız? Bunu nasıl düzeltin?

Bir özel durumla karşılasanız birkaç soru sormalı (ve yanıtla) gerekir:

* Bu özel durum yalnızca düzeltebilir bir hata mı? Veya

* Bu özel durum, kullanıcılarının karşılaş olabileceği bir durum mu?

Bu, eski ise hatayı düzeltir. (Örnek uygulamada, bu, bozuk verileri düzeltir anlamına gelir.) İkinci ise, bir blok kullanarak kodunuzda özel durumu işlemeniz gerekebilir `try/catch` (sonraki bölümde yer aldığı diğer stratejileri inceleyeceğiz). Örnek uygulamada aşağıdaki kodu değiştirin:

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

Bir `try/catch` blok bazı performans maliyetlerine sahiptir, bu nedenle yalnızca gerçekten ihtiyacınız olduğunda, yani (a) uygulamanın yayın sürümünde oluşabileceği ve (b) yöntemi için belge, özel durumu denetlemeniz gerektiğini (belgelerin tamamlandığı varsayılarak!) gösterir. Birçok durumda, bir özel durumu uygun şekilde işleyebilir ve kullanıcının bunu bilmesi gerekmez.

Özel durum işleme için birkaç önemli ipucu aşağıda verilmiştir:

* `catch (Exception) {}`Bir hatayı göstermek veya işlemek için uygun eylemi olmayan, gibi boş bir catch bloğu kullanmaktan kaçının. Boş veya bilgilendirici olmayan bir catch bloğu özel durumları gizleyebilir ve kodunuzu daha kolay hale getirmek yerine hata ayıklamanın daha zor hale getirebilirsiniz.

* `try/catch`Özel durumu oluşturan özel işlevin etrafındaki bloğu kullanın ( `ReadObject` Örneğin, örnek uygulamada). Daha büyük bir kod öbeği etrafında kullanıyorsanız hatanın konumunu gizlemiş olursunuz. Örneğin, `try/catch` burada gösterilen üst işleve yapılan çağrının etrafında bloğu kullanmayın `ReadToObject` veya tam olarak özel durumun nerede oluştuğunu bilemezsiniz.

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

* Uygulamanıza dahil ettiğiniz, özellikle dış verilerle (örneğin, bir Web isteği) etkileşimde bulunan tanıdık işlevler için, işlevin hangi özel durumları oluşturacaklarına bakmak için belgelere bakın. Bu, doğru hata işleme ve uygulamanızda hata ayıklama için kritik bilgiler olabilir.

Örnek uygulama için öğesini `SerializationException` `GetJsonData` olarak değiştirerek metodunu onarın `4o` `40` .

## <a name="clarify-your-code-intent-by-using-assert"></a>Onaylama kullanarak kod amacınızı açıklığa kavuşturun

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL**  +  **SHIFT**  +  **F5**) düğmesine tıklayın. Bu, uygulamayı daha az adımda yeniden başlatır. Konsol penceresinde aşağıdaki çıktıyı görürsünüz.

![Çıktıda null değer](../debugger/media/write-better-code-using-assert-null-output.png)

Bu çıktıda gerçekten doğru olmayan bir şeyi görebilirsiniz. üçüncü kaydın **adı** ve **Soyadı** boştur!

Bu, işlevinizdeki deyimleri kullanmak üzere genellikle az kullanılan, faydalı bir kodlama uygulaması hakkında konuşmak için iyi bir zamandır `assert` . Aşağıdaki kodu ekleyerek, ve ' nin olmadığından emin olmak için bir çalışma zamanı denetimi dahil edersiniz `firstname` `lastname` `null` . Yönteminde aşağıdaki kodu değiştirin `UpdateRecords` :

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

`assert`Geliştirme süreci sırasında işlevlerinize bu gibi deyimler ekleyerek, kodunuzun amacını belirtmenize yardımcı olabilirsiniz. Yukarıdaki örnekte, aşağıdakileri belirttik:

* İlk ad için geçerli bir dize gerekir
* Son ad için geçerli bir dize gerekiyor

Bu şekilde amacı belirterek gereksinimlerinizi zorunlu kılabilirsiniz. Bu, geliştirme sırasında hataları yüzeyde kullanabileceğiniz basit ve kullanışlı bir yöntemdir. ( `assert` deyimler Ayrıca birim testlerinde ana öğe olarak da kullanılır.)

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![Başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL**  +  **SHIFT**  +  **F5**) düğmesine tıklayın.

> [!NOTE]
> `assert`Kod yalnızca bir hata ayıklama derlemesinde etkindir.

' İ yeniden başlattığınızda, `assert` ifadesi `users[i].firstname != null` yerine olarak değerlendirdiği için hata ayıklayıcı deyimde duraklatılır `false` `true` .

![Onaylama, yanlış olarak çözümleniyor](../debugger/media/write-better-code-using-assert.png)

`assert`Hata, araştırmanız gereken bir sorun olduğunu söyler. `assert` , özel durum görmemenizi gerektiren birçok senaryoyu kapsayabilir. Bu örnekte, Kullanıcı bir özel durum görmez ve `null` Kayıt listenizde bir değer eklenir `firstname` . Bu, daha sonra (konsol çıktısında gördüğünüz gibi) sorunlara neden olabilir ve hata ayıklama zor olabilir.

> [!NOTE]
> Değer üzerinde bir yöntemi çağıran senaryolarda `null` , bir `NullReferenceException` sonuç. Genellikle `try/catch` genel bir özel durum için bir blok kullanmaktan kaçınmak istersiniz, diğer bir deyişle, belirli bir kitaplık işlevine bağlı olmayan bir özel durumdur. Herhangi bir nesne bir oluşturabilir `NullReferenceException` . Emin değilseniz, kitaplık işlevine yönelik belgelere bakın.

Hata ayıklama işlemi sırasında, `assert` gerçek bir kodu düzeltme ile değiştirmeniz gerektiğini öğrenene kadar belirli bir deyimin tutulması iyi olur. Kullanıcının, uygulamanın yayın derlemesinde özel durumla karşılaşmasına karar verdiğinizi varsayalım. Bu durumda, uygulamanızın önemli bir özel durum oluşturmadığını veya başka bir hatayla sonuçlanmayacağını doğrulamak için kodu yeniden düzenlemeniz gerekir. Bu nedenle, bu kodu onarmak için aşağıdaki kodu değiştirin:

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

Bu kodu kullanarak, kod gereksinimlerinizi karşılamanız ve veya değerine sahip bir kaydın `firstname` `lastname` `null` verilere eklenmediğinden emin olmanız gerekir.

Bu örnekte, `assert` bir döngünün içindeki iki deyimi ekledik. Genellikle, kullanırken `assert` `assert` bir işlevin veya yöntemin giriş noktasında (başlangıç) deyimler eklemek en iyisidir. Şu anda `UpdateRecords` örnek uygulamadaki yöntemine bakıyorsunuz. Bu yöntemde, yöntem bağımsız değişkenlerinden herhangi biri olduğunda sorun olduğunu bildiğiniz `null` `assert` için, işlevin giriş noktasındaki bir deyimle birlikte bunları işaretleyin.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Yukarıdaki deyimler için, size herhangi bir şeyi güncelleştirmeden önce var olan verileri ( `db` ) ve yeni verileri () almanızı ve amacınızı yapmanız gerekir `users` .

`assert`Veya olarak çözümlenen herhangi bir tür ifadeyle kullanabilirsiniz `true` `false` . Bu nedenle, örneğin, `assert` buna benzer bir ifade ekleyebilirsiniz.

```csharp
Debug.Assert(users[0].points > 0);
```

Aşağıdaki amacı belirtmek istiyorsanız, yukarıdaki kod yararlı olur: kullanıcının kaydını güncelleştirmek için sıfırdan büyük yeni bir nokta değeri (0) gerekir.

## <a name="inspect-your-code-in-the-debugger"></a>Hata ayıklayıcıda kodunuzu inceleyin

Şimdi, örnek uygulamada yanlış olan her şeyi düzelttiniz, diğer önemli malzelere geçebilirsiniz!

Hata ayıklayıcının özel durum Yardımcısı ' nı gösterdi, ancak hata ayıklayıcı, kodunuzda adım adım ve değişkenlerini İnceleme gibi diğer şeyleri de yapmanızı sağlayan çok daha güçlü bir araçtır. Bu daha güçlü yetenekler birçok senaryoda faydalıdır, özellikle aşağıdakiler aşağıda verilmiştir:

* Kodunuzda bir çalışma zamanı hatasını yalıtmak istiyorsunuz, ancak daha önce ele alınan yöntemleri ve araçları kullanarak yapamıyordu.

* Kodunuzu doğrulamak, diğer bir deyişle, çalışırken izlemek ve istediğiniz şekilde davrandığından emin olmak için, çalışırken izleyin.

    Çalışırken kodunuzu izlemek için kullanılır. Kodunuz hakkında daha fazla bilgi edinmek için bu yöntemi kullanabilirsiniz.

Hata ayıklayıcının temel özelliklerini nasıl kullanacağınızı öğrenmek için bkz. [mutlak yeni başlayanlar Için hata ayıklama](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Performans sorunlarını çözme

Başka bir türdeki hatalar, uygulamanızın yavaş çalışmasına veya çok fazla bellek kullanmasına neden olan verimsiz kod içerir. Genellikle, performansı en iyi duruma getirmek uygulama geliştirmede daha sonra yaptığınız şeydir. Bununla birlikte, performans sorunlarıyla karşılaşabilirsiniz (örneğin, uygulamanızın bir bölümünün yavaş çalıştığını görürsünüz) ve uygulamanızı önceden profil oluşturma araçlarıyla test etmeniz gerekebilir. CPU kullanımı aracı ve bellek Çözümleyicisi gibi profil oluşturma araçları hakkında daha fazla bilgi için bkz. [profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, kodunuzdaki birçok yaygın hatanın nasıl önleneceğini ve hata ayıklayıcının ne zaman kullanılacağını öğrendiniz. sonra, hataları onarmak için Visual Studio hata ayıklayıcıyı kullanma hakkında daha fazla bilgi edinin.

> [!div class="nextstepaction"]
> [Başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)
