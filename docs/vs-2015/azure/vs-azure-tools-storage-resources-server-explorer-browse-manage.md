---
title: Gözat ve Sunucu Gezgini kullanarak depolama kaynaklarını yönetme | Microsoft Docs
description: Göz atma ve Sunucu Gezgini kullanarak depolama kaynaklarını yönetme
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 36b2691525eb66bf946317c1bb5254796d5cd639
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291230"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Sunucu Gezgini'ni kullanarak depolama kaynaklarına göz atma ve bu kaynakları yönetme

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Genel Bakış

Microsoft Visual Studio için Azure Araçları'nı yüklediyseniz, depolama hesaplarınızı blob, kuyruk ve tablo verilerini Azure'a görüntüleyebilirsiniz. Sunucu Gezgini 'de Azure **depolama** düğümü, yerel depolama öykünücü hesabınızdaki ve diğer Azure depolama hesaplarınızdaki verileri gösterir.

Visual Studio 'da Sunucu Gezgini görüntülemek için, menü çubuğunda, **görünüm** > **Sunucu Gezgini**' yı seçin. **Depolama** düğümü, her bir Azure aboneliğinde veya bağlı olduğunuz sertifikada bulunan tüm depolama hesaplarını gösterir. Depolama Hesabınız görünmezse, [Bu makalenin ilerleyen kısımlarındaki](#add-storage-accounts-by-using-server-explorer)yönergeleri izleyerek ekleyebilirsiniz.

Azure SDK 2.7 başlayarak, Cloud Explorer görüntülemek ve Azure kaynaklarınızı yönetmek için de kullanabilirsiniz. Daha fazla bilgi için bkz. [Cloud Explorer Ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visual Studio'da depolama kaynakları görüntüleme ve yönetme

Sunucu Gezgini, depolama öykünücüsü hesabınızdaki BLOB'lar, kuyruklar ve tablolar listesini otomatik olarak gösterir. Depolama öykünücüsü hesabı, **depolama** düğümü altında, **geliştirme** düğümü olarak Sunucu Gezgini listelenir.

Depolama öykünücüsü hesabının kaynaklarını görmek için **geliştirme** düğümünü genişletin. **Geliştirme** düğümünü genişlettiğinizde depolama öykünücüsü başlatılmamışsa, otomatik olarak başlatılır. Bu işlem birkaç saniye sürebilir. Depolama öykünücüsü başlatılırken Visual Studio'nun diğer alanlarında çalışmaya devam edebilirsiniz.

Bir depolama hesabındaki kaynakları görüntülemek için, **BLOB**, **kuyruk**ve **tablo** düğümlerini gördüğünüz Sunucu Gezgini depolama hesabının düğümünü genişletin.

## <a name="work-with-blob-resources"></a>BLOB kaynakları ile çalışma

**BLOB 'lar** düğümü, seçilen depolama hesabı için kapsayıcıların listesini görüntüler. BLOB kapsayıcıları blob dosyaları içerir ve bu bloblar klasörlere ve alt düzenleyebilirsiniz. Daha fazla bilgi için bkz. [.net 'Ten blob depolamayı kullanma](/azure/storage/blobs/storage-dotnet-how-to-use-blobs).

### <a name="to-create-a-blob-container"></a>Bir blob kapsayıcısı oluşturmak için

1. **Bloblar** düğümünün kısayol menüsünü açın ve ardından **BLOB kapsayıcısı oluştur**' u seçin.
1. **BLOB kapsayıcısı oluştur** iletişim kutusunda yeni kapsayıcının adını girin.  
1. Enter'ı seçin, klavye veya tıklayabilir veya blob kapsayıcısını kaydetmek için ad alanı dokunun.

   > [!NOTE]
   > Blob kapsayıcısı adı, bir sayı (0-9) ya da küçük harf (a-z) başlaması gerekir.

### <a name="to-delete-a-blob-container"></a>Bir blob kapsayıcısını silmek için

Kaldırmak istediğiniz blob kapsayıcısı için kısayol menüsünü açın ve **Sil**' i seçin.

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Bir blob kapsayıcısını öğelerinin listesini görüntülemek için

Listede bir blob kapsayıcısı adı için kısayol menüsünü açın ve **Aç**' ı seçin.

Bir blob kapsayıcı içeriğini görüntülediğinizde, blob kapsayıcı görünümü olarak bilinen bir sekmesinde görünür.

![BLOB kapsayıcı görünümü](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Blob kapsayıcı görünümü sağ üst köşesinde bulunan düğmeleri kullanarak BLOB'ları aşağıdaki işlemleri gerçekleştirebilirsiniz:

* Bir filtre değeri girin ve uygulayın.
* Kapsayıcıdaki blobların listesini yenileyin.
* Bir dosyayı karşıya yükleyin.
* Bir blobu silin. (Bir dosya silindiğinde bir blob kapsayıcısından temel alınan dosya silinmiyor. Bu yalnızca bir blob kapsayıcısından kaldırır.)
* Bir blob açın.
* Bir blobu yerel bilgisayara kaydedin.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Bir klasörü veya alt klasör bir blob kapsayıcısını oluşturmak için

1. Blob kapsayıcısını Cloud Explorer'ı seçin. Kapsayıcı penceresinde, **blobu karşıya yükle** düğmesini seçin.

1. Karşıya **yeni dosya yükle** iletişim kutusunda, karşıya yüklemek istediğiniz dosyayı belirtmek Için, **tarayıcı** düğmesini seçin ve ardından **klasöre (isteğe bağlı)** bir klasör adı girin.

   ![Blob klasörüne bir dosya yükleniyor](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Aynı adımı takip ederek, kapsayıcı klasörlerinde alt klasörleri ekleyebilirsiniz. Dosya, klasör adı belirtmezseniz, blob kapsayıcısının en üst düzeye karşıya yüklendi. Dosya belirtilen kapsayıcı klasöründe görünür.

   ![Klasör bir blob kapsayıcıya eklendi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Klasörü çift tıklatın veya klasörün içeriğini görmek için Enter tuşuna basın. Kapsayıcının klasöründe olduğunuzda, **üst dizin aç** (ok) düğmesini seçerek kapsayıcının köküne gidebilirsiniz.

### <a name="to-delete-a-container-folder"></a>Bir kapsayıcı klasörü silmek için

Klasördeki tüm dosyaları silin.

Blob kapsayıcıları klasörlerinde sanal klasörler olduğundan, boş bir klasör oluşturulamıyor. Ayrıca dosya içeriğini silmek için bir klasör silinemez, ancak bunun yerine klasörü silmek için bir klasörün tüm içeriğini silmeniz gerekir.

### <a name="to-filter-blobs-in-a-container"></a>Bir kapsayıcıdaki blobları filtrelemek için

Ortak bir önek belirleyerek görüntülenen blobları filtreleyebilirsiniz.

Örneğin, filtre metin kutusuna **Hello** önekini girip **Yürüt** ( **!** ) düğmesini seçerseniz, yalnızca "Hello" ile başlayan Bloblar görüntülenir.

![Filtre metin kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Filtre metin kutusuna büyük küçük harfe duyarlıdır ve joker karakterlerle filtrelemeyi desteklemez. BLOB'ları yalnızca ön eke göre filtrelenebilir. Sanal bir hiyerarşide blobları düzenlemek için bir sınırlayıcı kullanıyorsanız öneki bir sınırlayıcı içerebilir. Örneğin, ön ek filtreleme "HelloFabric /" Bu dize ile başlayan tüm BLOB'ları döndürür.

### <a name="to-download-blob-data"></a>BLOB verilerini indirmek için

Cloud Explorer'da, aşağıdaki yöntemlerden birini kullanın:

* Bir veya daha fazla Blobun kısayol menüsünü açın ve **Aç**' ı seçin.
* Blob adını seçin ve sonra **Aç** düğmesini seçin.
* Blob adına çift tıklayın.

Blob indirmenin ilerleme durumu, **Azure etkinlik günlüğü** penceresinde görünür.

Blob, dosya türü için varsayılan Düzenleyicisi'nde açılır. Dosya türü işletim sistemini algılar, dosyayı yerel olarak yüklenmiş bir uygulamada açılır. Aksi takdirde, blob dosya türü için uygun bir uygulama seçmeniz istenir. Bir blob yüklediğinizde oluşturduğunuz yerel dosya salt okunur olarak işaretlenmiş.

BLOB verilerini yerel olarak önbelleğe alınmış ve Azure Blob Depolama alanında blob son değiştirilme zamanına karşılaştırılarak. Son yüklemenizden sonra blob güncelleştirildiyse, yeniden yüklenir. Aksi takdirde, blob yerel diskten yüklenir.

Varsayılan olarak, bir blob geçici bir dizine yüklenir. Blob 'ları belirli bir dizine indirmek için seçili blob adları için kısayol menüsünü açın ve **farklı kaydet**' i seçin. Bu şekilde bir blob kaydettiğinizde, blob dosyası açık değil ve yerel dosya okuma/yazma öznitelikleri ile oluşturulur.

### <a name="to-upload-blobs"></a>Blobları karşıya yüklemek için

Blobları karşıya yüklemek için, kapsayıcı blob kapsayıcısı görünümünde görüntülenmek üzere açıkken **blobu karşıya yükle** düğmesini seçin.

Karşıya yüklenecek bir veya daha fazla dosyaları seçebilirsiniz ve tüm dosya türlerini karşıya yükleyebilirsiniz. **Azure etkinlik günlüğü** penceresinde karşıya yükleme işleminin ilerleme durumu gösterilir. Blob verileriyle çalışma hakkında daha fazla bilgi için bkz. [.net 'Te Azure Blob depolamayı kullanma](https://go.microsoft.com/fwlink/p/?LinkId=267911).

### <a name="to-view-logs-transferred-to-blobs"></a>Blob'lara aktarılan günlükleri görüntülemek için

Azure Tanılama verileri Azure uygulamanızdan günlüğe kaydetmek için kullandığınız ve depolama hesabınıza günlükleri aktardınız, Azure için bu günlükleri oluşturulan kapsayıcı görürsünüz. Özellikle Azure'a dağıtıldıktan, sunucu Gezgini'nde bu günlükleri görüntüleme, uygulamanızdaki sorunları tanımlamak için kolay bir yoludur.

Azure Tanılama hakkında daha fazla bilgi için bkz. [Azure Tanılama kullanarak günlük verilerini toplama](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="to-get-the-url-for-a-blob"></a>Bir blobu URL'si almak için

Blobun kısayol menüsünü açın ve **URL 'Yi Kopyala**' yı seçin.

### <a name="to-edit-a-blob"></a>Bir blob düzenlemek için

Blobu seçin ve ardından **blobu aç** düğmesini seçin.

Dosyanın geçici bir konuma indirilir ve yerel bilgisayarda açılır. Blob, değişiklikleri yaptıktan sonra yeniden yükleyin.

## <a name="work-with-queue-resources"></a>Kuyruk kaynaklarını ile çalışma

Depolama Hizmetleri kuyrukları bir Azure depolama hesabında barındırılır. Bulut hizmeti rolleri, ileti geçirme mekanizması tarafından birbirleriyle ve diğer hizmetlerle iletişim kurmak izin vermek için kullanabilirsiniz. Sıranın program aracılığıyla bir bulut hizmeti aracılığıyla ve dış istemciler için bir web hizmeti üzerinden erişebilirsiniz. Sıranın doğrudan Visual Studio'da Sunucu Gezgini kullanarak da erişebilirsiniz.

Kuyrukları kullanan bir bulut hizmeti geliştirdiğinizde, Kuyrukları Oluşturma ve bunlarla etkileşimli olarak geliştirip kodunuzu test ederken çalışmak için Visual Studio'u kullanmayı isteyebilirsiniz.

Sunucu Gezgini'nde, kuyrukları bir depolama hesabında görüntülemek, oluşturmak ve sırayı silmek, iletileri görüntülemek için bir kuyruk açın ve bir kuyruğuna ileti ekleme. Bir kuyruğu görüntüleme açtığınızda, tek bir ileti görüntüleyebilir ve sol üst köşedeki düğmeleri kullanarak sıraya aşağıdaki eylemleri gerçekleştirebilirsiniz:

* Kuyruk görünümü yenileyin.
* Kuyruğa bir ileti ekleyin.
* En üstteki iletiyi sıradan çıkar.
* Kuyruğun tamamı temizleyin.

Aşağıdaki görüntüde, iki ileti içeren bir kuyruk gösterilmektedir:

![Bir kuyruğu görüntüleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Depolama Hizmetleri kuyrukları hakkında daha fazla bilgi için bkz. [.NET kullanarak Azure kuyruk depolama ile çalışmaya başlama](https://go.microsoft.com/fwlink/?LinkID=264702). Depolama Hizmetleri kuyrukları Web hizmeti hakkında daha fazla bilgi için bkz. [kuyruk hizmeti kavramları](https://go.microsoft.com/fwlink/?LinkId=264788). Visual Studio kullanarak bir depolama hizmetleri kuyruğuna ileti gönderme hakkında daha fazla bilgi için bkz. [Depolama Hizmetleri kuyruğuna Ileti gönderme](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Depolama Hizmetleri kuyruklarına, Azure Service Bus sıralarından farklıdır. Service Bus kuyrukları hakkında daha fazla bilgi için bkz. [Service Bus kuyruklar, konular ve abonelikler](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Tablo kaynakları ile çalışma

Azure tablo depolama, büyük miktarlarda yapısal veriyi depolar. Kimliği doğrulanmış çağrılarından içindeki ve Azure Bulutu dışındaki kabul eden bir NoSQL veri deposu hizmetidir. Azure tabloları, yapılandırılmış ve ilişkisel olmayan verilerin depolanması için idealdir.

### <a name="to-create-a-table"></a>Bir tablo oluşturmak için

1. Cloud Explorer 'da depolama hesabının **Tablolar** düğümünü seçin ve ardından **tablo oluştur**' u seçin.
1. **Tablo oluştur** iletişim kutusunda tablo için bir ad girin.

### <a name="to-view-table-data"></a>Tablo verilerini görüntülemek için

1. Cloud Explorer 'da **Azure** düğümünü açın ve **depolama** düğümünü açın.
1. İlgilendiğiniz depolama hesabı düğümünü açın ve ardından depolama hesabı için tabloların listesini görmek üzere **Tables** düğümünü açın.
1. Bir tablo için kısayol menüsünü açın ve ardından **tabloyu görüntüle**' yi seçin.

    ![Çözüm Gezgini'nde bir Azure tablosu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tablo, varlıkları (satırlarda gösterilen) ve özellikleri (sütunları gösterilmiştir) göre düzenlenir. Örneğin, bir sonraki çizimde Tablo Tasarımcısı'nda listelenen varlıkları gösterir.

### <a name="to-edit-table-data"></a>Tablo verileri düzenlemek için

Tablo Tasarımcısı, bir varlık (tek bir satır) veya bir Özellik (tek bir hücre) için kısayol menüsünü açın ve ardından **Düzenle**' yi seçin.

![Tablo varlığı ekleme veya düzenleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Varlıkları tek bir tabloda aynı özellikleri (sütunları) olan gerekli değildir. Görüntüleme ve düzenleme tablo verilerini aşağıdaki kısıtlamaları göz önünde bulundurun:

* İkili verileri görüntüleyemez veya düzenleyemezsiniz (`type byte[]`), ancak bir tabloda saklayabilirsiniz.
* Azure 'daki tablo depolaması bu işlemi desteklemediğinden **partitionkey** veya **rowkey** değerlerini düzenleyemezsiniz.
* **Zaman damgası**adlı bir özellik oluşturamazsınız. Azure depolama hizmetleri, bu ada sahip bir özelliğini kullanın.
* Bir **Tarih saat** değeri girerseniz, bilgisayarınızın bölge ve dil ayarlarına uygun bir biçimi izlemeniz gerekir (ÖRNEĞIN, aa/gg/yyyy HH: mm: SS [har | PM] ABD Ingilizcesi için).

### <a name="to-add-entities"></a>Varlık eklemek için

1. Tablo Tasarımcısı **varlık Ekle** düğmesini seçin.

    ![Varlık düğmesi ekleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. **Varlık Ekle** iletişim kutusunda, **Partitionkey** ve **rowkey** özelliklerinin değerlerini girin.

    ![Varlık Ekle iletişim kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Değerleri dikkatli bir şekilde girin. Bir varlığı silme ve yeniden ekleyin sürece iletişim kutusunu kapattıktan sonra değiştiremezsiniz.

### <a name="to-filter-entities"></a>Varlıkları filtrelemek için

Sorgu Oluşturucu kullanırsanız, bir tablodaki görünen varlık kümesini özelleştirebilirsiniz.

1. Sorgu tasarımcısını açmak için bir tablo görüntüleme için açın.
1. Tablo görünümü araç çubuğunda **Sorgu Tasarımcısı** düğmesini seçin.

    **Sorgu Tasarımcısı** iletişim kutusu görüntülenir. Aşağıdaki çizimde, Sorgu Oluşturucu'da oluşturulmakta olan bir sorguyu gösterir.

    ![Sorgu Oluşturucu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Bitirdiğinizde, sorgu oluşturma iletişim kutusunu kapatın. Sorgu sonuç metin biçiminde metin kutusunda, WCF Veri Hizmetleri filtre olarak görünür.
1. Sorguyu çalıştırmak için yeşil üçgeni simgesini seçin.

Ayrıca, girerseniz filtre metin kutusuna doğrudan bir WCF Veri Hizmetleri filtre dizesi Tablo Tasarımcısı'nda görüntülenen varlık verilerini filtreleyebilirsiniz. Bu tür bir dize, bir SQL WHERE yan tümcesine benzer ancak sunucusu bir HTTP isteği olarak gönderilir. Filtre dizeleri oluşturma hakkında daha fazla bilgi için bkz. [Tablo Tasarımcısı için filtre dizeleri](/azure/vs-azure-tools-table-designer-construct-filter-strings)oluşturma.

Geçerli filtre dizesinin aşağıda gösterilmiştir:

![Filtre dizesi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Depolama veri yenileme

Sunucu Gezgini bağlanır veya bir depolama hesabından verileri alır, işlem bir dakika kadar son kadar sürebilir. Sunucu Gezgini bağlanamıyorsa, işlem zaman aşımına uğrar. Veriler alınırken, Visual Studio 'nun diğer bölümlerinde çalışmaya devam edebilirsiniz. Çok uzun sürüyorsa işlemi iptal etmek için Sunucu Gezgini araç çubuğundaki **yenilemeyi durdur** düğmesini seçin.

### <a name="to-refresh-blob-container-data"></a>BLOB kapsayıcı verileri yenilemek için

* **Depolama**altındaki **Bloblar** düğümünü seçin ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.
* Görüntülenen blob 'ların listesini yenilemek için **Yürüt** düğmesini seçin.

### <a name="to-refresh-table-data"></a>Tablo verileri yenilemek için

* **Depolama**altındaki **Tablolar** düğümünü ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.
* Tablo Tasarımcısı ' de görüntülenen varlıkların listesini yenilemek için Tablo Tasarımcısı **Çalıştır** düğmesini seçin.

### <a name="to-refresh-queue-data"></a>Kuyruk verileri yenilemek için

**Depolama**altındaki **Kuyruklar** düğümünü seçin ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Bir depolama hesabındaki tüm öğeleri yenilemek için

Hesap adı ' nı seçin ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Sunucu Gezgini kullanarak depolama hesapları ekleme

Sunucu Gezgini kullanarak depolama hesapları eklemek için iki yolu vardır. Azure aboneliğinizde bir depolama hesabı oluşturabilir veya mevcut bir depolama hesabı ekleyebilirsiniz.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak bir depolama hesabı oluşturmak için

1. Sunucu Gezgini ' de, **depolama** düğümü için kısayol menüsünü açın ve **depolama hesabı oluştur**' u seçin.

1. **Depolama hesabı oluştur** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Depolama hesabını eklemek istediğiniz Azure aboneliği.
   * Yeni depolama hesabı için kullanmak istediğiniz adı.
   * Bölge veya benzeşim grubunda (örneğin, Batı ABD veya Doğu Asya).
   * Bir tür çoğaltma gibi depolama hesabı için kullanmak istediğiniz yerel olarak yedekli.

   ![Bir Azure depolama hesabı oluşturma](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. **Oluştur**' u seçin.

Yeni depolama hesabı Çözüm Gezgini ' deki **depolama** listesinde görüntülenir.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak mevcut bir depolama hesabını eklemek için

1. Sunucu Gezgini ' de Azure **Storage** düğümünün kısayol menüsünü açın ve **dış depolama Ekle**' yi seçin.

    ![Var olan bir depolama hesabını ekleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. **Depolama hesabı oluştur** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Eklemek istediğiniz mevcut bir depolama hesabı adı.
   * Seçili depolama hesabı anahtarı. Bir depolama hesabı seçtiğinizde bu değer genellikle sizin için sağlanır. Visual Studio 'Nun depolama hesabı anahtarını anımsamasını istiyorsanız, **hesap anahtarını anımsa** onay kutusunu seçin.
   * HTTP, HTTPS veya özel bir uç noktası gibi bir depolama hesabına bağlanmak için kullanılacak protokolü. Özel uç noktalar hakkında daha fazla bilgi için bkz. [bağlantı dizelerini yapılandırma](https://msdn.microsoft.com/library/azure/ee758697.aspx).

### <a name="to-view-the-secondary-endpoints"></a>İkincil uç noktaları görüntülemek için

**Okuma Erişimli Coğrafi olarak yedekli** çoğaltma seçeneğini kullanarak bir depolama hesabı oluşturduysanız, hesap adının kısayol menüsünü açarak ve ardından **Özellikler**' i seçerek ikincil uç noktalarını görüntüleyebilirsiniz.

![Depolama ikincil uç noktaları](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Sunucu Gezgini'nden bir depolama hesabını kaldırmak için

Sunucu Gezgini, hesap adının kısayol menüsünü açın ve **Sil**' i seçin. 

Bir depolama hesabı silerseniz, bu hesap için kaydedilen tüm anahtar bilgilerini de kaldırılır.

Sunucu Gezgini'nden bir depolama hesabı silerseniz, depolama hesabınıza veya içerdiği herhangi bir veri etkilemez. Yalnızca Sunucu Gezgini'nden başvuruyu kaldırır. Bir depolama hesabını kalıcı olarak silmek için [Azure Portal](https://portal.azure.com/)kullanın.

## <a name="next-steps"></a>Sonraki adımlar

Azure depolama hizmetleri 'ni kullanma hakkında daha fazla bilgi için bkz. [Azure depolama 'Ya giriş](/azure/storage/common/storage-introduction).
