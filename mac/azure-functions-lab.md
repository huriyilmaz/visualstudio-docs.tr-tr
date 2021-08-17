---
title: 'Öğretici: Azure İşlevleri'
description: Mac için Visual Studio 'de Azure işlevleriyle çalışmaya yönelik ayrıntılı bir yol.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/06/2020
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.topic: tutorial
ms.openlocfilehash: 2bb80c08b2d2fab16f3fd926d9a806898eeb68bbcd3b3632ffb3af478b34453c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121393891"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Öğretici: Azure Işlevleri 'ni kullanmaya başlama

bu laboratuvarda, Mac için Visual Studio kullanarak Azure işlevleri oluşturmaya nasıl başlayacağınızı öğreneceksiniz. Ayrıca, Azure Işlevleri geliştiricileri tarafından kullanılabilen çok sayıda bağlama ve tetikleyiciden birini temsil eden Azure depolama tabloları ile de tümleştirilebilir.

## <a name="objectives"></a>Hedefler

> [!div class="checklist"]
> * Yerel Azure Işlevleri oluştur ve hata ayıkla
> * Web ve Azure depolama kaynaklarıyla tümleştirin
> * Birden çok Azure Işlevi içeren bir iş akışını düzenleme

## <a name="requirements"></a>Gereksinimler

