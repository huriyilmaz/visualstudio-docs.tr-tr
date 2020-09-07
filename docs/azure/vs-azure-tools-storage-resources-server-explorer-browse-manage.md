---
title: Sunucu Gezgini kullanarak depolama kaynaklarına gözatıp yönetin | Microsoft Docs
description: Sunucu Gezgini kullanarak depolama kaynaklarına göz atma ve bunları yönetme
author: ghogen
manager: jillfra
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 8702b9814214a902a644cc5854250b600c301caa
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508450"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Sunucu Gezgini'ni kullanarak depolama kaynaklarına göz atma ve bu kaynakları yönetme

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Genel Bakış

Microsoft Visual Studio için Azure Araçları 'nı yüklediyseniz, Azure için depolama hesaplarınızdan blob, kuyruk ve tablo verilerini görüntüleyebilirsiniz. Sunucu Gezgini 'de Azure **depolama** düğümü, yerel depolama öykünücü hesabınızdaki ve diğer Azure depolama hesaplarınızdaki verileri gösterir.

Visual Studio 'da Sunucu Gezgini görüntülemek için, menü çubuğunda, Sunucu Gezgini **görüntüle**' yi seçin  >  **Server Explorer**. **Depolama** düğümü, her bir Azure aboneliğinde veya bağlı olduğunuz sertifikada bulunan tüm depolama hesaplarını gösterir. Depolama Hesabınız görünmezse, [Bu makalenin ilerleyen kısımlarındaki](#add-storage-accounts-by-using-server-explorer)yönergeleri izleyerek ekleyebilirsiniz.

Azure SDK 2,7 ' den başlayarak, Azure kaynaklarınızı görüntülemek ve yönetmek için bulut Gezgini 'ni de kullanabilirsiniz. Daha fazla bilgi için bkz. [Cloud Explorer Ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md).

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visual Studio 'da depolama kaynaklarını görüntüleme ve yönetme

Sunucu Gezgini, depolama öykünücü hesabınızdaki Bloblar, kuyruklar ve tablolar listesini otomatik olarak gösterir. Depolama öykünücüsü hesabı, **depolama** düğümü altında, **geliştirme** düğümü olarak Sunucu Gezgini listelenir.

Depolama öykünücüsü hesabının kaynaklarını görmek için **geliştirme** düğümünü genişletin. **Geliştirme** düğümünü genişlettiğinizde depolama öykünücüsü başlatılmamışsa, otomatik olarak başlatılır. Bu işlem birkaç saniye sürebilir. Depolama öykünücüsü başladığında Visual Studio 'nun diğer alanlarında çalışmaya devam edebilirsiniz.

Bir depolama hesabındaki kaynakları görüntülemek için, **BLOB**, **kuyruk**ve **tablo** düğümlerini gördüğünüz Sunucu Gezgini depolama hesabının düğümünü genişletin.

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
* Karşıya bir dosya yükleyin.
* Bir blobu silin. (Bir blob kapsayıcısından bir dosyayı silme, temeldeki dosyayı silmez. Yalnızca blob kapsayıcısından kaldırılır.)
* Blob açın.
* Bir blobu yerel bilgisayara kaydedin.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Blob kapsayıcısında klasör veya alt klasör oluşturmak için

1. **Cloud Explorer**'da blob kapsayıcısını seçin. Kapsayıcı penceresinde, **blobu karşıya yükle** düğmesini seçin.

1. Karşıya **yeni dosya yükle** iletişim kutusunda, karşıya yüklemek istediğiniz dosyayı belirtmek Için, **tarayıcı** düğmesini seçin ve ardından **klasöre (isteğe bağlı)** bir klasör adı girin.

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

Blobları karşıya yüklemek için, kapsayıcı blob kapsayıcısı görünümünde görüntülenmek üzere açıkken **blobu karşıya yükle** düğmesini seçin.

Karşıya yüklenecek bir veya daha fazla dosya seçebilir ve herhangi bir türde dosya yükleyebilirsiniz. **Azure etkinlik günlüğü** penceresinde karşıya yükleme işleminin ilerleme durumu gösterilir. Blob verileriyle çalışma hakkında daha fazla bilgi için bkz. [.net 'Te Azure Blob depolamayı kullanma](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

### <a name="to-view-logs-transferred-to-blobs"></a>Bloblara aktarılan günlükleri görüntülemek için

Azure uygulamanızdaki verileri günlüğe kaydetmek için Azure Tanılama kullanıyorsanız ve günlükleri depolama hesabınıza aktardıysanız, Azure 'un bu Günlükler için oluşturduğu kapsayıcıları görürsünüz. Bu günlükleri Sunucu Gezgini ' de görüntülemek, özellikle Azure 'a dağıtılırsa, uygulamanızla ilgili sorunları belirlemenin kolay bir yoludur.

Azure Tanılama hakkında daha fazla bilgi için bkz. [Azure Tanılama kullanarak günlük verilerini toplama](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="to-get-the-url-for-a-blob"></a>Bir Blobun URL 'sini almak için

Blobun kısayol menüsünü açın ve **URL 'Yi Kopyala**' yı seçin.

### <a name="to-edit-a-blob"></a>Bir blobu düzenlemek için

Blobu seçin ve ardından **blobu aç** düğmesini seçin.

Dosya geçici bir konuma indirilir ve yerel bilgisayarda açılır. Değişiklik yaptıktan sonra blobu yeniden yükleyin.

## <a name="work-with-queue-resources"></a>Kuyruk kaynaklarıyla çalışma

Depolama Hizmetleri kuyrukları bir Azure depolama hesabında barındırılır. Bunları, bulut hizmeti rollerinizin bir ileti geçirme mekanizmasıyla birbirleriyle ve diğer hizmetlerle iletişim kurmasına izin vermek için kullanabilirsiniz. Bir bulut hizmeti üzerinden ve dış istemciler için bir Web hizmeti üzerinden sıraya programlı bir şekilde erişebilirsiniz. Ayrıca, Visual Studio 'da Sunucu Gezgini kullanarak sıraya doğrudan erişebilirsiniz.

Kuyrukları kullanan bir bulut hizmeti geliştirirken, Visual Studio 'Yu kullanarak kuyruklar oluşturabilir ve kodunuzu geliştirip test ederken bu sıralara etkileşimli olarak çalışabilirsiniz.

Sunucu Gezgini, kuyrukları bir depolama hesabında görüntüleyebilir, kuyruklar oluşturup silebilir, iletilerini görüntülemek için bir kuyruk açabilir ve bir kuyruğa ileti ekleyebilirsiniz. Görüntüleme için bir kuyruğu açtığınızda, tek tek iletileri görüntüleyebilir ve sol üst köşedeki düğmeleri kullanarak sırada aşağıdaki eylemleri gerçekleştirebilirsiniz:

* Kuyruğun görünümünü yenileyin.
* Kuyruğa bir ileti ekleyin.
* En üstteki ileti sıradan çıkar.
* Tüm sırayı Temizle.

Aşağıdaki görüntüde iki ileti içeren bir sıra gösterilmektedir:

![Kuyruğu görüntüleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Depolama Hizmetleri kuyrukları hakkında daha fazla bilgi için bkz. [.NET kullanarak Azure kuyruk depolama ile çalışmaya başlama](/azure/storage/queues/storage-dotnet-how-to-use-queues). Depolama Hizmetleri kuyrukları Web hizmeti hakkında daha fazla bilgi için bkz. [kuyruk hizmeti kavramları](/rest/api/storageservices/Queue-Service-Concepts). Visual Studio kullanarak bir depolama hizmetleri kuyruğuna ileti gönderme hakkında daha fazla bilgi için bkz. [Depolama Hizmetleri kuyruğuna Ileti gönderme](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Depolama Hizmetleri kuyrukları Azure Service Bus kuyruklarından farklıdır. Service Bus kuyrukları hakkında daha fazla bilgi için bkz. [Service Bus kuyruklar, konular ve abonelikler](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Tablo kaynaklarıyla çalışma

Azure Tablo depolama, büyük miktarlarda yapısal veriyi depolar. Hizmet, Azure bulutu içinden ve dışından kimliği doğrulanmış çağrıları kabul eden bir NoSQL veri deposu olur. Azure tabloları, yapılandırılmış ve ilişkisel olmayan verilerin depolanması için idealdir.

### <a name="to-create-a-table"></a>Tablo oluşturmak için

1. **Cloud Explorer**'da depolama hesabının **Tablolar** düğümünü seçin ve ardından **tablo oluştur**' u seçin.
1. **Tablo oluştur** iletişim kutusunda tablo için bir ad girin.

### <a name="to-view-table-data"></a>Tablo verilerini görüntülemek için

1. **Cloud Explorer**'da **Azure** düğümünü açın ve **depolama** düğümünü açın.
1. İlgilendiğiniz depolama hesabı düğümünü açın ve ardından depolama hesabı için tabloların listesini görmek üzere **Tables** düğümünü açın.
1. Bir tablo için kısayol menüsünü açın ve ardından **tabloyu görüntüle**' yi seçin.

    ![Çözüm Gezgini bir Azure tablosu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

Tablo varlıklara (satırlarda gösterilen) ve özelliklerde (sütunlarda gösterilir) göre düzenlenir. Örneğin, bir sonraki çizimde Tablo Tasarımcısı listelenen varlıklar gösterilmektedir.

### <a name="to-edit-table-data"></a>Tablo verilerini düzenlemek için

**Tablo Tasarımcısı**, bir varlık (tek bir satır) veya bir Özellik (tek bir hücre) için kısayol menüsünü açın ve ardından **Düzenle**' yi seçin.

![Tablo varlığı ekleme veya düzenleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

Tek bir tablodaki varlıkların aynı özellik kümesine (sütun) sahip olması gerekmez. Tablo verilerini görüntüleme ve düzenlemeyle ilgili aşağıdaki kısıtlamaları göz önünde bulundurun:

* İkili verileri görüntüleyemez veya düzenleyemezsiniz ( `type byte[]` ), ancak bir tabloda saklayabilirsiniz.
* Azure Tablo Depolaması bu işlemi desteklemediğinden **partitionkey** veya **rowkey** değerlerini düzenleyemezsiniz.
* **Zaman damgası**adlı bir özellik oluşturamazsınız. Azure depolama hizmetleri, bu adı taşıyan bir özellik kullanır.
* Bir **Tarih saat** değeri girerseniz, bilgisayarınızın bölge ve dil ayarlarına uygun bir biçimi izlemeniz gerekir (ÖRNEĞIN, aa/gg/yyyy HH: mm: SS [har | PM] ABD Ingilizcesi için).

### <a name="to-add-entities"></a>Varlık eklemek için

1. **Tablo Tasarımcısı** **varlık Ekle** düğmesini seçin.

    ![Varlık Ekle düğmesi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. **Varlık Ekle** iletişim kutusunda, **Partitionkey** ve **rowkey** özelliklerinin değerlerini girin.

    ![Varlık Ekle iletişim kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    Değerleri dikkatle girin. Varlığı silip yeniden eklemediğiniz takdirde iletişim kutusunu kapattıktan sonra bu dosyaları değiştiremezsiniz.

### <a name="to-filter-entities"></a>Varlıkları filtrelemek için

Sorgu oluşturucuyu kullanıyorsanız bir tabloda görünen varlıkların kümesini özelleştirebilirsiniz.

1. Sorgu oluşturucuyu açmak için, görüntülemek üzere bir tablo açın.
1. Tablo görünümü araç çubuğunda **Sorgu Tasarımcısı** düğmesini seçin.

    **Sorgu Tasarımcısı** iletişim kutusu görüntülenir. Aşağıdaki çizimde sorgu oluşturucuda oluşturulan bir sorgu gösterilmektedir.

    ![Sorgu Oluşturucu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. Sorguyu oluşturmayı bitirdiğinizde iletişim kutusunu kapatın. Sorgunun ortaya çıkan metin formu, bir WCF Veri Hizmetleri filtresi olarak bir metin kutusunda görünür.
1. Sorguyu çalıştırmak için yeşil üçgen simgesini seçin.

Filtre metin kutusuna doğrudan bir WCF Veri Hizmetleri filtre dizesi girerseniz, Tablo Tasarımcısı görüntülenen varlık verilerini de filtreleyebilirsiniz. Bu tür bir dize bir SQL WHERE yan tümcesine benzer ancak sunucuya HTTP isteği olarak gönderilir. Filtre dizeleri oluşturma hakkında daha fazla bilgi için bkz. [Tablo Tasarımcısı için filtre dizeleri](vs-azure-tools-table-designer-construct-filter-strings.md)oluşturma.

Aşağıdaki çizimde geçerli bir filtre dizesi örneği gösterilmektedir:

![Filtre dizesi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Depolama verilerini yenile

Sunucu Gezgini bir depolama hesabına bağlanıp verileri aldığında, işlemin tamamlanması birkaç dakika sürebilir. Sunucu Gezgini bağlanamıyorsa, işlem zaman aşımına uğrar. Veriler alınırken, Visual Studio 'nun diğer bölümlerinde çalışmaya devam edebilirsiniz. Çok uzun sürüyorsa işlemi iptal etmek için Sunucu Gezgini araç çubuğundaki **yenilemeyi durdur** düğmesini seçin.

### <a name="to-refresh-blob-container-data"></a>Blob kapsayıcı verilerini yenilemek için

* **Depolama**altındaki **Bloblar** düğümünü seçin ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.
* Görüntülenen blob 'ların listesini yenilemek için **Yürüt** düğmesini seçin.

### <a name="to-refresh-table-data"></a>Tablo verilerini yenilemek için

* **Depolama**altındaki **Tablolar** düğümünü ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.
* **Tablo Tasarımcısı**' de görüntülenen varlıkların listesini yenilemek Için Tablo Tasarımcısı **Çalıştır** düğmesini seçin.

### <a name="to-refresh-queue-data"></a>Sıra verilerini yenilemek için

**Depolama**altındaki **Kuyruklar** düğümünü seçin ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Bir depolama hesabındaki tüm öğeleri yenilemek için

Hesap adı ' nı seçin ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Sunucu Gezgini kullanarak depolama hesapları ekleme

Sunucu Gezgini kullanarak depolama hesapları eklemenin iki yolu vardır. Azure aboneliğinizde bir depolama hesabı oluşturabilir veya var olan bir depolama hesabını iliştirebilirsiniz.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak bir depolama hesabı oluşturmak için

1. Sunucu Gezgini ' de, **depolama** düğümü için kısayol menüsünü açın ve **depolama hesabı oluştur**' u seçin.

1. **Depolama hesabı oluştur** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Depolama hesabını eklemek istediğiniz Azure aboneliği.
   * Yeni depolama hesabı için kullanmak istediğiniz ad.
   * Bölge veya benzeşim grubu (Batı ABD veya Doğu Asya gibi).
   * Depolama hesabı için kullanmak istediğiniz çoğaltma türü (yerel olarak yedekli).

   ![Azure depolama hesabı oluşturma](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. **Oluştur**’u seçin.

Yeni depolama hesabı Çözüm Gezgini ' deki **depolama** listesinde görüntülenir.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak var olan bir depolama hesabı eklemek için

1. Sunucu Gezgini ' de Azure **Storage** düğümünün kısayol menüsünü açın ve **dış depolama Ekle**' yi seçin.

    ![Var olan bir depolama hesabı ekleniyor](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. **Depolama hesabı oluştur** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Eklemek istediğiniz mevcut depolama hesabının adı.
   * Seçilen depolama hesabı için anahtar. Bu değer genellikle bir depolama hesabı seçtiğinizde sizin için sağlanır. Visual Studio 'Nun depolama hesabı anahtarını anımsamasını istiyorsanız, **hesap anahtarını anımsa** onay kutusunu seçin.
   * HTTP, HTTPS veya özel bir uç nokta gibi depolama hesabına bağlanmak için kullanılacak protokol. Özel uç noktalar hakkında daha fazla bilgi için bkz. [bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string).

### <a name="to-view-the-secondary-endpoints"></a>İkincil uç noktaları görüntülemek için

**Okuma Erişimli Coğrafi olarak yedekli** çoğaltma seçeneğini kullanarak bir depolama hesabı oluşturduysanız, hesap adının kısayol menüsünü açarak ve ardından **Özellikler**' i seçerek ikincil uç noktalarını görüntüleyebilirsiniz.

![Depolama ikincil uç noktaları](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Bir depolama hesabını Sunucu Gezgini kaldırmak için

Sunucu Gezgini, hesap adının kısayol menüsünü açın ve **Sil**' i seçin.

Bir depolama hesabını silerseniz, bu hesap için kaydedilen anahtar bilgileri de kaldırılır.

Bir depolama hesabını Sunucu Gezgini silerseniz, depolama hesabınızı veya içerdiği verileri etkilemez. Yalnızca Sunucu Gezgini başvuruyu kaldırır. Bir depolama hesabını kalıcı olarak silmek için [Azure Portal](https://portal.azure.com/)kullanın.

## <a name="next-steps"></a>Sonraki adımlar

Azure depolama hizmetleri 'ni kullanma hakkında daha fazla bilgi edinmek için bkz. [Azure Storage hizmetlerine erişme](/azure/storage/common/storage-introduction).
