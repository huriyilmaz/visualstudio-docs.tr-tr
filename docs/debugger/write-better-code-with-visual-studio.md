---
title: Hata ayıklama teknikleri ve araçları
description: Özel durumları onarmak, hataları onarmak ve kodunuzu geliştirmek için Visual Studio 'Yu kullanarak daha az hata ile daha iyi kod yazın
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89311397"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Daha iyi kod yazmanıza yardımcı olacak hata ayıklama teknikleri ve araçları

Kodunuzda hataların ve hataların düzeltilmesi, zaman alan ve bazen sinir bozucu bir görev olabilir. Etkin bir şekilde hata ayıklamanın nasıl yapılacağını öğrenmek zaman alabilir, ancak Visual Studio gibi güçlü bir IDE, işinizi çok daha kolay hale getirir. IDE, hataları düzeltmenize ve kodunuzun hatalarını daha hızlı şekilde hata ayıklamanıza yardımcı olabilir, ancak aynı zamanda daha az hata ile daha fazla kod yazmanıza yardımcı olabilir. Bu makalede, size "hata düzeltme" işleminin bir bütünsel görünümünü sunmamız, bu nedenle Code Analyzer 'ın ne zaman hata ayıklayıcıyı kullanacağınızı, özel durumların nasıl düzeltileceğini ve amaç kodunun nasıl yapılacağını bilmeniz için size "hata düzeltme" sürecinin bir görünümünü sunmaktır. Hata ayıklayıcıyı kullanmanız gerektiğini zaten biliyorsanız bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

Bu makalede, kodlama oturumlarınızın daha üretken olmasını sağlamak için IDE 'yi kullanma hakkında konuşuyoruz. Şöyle birçok göreve dokunuyoruz:

* IDE 'nin kod çözümleyicisini kullanarak kodunuzu hata ayıklama için hazırlayın

* Özel durumları çözme (çalışma zamanı hataları)

* Amacı kodlayarak hataları en aza indirme (onaylama kullanarak)

* Hata ayıklayıcının ne zaman kullanılacağı

Bu görevleri göstermek için, uygulamalarınızda hata ayıklamaya çalışırken karşılaşabileceğiniz en yaygın hata ve hata türlerinden birkaçını gösteririz. Örnek kod C# olsa da, kavramsal bilgiler genellikle C++, Visual Basic, JavaScript ve Visual Studio tarafından desteklenen diğer diller için geçerlidir (aksi belirtilmedikçe). Ekran görüntüleri C# ' de bulunur.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Bazı hatalar ve hatalarda bir örnek uygulama oluşturun

Aşağıdaki kodda, Visual Studio IDE kullanarak düzeltebilmeniz için bazı hatalar vardır. Bu uygulama, bazı bir işlemden JSON verisi alma, verileri bir nesne serisini kaldırma ve yeni verilerle basit bir listeyi güncelleştirme benzetimi yapan basit bir uygulamadır.

Uygulamayı oluşturmak için:

1. Oluşturmak istediğiniz uygulama türüne bağlı olarak, Visual Studio yüklü ve **.NET Core platformlar arası geliştirme** veya **.net masaüstü geliştirme** iş yükü yüklü olmalıdır.

    Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa **Araçlar**  >  **ve Özellikler al**' a tıklayın. Visual Studio Yükleyicisi başlatılır. **.NET Core platformlar arası geliştirme** veya **.net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde **Yeni proje oluştur**' u seçin. Arama kutusuna **konsolunu** yazın ve **konsol uygulaması (.NET Core)** ya da **konsol uygulaması (.NET Framework)** seçeneğini belirleyin. **İleri**’yi seçin. **Console_Parse_JSON** gibi bir proje adı yazın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#** altında, **konsol uygulaması**' nı seçin ve ardından Ortadaki bölmede **konsol uygulaması (.net Core)** veya **konsol uygulaması (.NET Framework)** seçeneğini belirleyin. **Console_Parse_JSON** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Konsol uygulaması (.NET Core)** veya **konsol uygulaması (.NET Framework)** proje şablonunu görmüyorsanız, **Araçlar**' a gidin  >  ve Visual Studio yükleyicisi açan araçlar**ve Özellikler**' e gidin. **.NET Core platformlar arası geliştirme** veya **.net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    Visual Studio, sağ bölmedeki Çözüm Gezgini görüntülenen konsol projesini oluşturur.