- Mac için Visual Studio 7,5 veya üzeri.
- Bir Azure aboneliği (öğesinden ücretsiz olarak kullanılabilir [https://azure.com/free](https://azure.com/free?ref=visualstudio) ).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Alıştırma 1: Azure Işlevleri projesi oluşturma

1. **Mac için Visual Studio** başlatın.

2. **Yeni çözüm > dosya**' yı seçin.

3. **Cloud > genel** kategorisinden **Azure işlevleri** şablonunu seçin. Azure Işlevleri 'ni barındıran bir .NET sınıf kitaplığı oluşturmak Için C# ' i kullanacaksınız. **İleri**’ye tıklayın.

    ![Azure işlevleri şablon seçimi](media/azure-functions-lab-image1.png)

4. **Project adını** **"AzureFunctionsLab"** olarak ayarlayın ve **oluştur**' a tıklayın.

    ![Azure işlev projenizi adlandırma ve oluşturma](media/azure-functions-lab-image2.png)

5. **Çözüm penceresindeki** düğümleri genişletin. varsayılan proje şablonu, çeşitli Azure webjobs paketlerine yönelik NuGet başvuruları ve ayrıca paketteki Newtonsoft.Jsiçerir.

     Ayrıca üç dosya vardır:-hizmet ayarlarını yapılandırmak için üzerinde ana bilgisayar **local.settings.js** genel yapılandırma seçeneklerini açıklamak için **üzerindehost.js** .
        -Proje şablonu, varsayılan bir HttpTrigger de oluşturur. Bu laboratuvarın sau için, **Httptrigger. cs** dosyasını projeden silmeniz gerekir.

    **Üzerindelocal.settings.js** açın. Varsayılan olarak iki boş bağlantı dizesi ayarı vardır.

    ![dosyada local.settings.jsgörüntüleyen çözüm penceresi](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Alıştırma 2: Azure depolama hesabı oluşturma

1. Konumundaki Azure hesabınızda oturum açın [https://portal.azure.com](https://portal.azure.com) .

1. ekranın solunda bulunan **sık kullanılanlar** bölümünün altında **Depolama hesapları**' nı seçin:

    ![depolama hesapları öğesini gösteren Azure portal sık kullanılanlar bölümü](media/azure-functions-lab-image4.png)

1. Yeni bir depolama hesabı oluşturmak için **Ekle** ' yi seçin:

    ![Yeni depolama hesabı ekleme düğmesi](media/azure-functions-lab-image5.png)

1. **Ad** için genel olarak benzersiz bir ad girin ve **kaynak grubu** için yeniden kullanın. Diğer tüm öğeleri varsayılan olarak tutabilirsiniz.

    ![Yeni depolama hesabı ayrıntıları](media/azure-functions-lab-image6.png)

1. **Oluştur**’a tıklayın. Depolama hesabının oluşturulması birkaç dakika sürebilir. Başarılı bir şekilde oluşturulduktan sonra bir bildirim alırsınız.

    ![Dağıtım başarılı bildirimi](media/azure-functions-lab-image7.png)

1. Bildirimden **Kaynağa Git** düğmesini seçin.

1. **Erişim tuşları** sekmesini seçin.

    ![erişim anahtarı ayarı](media/azure-functions-lab-image8.png)

1. İlk **bağlantı dizesini** kopyalayın. Bu dize, Azure depolama 'nın Azure Işlevlerinizi üzerinde daha sonra bütünleştirmek için kullanılır.

    ![anahtar 1 için bilgiler](media/azure-functions-lab-image9.png)

1. **Mac için Visual Studio** ' e dönün ve **local.settings.js**' de **AzureWebJobsStorage** ayarı olarak içindeki tam bağlantı dizesini yapıştırın. Artık, kaynaklarına erişmesi gereken işlevlere yönelik özniteliklerde ayar adına başvurabilirsiniz.

    ![bağlantı anahtarı girilen yerel ayarlar dosyası](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Örnek 3: bir Azure Işlevi oluşturma ve hata ayıklama

1. Artık kod eklemeye başlamaya hazırsınız. .NET sınıf kitaplığı ile çalışırken, Azure Işlevleri statik yöntemler olarak eklenir. **Çözüm penceresinde** **Azurefunctions** proje düğümüne sağ tıklayın ve **Ekle > Ekle işlevi**' ni seçin:

    ![İşlev seçeneği Ekle](media/azure-functions-lab-image11.png)

1. Yeni Azure Işlevleri iletişim kutusunda Genel Web kancası şablonunu seçin. **Eklenecek** **adı** ayarlayın ve Işlevinizi oluşturmak için **Tamam** ' a tıklayın:

    ![Yeni Azure işlevleri iletişim kutusu](media/azure-functions-lab-image12.png)

1. Yeni dosyanın en üstüne aşağıdaki **using** yönergelerini ekleyin:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Mevcut yöntemi kaldırın `Run` ve aşağıdaki yöntemi Azure işleviniz olarak sınıfına ekleyin:

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```

1. Şimdi de yönteme göre yöntem tanımı yürüeceğiz.

    Göreceğiniz ilk şey, bu yöntemi bir Azure Işlevi olarak işaretleyen **fonksiyonadı** özniteliğidir. Özniteliği, işlevin ortak adını belirler. Öznitelik adının gerçek yöntem adıyla eşleşmesi gerekmez.

    ![Fonksiyonadı özniteliği vurgulanmış şekilde yeni Run yöntemi](media/azure-functions-lab-image13.png)

1. Sonra, yöntemi **ortak statik** bir yöntem olarak işaretlenir ve bu gereklidir. Ayrıca, dönüş değerinin bir **int** olduğunu fark edeceksiniz. Aksi takdirde, yöntem özniteliklerini kullanarak belirtilmediği sürece, bir Azure Işlevinin void olmayan bir dönüş değeri istemciye metin olarak döndürülür. Varsayılan olarak, **XML** olarak döndürülür, ancak laboratuvarda daha sonra yapabileceğiniz **JSON** olarak değiştirilebilir.

    ![Yöntem başlatma vurgulanmış şekilde yeni Run yöntemi](media/azure-functions-lab-image14.png)

1. İlk parametre, bu yöntemin bir HTTP isteği tarafından çağrılmasını gösteren **Httptrigger** özniteliğiyle işaretlenir. Özniteliği Ayrıca yöntemin yetkilendirme düzeyini ve desteklediği fiilleri belirtir (Bu durumda yalnızca **"Get"** ). İsteğe bağlı olarak, yöntemin yolunu geçersiz kılan bir **yol** tanımlayabilir ve yoldan değişkenleri otomatik olarak ayıklamanın bir yolunu sunar. **Yol** burada null olduğundan, bu yöntemin yolu varsayılan olarak **/api/Add** olur.

    ![Parametresi vurgulanmış olarak yeni Run yöntemi](media/azure-functions-lab-image15.png)

1. Metodun son parametresi, tanılama ve hatalara yönelik iletileri günlüğe kaydetmek için kullanılabilecek bir **Tracewriter** .

    ![TraceWriter vurgulanmış olarak yeni Run yöntemi](media/azure-functions-lab-image16.png)

1. Satırın kenar boşluğuna tıklayarak yöntemin **dönüş** satırında bir kesme noktası ayarlayın:

    ![Dönüş satırında kesme noktası ayarlandı](media/azure-functions-lab-image17.png)

1. **F5** tuşuna basarak veya **hata ayıklamayı Başlat > Çalıştır**' a tıklayarak projeyi bir hata ayıklama oturumunda derleyin ve çalıştırın. Alternatif olarak, **Çalıştır** düğmesine tıklayabilirsiniz. Bu seçenekler aynı görevi gerçekleştirir. Bu laboratuvarın geri kalanında **F5**'e başvurmuş, ancak en rahat bulduğunuz yöntemi kullanabilirsiniz.

    ![Projeyi derleyin ve çalıştırın](media/azure-functions-lab-image18.png)

1. Projeyi çalıştırmak, Terminal uygulamasını otomatik olarak açar.

1. Proje, yöntem özniteliklerine ve bu makalenin ilerleyen kısımlarında ele alınan bir dosya kuralına dayalı olarak Azure Işlevleri algılama sürecindedir. Bu durumda, tek bir Azure Işlevi algılar ve "1 iş işlevi" oluşturur.

    ![Terminalde Azure Işlevinin çıkışı](media/azure-functions-lab-image19.png)

1. Başlangıç iletilerinin en altında, Azure Işlevleri ana bilgisayarı herhangi bir HTTP tetikleyici API 'Si URL 'sini yazdırır. Yalnızca bir tane olmalıdır. Bu URL 'YI kopyalayın ve yeni bir tarayıcı sekmesine yapıştırın.

    ![Azure Işlev API 'si URL 'si](media/azure-functions-lab-image20.png)

1. Kesme noktası hemen tetiklemelidir. Web isteği işleve yönlendirildi ve şimdi hata ayıklanabilir. Değerini görmek için **x** değişkeninin üzerinde fare.

    ![Kesme noktası tetiklendi](media/azure-functions-lab-image21.png)

1. Daha önce eklemek için kullanılan yöntemi kullanarak kesme noktasını kaldırın (kenar boşluğuna tıklayın veya satırı seçip **F9** tuşuna basın).

1. Çalışmaya devam etmek için **F5** tuşuna basın.

1. Tarayıcıda, yöntemin XML sonucu işlenir. Beklenildiği gibi, sabit kodlanmış toplama işlemi de bir üst sınırı üretir. Safari'de yalnızca "3" seçeneğini görüyorsanız **Safari > Tercihler > Gelişmiş'e** gidin ve " Menü çubuğundaKi Geliştirme menüsünü göster" onay kutusunu işaretleyin ve sayfayı yeniden yükleyin.

1. Hata **Mac için Visual Studio'** içinde **Durdur düğmesine** tıklayarak hata ayıklama oturumunu sona erer. Yeni değişikliklerin top olduğundan emin olmak için hata ayıklama oturumunu yeniden başlatmayı (durdurmayı ve sonra çalıştırmayı) unutmayın.

    ![Hata ayıklamayı durdur seçeneği](media/azure-functions-lab-image22.png)

1. Run **yönteminde** **x** ve **y tanımlarını** aşağıdaki kodla değiştirin. Bu kod, url'nin sorgu dizesinde yer alan değerleri ayıklar, böylece ekleme işlemi sağlanan parametrelere göre dinamik olarak gerçek olabilir.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Uygulamayı çalıştırın.

1. Tarayıcı penceresine geri dönüp dizeyi `/?x=2&y=3` URL'ye ekleyin. Url'nin tamamı artık `http://localhost:7071/api/Add?x=2&y=3` olmalıdır. Yeni URL'ye gidin.

1. Bu kez sonuç yeni parametreleri yansıtacak. Projeyi farklı değerlerle çalıştırmakta serbestsiniz. Herhangi bir hata denetimi olmadığını, dolayısıyla geçersiz veya eksik parametrelerin hataya neden olduğunu unutmayın.

1. Hata ayıklama oturumunu durdurun.

## <a name="exercise-4-working-with-functionjson"></a>Alıştırma 4: function.jsçalışma

1. Önceki bir alıştırmada, kitaplıkta tanımlanan Mac için Visual Studio Azure İşlevi için bir iş işlevinin "üreti" olduğu belirtildi. Bunun nedeni Azure İşlevleri çalışma zamanında yöntem özniteliklerini kullanmamış olması, bunun yerine derleme zamanı dosya sistemi kuralı kullanarak çalışma zamanının kullanılabilir olduğu yeri ve Azure İşlevleri yapılandırmadır. Çözüm Penceresinde **proje düğümünü** sağ tıklatın ve Bulıcı'da **Ortaya Çıkar'ı seçin.**

     ![Bulıcı menü seçeneğinde ortaya çıkar](media/azure-functions-lab-image23.png)

1. **bin/Debug/netstandard2.0'a ulaşana kadar dosya sisteminde aşağı gidin.** Ekle adlı bir klasör **olması gerekir.** Bu klasör, C# kodundaki işlev adı özniteliğine karşılık gelen şekilde oluşturulmuş. Dosyada tek bir dosyanın görünür olduğu klasörü **function.jsgenişletin.** Bu dosya, azure işlevini barındırmak ve yönetmek için çalışma zamanı tarafından kullanılır. Derleme zamanı desteği olmayan diğer dil modellerinde (C# betiği veya JavaScript gibi) bu klasörlerin el ile oluşturularak korunması gerekir. C# geliştiricileri için, derleme sırasında öznitelik meta verilerinden otomatik olarak oluşturulurlar. Aç'a **sağfunction.jstıklayın** ve seçerek bu seçeneği Visual Studio.

    ![function.jsdizininde](media/azure-functions-lab-image24.png)

1. Bu öğreticinin önceki adımlarını göz atarak, C# öznitelikleri hakkında temel bir anlayışa sahipsiniz. Bunu dikkate alarak bu JSON'un tanıdık olması gerekir. Ancak, önceki alıştırmalarda ele atılmlı birkaç öğe vardır. Örneğin, her **bağlamanın** kendi yön **kümesine sahip olması** gerekir. "in" parametresi, **parametrenin** giriş olduğu anlamına gelir ancak **"out",** parametrenin bir dönüş değeri **($return** aracılığıyla) veya yönteme yönelik bir out **parametresi** olduğunu gösterir. Ayrıca derleme içinde **scriptFile** (bu son konuma göre) ve **entryPoint** yöntemini (genel ve statik) belirtmeniz gerekir. Sonraki birkaç adımda bu modeli kullanarak özel bir işlev yolu ekliysiniz, bu nedenle bu dosyanın içeriğini panoya kopyalayın.

    ![function.jsmac için Visual Studio'da açık olan bir dosya üzerinde yükleme](media/azure-functions-lab-image25.png)

1. Çözüm Penceresinde **AzureFunctionsLab** proje düğümüne sağ tıklayın ve Yeni Klasöre **Ekle'> seçin.**  Yeni klasöre **Adder adını girin.** Varsayılan kural olarak, bu klasörün adı API'nin yolunu **(api/Adder gibi) tanımlar.**

    ![Yeni klasör seçeneği](media/azure-functions-lab-image26.png)

1. Adder klasörüne **sağ tıklayın ve** Yeni Dosya **ekle'> seçin.**

    ![Yeni dosya seçeneği](media/azure-functions-lab-image27.png)

1. Web **kategorisini** ve Boş **JSON Dosyası şablonunu** seçin. **Ad'ı işlev** olarak **ayarlayın ve** Yeni'ye **tıklayın.**

    ![Boş json dosyası seçeneği](media/azure-functions-lab-image28.png)

1. Yeni oluşturulan dosyanın varsayılan **içeriğinifunction.js** için diğer dosyanın içeriğini (3. adımdan) üzerine yapıştırın.

1. Aşağıdaki satırları json dosyasının üst kısmından kaldırın:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. İlk bağlamanın sonuna **("name": "req" satırına)** aşağıdaki özellikleri ekleyin. Önceki satıra virgül dahil etme. Bu özellik, artık **int** parametrelerini yoldan ayıklar ve **bunları x** ve y adlı yöntem parametrelerine yer değiştirecek şekilde varsayılan kökünü geçersiz **kılar.**

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. İlkin altına başka bir bağlama ekleyin. Bu bağlama işlevin dönüş değerini işler. Önceki satıra virgül dahil etme:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Ayrıca dosyanın en altındaki **entryPoint** özelliğini aşağıda gösterildiği gibi **"Add2"** adlı bir yöntem kullanmak için güncelleştirin. Bu, **api/Adder...** yolunun herhangi bir adla (buraya Ekle2) uygun bir yönteme **eşleyene bir yol olduğunu göstermektir.**

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Dosyada **function.jsdosyanız** aşağıdaki json'a benzer şekilde görünüyor:

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Tüm bu çalışmaları yapmak için gereken son adım, Mac için Visual Studio her değişiklikte bu dosyayı çıkış dizininde aynı göreli yola kopyalamasını talimatını etmektir. Dosya seçiliyken sağ çubuktan özellikler sekmesini seçin ve  Çıkış dizinine kopyala için Daha yeniyse **kopyala'ya tıklayın:**

    ![JSON dosyası için özellikler seçenekleri](media/azure-functions-lab-image30.png)

1. **Add.cs içinde** beklenen işlevi yerine getirmek için yöntemini `Run` (özniteliği dahil) aşağıdaki yöntemle değiştirin. çok benzerdir, ancak hiçbir öznitelik kullanmaz ve `Run` x ve y için açık **parametrelere** **sahip olur.**

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```

1. Projeyi **derlemek ve** çalıştırmak için F5 tuşuna basın.

1. Derleme tamamlandıktan ve platform hazırlandıktan sonra yeni eklenen yönteme eşlenen istekler için ikinci bir yol olduğunu gösterir:

    ![Http işlevlerinin URL'si](media/azure-functions-lab-image31.png)

1. Tarayıcı penceresini iade edin ve 'a **http://localhost:7071/api/Adder/3/5** gidin.

1. Bu kez yöntem bir kez daha çalışır, yoldan parametreleri çekerek bir toplam sağlar.

1. Hata **Mac için Visual Studio** ve hata ayıklama oturumunu sona erer.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Alıştırma 5: Azure depolama tabloları ile çalışma

Genellikle, derlemek için şu ana kadar gerçekleştirilen hizmetten çok daha karmaşık olabilir ve yürütülecek önemli miktarda zaman ve/veya altyapıya ihtiyaç vardır. Bu durumda, kaynaklar kullanılabilir olduğunda iş için kuyruğa alınan istekleri kabul etme ve bu istekler için destek Azure İşlevleri bulabilirsiniz. Diğer durumlarda, verileri merkezi olarak depolamak istemeyebilirsiniz. Azure Depolama tabloları bunu hızlı bir şekilde yapmalarını sağlar.

1. Aşağıdaki sınıfı **Add.cs'ye ekleyin.** Ad alanının içine ancak var olan sınıfın dışına girilir.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. Add **sınıfına** başka bir işlev eklemek için aşağıdaki kodu ekleyin. Bunun şu ana kadar http yanıtı içermeyen benzersiz olduğunu unutmayın. Son satır, daha sonra (**PartitionKey** ve **RowKey**) daha sonra almayı kolaylaştıracak bazı önemli bilgilerle doldurulmuş yeni bir **TableRow** ile birlikte parametrelerini ve toplamını döndürür. yöntemi içindeki kod, işlev çalıştırılırken daha kolay bilgi için **TraceWriter** kullanır.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```

1. Projeyi **derlemek ve** çalıştırmak için F5 tuşuna basın.

1. Tarayıcı sekmesinde, 'a **http://localhost:7071/api/Process/4/6** gidin. Bu, kuyruğa başka bir ileti ekleniyor ve sonunda tabloya başka bir satır ekleniyor.

1. **Terminal'e geri** dönüp **4 + 6 için gelen isteği izleyin.**

    ![Toplama isteğini gösteren terminal çıkışı](media/azure-functions-lab-image32.png)

1. İsteği aynı URL'ye yenilemek için tarayıcıya geri dönebilirsiniz. Bu kez Process yönteminden sonra bir **hatayla karşılaştısınız.** Bunun nedeni, kodun zaten var olan bir bölüm ve satır Depolama kullanarak Azure Tablo tablosuna satır eklemeye denemesidir.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Hata ayıklama oturumunu sona erer.

1. Hatayı azaltmak için aşağıdaki parametreyi TraceWriter parametresinin hemen öncesinde yöntem **tanımına** ekleyin. Bu parametre, Azure İşlevleri platforma sonuçları depolamak için kullanmakta olduğu  **PartitionKey'te** Bulunan Sonuçlar tablosundan **TableRow** alma girişiminde bulunarak bunu denemesi talimatı verir. Ancak **RowKey'in** aynı yöntem için diğer **x** ve **y** parametrelerine göre dinamik olarak oluşturulduğuna dikkat edin. Bu satır zaten varsa, **yöntem geliştiricinin** fazladan çalışması gerektirerek başladığında tableRow bu satıra sahip olur. Satır yoksa yalnızca null olur. Bu verimlilik, geliştiricilerin altyapıya değil önemli iş mantığına odaklanmalarını sağlar.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Aşağıdaki kodu yönteminin başına ekleyin. **tableRow** null değilse, istenen işlem için zaten sonuçlarımız vardır ve bunu hemen döndürenin. Aksi takdirde işlev daha önce olduğu gibi devam eder. Verileri iade etmek için en güçlü yol bu değildir ancak çok az kodla birden çok ölçeklenebilir katmanda son derece karmaşık işlemleri düzenlemenizi sağlar.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Projeyi **derlemek ve** çalıştırmak için F5 tuşuna basın.

1. Tarayıcı sekmesindeki URL'yi **http://localhost:7071/api/Process/4/6** yenileyin. Bu kaydın tablo satırı mevcut olduğu için hemen ve hatasız olarak geri dönilmelidir. HTTP çıkışına sahip olmadığınız için çıkışı Terminal'de de görebilirsiniz.

    ![Tablo satırı zaten var olduğunu gösteren terminal çıkışı](media/azure-functions-lab-image33.png)

1. URL'yi gibi henüz test edilmemiş bir birleşimi yansıtacak şekilde **http://localhost:7071/api/Process/5/7** güncelleştirin. Terminal'de tablo satırı bulunamadı (beklendiği gibi) belirten iletiyi not alırsınız.

    ![Yeni işlemi gösteren terminal çıkışı](media/azure-functions-lab-image34.png)

1. Hata **Mac için Visual Studio** ve hata ayıklama oturumunu sona erer.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Özet

Bu laboratuvarda, Azure İşlevleri ile Mac için Visual Studio.
