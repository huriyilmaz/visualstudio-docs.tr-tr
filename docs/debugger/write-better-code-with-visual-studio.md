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
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416418"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Daha iyi kod yazmanıza yardımcı olacak hata ayıklama teknikleri ve araçları

Kodunuzda hataların ve hataların düzeltilmesi, zaman alan ve bazen sinir bozucu bir görev olabilir. Etkili bir şekilde hata ayıklama hakkında bilgi edinmek için zaman alır, ancak Visual Studio gibi güçlü bir IDE işinizi çok daha kolay hale getirebilirsiniz. IDE, hataları düzeltmenize ve kodunuzun hatalarını daha hızlı şekilde hata ayıklamanıza yardımcı olabilir, ancak aynı zamanda daha az hata ile daha fazla kod yazmanıza yardımcı olabilir. Bu makalede, size "hata düzeltme" işleminin bir bütünsel görünümünü sunmamız, bu nedenle Code Analyzer 'ın ne zaman hata ayıklayıcıyı kullanacağınızı, özel durumların nasıl düzeltileceğini ve amaç kodunun nasıl yapılacağını bilmeniz için size "hata düzeltme" sürecinin bir görünümünü sunmaktır. Hata ayıklayıcıyı kullanmanız gerektiğini zaten biliyorsanız bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

Bu makalede, kodlama oturumlarınızın daha üretken olmasını sağlamak için IDE 'yi kullanma hakkında konuşuyoruz. Biz gibi çeşitli görevler üzerinde dokunma:

* Kodunuzu IDE'nin kod Çözümleyicisi yararlanarak hata ayıklama için hazırlama

* Özel durumlar (çalışma zamanı hataları) nasıl

* Amacı kodlayarak hataları en aza indirme (onaylama kullanarak)

* Hata ayıklayıcıyı kullanma zamanı

Bu görevleri göstermek için sık karşılaşılan hatalar ve uygulamalarınızın hatalarını ayıklamak çalışırken karşılaşabileceğiniz hatalar birkaçını göstereceğiz. Örnek kod olmasına rağmen C#, kavramsal bilgiler için C++, Visual Basic JavaScript genel olarak geçerli olduğunu ve diğer diller (belirtilenler dışında) Visual Studio tarafından desteklenen. Ekran görüntüleri C# ' de var.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Bazı hatalar ve hatalarda bir örnek uygulama oluşturun

Aşağıdaki kod, Visual Studio IDE kullanarak düzeltebilirsiniz bazı hatalar var. Buradan uygulama bazı işlemi, verileri bir nesne seri durumdan çıkarılırken ve yeni veriler ile basit bir liste güncelleştiriliyor alınırken JSON veri benzetimi gerçekleştiren basit bir uygulamadır.

Uygulamayı oluşturmak için:

1. Oluşturmak istediğiniz uygulama türüne bağlı olarak, Visual Studio yüklü ve **.NET Core platformlar arası geliştirme** veya **.net masaüstü geliştirme** iş yükü yüklü olmalıdır.

    Visual Studio 'Yu henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa Araçlar **ve Özellikler al** > **Araçlar** ' a tıklayın. Visual Studio Yükleyicisi'ni başlatır. **.NET Core platformlar arası geliştirme** veya **.net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

1. Visual Studio'yu açın.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresinde **Yeni proje oluştur**' u seçin. Arama kutusuna **konsolunu** yazın ve **konsol uygulaması (.NET Core)** ya da **konsol uygulaması (.NET Framework)** seçeneğini belirleyin. **İleri**’yi seçin. **Console_Parse_JSON** gibi bir proje adı yazın ve **Oluştur**' a tıklayın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **görsel C#** altında **konsol uygulaması**' nı seçin ve ardından Ortadaki bölmede **konsol uygulaması (.NET Core)** veya **konsol uygulaması (.NET Framework)** seçeneğini belirleyin. **Console_Parse_JSON** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Konsol uygulaması (.NET Core)** veya **konsol uygulaması (.NET Framework)** proje şablonunu görmüyorsanız, Visual Studio yükleyicisi açan araçlar **ve Özellikler al** > **Araçlar** ' a gidin. **.NET Core platformlar arası geliştirme** veya **.net masaüstü geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

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

## <a name="find-the-red-and-green-squiggles"></a>Kırmızı ve yeşil dalgalı çizgiler öğrenin!

