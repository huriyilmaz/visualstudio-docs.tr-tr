---
title: Depolama kaynaklarına göz atma ve kaynakları yönetme
description: Sunucu Gezgini kullanarak depolama kaynaklarına göz atma ve kaynakları yönetme
ms.custom: SEO-VS-2020
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 18726b1fa7f42b46cd309cfd4edef289d9469d39
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633014"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>Sunucu Gezgini'ni kullanarak depolama kaynaklarına göz atma ve bu kaynakları yönetme

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>Genel Bakış

Microsoft Visual Studio için Azure Araçları'Microsoft Visual Studio, Azure için depolama hesaplarından blob, kuyruk ve tablo verilerini görüntüebilirsiniz. Azure **Depolama** düğümü Sunucu Gezgini yerel depolama öykünücüsü hesabınızla diğer Azure depolama hesaplarınızı gösteren veriler gösterir.

Veri Sunucu Gezgini görüntülemek Visual Studio menü çubuğunda Görünüm'Sunucu Gezgini.   >   Depolama  düğümü, bağlı olduğunu her Bir Azure aboneliği veya sertifikası altında var olan tüm depolama hesaplarını gösterir. Depolama hesabınız görünmüyorsa, bu makalenin devamlarında yer alan yönergeleri [izleyerek ekleyin.](#add-storage-accounts-by-using-server-explorer)

Azure SDK 2.7'den başlayarak, Azure kaynaklarınızı görüntülemek ve yönetmek için Bulut Gezgini'ni de kullanabilirsiniz. Daha fazla bilgi için [bkz. Cloud Explorer ile Azure kaynaklarını yönetme.](vs-azure-tools-resources-managing-with-cloud-explorer.md)

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>Visual Studio'de depolama kaynaklarını görüntüleme ve yönetme

Sunucu Gezgini depolama öykünücüsü hesapta blobların, kuyrukların ve tabloların listesini otomatik olarak gösterir. Depolama öykünücüsü hesabı, Sunucu Gezgini düğümü altında **Depolama** düğümü olarak **listelenir.**

Depolama öykünücüsü hesabının kaynaklarını görmek için Geliştirme **düğümünü** genişletin. Geliştirme düğümünü genişletilirken depolama öykünücüsü **başlatılamamışsa** otomatik olarak başlatılır. Bu işlem birkaç saniye sürebilir. Depolama öykünücüsü başlatılırken diğer Visual Studio alanlarda çalışmaya devam edersiniz.

Bir depolama hesabıdaki kaynakları görüntülemek için bloblar, kuyruklar ve tablolar Sunucu Gezgini depolama hesabının **düğümünü** genişletin.

## <a name="work-with-blob-resources"></a>Blob kaynaklarıyla çalışma