1. Projenin *program.cs* dosyasındaki varsayılan kodu aşağıdaki örnek kodla değiştirin.

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

## <a name="find-the-red-and-green-squiggles"></a>Kırmızı ve yeşil dalgalı çizgiler bulun!

Örnek uygulamayı başlatmayı ve hata ayıklayıcıyı çalıştırmayı denemeden önce, kırmızı ve yeşil dalgalı çizgiler için kod düzenleyicisinde kodu kontrol edin. Bunlar, IDE 'nin kod Çözümleyicisi tarafından tanımlanan hataları ve uyarıları temsil eder. Kırmızı dalgalı çizgiler, kodu çalıştırmadan önce düzeltilmesi gereken derleme zamanı hatalardır. Yeşil dalgalı çizgiler uyarılardır. Genellikle, uyarıları düzeltmeden uygulamanızı çalıştırabilmenize karşın, bu hatalar bir hata kaynağı olabilir ve genellikle kendinizi inceleyerek kendi zaman ve sorunlarını kaydedebilirsiniz. Bu uyarılar ve hatalar Ayrıca bir liste görünümünü tercih ediyorsanız **hata listesi** penceresinde görünür.

Örnek uygulamada, düzeltilmesi gereken birkaç kırmızı dalgalı çizgiler ve bakacağımız yeşil bir tane görürsünüz. İlk hata şudur.

![Kırmızı dalgalı çizgi olarak gösterilen hata](../debugger/media/write-better-code-red-squiggle.png)

Bu hatayı onarmak için, bir IDE 'nin ampul simgesiyle temsil eden başka bir özelliğine bakacaksınız.

## <a name="check-the-light-bulb"></a>Ampul ' i kontrol edin!

İlk kırmızı dalgalı çizgi bir derleme zamanı hatasını temsil eder. Üzerine gelin ve iletiyi görürsünüz ```The name `Encoding` does not exist in the current context``` .

Bu hata, sol alt tarafta bir ampul simgesi gösterdiğine dikkat edin. Screwdriver simgesi ![ screwdriver simgesiyle birlikte ampul simgesi ](../ide/media/screwdriver-icon.png) ![ ampul simgesi, ](../ide/media/light-bulb-icon.png) kodu satır içi olarak düzeltmenize veya yeniden oluşturmanıza yardımcı olabilecek hızlı eylemleri temsil eder. Ampul, düzeltilmesi *gereken* sorunları temsil eder. Screwdriver, düzeltilmesi gerekebilecek sorunlar içindir. Soldaki **System. Text öğesini kullanarak** bu hatayı çözmek için ilk önerilen sorunu kullanın.

![Kodu onarmak için ampul kullanın](../debugger/media/write-better-code-missing-include.png)

Bu öğeye tıkladığınızda, Visual Studio `using System.Text` *program.cs* dosyasının en üstüne ifadesini ekler ve kırmızı dalgalı çizgi kaybolur. (Önerilen bir düzeltmesinin ne yapacakından emin değilseniz, bu değişikliği uygulamadan önce sağ taraftaki **Değişiklikleri Önizle** bağlantısını seçin.)

Yukarıdaki hata, kodunuza yeni bir ifade ekleyerek genellikle düzelten yaygın bir yoldur `using` . Bu tür hatalar gibi bu tür hataların yaygın olarak karşılaşılan birkaç hatası vardır ```The type or namespace `Name` cannot be found.``` (projeye sağ tıklayın, başvuru **Ekle**' yi seçin  >  **Reference**), yanlış yazılmış bir ad veya eklemeniz gereken eksik bir kitaplık olabilir (C# için projeye sağ tıklayıp **NuGet Paketlerini Yönet**' i seçin).

## <a name="fix-the-remaining-errors-and-warnings"></a>Kalan hataları ve uyarıları çözme

