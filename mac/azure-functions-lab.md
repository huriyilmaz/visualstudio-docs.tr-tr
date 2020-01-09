---
title: 'Öğretici: Azure Işlevleri'
description: Mac için Visual Studio 'de Azure işlevleri 'ni kullanma.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 1a3c4f3283ab10cfc4f8ee8364113dcb7f075af8
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75398169"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Öğretici: Azure Işlevleri 'ni kullanmaya başlama

Bu laboratuvarda, Mac için Visual Studio kullanarak Azure Işlevleri oluşturmaya nasıl başlayacağınızı öğreneceksiniz. Ayrıca, Azure Işlevleri geliştiricileri tarafından kullanılabilen çok sayıda bağlama ve tetikleyiciden birini temsil eden Azure depolama tabloları ile de tümleştirilebilir.

## <a name="objectives"></a>Amaçlar

> [!div class="checklist"]
> * Yerel Azure Işlevleri oluştur ve hata ayıkla
> * Web ve Azure depolama kaynaklarıyla tümleştirin
> * Birden çok Azure Işlevi içeren bir iş akışını düzenleme

## <a name="requirements"></a>Gereksinimler

- Mac için Visual Studio 7,5 veya üzeri.
- Bir Azure aboneliği ( [https://azure.com/free](https://azure.com/free?ref=visualstudio)ücretsiz olarak kullanılabilir).

## <a name="exercise-1-creating-an-azure-functions-project"></a>Alıştırma 1: Azure Işlevleri projesi oluşturma

1. **Mac için Visual Studio**başlatın.

2. **Yeni çözüm > dosya**' yı seçin.

3. **Cloud > genel** kategorisinden **Azure işlevleri** şablonunu seçin. Azure Işlevleri C# 'ni barındıran bir .NET sınıf kitaplığı oluşturmak için ' i kullanacaksınız. **İleri**'ye tıklayın.

    ![Azure işlevleri şablon seçimi](media/azure-functions-lab-image1.png)

4. **Proje adını** **"AzureFunctionsLab"** olarak ayarlayın ve **Oluştur**' a tıklayın.

    ![Azure işlev projenizi adlandırma ve oluşturma](media/azure-functions-lab-image2.png)

5. **Çözüm bölmesi**düğümleri genişletin. Varsayılan proje şablonu, çeşitli Azure WebJobs paketlerinin yanı sıra Newtonsoft. JSON paketine yönelik NuGet başvuruları içerir.

     Ayrıca üç dosya vardır:-Host **. JSON** , hizmet ayarlarını yapılandırmak için ana bilgisayar- **yerel. Settings. JSON** için genel yapılandırma seçeneklerini tanımlar.
        - Proje şablonu ayrıca bir varsayılan HttpTrigger oluşturur. Bu laboratuvarın sau için, **HttpTrigger.cs** dosyasını projeden silmelisiniz.

    **Local. Settings. JSON**öğesini açın. Varsayılan olarak iki boş bağlantı dizesi ayarı vardır.

    ![Yerel. Settings. json dosyasını görüntüleyen çözüm paneli](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Alıştırma 2: Azure depolama hesabı oluşturma

1. [https://portal.azure.com](https://portal.azure.com)adresinden Azure hesabınızda oturum açın.

1. Ekranın solunda bulunan **Sık Kullanılanlar** bölümünde **depolama hesapları**' nı seçin:

    ![depolama hesapları öğesini gösteren Azure portal sık kullanılanlar bölümü](media/azure-functions-lab-image4.png)

1. Yeni bir depolama hesabı oluşturmak için **Ekle** ' yi seçin:

    ![Yeni depolama hesabı ekleme düğmesi](media/azure-functions-lab-image5.png)

1. **Ad** için genel olarak benzersiz bir ad girin ve **kaynak grubu**için yeniden kullanın. Diğer tüm öğeleri varsayılan olarak tutabilirsiniz.

    ![Yeni depolama hesabı ayrıntıları](media/azure-functions-lab-image6.png)

1. **Oluştur**'u tıklatın. Depolama hesabının oluşturulması birkaç dakika sürebilir. Başarılı bir şekilde oluşturulduktan sonra bir bildirim alırsınız.

    ![Dağıtım başarılı bildirimi](media/azure-functions-lab-image7.png)

1. Bildirimden **Kaynağa Git** düğmesini seçin.

1. **Erişim tuşları** sekmesini seçin.

    ![erişim anahtarı ayarı](media/azure-functions-lab-image8.png)

1. İlk **bağlantı dizesini**kopyalayın. Bu dize, Azure depolama 'nın Azure Işlevlerinizi üzerinde daha sonra bütünleştirmek için kullanılır.

    ![anahtar 1 için bilgiler](media/azure-functions-lab-image9.png)

1. **Mac için Visual Studio** dön ve tam bağlantı dizesini **yerel. Settings. JSON**içinde **AzureWebJobsStorage** ayarı olarak içine yapıştırın. Artık, kaynaklarına erişmesi gereken işlevlere yönelik özniteliklerde ayar adına başvurabilirsiniz.

    ![bağlantı anahtarı girilen yerel ayarlar dosyası](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Örnek 3: bir Azure Işlevi oluşturma ve hata ayıklama

1. Artık kod eklemeye başlamaya hazırsınız. .NET sınıf kitaplığı ile çalışırken, Azure Işlevleri statik yöntemler olarak eklenir. **Çözüm bölmesi**, **Azurefunctions** proje düğümüne sağ tıklayın ve **Ekle > Ekle işlevi**' ni seçin:

    ![İşlev seçeneği Ekle](media/azure-functions-lab-image11.png)

1. Yeni Azure Işlevleri iletişim kutusunda Genel Web kancası şablonunu seçin. **Eklenecek** **adı** ayarlayın ve Işlevinizi oluşturmak için **Tamam** ' a tıklayın:

    ![Yeni Azure işlevleri iletişim kutusu](media/azure-functions-lab-image12.png)

1. Yeni dosyanın en üstüne aşağıdaki **using** yönergelerini ekleyin:

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. Mevcut `Run` yöntemini kaldırın ve aşağıdaki yöntemi Azure Işleviniz olarak sınıfına ekleyin:

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

1. Sonra, yöntemi **ortak statik** bir yöntem olarak işaretlenir ve bu gereklidir. Ayrıca, dönüş değerinin bir **int**olduğunu fark edeceksiniz. Aksi takdirde, yöntem özniteliklerini kullanarak belirtilmediği sürece, bir Azure Işlevinin void olmayan bir dönüş değeri istemciye metin olarak döndürülür. Varsayılan olarak, **XML**olarak döndürülür, ancak laboratuvarda daha sonra yapabileceğiniz **JSON**olarak değiştirilebilir.

    ![Yöntem başlatma vurgulanmış şekilde yeni Run yöntemi](media/azure-functions-lab-image14.png)

1. İlk parametre, bu yöntemin bir HTTP isteği tarafından çağrılmasını gösteren **Httptrigger** özniteliğiyle işaretlenir. Özniteliği Ayrıca yöntemin yetkilendirme düzeyini ve desteklediği fiilleri belirtir (Bu durumda yalnızca **"Get"** ). İsteğe bağlı olarak, yöntemin yolunu geçersiz kılan bir **yol** tanımlayabilir ve yoldan değişkenleri otomatik olarak ayıklamanın bir yolunu sunar. **Yol** burada null olduğundan, bu yöntemin yolu varsayılan olarak **/api/Add**olur.

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

1. Daha önce eklemek için kullanılan yöntemi kullanarak kesme noktasını kaldırın (kenar boşluğuna tıklayın veya satırı seçip **F9**tuşuna basın).

1. Çalışmaya devam etmek için **F5** tuşuna basın.

1. Tarayıcıda, yöntemin XML sonucu işlenir. Beklenildiği gibi, sabit kodlanmış toplama işlemi de bir üst sınırı üretir. Bkz. Safari 'de yalnızca "3" görüyorsanız, **safari > tercihleri** ' ne gidin > Gelişmiş ' e gidin ve "**menü çubuğunda geliştirme menüsünü göster**" onay kutusunu işaretleyin ve sayfayı yeniden yükleyin.

1. **Mac için Visual Studio**, hata ayıklama oturumunu sonlandırmak için **Durdur** düğmesine tıklayın. Yeni değişikliklerin tamamlandığından emin olmak için, hata ayıklama oturumunu yeniden başlatmayı (durdurmak ve çalıştırmak) unutmayın.

    ![Hata ayıklamayı Durdur seçeneği](media/azure-functions-lab-image22.png)

1. **Run** yönteminde **x** ve **y** tanımlarını aşağıdaki kodla değiştirin. Bu kod, ek işlemin belirtilen parametrelere göre dinamik olarak gerçekleştirilebilmesi için URL 'nin sorgu dizesinden değerleri ayıklar.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. Uygulamayı çalıştırın.

1. Tarayıcı penceresine dönün ve `/?x=2&y=3` dize URL 'sini ekleyin. URL 'nin tamamı artık `http://localhost:7071/api/Add?x=2&y=3`olmalıdır. Yeni URL 'ye gidin.

1. Bu kez, sonuç yeni parametreleri yansıtmalıdır. Projeyi farklı değerlerle çalıştırmayı ücretsiz olarak hissetmekten çekinmeyin. Hata denetimi olmadığını unutmayın, bu nedenle geçersiz veya eksik parametreler hata oluşturacak.

1. Hata ayıklama oturumunu durdurun.

## <a name="exercise-4-working-with-functionjson"></a>Alıştırma 4: Function. JSON ile çalışma

1. Önceki bir alıştırmada, kitaplıkta tanımlanan Azure Işlevi için "üretilmiş" bir iş işlevi Mac için Visual Studio bahsedildi. Bunun nedeni, Azure Işlevlerinin çalışma zamanında Yöntem özniteliklerini kullanmamaktır ancak bunun yerine, Azure Işlevlerinin nerede ve nasıl kullanılabilir hale getirilmekte olduğunu yapılandırmak için derleme zamanı dosya sistemi kuralını kullanır. **Çözüm bölmesi**, proje düğümünüz üzerinde sağ tıklayın ve **Finder 'da açığa çıkar**' ı seçin.

     ![Finder 'da açığa çıkar menü seçeneği](media/azure-functions-lab-image23.png)

1. **Bin/Debug/Netstandard 2.0**'a ulaşana kadar dosya sisteminde ilerleyin. **Add**adlı bir klasör olmalıdır. Bu klasör, C# koddaki işlev adı özniteliğiyle birlikte kullanılacak şekilde oluşturulmuştur. Tek bir **function. JSON** dosyasını açığa çıkarmak için Ekle klasörünü genişletin. Bu dosya, Azure Işlevini barındırmak ve yönetmek için çalışma zamanı tarafından kullanılır. Derleme zamanı desteği olmayan diğer dil modellerinde ( C# betik veya JavaScript gibi), bu klasörlerin el ile oluşturulması ve saklanması gerekir. Geliştiriciler C# için, derleme sırasında öznitelik meta verilerinden otomatik olarak oluşturulur. **Function. JSON** öğesine sağ tıklayın ve Visual Studio 'da açmak için seçin.

    ![dosya dizininde function. JSON](media/azure-functions-lab-image24.png)

1. Bu öğreticinin önceki adımları verildiğinde, C# özniteliklerin temel olarak anlaşılmalıdır. Bu şekilde hesaba katılarak, bu JSON tanıdık görünmelidir. Ancak, önceki alıştırmalarda kapsanmayan birkaç öğe vardır. Örneğin, her **bağlamanın** **Yön** kümesi olmalıdır. **"İçinde", "ın"** parametresi, parametrenin giriş olduğu anlamına gelir, yani **"Out"** parametresi, bir dönüş değeri ( **$Return**aracılığıyla) veya yönteme **giden** bir parametre olduğunu gösterir. Ayrıca, derleme içinde **scriptfile** (Bu son konuma göre) ve **entryPoint** yöntemi (public ve static) belirtmeniz gerekir. Sonraki birkaç adımda, bu modeli kullanarak özel bir işlev yolu ekleyeceksiniz, bu nedenle bu dosyanın içeriğini Pano 'ya kopyalayın.

    ![Mac için Visual Studio 'da işlev. JSON dosyası açık](media/azure-functions-lab-image25.png)

1. **Çözüm bölmesi**, **AzureFunctionsLab** proje düğümüne sağ tıklayın ve **> Yeni klasör ekle**' yi seçin. Yeni klasörü **Adder**olarak adlandırın. Varsayılan kural olarak, bu klasörün adı API **/Adder**gibi API 'nin yolunu tanımlar.

    ![Yeni klasör seçeneği](media/azure-functions-lab-image26.png)

1. **Adder** klasörüne sağ tıklayın ve **> yeni dosya Ekle**' yi seçin.

    ![Yeni dosya seçeneği](media/azure-functions-lab-image27.png)

1. **Web** kategorisini ve **boş JSON dosyası** şablonunu seçin. **Adı** **işlev** olarak ayarlayın ve **Yeni**' ye tıklayın.

    ![Boş JSON dosyası seçeneği](media/azure-functions-lab-image28.png)

1. Yeni oluşturulan dosyanın varsayılan içeriğini değiştirmek için içindeki diğer **function. JSON** (3. adım) içeriğini yapıştırın.

1. JSON dosyasının en üstünden aşağıdaki satırları kaldırın:

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. İlk bağlamanın sonunda ( **"Name": "REQ"** satırı), aşağıdaki özellikleri ekleyin. Önceki satıra virgül eklemeyi unutmayın. Bu özellik varsayılan kökü geçersiz kılar, böylece artık yoldan **int** parametreleri ayıklar ve bunları **x** ve **y**adlı yöntem parametrelerine yerleştirebilirsiniz.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. İlk altında başka bir bağlama ekleyin. Bu bağlama işlevinin dönüş değerini işler. Önceki satıra virgül eklemeyi unutmayın:

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Ayrıca, aşağıda gösterildiği gibi, dosyanın alt kısmındaki **entryPoint** özelliğini **"Add2"** adlı bir yöntemi kullanacak şekilde güncelleştirin. Bu, **API/Adder...** yolunun herhangi bir ada sahip uygun bir yönteme (**Add2** burada) eşlendiğini göstermek için kullanılır.

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Son **function. JSON** dosyanız aşağıdaki JSON gibi görünmelidir:

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

1. Bu işi yapmak için gereken son adım, bu dosyayı her değiştiğinde çıkış dizinindeki aynı göreli yola kopyalamak Mac için Visual Studio söylemek. Dosya seçili olduğunda sağ taraftaki çubuktan Özellikler sekmesini seçin ve **Çıkış Dizinine Kopyala** ' yı seçerseniz, **daha yeniyse kopyala**' yı seçin:

    ![JSON dosyası için Özellikler seçenekleri](media/azure-functions-lab-image30.png)

1. **Add.cs**içinde, beklenen işlevi yerine getirmek için `Run` yöntemini (özniteliği dahil) aşağıdaki yöntemle değiştirin. `Run`, öznitelik olmaması ve **x** ve **y**için açık parametrelere sahip olması dışında, benzerdir.

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

1. Projeyi derlemek ve çalıştırmak için **F5** tuşuna basın.

1. Yapı tamamlandığından ve platform dönerek, artık yeni eklenen yönteme eşlenen istekler için kullanılabilen ikinci bir yol olduğunu gösterir:

    ![Http işlevleri URL 'SI](media/azure-functions-lab-image31.png)

1. Tarayıcı penceresini döndürün ve **http://localhost:7071/api/Adder/3/5** ' a gidin.

1. Bu kez Yöntem bir kez daha çalışarak yoldan parametreler çekerek ve bir toplam üretir.

1. **Mac için Visual Studio** dönün ve hata ayıklama oturumunu sonlandırın.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Alıştırma 5: Azure depolama tablolarıyla çalışma

Genellikle, oluşturduğunuz hizmet şimdiye kadar geliştirdiğimiz ve önemli miktarda zaman ve/veya altyapı gerektiren çok daha karmaşık olabilir. Bu durumda, kaynaklar kullanılabilir olduğunda işlenmek üzere sıraya alınmış istekleri kabul etmek için uygun olduğunu, hangi Azure Işlevleri için destek sağladığını de fark edebilirsiniz. Diğer durumlarda, verileri merkezi olarak saklamak isteyeceksiniz. Azure depolama tabloları bunu hızla yapmanızı sağlar.

1. Aşağıdaki sınıfı **Add.cs**öğesine ekleyin. Ad alanı içinde, ancak var olan sınıfın dışına gitmelidir.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. **Add** sınıfı içinde, başka bir işlevi tanıtmak için aşağıdaki kodu ekleyin. Bunun, bir HTTP yanıtı içermediğinden bu ana kadar benzersiz olduğunu unutmayın. Son satır, daha sonra (**partitionkey** ve **rowkey**), ayrıca parametrelerini ve toplamlarını daha sonra almayı kolaylaştıran bazı önemli bilgilerle doldurulmuş yeni bir **TableRow** döndürür. Yöntemi içindeki kod ayrıca, işlevin ne zaman çalıştığını daha kolay bilmesini sağlamak için **Tracewriter** kullanır.

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

1. Projeyi derlemek ve çalıştırmak için **F5** tuşuna basın.

1. Tarayıcı sekmesinde **http://localhost:7071/api/Process/4/6** ' a gidin. Bu, kuyruğa başka bir ileti yerleştirir. Bu, sonunda tabloya başka bir satırın eklenmesine neden olur.

1. **Terminal** 'e dönün ve **4 + 6**gelen isteğini izleyin.

    ![Ek isteği gösteren Terminal çıkışı](media/azure-functions-lab-image32.png)

1. İsteği aynı URL 'ye yenilemek için tarayıcıya dönün. Bu kez, **işlem** yönteminden sonra bir hata görürsünüz. Bunun nedeni, kodun zaten var olan bir bölüm ve satır anahtarı birleşimini kullanarak Azure Tablo depolama tablosuna bir satır eklemeye çalışıyor olması.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Hata ayıklama oturumunu sonlandırın.

1. Hatayı hafifletmek için, **Tracewriter** parametresinden hemen önce Yöntem tanımına aşağıdaki parametreyi ekleyin. Bu parametre, Azure Işlevleri platformunu, sonuçları depolamak için kullandığımız **Partitionkey** üzerindeki **sonuçlar** tablosundan bir **TableRow** almaya çalışacak şekilde yönlendirir. Ancak, aynı yöntemin diğer **x** ve **y** parametrelerine göre **rowkey** 'in dinamik olarak oluşturulduğunu fark ettiğinizde gerçek sihirli bir kısmı oynatma halinde gelir. Bu satır zaten varsa, **tableRow** geliştirici tarafından gerekli ek iş olmadan başladığında, bu durumda olur. Satır yoksa, yalnızca null olur. Bu verimlilik sıralaması, geliştiricilerin altyapıya değil önemli iş mantığına odaklanmasını sağlar.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. Aşağıdaki kodu yönteminin başına ekleyin. **TableRow** null değilse, işlem için beklenen sonuçlara zaten sahip olduğumuz ve anında dönebiliyoruz. Aksi takdirde, işlev daha önce olduğu gibi devam eder. Bu, verileri döndürmek için en güçlü yol olmayabilir, ancak çok az kod içeren birden çok ölçeklenebilir katmanda inanılmaz gelişmiş işlemleri düzenleyebilmenin noktasını gösterir.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. Projeyi derlemek ve çalıştırmak için **F5** tuşuna basın.

1. Tarayıcı sekmesinde **http://localhost:7071/api/Process/4/6** URL 'yi yenileyin. Bu kaydın tablo satırı var olduğundan, hemen ve hatasız döndürmelidir. HTTP çıktısı olmadığından çıktıyı terminalde görebilirsiniz.

    ![Tablo satırını gösteren Terminal çıkışı zaten var](media/azure-functions-lab-image33.png)

1. URL 'YI, **http://localhost:7071/api/Process/5/7** gibi henüz sınanmamıştır bir birleşimi yansıtacak şekilde güncelleştirin. Terminal 'teki, tablo satırının bulunamadığını (beklenen şekilde) belirten iletiyi not edin.

    ![Yeni işlemi gösteren Terminal çıkışı](media/azure-functions-lab-image34.png)

1. **Mac için Visual Studio** dönün ve hata ayıklama oturumunu sonlandırın.

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

Bu laboratuvarda, Mac için Visual Studio ile Azure Işlevleri oluşturmaya nasıl başladığınızı öğrendiniz.