**Bloblar düğümü,** seçili depolama hesabı için kapsayıcıların listesini görüntüler. Blob kapsayıcıları blob dosyaları içerir ve bu blobları klasörler ve alt klasörler olarak düzenleyebilirsiniz. Daha fazla bilgi için [bkz. .NET'den Blob depolama kullanma.](/azure/storage/blobs/storage-dotnet-how-to-use-blobs)

### <a name="to-create-a-blob-container"></a>Blob kapsayıcısı oluşturmak için

1. **Bloblar** düğümünün kısayol menüsünü açın ve Blob Kapsayıcısı **Oluştur'a tıklayın.**
1. Blob **Kapsayıcısı Oluştur** iletişim kutusuna yeni kapsayıcının adını girin.
1. Klavyenizde Enter'ı seçin veya ad alanı dışına tıklar veya dokunarak blob kapsayıcıyı kaydedebilirsiniz.

   > [!NOTE]
   > Blob kapsayıcısı adı bir sayı (0-9) veya küçük harfle (a-z) başlasın.

### <a name="to-delete-a-blob-container"></a>Blob kapsayıcısı silmek için

Kaldırmak istediğiniz blob kapsayıcısı için kısayol menüsünü açın ve Sil'i **seçin.**

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Blob kapsayıcısı içinde öğelerin listesini görüntülemek için

Listede blob kapsayıcısı adının kısayol menüsünü açın ve Aç'ı **seçin.**

Bir blob kapsayıcının içeriğini görüntülendiğinde, blob kapsayıcısı görünümü olarak bilinen bir sekmede görünür.

![Blob kapsayıcısı görünümü](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Blob kapsayıcı görünümünün sağ üst köşesindeki düğmeleri kullanarak bloblarda aşağıdaki işlemleri gerçekleştirebilirsiniz:

* Bir filtre değeri girin ve bunu uygulama.
* Kapsayıcıda blob listesini yenileyin.
* Upload bir dosya seçin.
* Bir blobu silin. (Blob kapsayıcıdan dosya silmek, temel alınan dosyayı silemez. Yalnızca blob kapsayıcıdan kaldırır.)
* Bir blob açın.
* Bir blobu yerel bilgisayara kaydedin.

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Blob kapsayıcısı içinde klasör veya alt klasör oluşturmak için

1. Cloud Explorer'da blob **kapsayıcısını seçin.** Kapsayıcı penceresinde Blob'a **Upload seçin.**

1. Yeni **Upload** Ekle iletişim kutusunda, karşıya  yüklemek istediğiniz dosyayı belirtmek için Gözat düğmesini seçin ve ardından Klasör **(isteğe bağlı)** kutusuna bir klasör adı girin.

   ![Blob klasörüne dosya yükleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   Aynı adımı kullanarak kapsayıcı klasörlerine alt klasörler ebilirsiniz. Bir klasör adı belirtmezseniz, dosya blob kapsayıcının en üst düzeyine karşıya yükler. Dosya, kapsayıcıda belirtilen klasörde görünür.

   ![Blob kapsayıcıya eklenen klasör](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. Klasörün içeriğini görmek için klasöre çift tıklayın veya Enter tarak seçin. Kapsayıcının klasöründeyken Üst Dizini Aç **(ok)** düğmesini seçerek kapsayıcının köküne dönebilirsiniz.

### <a name="to-delete-a-container-folder"></a>Kapsayıcı klasörünü silmek için

Klasördeki tüm dosyaları silin.

Blob kapsayıcılarında klasörler sanal klasörler olduğundan boş bir klasör oluşturasınız. Ayrıca, bir klasörü silemez ve dosya içeriğini silemezsiniz, ancak klasörün kendisini silmek için klasörün içeriğinin tamamını silmeniz gerekir.

### <a name="to-filter-blobs-in-a-container"></a>Kapsayıcıda blobları filtrelemek için

Ortak bir ön ek belirterek görüntülenen blobları filtrelebilirsiniz.

Örneğin, filtre metin kutusuna **hello** ön eki girer ve ardından Yürüt **(** **!**) düğmesini seçersiniz, yalnızca "hello" ile başlayan bloblar görüntülenir.

![Filtre metin kutusu](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

Filtre metin kutusu büyük/büyük harfe duyarlıdır ve joker karakterlerle filtrelemeyi desteklemez. Bloblar yalnızca ön eke göre filtrelenmiş olabilir. Sanal hiyerarşide blobları düzenlemek için sınırlayıcı kullanıyorsanız ön ek bir sınırlayıcı içerebilir. Örneğin, "HelloFabric/" öneki üzerinde filtrelemek, bu dizeyle başlayan tüm blobları döndürür.

### <a name="to-download-blob-data"></a>Blob verilerini indirmek için

Cloud **Explorer'da** aşağıdaki yöntemlerden birini kullanın:

* Bir veya daha fazla blob için kısayol menüsünü açın ve Aç'ı **seçin.**
* Blob adını ve ardından Aç **düğmesini** seçin.
* Blob adına çift tıklayın.

Blob indirmenin ilerleme durumu **Azure** Etkinlik Günlüğü penceresinde görüntülenir.

Blob, bu dosya türü için varsayılan düzenleyicide açılır. İşletim sistemi dosya türünü tanırsa, dosya yerel olarak yüklenmiş bir uygulamada açılır. Aksi takdirde, blob'un dosya türüne uygun bir uygulama seçmeniz istenir. Blob indirken oluşturulan yerel dosya salt okunur olarak işaretlenir.

Blob verileri yerel olarak önbelleğe alınarak Blob'un Azure Blob depolama alanında son değiştirme zamanıyla ilgili olarak denetlenir. Blob son indirildikten sonra güncelleştirilmişse yeniden indirilir. Aksi takdirde blob yerel diskten yüklenir.

Varsayılan olarak, bir blob geçici bir dizine indirilir. Blobları belirli bir dizine indirmek için, seçili blob adlarının kısayol menüsünü açın ve Farklı **Kaydet'i seçin.** Bir blobu bu şekilde kaydeden blob dosyası açık olmaz ve yerel dosya okuma/yazma öznitelikleriyle oluşturulur.

### <a name="to-upload-blobs"></a>Blobları karşıya yüklemek için

Blobları karşıya yüklemek için, **Upload blob** kapsayıcı görünümünde görüntülemeye açık olduğunda Blobu Seç düğmesini seçin.

Karşıya yüklemek için bir veya daha fazla dosya seçebilir ve istediğiniz türde dosyaları karşıya yükleyebilirsiniz. **Azure Etkinlik Günlüğü penceresinde** karşıya yüklemenin ilerleme durumu gösterilir. Blob verileriyle çalışma hakkında daha fazla bilgi için [bkz. .NET'te Azure Blob depolamayı kullanma.](/azure/storage/blobs/storage-quickstart-blobs-dotnet)

### <a name="to-view-logs-transferred-to-blobs"></a>Bloblara aktarılan günlükleri görüntülemek için

Azure uygulamanıza Azure Tanılama verileri günlüğe kaydederken günlükleri depolama hesabınıza aktardıysanız, Azure'ın bu günlükler için oluşturduğu kapsayıcıları alırsınız. Bu günlükleri Sunucu Gezgini, özellikle de Azure'a dağıtılmışsa uygulamayla ilgili sorunları tanımlamanın kolay bir yolu olabilir.

Daha fazla bilgi Azure Tanılama için [bkz. Azure Tanılama Kullanarak Günlük Verileri Toplama.](/azure/cloud-services/cloud-services-dotnet-diagnostics)

### <a name="to-get-the-url-for-a-blob"></a>Blob url'sini almak için

Blobun kısayol menüsünü açın ve URL'yi **kopyala'yı seçin.**

### <a name="to-edit-a-blob"></a>Blobu düzenlemek için

Blobu ve ardından Blobu Aç **düğmesini** seçin.

Dosya geçici bir konuma indirilir ve yerel bilgisayarda açılır. Upload sonra blobu yeniden deneyin.

## <a name="work-with-queue-resources"></a>Kuyruk kaynaklarıyla çalışma

Depolama hizmetleri kuyrukları bir Azure depolama hesabında barındırıldı. Bulut hizmeti rollerinin birbirleriyle ve diğer hizmetlerle bir ileti geçirme mekanizmasıyla iletişim kurmasına izin vermek için bunları kullanabilirsiniz. Bir bulut hizmeti üzerinden ve dış istemciler için bir Web hizmeti üzerinden sıraya programlı bir şekilde erişebilirsiniz. Kuyruğa doğrudan Visual Studio Sunucu Gezgini kullanarak da erişebilirsiniz.

kuyrukları kullanan bir bulut hizmeti geliştirirken,, kodunuzu geliştirip test ederken, kuyruklar oluşturmak ve bunlarla etkileşimli olarak çalışmak için Visual Studio kullanmak isteyebilirsiniz.

Sunucu Gezgini, kuyrukları bir depolama hesabında görüntüleyebilir, kuyruklar oluşturup silebilir, iletilerini görüntülemek için bir kuyruk açabilir ve bir kuyruğa ileti ekleyebilirsiniz. Görüntüleme için bir kuyruğu açtığınızda, tek tek iletileri görüntüleyebilir ve sol üst köşedeki düğmeleri kullanarak sırada aşağıdaki eylemleri gerçekleştirebilirsiniz:

* Kuyruğun görünümünü yenileyin.
* Kuyruğa bir ileti ekleyin.
* En üstteki ileti sıradan çıkar.
* Tüm sırayı Temizle.

Aşağıdaki görüntüde iki ileti içeren bir sıra gösterilmektedir:

![Kuyruğu görüntüleme](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

Depolama Hizmetleri kuyrukları hakkında daha fazla bilgi için bkz. [.NET kullanarak Azure kuyruk depolama ile çalışmaya başlama](/azure/storage/queues/storage-dotnet-how-to-use-queues). Depolama Hizmetleri kuyrukları Web hizmeti hakkında daha fazla bilgi için bkz. [kuyruk hizmeti kavramları](/rest/api/storageservices/Queue-Service-Concepts). Visual Studio kullanarak bir depolama hizmetleri kuyruğuna ileti gönderme hakkında daha fazla bilgi için bkz. [bir Depolama hizmetleri kuyruğuna ileti gönderme](/azure/visual-studio/vs-storage-cloud-services-getting-started-queues).

> [!NOTE]
> Depolama services kuyrukları Azure Service Bus kuyruklarından farklıdır. Service Bus kuyrukları hakkında daha fazla bilgi için bkz. [Service Bus kuyruklar, konular ve abonelikler](/azure/service-bus-messaging/service-bus-queues-topics-subscriptions).

## <a name="work-with-table-resources"></a>Tablo kaynaklarıyla çalışma

Azure Tablo depolama, büyük miktarlarda yapısal veriyi depolar. Hizmet, Azure bulutu içinden ve dışından kimliği doğrulanmış çağrıları kabul eden bir NoSQL veri deposu olur. Azure tabloları, yapılandırılmış ve ilişkisel olmayan verilerin depolanması için idealdir.

### <a name="to-create-a-table"></a>Tablo oluşturmak için

1. **Cloud Explorer**'da depolama hesabının **Tablolar** düğümünü seçin ve ardından **tablo oluştur**' u seçin.
1. **Tablo oluştur** iletişim kutusunda tablo için bir ad girin.

### <a name="to-view-table-data"></a>Tablo verilerini görüntülemek için

1. **Cloud Explorer**'da **Azure** düğümünü açın ve **Depolama** düğümünü açın.
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
* **Zaman damgası** adlı bir özellik oluşturamazsınız. Azure depolama hizmetleri, bu adı taşıyan bir özellik kullanır.
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
1. Sorguyu oluşturmayı bitirdiğinizde iletişim kutusunu kapatın. sorgunun ortaya çıkan metin formu, bir WCF Veri Hizmetleri filtresi olarak bir metin kutusunda görünür.
1. Sorguyu çalıştırmak için yeşil üçgen simgesini seçin.

filtre metin kutusuna doğrudan bir WCF Veri Hizmetleri filtre dizesi girerseniz, Tablo Tasarımcısı görüntülenen varlık verilerini de filtreleyebilirsiniz. bu tür bir dize, bir SQL where yan tümcesine benzerdir ancak sunucuya HTTP isteği olarak gönderilir. Filtre dizeleri oluşturma hakkında daha fazla bilgi için bkz. [Tablo Tasarımcısı için filtre dizeleri](vs-azure-tools-table-designer-construct-filter-strings.md)oluşturma.

Aşağıdaki çizimde geçerli bir filtre dizesi örneği gösterilmektedir:

![Filtre dizesi](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>Depolama verilerini yenile

Sunucu Gezgini bir depolama hesabına bağlanıp verileri aldığında, işlemin tamamlanması birkaç dakika sürebilir. Sunucu Gezgini bağlanamıyorsa, işlem zaman aşımına uğrar. Veriler alınırken, Visual Studio diğer bölümlerinde çalışmaya devam edebilirsiniz. Çok uzun sürüyorsa işlemi iptal etmek için Sunucu Gezgini araç çubuğundaki **yenilemeyi durdur** düğmesini seçin.

### <a name="to-refresh-blob-container-data"></a>Blob kapsayıcı verilerini yenilemek için

* **Depolama** altındaki **bloblar** düğümünü seçin ve sonra Sunucu Gezgini araç çubuğunda **yenile** düğmesini seçin.
* Görüntülenen blob 'ların listesini yenilemek için **Yürüt** düğmesini seçin.

### <a name="to-refresh-table-data"></a>Tablo verilerini yenilemek için

* **Depolama** altındaki **tablolar** düğümünü seçin ve sonra Sunucu Gezgini araç çubuğunda **yenile** düğmesini seçin.
* **Tablo Tasarımcısı**' de görüntülenen varlıkların listesini yenilemek Için Tablo Tasarımcısı **Çalıştır** düğmesini seçin.

### <a name="to-refresh-queue-data"></a>Sıra verilerini yenilemek için

**Depolama** altındaki **kuyruklar** düğümünü seçin ve sonra Sunucu Gezgini araç çubuğunda **yenile** düğmesini seçin.

### <a name="to-refresh-all-items-in-a-storage-account"></a>Bir depolama hesabındaki tüm öğeleri yenilemek için

Hesap adı ' nı seçin ve ardından Sunucu Gezgini araç çubuğunda **Yenile** düğmesini seçin.

## <a name="add-storage-accounts-by-using-server-explorer"></a>Sunucu Gezgini kullanarak depolama hesapları ekleme

Sunucu Gezgini kullanarak depolama hesapları eklemenin iki yolu vardır. Azure aboneliğinizde bir depolama hesabı oluşturabilir veya var olan bir depolama hesabını iliştirebilirsiniz.

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak bir depolama hesabı oluşturmak için

1. Sunucu Gezgini ' de, **Depolama** düğümünün kısayol menüsünü açın ve **Depolama hesabı oluştur**' u seçin.

1. **Depolama hesabı oluştur** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Depolama hesabını eklemek istediğiniz Azure aboneliği.
   * Yeni depolama hesabı için kullanmak istediğiniz ad.
   * Bölge veya benzeşim grubu (Batı ABD veya Doğu Asya gibi).
   * Depolama hesabı için kullanmak istediğiniz çoğaltma türü (yerel olarak yedekli).

   ![Azure depolama hesabı oluşturma](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. **Oluştur**’u seçin.

yeni depolama hesabı, Çözüm Gezgini **Depolama** listesinde görünür.

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>Sunucu Gezgini kullanarak var olan bir depolama hesabı eklemek için

1. Sunucu Gezgini ' de Azure **Depolama** düğümünün kısayol menüsünü açın ve **dış Depolama ekle**' yi seçin.

    ![Var olan bir depolama hesabı ekleniyor](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. **Depolama hesabı oluştur** iletişim kutusunda aşağıdaki bilgileri seçin veya girin:

   * Eklemek istediğiniz mevcut depolama hesabının adı.
   * Seçilen depolama hesabı için anahtar. Bu değer genellikle bir depolama hesabı seçtiğinizde sizin için sağlanır. depolama hesabı anahtarını hatırlamak Visual Studio istiyorsanız, **hesap anahtarını anımsa** onay kutusunu seçin.
   * HTTP, HTTPS veya özel bir uç nokta gibi depolama hesabına bağlanmak için kullanılacak protokol. Özel uç noktalar hakkında daha fazla bilgi için bkz. [bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string).

### <a name="to-view-the-secondary-endpoints"></a>İkincil uç noktaları görüntülemek için

Okuma Erişimli Coğrafi Olarak  Yedekli çoğaltma seçeneğini kullanarak bir depolama hesabı oluşturduysanız, hesap adının kısayol menüsünü açarak ikincil uç noktalarını ekleyebilirsiniz ve ardından Özellikler'i **seçebilirsiniz.**

![Depolama uç noktaları yapılandırma](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>Depolama hesabını bir depolama hesabından Sunucu Gezgini

Bu Sunucu Gezgini hesap adı kısayol menüsünü açın ve Sil'i **seçin.**

Bir depolama hesabını silersiniz, bu hesap için kaydedilen tüm anahtar bilgileri de kaldırılır.

Bir depolama hesabını Sunucu Gezgini, depolama hesabınızı veya içerdiği verileri etkilemez. Bu işlem yalnızca başvurudan Sunucu Gezgini. Bir depolama hesabını kalıcı olarak silmek için [Azure portal.](https://portal.azure.com/)

## <a name="next-steps"></a>Sonraki adımlar

Azure depolama hizmetlerini kullanma hakkında daha fazla bilgi edinmek için [bkz. Azure Depolama Hizmetleri'ne erişme.](/azure/storage/common/storage-introduction)
