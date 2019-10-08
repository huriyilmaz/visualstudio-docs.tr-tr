---
title: Hata ayıklama teknikleri ve araçları
description: Özel durumları onarmak, hataları onarmak ve kodunuzu geliştirmek için Visual Studio 'Yu kullanarak daha az hata ile daha iyi kod yazın
ms.custom:
- debug-experiment
- seodec18
ms.date: 01/24/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1fe0a9bb1e966bd1451bb5d816eaab814071fb5
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000169"
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

1. Visual Studio 'Yu açın ve **dosya** > **Yeni** > **Proje**' yi seçin. Altında **Visual C#** , seçin **Windows Masaüstü** veya **.NET Core**seçip Ortadaki bölmeden bir **konsol uygulaması**.

    > [!NOTE]
    > Görmüyorsanız **konsol uygulaması** proje şablonu, tıklayın **açık Visual Studio yükleyicisi** sol bölmesinde bağlantıyı **yeni proje** iletişim kutusu. Visual Studio Yükleyicisi'ni başlatır. Seçin **.NET masaüstü geliştirme** veya **.NET Core çoklu platform geliştirme** iş yükü, ardından **Değiştir**.

2. **Ad** alanına **Console_Parse_JSON** yazın ve **Tamam**' a tıklayın. Visual Studio projesi oluşturur.

3. Projenin *program.cs* dosyasındaki varsayılan kodu aşağıdaki örnek kodla değiştirin.

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

Örnek uygulamayı başlatın ve hata ayıklayıcıyı çalıştırmak denemeden önce kırmızı ve yeşil dalgalı çizgiler için Kod Düzenleyicisi'nde kodunu kontrol edin. Bu, hataları ve Uyarıları IDE'nin kod Çözümleyicisi tarafından tanımlanan temsil eder. Derleme zamanı hataları, kırmızı dalgalı çizgiler olan, önce düzeltmeniz gerekiyor kodu çalıştırabilirsiniz. Yeşil dalgalı çizgiler uyarıları var. Uyarıları düzeltmeden uygulamanızı genellikle çalıştırabilirsiniz, ancak hatalar, kaynak olabilirler ve, genellikle kendiniz zaman ve sorun araştırma olarak kaydedin. Bu uyarılar ve hatalar da gösterilmesi **hata listesi** bir liste görünümü isterseniz penceresi.

Örnek uygulamada, düzeltmeniz gereken birkaç kırmızı dalgalı çizgiler ve şu konuları inceleyeceğiz bir yeşil bir bakın. İlk hata aşağıda verilmiştir.

![Bir kırmızı dalgalı çizgi gösterme hatası](../debugger/media/write-better-code-red-squiggle.png)

Bu hatayı düzeltmek için başka bir özelliği ampul simgesini tarafından temsil edilen IDE'nin yaratacağını göreceğiz.

## <a name="check-the-light-bulb"></a>Ampul kontrol edin!

İlk kırmızı dalgalı bir derleme zamanı hatası temsil eder. Üzerine gelin ve ileti gördüğünüz ```The name `Encoding` does not exist in the current context```.

Bu hata sol alt köşesinde bir ampul simgesini gösterdiğine dikkat edin. Tornavida simgesi birlikte ![tornavida simgesi](../ide/media/screwdriver-icon.png), ampul ![ampul](../ide/media/light-bulb-icon.png) temsil yardımcı olabilecek hızlı Eylemler düzeltin veya yeniden düzenleyin, satır içi kod. Ampul temsil sorunları *gereken* düzeltin. Tornavida düzeltmek için tercih edebileceğiniz sorunlarda veririz. Tıklayarak bu hatayı gidermek için ilk önerilen düzeltmeyi kullanın **System.Text kullanarak** soldaki.

![Kodu düzeltmek için ampul kullanın](../debugger/media/write-better-code-missing-include.png)

Bu öğe tıkladığınızda, Visual Studio ekler `using System.Text` en üstündeki deyimi *Program.cs* dosya ve kırmızı dalgalı çizgi kaybolur. (Önerilen düzeltme ne yapacağını emin değilseniz, seçin **değişiklik önizlemesi** düzeltmeyi uygulamadan önce sağdaki bağlantıyı.)