Örnek uygulamayı başlatın ve hata ayıklayıcıyı çalıştırmak denemeden önce kırmızı ve yeşil dalgalı çizgiler için Kod Düzenleyicisi'nde kodunu kontrol edin. Bu, hataları ve Uyarıları IDE'nin kod Çözümleyicisi tarafından tanımlanan temsil eder. Derleme zamanı hataları, kırmızı dalgalı çizgiler olan, önce düzeltmeniz gerekiyor kodu çalıştırabilirsiniz. Yeşil dalgalı çizgiler uyarıları var. Uyarıları düzeltmeden uygulamanızı genellikle çalıştırabilirsiniz, ancak hatalar, kaynak olabilirler ve, genellikle kendiniz zaman ve sorun araştırma olarak kaydedin. Bu uyarılar ve hatalar Ayrıca bir liste görünümünü tercih ediyorsanız **hata listesi** penceresinde görünür.

Örnek uygulamada, düzeltmeniz gereken birkaç kırmızı dalgalı çizgiler ve şu konuları inceleyeceğiz bir yeşil bir bakın. İlk hata aşağıda verilmiştir.

![Bir kırmızı dalgalı çizgi gösterme hatası](../debugger/media/write-better-code-red-squiggle.png)

Bu hatayı düzeltmek için başka bir özelliği ampul simgesini tarafından temsil edilen IDE'nin yaratacağını göreceğiz.

## <a name="check-the-light-bulb"></a>Ampul kontrol edin!

İlk kırmızı dalgalı bir derleme zamanı hatası temsil eder. Üzerine gelin ve ```The name `Encoding` does not exist in the current context```iletiyi görürsünüz.

Bu hata sol alt köşesinde bir ampul simgesini gösterdiğine dikkat edin. Screwdriver simgesi ![screwdriver simgesi](../ide/media/screwdriver-icon.png), ampul simgesi ![ampul simgesi](../ide/media/light-bulb-icon.png) satır içi kodu düzeltmenize veya yeniden oluşturmanıza yardımcı olabilecek hızlı eylemleri temsil eder. Ampul, düzeltilmesi *gereken* sorunları temsil eder. Tornavida düzeltmek için tercih edebileceğiniz sorunlarda veririz. Soldaki **System. Text öğesini kullanarak** bu hatayı çözmek için ilk önerilen sorunu kullanın.

![Kodu düzeltmek için ampul kullanın](../debugger/media/write-better-code-missing-include.png)

Bu öğeye tıkladığınızda, Visual Studio, *program.cs* dosyasının üst kısmına `using System.Text` ifadesini ekler ve kırmızı dalgalı çizgi kaybolur. (Önerilen bir düzeltmesinin ne yapacakından emin değilseniz, bu değişikliği uygulamadan önce sağ taraftaki **Değişiklikleri Önizle** bağlantısını seçin.)

