---
title: Depolama kaynaklarına gözatıp yönetme
description: Sunucu Gezgini kullanarak depolama kaynaklarına göz atma ve bunları yönetme
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 18726b1fa7f42b46cd309cfd4edef289d9469d39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053415"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Sunucu Gezgini'ni kullanarak depolama kaynaklarına göz atma ve bu kaynakları yönetme

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Genel Bakış

Microsoft Visual Studio için azure araçları 'nı yüklediyseniz, azure için depolama hesaplarınızdan blob, kuyruk ve tablo verilerini görüntüleyebilirsiniz. Sunucu Gezgini azure **Depolama** düğümü, yerel depolama öykünücü hesabınızdaki ve diğer Azure depolama hesaplarınızdaki verileri gösterir.

Sunucu Gezgini Visual Studio görüntülemek için, menü çubuğunda **görünüm**  >  **Sunucu Gezgini**' yı seçin. **Depolama** düğümü, her bir Azure aboneliğinde veya bağlı olduğunuz sertifikada bulunan tüm depolama hesaplarını gösterir. Depolama Hesabınız görünmezse, [Bu makalenin ilerleyen kısımlarındaki](#add-storage-accounts-by-using-server-explorer)yönergeleri izleyerek ekleyebilirsiniz.

Azure SDK 2,7 ' den başlayarak, Azure kaynaklarınızı görüntülemek ve yönetmek için bulut Gezgini 'ni de kullanabilirsiniz. Daha fazla bilgi için bkz. [Cloud Explorer Ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visual Studio 'de depolama kaynaklarını görüntüleyin ve yönetin

Sunucu Gezgini, depolama öykünücü hesabınızdaki Bloblar, kuyruklar ve tablolar listesini otomatik olarak gösterir. depolama öykünücüsü hesabı, **Depolama** düğümü altında, **geliştirme** düğümü olarak Sunucu Gezgini listelenir.

Depolama öykünücüsü hesabının kaynaklarını görmek için **geliştirme** düğümünü genişletin. **Geliştirme** düğümünü genişlettiğinizde depolama öykünücüsü başlatılmamışsa, otomatik olarak başlatılır. Bu işlem birkaç saniye sürebilir. depolama öykünücüsü başladığında Visual Studio diğer alanlarında çalışmaya devam edebilirsiniz.

Bir depolama hesabındaki kaynakları görüntülemek için, **BLOB**, **kuyruk** ve **tablo** düğümlerini gördüğünüz Sunucu Gezgini depolama hesabının düğümünü genişletin.

## <a name="work-with-blob-resources"></a>Blob kaynaklarıyla çalışma

**BLOB 'lar** düğümü, seçilen depolama hesabı için kapsayıcıların listesini görüntüler. Blob kapsayıcıları blob dosyaları içerir ve bu Blobları klasörler ve alt klasörler halinde düzenleyebilirsiniz. Daha fazla bilgi için bkz. [.net 'Ten blob depolamayı kullanma](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Blob kapsayıcısı oluşturmak için

1. **Bloblar** düğümünün kısayol menüsünü açın ve ardından **BLOB kapsayıcısı oluştur**' u seçin.
1. **BLOB kapsayıcısı oluştur** iletişim kutusunda yeni kapsayıcının adını girin.
1. Klavyenizde Enter ' u seçin veya blob kapsayıcısını kaydetmek için ad alanının dışına tıklayabilir veya dokunabilirsiniz.

   > [!NOTE]
   > Blob kapsayıcısı adı bir sayı (0-9) veya küçük harf (a-z) ile başlamalıdır.

### <a name="to-delete-a-blob-container"></a>Blob kapsayıcısını silmek için

Kaldırmak istediğiniz blob kapsayıcısı için kısayol menüsünü açın ve **Sil**' i seçin.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Blob kapsayıcısındaki öğelerin listesini görüntüleme

Listede bir blob kapsayıcısı adı için kısayol menüsünü açın ve **Aç**' ı seçin.

Blob kapsayıcısının içeriğini görüntülediğinizde, blob kapsayıcı görünümü olarak bilinen bir sekmede görüntülenir.

![Blob kapsayıcı görünümü](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Blob kapsayıcı görünümünün sağ üst köşesindeki düğmeleri kullanarak bloblarda aşağıdaki işlemleri yapabilirsiniz:

* Bir filtre değeri girin ve uygulayın.
* Kapsayıcıdaki Blobların listesini yenileyin.
* bir dosya Upload.
* Bir blobu silin. (Bir blob kapsayıcısından bir dosyayı silme, temeldeki dosyayı silmez. Yalnızca blob kapsayıcısından kaldırılır.)
* Blob açın.
* Bir blobu yerel bilgisayara kaydedin.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Blob kapsayıcısında klasör veya alt klasör oluşturmak için

1. **Cloud Explorer**'da blob kapsayıcısını seçin. kapsayıcı penceresinde, **Upload Blob** düğmesini seçin.

1. **yeni dosya Upload** iletişim kutusunda, karşıya yüklemek istediğiniz dosyayı belirtmek için, **gözden** geçirme düğmesini seçin ve ardından **klasör (isteğe bağlı)** kutusuna bir klasör adı girin.

   ![Blob klasörüne dosya yükleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Aynı adımı izleyerek kapsayıcı klasörlerine alt klasörler ekleyebilirsiniz. Bir klasör adı belirtmezseniz, dosya BLOB kapsayıcısının en üst düzeyine yüklenir. Dosya, kapsayıcıda belirtilen klasörde görüntülenir.

   ![Bir blob kapsayıcısına eklenen klasör](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Klasörün içeriğini görmek için klasörü çift tıklatın veya ENTER ' u seçin. Kapsayıcının klasöründe olduğunuzda, **üst dizin aç** (ok) düğmesini seçerek kapsayıcının köküne gidebilirsiniz.

### <a name="to-delete-a-container-folder"></a>Bir kapsayıcı klasörünü silmek için

Klasördeki tüm dosyaları silin.

Blob kapsayıcılarındaki klasörler sanal klasörlerdir, boş bir klasör oluşturamazsınız. Ayrıca, dosya içeriklerini silmek için bir klasörü silemez, ancak bunun yerine klasörü silmek için bir klasörün tüm içeriğini silmeniz gerekir.

### <a name="to-filter-blobs-in-a-container"></a>Bir kapsayıcıdaki Blobları filtrelemek için

Ortak bir ön ek belirterek görüntülenen Blobları filtreleyebilirsiniz.

Örneğin, filtre metin kutusuna **Hello** önekini girip **Yürüt** (**!**) düğmesini seçerseniz, yalnızca "Hello" ile başlayan Bloblar görüntülenir.

![Filtre metin kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Filtre metin kutusu, büyük/küçük harfe duyarlıdır ve joker karakterlerle filtrelemeyi desteklemez. Blob 'lar yalnızca ön eke göre filtrelenebilir. Bir sanal hiyerarşide Blobları düzenlemek için bir sınırlayıcı kullanıyorsanız, ön ek bir sınırlayıcı içerebilir. Örneğin, "HelloFabric/" ön ekine filtre uygulamak, bu dizeyle başlayan tüm blob 'ları döndürür.

### <a name="to-download-blob-data"></a>Blob verilerini indirmek için

**Cloud Explorer**'da aşağıdaki yöntemlerden birini kullanın:

* Bir veya daha fazla Blobun kısayol menüsünü açın ve **Aç**' ı seçin.
* Blob adını seçin ve sonra **Aç** düğmesini seçin.
* Blob adına çift tıklayın.

Blob indirmenin ilerleme durumu, **Azure etkinlik günlüğü** penceresinde görünür.

Blob, bu dosya türü için varsayılan düzenleyicide açılır. İşletim sistemi dosya türünü tanırsa, dosya yerel olarak yüklenmiş bir uygulamada açılır. Aksi takdirde, Blobun dosya türü için uygun bir uygulama seçmeniz istenir. Bir blobu karşıdan yüklerken oluşturulan yerel dosya salt okunurdur.

Blob verileri yerel olarak önbelleğe alınır ve BLOB 'un Azure Blob depolamada son değiştirilme zamanına karşı denetlenir. Blob son indirildikten sonra güncelleştirilirse, yeniden indirilir. Aksi takdirde, blob yerel diskten yüklenir.

Varsayılan olarak, bir blob geçici bir dizine indirilir. Blob 'ları belirli bir dizine indirmek için seçili blob adları için kısayol menüsünü açın ve **farklı kaydet**' i seçin. Bir blobu bu şekilde kaydettiğinizde, blob dosyası açılmaz ve yerel dosya okuma/yazma öznitelikleriyle oluşturulur.

### <a name="to-upload-blobs"></a>Blobları karşıya yüklemek için

blobları karşıya yüklemek için, kapsayıcı blob kapsayıcısı görünümünde görüntülenmek üzere açıkken **Upload blob** düğmesini seçin.

Karşıya yüklenecek bir veya daha fazla dosya seçebilir ve herhangi bir türde dosya yükleyebilirsiniz. **Azure etkinlik günlüğü** penceresinde karşıya yükleme işleminin ilerleme durumu gösterilir. Blob verileriyle çalışma hakkında daha fazla bilgi için bkz. [.net 'Te Azure Blob depolamayı kullanma](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

### <a name="to-view-logs-transferred-to-blobs"></a>Bloblara aktarılan günlükleri görüntülemek için

Azure uygulamanızdaki verileri günlüğe kaydetmek için Azure Tanılama kullanıyorsanız ve günlükleri depolama hesabınıza aktardıysanız, Azure 'un bu Günlükler için oluşturduğu kapsayıcıları görürsünüz. Bu günlükleri Sunucu Gezgini ' de görüntülemek, özellikle Azure 'a dağıtılırsa, uygulamanızla ilgili sorunları belirlemenin kolay bir yoludur.

Azure Tanılama hakkında daha fazla bilgi için bkz. [Azure Tanılama kullanarak günlük verilerini toplama](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="to-get-the-url-for-a-blob"></a>Bir Blobun URL 'sini almak için

Blobun kısayol menüsünü açın ve **URL 'Yi Kopyala**' yı seçin.

### <a name="to-edit-a-blob"></a>Bir blobu düzenlemek için

Blobu seçin ve ardından **blobu aç** düğmesini seçin.

Dosya geçici bir konuma indirilir ve yerel bilgisayarda açılır. değişiklikleri yaptıktan sonra blobu yeniden Upload.

## <a name="work-with-queue-resources"></a>Kuyruk kaynaklarıyla çalışma

Depolama services kuyrukları bir Azure depolama hesabında barındırılır. Bunları, bulut hizmeti rollerinizin bir ileti geçirme mekanizmasıyla birbirleriyle ve diğer hizmetlerle iletişim kurmasına izin vermek için kullanabilirsiniz. Kuyruğa program aracılığıyla bir bulut hizmeti ve dış istemciler için bir web hizmeti üzerinden erişin. Ayrıca kuyrukta yer alan Sunucu Gezgini kullanarak Visual Studio.

Kuyrukları kullanan bir bulut hizmeti geliştirirken, siz kodunuzu geliştirirken ve test ederken Visual Studio oluşturmak ve onlarla etkileşimli olarak çalışmak için Visual Studio'i kullanabilirsiniz.

Bu Sunucu Gezgini, kuyrukları bir depolama hesabında görüntüleme, kuyruk oluşturma ve silme, iletilerini görüntülemek için bir kuyruk açma ve kuyruğa ileti ekleme. Görüntülemek üzere bir kuyruk asanız, tek tek iletileri görüntüebilirsiniz ve sol üst köşedeki düğmeleri kullanarak kuyrukta aşağıdaki eylemleri gerçekleştirebilirsiniz:

* Kuyruğun görünümünü yenileyin.
* Kuyruğa bir ileti ekleyin.
* En üstteki iletiyi sıra dışı bırakın.
* Kuyruğun tamamını temizleme.

Aşağıdaki görüntüde, iki ileti içeren bir kuyruk gösterir:

![Kuyruğu görüntüleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Depolama hizmetleri kuyrukları hakkında daha fazla bilgi için [bkz. .NET Kullanmaya başlayın Azure Kuyruk depolama ile depolamayı kullanma.](/azure/storage/queues/storage-dotnet-how-to-use-queues) Depolama hizmetleri kuyrukları için web hizmeti hakkında daha fazla bilgi için bkz. [Kuyruk Hizmeti Kavramları.](/rest/api/storageservices/Queue-Service-Concepts) Visual Studio kullanarak bir depolama hizmetleri kuyruğuna ileti gönderme hakkında bilgi için bkz. [Depolama Hizmetleri Kuyruğuna İleti Gönderme.](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues)

> [!NOTE]
> Depolama hizmetleri kuyrukları Azure hizmet kuyruklarından Service Bus farklıdır. Kuyrukları yeniden Service Bus için [bkz. Service Bus, konu başlıkları ve abonelikleri.](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)

## <a name="work-with-table-resources"></a>Tablo kaynaklarıyla çalışma

Azure Tablo depolama, büyük miktarlarda yapısal veriyi depolar. Hizmet, Azure bulutu içinden ve dışından kimliği doğrulanmış çağrıları kabul eden bir NoSQL veri deposu hizmetidir. Azure tabloları, yapılandırılmış ve ilişkisel olmayan verilerin depolanması için idealdir.

### <a name="to-create-a-table"></a>Tablo oluşturmak için

1. Bulut **Gezgini'nde** depolama **hesabının Tablolar** düğümünü ve ardından Tablo Oluştur'ı **seçin.**
1. Tablo **Oluştur iletişim** kutusuna tablo için bir ad girin.

### <a name="to-view-table-data"></a>Tablo verilerini görüntülemek için

1. Cloud **Explorer'da** **Azure** düğümünü açın ve ardından azure **Depolama** açın.
1. İlgilenilen depolama hesabı düğümünü açın ve ardından depolama hesabı **için** tabloların listesini görmek için Tablolar düğümünü açın.
1. Bir tablonun kısayol menüsünü açın ve Tabloyu **Görüntüle'yi seçin.**

    ![Çözüm Gezgini'de bir Azure tablosu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tablo varlıklara (satırlarda gösterilir) ve özelliklere (sütunlarda gösterilir) göre düzenlenmiştir. Örneğin, sonraki çizimde aşağıdaki çizimde listelenen varlıklar Tablo Tasarımcısı.

### <a name="to-edit-table-data"></a>Tablo verilerini düzenlemek için

Bu **Tablo Tasarımcısı** varlığın kısayol menüsünü (tek satır) veya bir özelliği (tek bir hücre) açın ve düzenle'yi **seçin.**

![Tablo varlığı ekleme veya düzenleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Tek bir tablodaki varlıkların aynı özellik kümesine (sütunlar) sahip olması gerekmez. Tablo verilerini görüntüleme ve düzenlemeyle ilgili aşağıdaki kısıtlamaları unutmayın:

* İkili verileri ( ) görüntüleyemez veya `type byte[]` düzenleyemezsiniz, ancak bir tabloda depolarsınız.
* Azure Tablo depolaması bu işlemi desteklemey olduğundan **PartitionKey** veya **RowKey** değerlerini düzenleyemezsiniz.
* Timestamp adlı bir özellik **oluşturayazabilirsiniz.** Azure depolama hizmetleri bu adla bir özellik kullanır.
* Bir Tarih Saat **değeri** girersiniz, bilgisayarınızın bölge ve dil ayarlarına (örneğin, AA/D/YYYY SS:MM:SS [AM| ABD İngilizcesi için PM] ).

### <a name="to-add-entities"></a>Varlık eklemek için

1. Bu **Tablo Tasarımcısı** Varlık Ekle **düğmesini** seçin.

    ![Varlık Ekle düğmesi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. Varlık **Ekle iletişim** kutusunda **PartitionKey** ve **RowKey** özelliklerinin değerlerini girin.

    ![Varlık Ekle iletişim kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Değerleri dikkatli bir şekilde girin. Varlığı sildikten sonra yeniden eklemedikçe iletişim kutusunu kapatarak bunları değiştiremezsiniz.

### <a name="to-filter-entities"></a>Varlıkları filtrelemek için

Sorgu oluşturucuyu kullanıyorsanız tabloda görünen varlık kümelerini özelleştirebilirsiniz.

1. Sorgu oluşturucuyu açmak için görüntülemek için bir tablo açın.
1. Tablo **Sorgu Tasarımcısı** araç çubuğundaKimlik düğmesi seçin.

    Sorgu Tasarımcısı  iletişim kutusu görüntülenir. Aşağıdaki çizimde, sorgu oluşturucuda yerleşik olarak yer alan bir sorgu gösterilmiştir.

    ![Sorgu oluşturucu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Sorguyu oluşturma işi bittiğinde iletişim kutusunu kapatın. Sorgunun sonuçta elde edilen metin biçimi, bir metin kutusunda bir metin WCF Veri Hizmetleri görünür.
1. Sorguyu çalıştırmak için yeşil üçgen simgesini seçin.

Ayrıca, doğrudan filtre metin kutusuna Tablo Tasarımcısı bir filtre dizesi WCF Veri Hizmetleri içinde görünen varlık verilerini filtreleebilirsiniz. Bu tür dize, WHERE yan tümcesine SQL ancak sunucuya HTTP isteği olarak gönderilir. Filtre dizeleri oluşturma hakkında bilgi için [bkz. Tablo tasarımcısı için filtre dizeleri oluşturma.](vs-azure-tools-table-designer-construct-filter-strings.md)

Aşağıdaki çizimde geçerli bir filtre dizesi örneği gösterilmiştir:

![Filtre dizesi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Depolama verilerini yenileme

Bir Sunucu Gezgini bir depolama hesabına bağlandığında veya bu hesaptan veri alıyorsa, işlemi tamamlamak bir dakika kadar zaman alır. Bağlantı Sunucu Gezgini, işlem zaman zaman uzer. Veriler alınırken verilerin diğer kısımlarında çalışmaya devam Visual Studio. Çok uzun süren işlemi iptal etmek için, araç **çubuğundaki** Yenilemeyi Durdur Sunucu Gezgini seçin.

### <a name="to-refresh-blob-container-data"></a>Blob kapsayıcı verilerini yenilemek için

* öğesinin **altındaki Bloblar** **Depolama** seçin ve sonra  da araç çubuğunda yenile Sunucu Gezgini seçin.
* Görüntülenen blob listesini yenilemek için Yürüt **düğmesini** seçin.

### <a name="to-refresh-table-data"></a>Tablo verilerini yenilemek için

* öğesinin **altındaki** Tablolar **Depolama** seçin ve sonra  da araç çubuğunda yenile Sunucu Gezgini seçin.
* içinde görüntülenen varlıkların listesini yenilemek için **Tablo Tasarımcısı** içinde **Yürüt** düğmesini Tablo Tasarımcısı.

### <a name="to-refresh-queue-data"></a>Kuyruk verilerini yenilemek için

öğesinin **altındaki Kuyruklar** **Depolama** seçin ve ardından araç **çubuğunda** yenile Sunucu Gezgini seçin.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Depolama hesabıdaki tüm öğeleri yenilemek için

Hesap adını seçin ve ardından araç **çubuğunda** yenile Sunucu Gezgini seçin.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Sunucu Gezgini kullanarak depolama Sunucu Gezgini

Depolama hesaplarını, depolama hesabı eklemenin iki yolu Sunucu Gezgini. Azure aboneliğinize bir depolama hesabı oluşturabilir veya var olan bir depolama hesabını iliştirebilirsiniz.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Depolama hesabını kullanarak depolama hesabı Sunucu Gezgini

1. Sunucu Gezgini düğümü için kısayol menüsünü açın **ve Depolama** Oluştur'Depolama **seçin.**

1. Hesap **Oluştur Depolama** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Depolama hesabını eklemek istediğiniz Azure aboneliği.
   * Yeni depolama hesabı için kullanmak istediğiniz ad.
   * Bölge veya benzeşm grubu (örneğin, Batı ABD veya Doğu Asya).
   * Yerel olarak yedekli gibi depolama hesabı için kullanmak istediğiniz çoğaltma türü.

   ![Azure depolama hesabı oluşturma](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. **Oluştur**’u seçin.

Yeni depolama hesabı, Depolama **listesinde** Çözüm Gezgini.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Var olan bir depolama hesabını Sunucu Gezgini

1. Azure Sunucu Gezgini düğümü için kısayol menüsünü **açın ve Depolama** Ekle'yi **Depolama.**

    ![Mevcut depolama hesabını ekleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. Hesap **Oluştur Depolama** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Eklemek istediğiniz mevcut depolama hesabının adı.
   * Seçilen depolama hesabının anahtarı. Bu değer genellikle bir depolama hesabı seçerek sizin için sağlanır. Depolama hesabı Visual Studio hatırlamak istemiyorsanız Hesap anahtarını anımsa **onay** kutusunu seçin.
   * HTTP, HTTPS veya özel uç nokta gibi depolama hesabına bağlanmak için kullanabileceğiniz protokol. Özel uç noktalar hakkında daha fazla bilgi için [bkz. Bağlantı Dizelerini Yapılandırma.](/azure/storage/common/storage-configure-connection-string)

### <a name="to-view-the-secondary-endpoints"></a>İkincil uç noktaları görüntülemek için

Okuma Erişimli Coğrafi Olarak  Yedekli çoğaltma seçeneğini kullanarak bir depolama hesabı oluşturduysanız, hesap adının kısayol menüsünü açarak ikincil uç noktalarını ekleyebilirsiniz ve ardından Özellikler'i **seçebilirsiniz.**

![Depolama uç noktaları yapılandırma](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Depolama hesabını bir depolama hesabından Sunucu Gezgini

Bu Sunucu Gezgini hesap adı kısayol menüsünü açın ve Sil'i **seçin.**

Bir depolama hesabını silersiniz, bu hesap için kaydedilen tüm anahtar bilgileri de kaldırılır.

Bir depolama hesabını Sunucu Gezgini, depolama hesabınızı veya içerdiği verileri etkilemez. Bu işlem yalnızca başvurudan Sunucu Gezgini. Bir depolama hesabını kalıcı olarak silmek için [Azure portal.](https://portal.azure.com/)

## <a name="next-steps"></a>Sonraki adımlar

Azure depolama hizmetlerini kullanma hakkında daha fazla bilgi edinmek için [bkz. Azure Depolama Hizmetleri'ne erişme.](/azure/storage/common/storage-introduction)