Bu kodda aranacak birkaç dalgalı çizgiler daha vardır. Burada, ortak bir tür dönüştürme hatası görürsünüz. Dalgalı çizgi üzerine geldiğinizde, kodun bir dizeyi bir int 'e dönüştürmeye çalışıyor olduğunu görürsünüz. Bu, dönüştürmeyi yapmak için açık kod eklemediğiniz takdirde desteklenmez.

![Tür dönüştürme hatası](../debugger/media/write-better-code-conversion-error.png)

Kod Çözümleyicisi amacınızı tahmin edemediği için, bu süreyi kullanmanıza yardımcı olacak açık bir bulu yok. Bu hatayı onarmak için kodun amacını bilmeniz gerekir. Bu örnekte, ' `points` ye eklemeye çalıştığınız için sayısal (tamsayı) değeri olması gerektiğini görmek çok zor değildir `points` `totalpoints` .

Bu hatayı onarmak için `points` sınıfın üyesini şu şekilde değiştirin `User` :

```csharp
[DataMember]
internal string points;
```

şu şekilde:

```csharp
[DataMember]
internal int points;
```

Kod düzenleyicisinde kırmızı dalgalı çizgiler kaybolur.

Ardından, veri üyesinin bildiriminde yeşil dalgalı çizgi üzerine gelin `points` . Kod çözümleyici, değişkene hiçbir değer atanmadığını söyler.

![Atanmamış değişken için uyarı iletisi](../debugger/media/write-better-code-warning-message.png)

Genellikle, bu, düzeltilmesi gereken bir sorunu temsil eder. Ancak, örnek uygulamada, `points` seri durumdan çıkarma işlemi sırasında verileri değişkende depolarsınız ve sonra bu değeri `totalpoints` veri üyesine ekleyebilirsiniz. Bu örnekte, kodun amacını bilir ve uyarıyı güvenle yoksayabilirsiniz. Ancak, uyarıyı ortadan kaldırmak istiyorsanız aşağıdaki kodu değiştirebilirsiniz:

```csharp
item.totalpoints = users[i].points;
```

şununla değiştirin:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Yeşil dalgalı çizgi kaybolur.

## <a name="fix-an-exception"></a>Özel durumu çözme

Tüm Red dalgalı çizgiler ve çözümlenen--veya en az araştırılan--tüm yeşil dalgalı çizgiler, hata ayıklayıcıyı başlatmaya ve uygulamayı çalıştırmaya başlayabilirsiniz.

Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata**Ayıkla > Başlat**) ![veya hata](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

Bu noktada, örnek uygulama bir `SerializationException` özel durum (çalışma zamanı hatası) oluşturur. Yani, uygulama Serileştirmeye çalıştığı verileri alır. Uygulamayı hata ayıklama modunda (hata ayıklayıcı ekli) başlattığınız için, hata ayıklayıcının özel durum Yardımcısı özel durumu oluşturan koda doğru bir hata iletisi verir.

![SerializationException meydana geldi](../debugger/media/write-better-code-serialization-exception.png)

Hata mesajı, değerin `4o` tamsayı olarak ayrıştırılamadığına bildirir. Bu nedenle, bu örnekte verilerin hatalı olduğunu bilirsiniz: `4o` olmalıdır `40` . Ancak gerçek bir senaryoda (bir Web hizmetinden alıyoruz) verilerin denetiminde değilseniz, bununla ilgili ne yapmanız gerekir? Bunu nasıl giderebilirim?

Bir özel durum vurmanız durumunda, birkaç soruyu sormanız (ve yanıtlamanız) gerekir:

* Bu özel durum yalnızca çözebilmeniz için bir hata mu? Veya

* Bu özel durum, kullanıcılarınızın karşılaşabileceği bir şeydir mi?

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

Bu makalede, kodunuzdaki birçok yaygın hatanın nasıl önleneceğini ve hata ayıklayıcının ne zaman kullanılacağını öğrendiniz. Ardından, hataları onarmak için Visual Studio hata ayıklayıcısını kullanma hakkında daha fazla bilgi edinin.

> [!div class="nextstepaction"]
> [Başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)