Önceki hatayı genellikle yeni bir ekleyerek düzeltmek ortak bir adrestir `using` kodunuzda deyimi. Bu tür yaygın, benzer hatalar vardır ```The type or namespace `Name` cannot be found.``` bu tür hatalar eksik bir derleme başvurusunu gösterebilir (projeye sağ tıklayın,  > **başvuru** **Ekle**), yanlış yazılmış bir ad veya ihtiyacınız olan bir kitaplık eklemek (için C#, projeye sağ tıklayıp **NuGet Paketlerini Yönet**' i seçin).

## <a name="fix-the-remaining-errors-and-warnings"></a>Kalan hataları ve uyarıları çözme

Bu kodda bakmak için birkaç daha fazla dalgalı çizgiler vardır. Burada, bir ortak tür dönüştürme hatası görürsünüz. Dalgalı çizgi geldiğinizde, kodun bir dize dönüştürme yapmak için açık kod eklemediğiniz sürece, desteklenmeyen bir int'e dönüştürme çalıştığını görürsünüz.

![Tür dönüştürme hatası](../debugger/media/write-better-code-conversion-error.png)

Kod Çözümleyicisi amacınızı olamaz çünkü bu zaman aşımına yardımcı olmak için hiçbir ampuller vardır. Bu hatayı düzeltmek için kodun amacı bilmeniz gerekir. Bu örnekte, bu, görmek sabit değil `points` eklemeye çalıştığınız bu yana bir (tamsayı) sayısal değer olmalıdır `points` için `totalpoints`.

Bu hatayı düzeltmek için değiştirme `points` üyesi `User` bu sınıfı:

```csharp
[DataMember]
internal string points;
```

Şu şekilde:

```csharp
[DataMember]
internal int points;
```

Kod düzenleyicisinde kırmızı dalgalı çizgiler kaybolur.

Sonra, `points` veri üyesinin bildiriminde yeşil dalgalı çizgi üzerine gelin. Kod Çözümleyicisi değişkeni hiçbir zaman bir değer atanır söyler.

![Atanmamış değişken için uyarı iletisi](../debugger/media/write-better-code-warning-message.png)

Genellikle, bu düzeltilmesi gereken bir sorunu temsil eder. Ancak, örnek uygulamada, aslında veri depoladığını `points` seri durumdan çıkarma işlemi ve ardından bu değere ekleme sırasında değişken `totalpoints` veri üyesi. Bu örnekte, kodun amacı bildiğiniz ve uyarıyı yok sayabilirsiniz. Ancak, uyarıyı ortadan kaldırmak istiyorsanız, aşağıdaki kodu değiştirin:

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

Tuşuna **F5** (**hata ayıklama > hata ayıklamayı Başlat**) veya **hata ayıklamayı Başlat** düğmesi ![hata ayıklamayı Başlat](../debugger/media/dbg-tour-start-debugging.png "hata ayıklamayı Başlat ") hata ayıklama araç çubuğu.

Bu noktada, örnek uygulamayı oluşturur bir `SerializationException` özel durum (çalışma zamanı hatası). Diğer bir deyişle, uygulama seri hale getirilmeye çalışıldığında veri sıkıştıracak. Uygulamayı (hata ayıklayıcısı ekli) hata ayıklama modunda başlatıldığından, hata ayıklayıcı'nın özel durum Yardımcısı, özel durum oluşturdu ve yararlı bir hata mesajıyla sağ koduna götürür.

![Bir SerializationException gerçekleşir](../debugger/media/write-better-code-serialization-exception.png)

Hata iletisi yönlendiren, değer `4o` tamsayı olarak ayrıştırılamıyor. Bu nedenle, bu örnekte, veriler bozuk bildiğiniz: `4o` olmalıdır `40`. Ancak, gerçek bir senaryo (örneğin, gün geçtikçe, bir web hizmetinden) verilerin denetiminde olup olmadığını, ne yaparsınız hakkında? Nasıl bu sorunu?

Bir özel durum ulaştığınızda birkaç soru sormak (ve yanıtlamak) gerekir:

* Bu özel durumu düzeltmek bir hata mı? veya,

* Bu durum, kullanıcılarınızın karşılaşabileceği bir şey mi?

Eski ise, hata düzeltildi. (Örnek uygulamada, bozuk veri düzeltme anlamına gelir.) Bu ikinci ise, `try/catch` bloğu kullanarak kodunuzda özel durumu işlemeniz gerekebilir (bir sonraki bölümde olası diğer stratejileri inceleyeceğiz). Örnek uygulamada, aşağıdaki kodu değiştirin:

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

A `try/catch` bloğu için denetlemeniz gereken yöntemini gösterir. Bu bazı performans maliyetine, yalnızca gerçekten, diğer bir deyişle, ihtiyacınız olduğunda bunları burada (a), uygulamanın yayın sürümünde oluşabilir kullanmak isteyeceksiniz ve burada, (b) belgelere var özel durum (belgeler tamamlandı olduğunu varsayarak!). Çoğu durumda, kullanıcının hiçbir zaman bunu bilmek gerekir ve bir özel durum uygun şekilde işleyebilir.

Birkaç özel durum işleme için önemli ipuçları şunlardır:

* Boş bir catch bloğu, gibi kullanmaktan kaçının `catch (Exception) {}`, kullanıma veya bir hatayı işlemek için uygun eylemi almaz. Bir boş veya bilgilendirici olmayan yakalama bloğu özel durumları gizleyebilirsiniz ve kodunuzu yerine kolay bir şekilde hata ayıklamak daha zor hale getirebilir.

* Kullanım `try/catch` bloğu özel durum oluşturan belirli işlevin içine (`ReadObject`, örnek uygulamada). Kod daha büyük öbek geçici bir çözüm kullanıyorsanız hatanın konumunu gizleme yukarı bitmelidir. Örneğin, kullanmayın `try/catch` bloğu içine üst işlevi çağrısı `ReadToObject`, burada gösterilen veya tam olarak özel durumun gerçekleştiği bilemezsiniz.

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

Örnek uygulama için düzeltme `SerializationException` içinde `GetJsonData` değiştirerek yöntemi `4o` için `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Assert kullanarak, kodun amacı açıklamak

Tıklayın **yeniden** ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "RestartApp") hata ayıklama araç çubuğu düğmesini (**Ctrl** + **kaydırma**   +  **F5**). Bu, daha az adımları uygulamayı yeniden başlatır. Konsol penceresinde aşağıdaki çıktıyı görürsünüz.

![Çıkış değeri null](../debugger/media/write-better-code-using-assert-null-output.png)

Oldukça doğru değil Bu çıktıyı bir şey görebilirsiniz. **adı** ve **lastname** üçüncü için kayıt boş!

Bu, kullanılacak olan çoğu zaman yeterince, bir yardımcı kodlama yöntem hakkında konuşmak için iyi bir zamandır `assert` işlevlerinizi deyimlerinde. Aşağıdaki kodu ekleyerek emin olmak için bir çalışma zamanı denetimi içeren `firstname` ve `lastname` değil `null`. Aşağıdaki kodda değiştirin `UpdateRecords` yöntemi:

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

Ekleyerek `assert` geliştirme işlemi sırasında işlevlere deyimleri şöyle yardımcı olabilirsiniz, kodun amacı belirtin. Önceki örnekte, biz aşağıdakileri belirtin:

* Geçerli bir dize için ad gereklidir
* Geçerli bir dize için Soyadı gereklidir

Bu şekilde hedefi belirterek, gereksinimlerinizi uygular. Bu, geliştirme sırasında yüzey hataları için kullanabileceğiniz basit ve kullanışlı bir yöntemdir. (`assert` deyimleri birim testleri ana öğesi olarak da kullanılır.)

Tıklayın **yeniden** ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "RestartApp") hata ayıklama araç çubuğu düğmesini (**Ctrl** + **kaydırma**   +  **F5**).

> [!NOTE]
> `assert` Kod yalnızca hata ayıklama derlemesinde etkin olduğu.

Yeniden başlattığınızda, hata ayıklayıcı üzerinde duraklatır `assert` deyimi, çünkü ifade `users[i].firstname != null` değerlendiren `false` yerine `true`.

![Assert false çözümler](../debugger/media/write-better-code-using-assert.png)

`assert` Hata bildirir araştırmanız gereken bir sorun yoktur. `assert` bir özel durum burada mutlaka görmüyor birçok senaryolarını kapsayan. Bu örnekte, bir özel durum kullanıcı görmez ve `null` katma değer olarak `firstname` kayıtların listenizde. (Konsol çıkışında gördüğünüz gibi) bu sorunlara daha sonra neden olabilir ve hata ayıklamak için daha zor olabilir.

> [!NOTE]
> Çağırdığınız bir yöntem üzerinde senaryolarda `null` değeri bir `NullReferenceException` sonuçları. Normalde kullanmaktan kaçınmak istediğiniz bir `try/catch` genel bir özel durum için diğer bir deyişle, belirli bir kitaplığı işleve bağlı olmayan bir özel durum engelleyin. Herhangi bir nesne oluşturabilecek bir `NullReferenceException`. Emin değilseniz kitaplığı işlevine yönelik belgelere bakın.

Hata ayıklama işlemi sırasında belirli bir tutmak iyi `assert` bildiğiniz bir gerçek kod düzeltmesi ile değiştirmek için gereksinim duyduğunuz kadar deyimi. Kullanıcının uygulamanın derleme bir özel durum karşılaşabilirsiniz karar varsayalım. Bu durumda, uygulamanız önemli bir durum değil veya diğer bazı hataya neden emin olmak için kodu yeniden düzenleme gerekir. Bu nedenle, bu kodu düzeltmek için aşağıdaki kodu değiştirin:

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

Bu kodu kullanarak kod gereksinimlerinizi karşılamak ve emin bir kayıtla bir `firstname` veya `lastname` değerini `null` veri eklenmez.

Bu örnekte, eklediğimiz iki `assert` deyimleri bir döngü içinde. Genellikle, kullanırken `assert`, eklemek en iyi `assert` deyimini bir işlev veya metot giriş noktası (Başlangıç). Şu anda Baktığınız `UpdateRecords` örnek uygulamada yöntemi. Bu yöntemde, yöntem bağımsız olması durumunda sorun misiniz bildiğiniz `null`, böylece bunları hem denetleyin bir `assert` işlevin Giriş noktasında deyimi.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Mevcut verileri yükleme amacınızla önceki deyimleri için olan (`db`) ve yeni veri alma (`users`) herhangi bir şey güncelleştirmeden önce.

Kullanabileceğiniz `assert` herhangi bir türden çözümler ifade ile `true` veya `false`. Bu nedenle, örneğin, ekleyebilirsiniz bir `assert` şöyle deyimi.

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

Hata Ayıklayıcı'nın temel özelliklerinin nasıl kullanılacağını öğrenmek için bkz: [yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Performans sorunlarını çözün

Başka bir tür hataları, uygulamanızın yavaş çalışmasına veya çok fazla bellek kullanmasına neden olan verimsiz kodu içerir. Genellikle, performansı en iyi duruma getirme uygulama geliştirmede daha sonra bunu bir şeydir. Ancak, performans sorunlarını erkenden çalıştırabilirsiniz (örneğin, uygulamanızın bir kısmını yavaş çalışıp çalışmadığını), ve uygulamanızı profil oluşturma Araçlar ile erkenden test gerekebilir. Profil oluşturma araçlarında CPU kullanımı aracı ve bellek Çözümleyicisi gibi hakkında daha fazla bilgi için bkz. [ilk profil oluşturma araçları bakış](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, kodunuzda birçok yaygın hataları önlemek ve nasıl ve ne zaman hata ayıklayıcının kullanılacağını öğrendiniz. Ardından, hataları düzeltmek için Visual Studio hata ayıklayıcısını kullanma hakkında daha fazla bilgi edinin.

> [!div class="nextstepaction"]
> [Yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)
