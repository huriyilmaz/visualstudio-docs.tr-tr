---
title: 'Öğretici: Azure İşlevleri'
description: Mac için Visual Studio'da Azure işlevlerini kullanma.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 1a3c4f3283ab10cfc4f8ee8364113dcb7f075af8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75398169"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Öğretici: Azure İşlevlerini başlatma

Bu laboratuvarda, Mac için Visual Studio'u kullanarak Azure İşlevlerini oluşturmaya nasıl başlayacağınızı öğreneceksiniz. Ayrıca, Azure İşlevleri geliştiricileri tarafından kullanılabilen birçok bağlama ve tetikleyici türünden birini temsil eden Azure depolama tablolarıyla da tümleşirsiniz.

## <a name="objectives"></a>Amaçlar

> [!div class="checklist"]
> * Yerel Azure Fonksiyonları oluşturma ve hata ayıklama
> * Web ve Azure depolama kaynaklarıyla tümleştirme
> * Birden çok Azure İşi içeren bir iş akışı düzenleme

## <a name="requirements"></a>Gereksinimler

- Mac 7.5 veya üzeri için Visual Studio.
- Azure aboneliği (ücretsiz). [https://azure.com/free](https://azure.com/free?ref=visualstudio)

## <a name="exercise-1-creating-an-azure-functions-project"></a>Alıştırma 1: Azure İşlevleri projesi oluşturma

1. **Mac için Visual Studio**başlatın.

2. **Yeni Çözüm > Dosya'yı**seçin.

3. Bulut **> Genel** kategorisinden **Azure İşlevler** şablonu'nu seçin. Azure İşlevlerini barındıran bir .NET sınıf kitaplığı oluşturmak için C# kullanırsınız. **İleri**'ye tıklayın.

    ![azure fonksiyonları şablon seçimi](media/azure-functions-lab-image1.png)

4. Proje **Adını** **"AzureFunctionsLab"** olarak ayarlayın ve **Oluştur'u**tıklatın.

    ![azure işlev projenizi adlandırma ve oluşturma](media/azure-functions-lab-image2.png)

5. **Çözüm Pad'deki**düğümleri genişletin. Varsayılan proje şablonu, Çeşitli Azure Web İşler paketlerinin yanı sıra Newtonsoft.Json paketine yapılan NuGet başvurularını içerir.

     Ayrıca üç dosya vardır: - host için genel yapılandırma seçeneklerini açıklamak için **host.json** - hizmet ayarlarını yapılandırmak için **local.settings.json.**
        - Proje şablonu da varsayılan bir HttpTrigger oluşturur. Bu laboratuvarın iyiliği için, **projeden HttpTrigger.cs** dosyayı silmelisiniz.

    **Yerel.settings.json'u**aç. İki boş bağlantı dizesi ayarı olması varsayılan olarak.

    ![local.settings.json dosyagörüntüleme çözüm defteri](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Alıştırma 2: Azure depolama hesabı oluşturma

1. Azure hesabınızda 'da [https://portal.azure.com](https://portal.azure.com)oturum açın.

1. Ekranın solunda bulunan **Sık Kullanılanlar** bölümünde, **Depolama Hesapları'nı**seçin:

    ![depolama hesapları öğesini gösteren Azure portalının sık kullanılanlar bölümü](media/azure-functions-lab-image4.png)

1. Yeni bir depolama hesabı oluşturmak için **Ekle'yi** seçin:

    ![Yeni depolama hesabı eklemek için düğme](media/azure-functions-lab-image5.png)

1. **Ad** için genel olarak benzersiz bir ad girin ve **Kaynak grubu**için yeniden kullanın. Diğer tüm öğeleri varsayılan olarak tutabilirsiniz.

    ![yeni depolama hesabı ayrıntıları](media/azure-functions-lab-image6.png)

1. **Oluştur'u**tıklatın. Depolama hesabının oluşturulması birkaç dakika sürebilir. Başarıyla oluşturulduktan sonra bir bildirim alırsınız.

    ![Dağıtım başarılı bildirim](media/azure-functions-lab-image7.png)

1. Bildirimden **kaynağa Git** düğmesini seçin.

1. Erişim **tuşları** sekmesini seçin.

    ![erişim anahtarı ayarı](media/azure-functions-lab-image8.png)

1. İlk **Bağlantı Dizesini**kopyalayın. Bu dize, Azure depolama alanını daha sonra Azure İşlevlerinizile tümleştirmek için kullanılır.

    ![anahtar 1 için bilgi](media/azure-functions-lab-image9.png)

1. Mac **için Visual Studio'ya** dönün ve tam bağlantı dizesini **local.settings.json'da** **AzureWebJobsStorage** ayarı olarak yapıştırın. Artık, kaynaklarına erişması gereken işlevler için özniteliklerdeki ayarın adını başvurursunuz.

    ![bağlantı anahtarı girilen yerel ayarlar dosyası](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Örnek 3: Azure İşlevi oluşturma ve hata ayıklama

1. Artık bazı kodeklemeye başlamaya hazırsınız. .NET sınıf kitaplığıyla çalışırken, Azure İşlevleri statik yöntemler olarak eklenir. **Solution Pad'den**Azure **Functions** proje düğümüne sağ tıklayın ve Ekle **> İşlev Ekle'yi**seçin:

    ![Fonksiyon seçeneği ekle](media/azure-functions-lab-image11.png)

1. Yeni Azure İşlevler iletişim kutusunda Genel webhook şablonu'nu seçin. **Adınızı** **Ekle'ye** ayarlayın ve işlevinizi oluşturmak için **Tamam'ı** tıklatın:

    ![Yeni azure işlevleri iletişim kutusu](media/azure-functions-lab-image12.png)

1. Yeni dosyanın üst kısmında, **aşağıdaki yönergeleri kullanarak** ekleyin:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Varolan `Run` yöntemi kaldırın ve aşağıdaki yöntemi Azure İşleviniz olarak sınıfa ekleyin:

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

1. Yöntem tanımını parça parça yürüyelim.

    Göreceğiniz ilk şey, bu yöntemi Azure İşlevi olarak işaretleyen **FunctionName** özniteliğidir. Öznitelik, işlevin genel adını belirtir. Öznitelik adının gerçek yöntem adıyla eşleşmesi gerekmez.

    ![FunctionName özniteliği vurgulanmış yeni çalıştırma yöntemi](media/azure-functions-lab-image13.png)

1. Daha sonra, yöntem gerekli olan **ortak statik** yöntem olarak işaretlenir. Ayrıca, iade değerinin bir **int**olduğunu da fark edeceksiniz. Yöntem öznitelikleri kullanılarak aksi belirtilmedikçe, bir Azure İşlevinin geçersiz olmayan iade değeri istemciye metin olarak döndürülür. Varsayılan olarak **XML**olarak döndürülür, ancak daha sonra laboratuvarda yapacağınız **JSON**olarak değiştirilebilir.

    ![Yöntem başlatma vurgulanan yeni çalıştırma yöntemi](media/azure-functions-lab-image14.png)

1. İlk parametre, bu yöntemin bir HTTP isteği tarafından çağrıldığını gösteren **HttpTrigger** özniteliği ile işaretlenir. Öznitelik ayrıca yöntemin yetkilendirme düzeyini ve desteklediği fiilleri (bu durumda yalnızca **"GET" olarak)** belirtir. Ayrıca isteğe bağlı olarak yönteme giden yolu geçersiz kılan ve değişkenleri yoldan otomatik olarak ayıklamak için bir yol sunan bir **Rota** tanımlayabilirsiniz. **Rota** burada null olduğundan, bu yönteme giden yol varsayılan **olarak /api/Add**olacaktır.

    ![Parametre vurgulanmış yeni çalıştırma yöntemi](media/azure-functions-lab-image15.png)

1. Yöntemin son parametresi, tanılama ve hatalar için iletileri günlüğe kaydetmek için kullanılabilecek bir **TraceWriter'dır.**

    ![TraceWriter vurgulanan yeni çalıştırma yöntemi](media/azure-functions-lab-image16.png)

1. SatırKenar boşluğuna tıklayarak yöntemin **dönüş** satırında bir kesme noktası ayarlayın:

    ![Dönüş satırında kesme noktası kümesi](media/azure-functions-lab-image17.png)

1. **F5** tuşuna basarak veya Hata Ayıklama başlat'> çalıştır'ı seçerek projeyi hata ayıklama oturumunda oluşturun ve **çalıştırın.** Alternatif olarak **Çalıştır** düğmesini tıklatabilirsiniz. Bu seçeneklerin tümü aynı görevi gerçekleştirir. Bu laboratuvar referansları **F5**geri kalanı, ancak en rahat bulduğunuz yöntemi kullanabilirsiniz.

    ![Proje Oluştur ve Çalıştır](media/azure-functions-lab-image18.png)

1. Projeyi çalıştırmak Terminal uygulamasını otomatik olarak açar.

1. Proje, yöntem özniteliklerine ve bu makalede daha sonra kapsanan bir dosya kuralına dayalı olarak Azure İşlevlerini algılama sürecinden geçer. Bu durumda, tek bir Azure İşi algılar ve 1 iş işlevini "oluşturur".

    ![Terminalde Azure İşleviçıktısı](media/azure-functions-lab-image19.png)

1. Başlangıç iletilerinin alt kısmında, Azure İşlemeleri ana bilgisayar, herhangi bir HTTP tetikleyici API'nin URL'lerini yazdırır. Sadece bir tane olmalı. Bu URL'yi kopyalayın ve yeni bir tarayıcı sekmesine yapıştırın.

    ![Azure İşlevi API URL'si](media/azure-functions-lab-image20.png)

1. Kesme noktası hemen tetiklenmelidir. Web isteği işleve yönlendirildi ve şimdi debugged olabilir. Değerini görmek için **x** değişkeninin üzerinde fare.

    ![Kesme noktası tetiklendi](media/azure-functions-lab-image21.png)

1. Daha önce eklemek için kullanılan aynı yöntemi kullanarak kesme noktasını kaldırın (kenar boşluğuna tıklayın veya satırı seçin ve **F9**tuşuna basın).

1. Çalışmaya devam etmek için **F5** tuşuna basın.

1. Tarayıcıda, yöntemin XML sonucu işlenir. Beklendiği gibi, kodlanmış ekleme işlemi makul bir meblağ üretir. Safari'de yalnızca "3" görüyorsanız, **Safari > Tercihleri > İleri'ye** gidin ve **" Menü çubuğunda Geliştir menüsünü göster**" onay kutusunu işaretleyin ve sayfayı yeniden yükleyin.

1. **Mac için Visual Studio'da**hata ayıklama oturumunu sona erdirmek için **Durdur** düğmesini tıklatın. Yeni değişikliklerin alındığından emin olmak için hata ayıklama oturumunu yeniden başlatmayı (durdurmayı ve çalıştırmayı) unutmayın.

    ![Hata ayıklama yı durdurma seçeneği](media/azure-functions-lab-image22.png)

1. **Çalıştır** **yönteminde, x** ve **y** tanımlarını aşağıdaki kodla değiştirin. Bu kod, ek işlemin sağlanan parametrelere dayalı olarak dinamik olarak gerçekleştirilebilmeleri için URL'nin sorgu dizesinden değerleri ayıklar.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Uygulamayı çalıştırın.

1. Tarayıcı penceresine dönün ve dizeyi `/?x=2&y=3` URL'ye eklayın. Tüm URL şimdi `http://localhost:7071/api/Add?x=2&y=3`olmalıdır . Yeni URL'ye gidin.

1. Bu kez sonuç yeni parametreleri yansıtmalıdır. Projeyi farklı değerlerle çalıştırmakiçin çekinmeyin. Herhangi bir hata denetimi olmadığını, bu nedenle geçersiz veya eksik parametrelerin hata atacağını unutmayın.

1. Hata ayıklama oturumunu durdurun.

## <a name="exercise-4-working-with-functionjson"></a>Egzersiz 4: function.json ile çalışma

1. Daha önceki bir alıştırmada, Mac için Visual Studio'nun kitaplıkta tanımlanan Azure İşlevi için bir iş işlevini "oluşturduğu" belirtilmişti. Bunun nedeni, Azure İşlevlerinin çalışma zamanında yöntem özniteliklerini aslında kullanmaması, daha çok Azure Işlevlerinin nerede ve nasıl kullanılabilir hale getirildiğine yapılandırmak için derleme zamanı dosya sistemi kuralı kullanmasıdır. **Çözüm Defteri'nden**proje düğümünüze sağ tıklayın ve **Finder'da Göster'i**seçin.

     ![Finder menüsünde göster seçeneği](media/azure-functions-lab-image23.png)

1. **Dosya/Hata Ayıklama/netstandard2.0'a**ulaşana kadar dosya sisteminde aşağı doğru gidin. **Ekle**adlı bir klasör olmalıdır. Bu klasör, C# kodundaki işlev adı özniteliğiyle karşılık gelecek şekilde oluşturuldu. Tek bir **function.json** dosyasını ortaya çıkarmak için Ekle klasörünü genişletin. Bu dosya, çalışma zamanı tarafından Azure İşi'ni barındırmak ve yönetmek için kullanılır. Derleme zamanı desteği olmayan diğer dil modelleri için (C# script veya JavaScript gibi), bu klasörlerin el ile oluşturulması ve bakımı gerekir. C# geliştiricileri için, otomatik olarak yapı üzerine öznitelik meta verilerden oluşturulur. **Function.json'a** sağ tıklayın ve Visual Studio'da açmak için seçin.

    ![dosya dizininde function.json](media/azure-functions-lab-image24.png)

1. Bu öğreticinin önceki adımları göz önüne alındığında, C# öznitelikleri hakkında temel bir anlayışa sahip olmalısınız. Bunu göz önünde bulundurarak, bu JSON tanıdık görünmeli. Ancak, daha önceki alıştırmalarda yer almayan birkaç öğe vardır. Örneğin, her **bağlamanın** **bir yönü** olmalıdır. Çıkaracağınız gibi, **"in"** parametrenin giriş olduğu anlamına gelirken, **"out"** parametrenin bir dönüş değeri **($return**yoluyla) veya yönteme **giden** bir parametre olduğunu gösterir. Ayrıca **komut dosyasıDosya** (bu son konuma göre) ve **girişNokta** yöntemi (ortak ve statik) derleme içinde belirtmeniz gerekir. Sonraki birkaç adımda bu modeli kullanarak özel bir işlev yolu eklersiniz, bu nedenle bu dosyanın içeriğini panoya kopyalayın.

    ![function.json dosya mac için visual studio açık](media/azure-functions-lab-image25.png)

1. **Çözüm Defteri'nde** **AzureFunctionsLab** proje düğümüne sağ tıklayın ve **Yeni Klasör > ekle'yi**seçin. Yeni klasör **Adder'ı**adlandırın. Varsayılan kuralı olarak, bu klasörün adı **API/Adder**gibi API'ye giden yolu tanımlar.

    ![Yeni klasör seçeneği](media/azure-functions-lab-image26.png)

1. **Adder** klasörüne sağ tıklayın ve **Yeni Dosya > Ekle'yi**seçin.

    ![Yeni dosya seçeneği](media/azure-functions-lab-image27.png)

1. **Web** kategorisini ve **Boş JSON Dosyası** şablonu'nu seçin. **İşlev** için **function** Adı ayarlayın ve **Yeni'yi**tıklatın.

    ![Boş json dosya seçeneği](media/azure-functions-lab-image28.png)

1. Yeni oluşturulan dosyanın varsayılan içeriğini değiştirmek için diğer **işlev.json'un** (adım 3'ten) içeriğini yapıştırın.

1. Json dosyasının üst kısmından aşağıdaki satırları kaldırın:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. İlk bağlamanın sonunda **("ad": "req"** satırından sonra), aşağıdaki özellikleri ekleyin. Önceki satıra virgül eklemeyi unutmayın. Bu özellik, artık **int** parametrelerini yoldan ayıklayacak ve **bunları x** ve **y**olarak adlandırılan yöntem parametrelerine yerleştirecek şekilde varsayılan kökü geçersiz kılar.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. İlkinin altına başka bir bağlama ekleyin. Bu bağlama, işlevin geri dönüş değerini işler. Önceki satıra virgül eklemeyi unutmayın:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Ayrıca, aşağıda gösterildiği gibi **"Add2"** adlı bir yöntem kullanmak için dosyanın altındaki **entryPoint** özelliğini güncelleştirin. Bu yol **api / Adder ...** herhangi bir ad **(Add2** burada) ile uygun bir yöntem için eşolabilir göstermek tir.

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Son **işlev.json** dosyanız aşağıdaki json gibi görünmelidir:

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

1. Tüm bu iş yapmak için gerekli son bir adım, Mac için Visual Studio bu dosyayı her değiştiğinde çıkış dizininde aynı göreli yola kopyalamak için talimat vermektir. Dosya seçilirken, sağ çubuğundan özellikler sekmesini seçin ve daha **yeniyse**Kopya'yı seçseçeneğini **çıktıdizini için** Kopyala'yı seçin:

    ![json dosyası için özellikler seçenekleri](media/azure-functions-lab-image30.png)

1. **Add.cs,** beklenen `Run` işlevi yerine getirmek için yöntemi (öznitelik dahil) aşağıdaki yöntemle değiştirin. Hiçbir öznitelik kullanmaması ve `Run` **x** ve **y**için açık parametreleri olması dışında, çok benzer.

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

1. Projeyi oluşturmak ve çalıştırmak için **F5** tuşuna basın.

1. Yapı tamamlanır ve platform döndükçe, yeni eklenen yöntemle eşleyen istekler için ikinci bir rota olduğunu gösterir:

    ![Http işlevleri için URL](media/azure-functions-lab-image31.png)

1. Tarayıcı penceresini döndürün ve ''ye **http://localhost:7071/api/Adder/3/5**gidin.

1. Bu kez yöntem bir kez daha çalışır, yoldan parametreleri çekerek ve bir toplam üreten.

1. Mac **için Visual Studio'ya** dönün ve hata ayıklama oturumunu sonla.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Egzersiz 5: Azure depolama tablolarıyla çalışma

Genellikle, oluşturduğunuz hizmet şimdiye kadar oluşturduğumuz hizmetten çok daha karmaşık olabilir ve yürütülmesi için önemli miktarda zaman ve/veya altyapı gerektirebilir. Bu durumda, kaynaklar kullanılabilir olduğunda işlenmek üzere sıraya giren ve Azure İşlevlerinin destek sağladığı istekleri kabul etmeyi etkili bulabilirsiniz. Diğer durumlarda, verileri merkezi olarak depolamak isteyebilirsiniz. Azure Depolama tabloları bunu hızlı bir şekilde yapmanıza izin sağlar.

1. Aşağıdaki sınıfı **Add.cs.** Ad alanının içine, ancak varolan sınıfın dışına gitmeli.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. **Ekle** sınıfı içinde, başka bir işlev tanıtmak için aşağıdaki kodu ekleyin. Bu bir HTTP yanıtı içermez şimdiye kadar benzersiz olduğunu unutmayın. Son satır, parametreleri ve toplamının yanı sıra, daha sonra **(PartitionKey** ve **RowKey)** alınmasını kolaylaştıracak bazı önemli bilgilerle dolu yeni bir **TableRow** döndürür. Yöntem içindeki kod, işlevin ne zaman çalıştığını bilmeyi kolaylaştırmak için **TraceWriter'ı** da kullanır.

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

1. Projeyi oluşturmak ve çalıştırmak için **F5** tuşuna basın.

1. Tarayıcı sekmesinde, 'ye **http://localhost:7071/api/Process/4/6**gidin. Bu, sıraya başka bir ileti koyar ve sonunda tabloya başka bir satır eklenmesine neden olur.

1. **Terminale** dönün ve 4 + **6**için gelen isteği izleyin.

    ![Ek isteğini gösteren terminal çıktısı](media/azure-functions-lab-image32.png)

1. İsteği aynı URL'de yenilemek için tarayıcıya dönün. Bu kez **İşlem** yönteminden sonra bir hata görürsünüz. Bunun nedeni, kodun zaten var olan bir bölüm ve satır tuşu birleşimini kullanarak Azure Tablo Depolama tablosuna bir satır eklemeye çalışmasıdır.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Hata ayıklama oturumunu sonla.

1. Hatayı azaltmak için **TraceWriter** parametresinden hemen önce yöntem tanımına aşağıdaki parametreyi ekleyin. Bu parametre, Azure İşlevler platformuna sonuçları depolamak için kullandığımız **PartitionKey'deki** **Sonuçlar** tablosundan bir **TableRow** almaya çalışmasını bildirir. Ancak, **rowkey** dinamik olarak aynı yöntem için diğer **x** ve **y** parametreleri dayalı oluşturulan olduğunu fark ettiğinizde bazı gerçek büyü devreye girer. Bu satır zaten varsa, yöntem geliştirici tarafından gerekli hiçbir ek çalışma ile başladığında **tableRow** olacaktır. Eğer satır yoksa, o zaman sadece null olacak. Bu tür bir verimlilik, geliştiricilerin altyapıya değil, önemli iş mantığına odaklanmalarını sağlar.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Aşağıdaki kodu yöntemin başına ekleyin. **TableRow** geçersiz değilse, o zaman zaten istenen işlem için sonuçları var ve hemen döndürebilirsiniz. Aksi takdirde, işlev eskisi gibi devam eder. Bu, verileri döndürmenin en sağlam yolu olmasa da, çok az kodla birden çok ölçeklenebilir katmanda inanılmaz derecede karmaşık işlemleri düzenleyebileceğiniz noktayı gösterir.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Projeyi oluşturmak ve çalıştırmak için **F5** tuşuna basın.

1. Tarayıcı sekmesinde, URL'yi **http://localhost:7071/api/Process/4/6**. Bu kaydın tablo satırı olduğundan, hemen ve hatasız dönmelidir. HTTP çıkışı olmadığından, çıkışı Terminal'de görebilirsiniz.

    ![Tablo satırını gösteren terminal çıktısı zaten var](media/azure-functions-lab-image33.png)

1. URL'yi henüz test edilmemiş bir kombinasyonu **http://localhost:7071/api/Process/5/7**yansıtacak şekilde güncelleştirin. Tablo satırının (beklendiği gibi) bulunamadını belirten Terminal'deki iletiyi not edin.

    ![Yeni süreci gösteren terminal çıktısı](media/azure-functions-lab-image34.png)

1. Mac **için Visual Studio'ya** dönün ve hata ayıklama oturumunu sonla.

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

Bu laboratuvarda, Mac için Visual Studio ile Azure İşlevlerini oluşturmaya nasıl başladığınızı öğrendiniz.