Yukarıdaki hata, kodunuza yeni bir `using` beyanını ekleyerek genellikle Düzeltmelerinizin yaygın bir yoldur. Bu tür hataların yaygın, benzer bir şekilde ```The type or namespace `Name` cannot be found.``` olması gibi birçok hata vardır (projeye sağ tıklayın, > **başvuru** C# **Ekle** ), yanlış yazılmış bir ad veya eklemek için gereken eksik bir kitaplık (Için, projeye sağ tıklayıp **NuGet Paketlerini Yönet**' i seçin).

## <a name="fix-the-remaining-errors-and-warnings"></a>Kalan hataları ve uyarıları çözme

Bu kodda bakmak için birkaç daha fazla dalgalı çizgiler vardır. Burada, bir ortak tür dönüştürme hatası görürsünüz. Dalgalı çizgi geldiğinizde, kodun bir dize dönüştürme yapmak için açık kod eklemediğiniz sürece, desteklenmeyen bir int'e dönüştürme çalıştığını görürsünüz.

![Tür dönüştürme hatası](../debugger/media/write-better-code-conversion-error.png)

Kod Çözümleyicisi amacınızı olamaz çünkü bu zaman aşımına yardımcı olmak için hiçbir ampuller vardır. Bu hatayı düzeltmek için kodun amacı bilmeniz gerekir. Bu örnekte, `totalpoints``points` eklemeye çalıştığınız için `points` sayısal (tamsayı) değer olması gerektiğini görmek çok zor değildir.

Bu hatayı onarmak için `User` sınıfının `points` üyesini şu şekilde değiştirin:

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

Sonra, `points` veri üyesinin bildiriminde yeşil dalgalı çizgi üzerine gelin. Kod Çözümleyicisi değişkeni hiçbir zaman bir değer atanır söyler.

![Atanmamış değişken için uyarı iletisi](../debugger/media/write-better-code-warning-message.png)

Genellikle, bu düzeltilmesi gereken bir sorunu temsil eder. Ancak, örnek uygulamada, kaldırma işlemi sırasında verileri `points` değişkenine depolarsınız ve sonra bu değeri `totalpoints` veri üyesine eklersiniz. Bu örnekte, kodun amacı bildiğiniz ve uyarıyı yok sayabilirsiniz. Ancak, uyarıyı ortadan kaldırmak istiyorsanız, aşağıdaki kodu değiştirin:

```csharp
item.totalpoints = users[i].points;
```

şununla değiştirin:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Yeşil dalgalı çizgi kaybolduktan.

## <a name="fix-an-exception"></a>Bir özel durum düzeltme

Tüm kırmızı dalgalı çizgiler sabit ve çözümlenen--veya en az araştırılması--tüm yeşil dalgalı hata ayıklayıcıyı başlatın ve uygulamayı çalıştırmak hazır olursunuz.

Hata ayıklama araç çubuğunda **F5** tuşuna basın (hata**Ayıkla > Başlat**) ![veya hata](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") **ayıklamayı** Başlat düğmesine basın.

Bu noktada, örnek uygulama `SerializationException` bir özel durum oluşturur (bir çalışma zamanı hatası). Diğer bir deyişle, uygulama seri hale getirilmeye çalışıldığında veri sıkıştıracak. Uygulamayı (hata ayıklayıcısı ekli) hata ayıklama modunda başlatıldığından, hata ayıklayıcı'nın özel durum Yardımcısı, özel durum oluşturdu ve yararlı bir hata mesajıyla sağ koduna götürür.

![Bir SerializationException gerçekleşir](../debugger/media/write-better-code-serialization-exception.png)

Hata iletisi, `4o` değer bir tamsayı olarak ayrıştırılamadığına bildirir. Bu nedenle, bu örnekte verilerin bozuk olduğunu bilirsiniz: `4o` `40`olmalıdır. Ancak, gerçek bir senaryo (örneğin, gün geçtikçe, bir web hizmetinden) verilerin denetiminde olup olmadığını, ne yaparsınız hakkında? Nasıl bu sorunu?

Bir özel durum ulaştığınızda birkaç soru sormak (ve yanıtlamak) gerekir:

* Bu özel durumu düzeltmek bir hata mı? Veya

* Bu durum, kullanıcılarınızın karşılaşabileceği bir şey mi?

Eski ise, hata düzeltildi. (Örnek uygulamada, bu, bozuk verileri düzeltir anlamına gelir.) İkinci ise, `try/catch` bir blok kullanarak kodunuzda özel durumu işlemeniz gerekebilir (sonraki bölümde yer aldığı diğer stratejileri inceleyeceğiz). Örnek uygulamada, aşağıdaki kodu değiştirin:

```csharp
users = ser.ReadObject(ms) as User[];
```

Bu kod ile:

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

`try/catch` bloğu bazı performans maliyetlerine sahiptir, bu nedenle yalnızca gerçekten ihtiyacınız olduğunda, yani (a) uygulamanın yayın sürümünde oluşabileceği ve (b) yöntemi için belge, özel durumu denetlemeniz gerektiğini (belgelerin tamamlandığı varsayılarak!) gösterir. Çoğu durumda, kullanıcının hiçbir zaman bunu bilmek gerekir ve bir özel durum uygun şekilde işleyebilir.

Birkaç özel durum işleme için önemli ipuçları şunlardır:

* Bir hatayı açığa çıkarmak veya işlemek için uygun eylemi olmayan `catch (Exception) {}`gibi boş bir catch bloğu kullanmaktan kaçının. Bir boş veya bilgilendirici olmayan yakalama bloğu özel durumları gizleyebilirsiniz ve kodunuzu yerine kolay bir şekilde hata ayıklamak daha zor hale getirebilir.

* Özel durumu oluşturan özel işlevin etrafında `try/catch` bloğunu kullanın (`ReadObject`, örnek uygulamada). Kod daha büyük öbek geçici bir çözüm kullanıyorsanız hatanın konumunu gizleme yukarı bitmelidir. Örneğin, burada gösterilen ana işlev `ReadToObject`çağrısının etrafında `try/catch` bloğunu kullanmayın veya tam olarak özel durumun nerede oluştuğunu bilemezsiniz.

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

* Uygulamanıza dahil ettiğiniz, özellikle dış verilerle (örneğin, bir Web isteği) etkileşimde bulunan tanıdık işlevler için, işlevin hangi özel durumları oluşturacaklarına bakmak için belgelere bakın. Bu kritik bilgilerini uygun hata işleme ve uygulamanızın hatalarını ayıklamak için olabilir.

Örnek uygulama için `4o` `40`olarak değiştirerek `GetJsonData` yöntemindeki `SerializationException` onarın.

## <a name="clarify-your-code-intent-by-using-assert"></a>Assert kullanarak, kodun amacı açıklamak

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın. Bu, daha az adımları uygulamayı yeniden başlatır. Konsol penceresinde aşağıdaki çıktıyı görürsünüz.

![Çıkış değeri null](../debugger/media/write-better-code-using-assert-null-output.png)

Oldukça doğru değil Bu çıktıyı bir şey görebilirsiniz. üçüncü kaydın **adı** ve **Soyadı** boştur!

Bu, işlevinizdeki `assert` deyimlerini kullanmak üzere genellikle az kullanılan, faydalı bir kodlama uygulaması hakkında konuşmak için iyi bir zamandır. Aşağıdaki kodu ekleyerek, `firstname` ve `lastname` `null`olmadığından emin olmak için bir çalışma zamanı denetimi dahil edersiniz. `UpdateRecords` yönteminde aşağıdaki kodu değiştirin:

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

Geliştirme işlemi sırasında işlevlerinize bu gibi `assert` deyimler ekleyerek, kodunuzun amacını belirtmeye yardımcı olabilirsiniz. Önceki örnekte, biz aşağıdakileri belirtin:

* Geçerli bir dize için ad gereklidir
* Geçerli bir dize için Soyadı gereklidir

Bu şekilde hedefi belirterek, gereksinimlerinizi uygular. Bu, geliştirme sırasında yüzey hataları için kullanabileceğiniz basit ve kullanışlı bir yöntemdir. (`assert` deyimleri, birim testlerinde ana öğe olarak da kullanılır.)

Hata ayıklama araç çubuğundaki uygulamayı **yeniden** ![başlat](../debugger/media/dbg-tour-restart.png "RestartApp") (**CTRL** + **SHIFT** + **F5**) düğmesine tıklayın.

> [!NOTE]
> `assert` kodu yalnızca bir hata ayıklama derlemesinde etkindir.

Yeniden başlattığınızda, ifade `users[i].firstname != null` `true`yerine `false` olarak değerlendirildiği için hata ayıklayıcı `assert` deyiminde duraklatılır.

![Assert false çözümler](../debugger/media/write-better-code-using-assert.png)

`assert` hatası, araştırmanız gereken bir sorun olduğunu söyler. `assert` bir özel durum görmemenizi pek çok senaryoyu kapsayabilir. Bu örnekte, Kullanıcı bir özel durum görmez ve Kayıt listenizde `firstname` olarak `null` bir değer eklenir. (Konsol çıkışında gördüğünüz gibi) bu sorunlara daha sonra neden olabilir ve hata ayıklamak için daha zor olabilir.

> [!NOTE]
> `null` değerinde bir yöntemi çağırdığınız senaryolarda, `NullReferenceException` bir sonuç elde edersiniz. Genellikle genel bir özel durum için `try/catch` bloğu kullanmaktan kaçınmak istersiniz, diğer bir deyişle, belirli bir kitaplık işlevine bağlı olmayan bir özel durumdur. Herhangi bir nesne `NullReferenceException`oluşturabilir. Emin değilseniz kitaplığı işlevine yönelik belgelere bakın.

Hata ayıklama işlemi sırasında, gerçek bir kod düzeltmesinin yerine getirmeniz gerektiğini öğrenene kadar belirli bir `assert` ekstresini tutmak iyi olur. Kullanıcının uygulamanın derleme bir özel durum karşılaşabilirsiniz karar varsayalım. Bu durumda, uygulamanız önemli bir durum değil veya diğer bazı hataya neden emin olmak için kodu yeniden düzenleme gerekir. Bu nedenle, bu kodu düzeltmek için aşağıdaki kodu değiştirin:

```csharp
if (existingUser == false)
{
    User user = new User();
```

Bu kod ile:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Bu kodu kullanarak, kod gereksinimlerinizi karşılamanız ve `null` `firstname` veya `lastname` değerine sahip bir kaydın verilere eklenmediğinden emin olmanız gerekir.

Bu örnekte, bir döngünün içinde iki `assert` deyimini ekledik. Genellikle `assert`kullanırken, bir işlevin veya yöntemin giriş noktasında (başlangıç) `assert` deyimleri eklemek en iyisidir. Şu anda örnek uygulamadaki `UpdateRecords` yöntemine bakıyorsunuz. Bu yöntemde, yöntem bağımsız değişkenlerinden biri `null`olduğunda sorun yaşadıysanız, bu nedenle bunları işlevin giriş noktasındaki `assert` bildirimiyle birlikte denetleyin.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Yukarıdaki deyimler için, size herhangi bir şeyi güncelleştirmeden önce varolan verileri (`db`) yükleyip yeni verileri (`users`) almanızı öneririz.

`assert`, `true` veya `false`çözen her türlü ifade ile kullanabilirsiniz. Bu nedenle, örneğin, buna benzer bir `assert` deyimleri ekleyebilirsiniz.

```csharp
Debug.Assert(users[0].points > 0);
```

Yukarıdaki kod, aşağıdaki amacını belirtmek istiyorsanız kullanışlıdır: yeni bir noktası değeri sıfır (0), kullanıcının kaydı güncelleştirmek için gerekenden daha büyük.

## <a name="inspect-your-code-in-the-debugger"></a>Hata ayıklayıcı kodunuzda inceleyin

Tamam, her şeyi kritik örnek uygulaması ile yanlış düzelttik, diğer önemli şeyler taşıyın!

Biz Hata Ayıklayıcı'nın özel durum Yardımcısı gösterilmiştir, ancak hata ayıklayıcı değişkenlerini inceleyin ve kodunuzu Adımlama gibi diğer işlemler de imkan tanıyan çok daha güçlü bir araçtır. Daha güçlü yeteneklere birçok senaryoda özellikle aşağıdakiler için yararlıdır:

* Bir çalışma zamanı hata kodunuza yalıtmak çalışıyorsunuz, ancak henüz yöntemlerini ve daha önce açıklanan araçları kullanarak yapmak yüklenemiyor.

* İstediğiniz olan diğer bir deyişle, kodunuzu doğrulamak için beklediğiniz şekilde davrandığından ve ne için istediğiniz yapılması emin olmak için çalışırken izleyin.

    Kodunuz çalışırken izleyin yönergeli. Bunlar herhangi bir belirgin Belirtiler bildirim önce hataları genellikle tanımlayabilir ve bu şekilde kodunuz hakkında daha fazla bilgi edinebilirsiniz.

Hata ayıklayıcının temel özelliklerini nasıl kullanacağınızı öğrenmek için bkz. [mutlak yeni başlayanlar Için hata ayıklama](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Performans sorunlarını çözün

Başka bir tür hataları, uygulamanızın yavaş çalışmasına veya çok fazla bellek kullanmasına neden olan verimsiz kodu içerir. Genellikle, performansı en iyi duruma getirme uygulama geliştirmede daha sonra bunu bir şeydir. Ancak, performans sorunlarını erkenden çalıştırabilirsiniz (örneğin, uygulamanızın bir kısmını yavaş çalışıp çalışmadığını), ve uygulamanızı profil oluşturma Araçlar ile erkenden test gerekebilir. CPU kullanımı aracı ve bellek Çözümleyicisi gibi profil oluşturma araçları hakkında daha fazla bilgi için bkz. [profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, kodunuzda birçok yaygın hataları önlemek ve nasıl ve ne zaman hata ayıklayıcının kullanılacağını öğrendiniz. Ardından, hataları düzeltmek için Visual Studio hata ayıklayıcısını kullanma hakkında daha fazla bilgi edinin.

> [!div class="nextstepaction"]
> [Mutlak yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)
