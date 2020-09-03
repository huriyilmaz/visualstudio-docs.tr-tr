---
title: 'İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- updating Ribbon controls
- Ribbon [Office development in Visual Studio], dynamic menu
- dynamic menus [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 425918ea32c14e6ba905d6b32864a2844d2b5a90
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255347"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme

Bu izlenecek yol, Şerit Office uygulamasına yüklendikten sonra Şeritteki denetimleri güncelleştirmek için şerit nesne modelinin nasıl kullanılacağını gösterir.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Örnek, Microsoft Office Outlook 'ta açılan bir kutuyu ve menüyü doldurmak için Northwind örnek veritabanından veri çeker. Bu denetimlerde seçtiğiniz öğeler **, ve gibi alanları otomatik olarak bir** e-posta **iletisine doldurur.**

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Yeni bir Outlook VSTO eklentisi projesi oluşturun.

- Özel bir Şerit grubu tasarlayın.

- Özel grubu yerleşik bir sekmeye ekleyin.

- Çalışma zamanında Şeritteki denetimleri güncelleştirin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Ön koşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklentisi projesi oluşturma

İlk olarak, bir Outlook VSTO eklenti projesi oluşturun.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Yeni bir Outlook VSTO eklentisi projesi oluşturmak için

1. İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **Ribbon_Update_At_Runtime**ADLı bir Outlook VSTO eklentisi projesi oluşturun.

2. **Yeni proje** iletişim kutusunda, **çözüm için dizin oluştur**' u seçin.

3. Projeyi varsayılan proje dizinine kaydedin.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Özel Şerit grubu tasarlama

Bir Kullanıcı yeni bir posta iletisi yazdığında bu örnek için şerit görüntülenir. Şerit için özel bir grup oluşturmak için, önce projenize bir şerit öğesi ekleyin ve ardından grubu Şerit tasarımcısında tasarlayın. Bu özel grup, bir veritabanından adları ve sıra geçmişlerini çekerek müşterilere yönelik izleme e-posta iletileri oluşturmanıza yardımcı olur.

### <a name="to-design-a-custom-group"></a>Özel bir grup tasarlamak için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin.

3. Yeni şerit 'in adını **CustomerRibbon**olarak değiştirin ve **Ekle**' ye tıklayın.

     *CustomerRibbon.cs* veya *CustomerRibbon. vb* dosyası Şerit Tasarımcısı 'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit Tasarımcısına tıklayarak seçin.

5. **Özellikler** penceresinde, **RibbonType** özelliğinin yanındaki açılan oka tıklayın ve ardından **Microsoft. Outlook. mail. Compose**' a tıklayın.

     Bu, Kullanıcı Outlook 'ta yeni bir posta iletisi yazdığında şeridin görünmesini sağlar.

6. Şerit tasarımcısında, seçmek için **grup1** ' e tıklayın.

7. **Özellikler** penceresinde, **etiketi** **müşteri satın alımları**olarak ayarlayın.

8. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden **Müşteri Harcamaları** grubuna bir **açılan kutu** sürükleyin.

9. Seçmek için **ComboBox1** öğesine tıklayın.

10. **Özellikler** penceresinde, **etiketi** **müşterilere**ayarlayın.

11. **Araç kutusunun** **Office Şerit denetimleri** sekmesinden bir **menüyü** **Müşteri satınalmaları** grubuna sürükleyin.

12. **Özellikler** penceresinde **etiket** ' i **satın alınan ürün**olarak ayarlayın.

13. **Dynamic** **değerini true**olarak ayarlayın.

     Bu, Şerit Office uygulamasına yüklendikten sonra çalışma zamanında menüdeki denetimleri eklemenize ve kaldırmanıza olanak sağlar.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Özel grubu yerleşik bir sekmeye ekleme

Yerleşik sekme, zaten bir Outlook Gezgini veya Inspector şeridinde bulunan bir sekmedir. Bu yordamda, özel grubu yerleşik bir sekmeye ekleyecek ve sonra sekmede özel grubun konumunu belirtmelisiniz.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Özel grubu yerleşik bir sekmeye eklemek için

1. **TabAddins (yerleşik)** sekmesine tıklayarak seçin.

2. **Özellikler** penceresinde **ControlID** özelliğini genişletin ve ardından **OfficeId** 'yi **TabNewMailMessage**olarak ayarlayın.

     Bu, **müşteri satın alımları** grubunu yeni bir posta iletisinde görünen şeridin **iletiler** sekmesine ekler.

3. **Müşteri satın alımları** grubuna tıklayarak seçin.

4. **Özellikler** penceresinde, **konum** özelliğini genişletin, **PositionType** özelliğinin yanındaki açılan oka tıklayın ve ardından **BeforeOfficeId**' ye tıklayın.

5. **OfficeId** özelliğini **GroupClipboard**olarak ayarlayın.

     Bu, **iletiler** sekmesinin **Pano** grubundan önce **müşterinin satın** alma grubunu konumlandırır.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' ye tıklayın.

     Bu, **veri kaynağı Yapılandırma Sihirbazı 'nı**başlatır.

2. **Veritabanı**' nı seçin ve ardından **İleri**' ye tıklayın.

3. **Veri kümesi**' ni seçin ve ardından **İleri**' ye tıklayın.

4. Northwind örnek Microsoft SQL Server Compact 4,0 veritabanına yönelik bir veri bağlantısı seçin veya **Yeni bağlantı** düğmesini kullanarak yeni bir bağlantı ekleyin.

5. Bir bağlantı seçildikten veya oluşturulduktan sonra **İleri**' ye tıklayın.

6. Bağlantı dizesini kaydetmek için **İleri** ' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar**' ı genişletin.

8. Aşağıdaki tabloların yanındaki onay kutusunu işaretleyin:

    1. **Müşteriler**

    2. **Sipariş Ayrıntıları**

    3. **Siparişler**

    4. **Ürünler**

9. **Son**'a tıklayın.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Çalışma zamanında özel gruptaki denetimleri Güncelleştir

Aşağıdaki görevleri gerçekleştirmek için şerit nesne modelini kullanın:

- Müşteri adlarını **müşteriler** Birleşik giriş kutusuna ekleyin.

- Satış siparişlerini ve satılan ürünleri temsil eden **ürünler satın alınan** menüye menü ve düğme denetimleri ekleyin.

- **Müşteriler** Birleşik giriş kutusu ve **satın alınan ürünler** menüsündeki verileri kullanarak yeni posta Iletilerinin ' e, konu ve gövde alanlarını doldurun.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Şerit nesne modelini kullanarak özel gruptaki denetimleri güncelleştirmek için

1. **Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, **System. Data. LINQ** derlemesini seçin ve ardından **Tamam**' a tıklayın.

    Bu derleme, dil ile tümleşik sorguları (LINQ) kullanmak için sınıflar içerir. Özel gruptaki denetimleri Northwind veritabanındaki verilerle doldurmak için LINQ kullanacaksınız.

3. **Çözüm Gezgini**' de, seçmek için **CustomerRibbon.cs** veya **CustomerRibbon. vb** ' ye tıklayın.

4. **Görünüm** menüsünde **kod**' a tıklayın.

    Şerit kod dosyası kod düzenleyicisinde açılır.

5. Aşağıdaki deyimlerini Şerit kod dosyasının en üstüne ekleyin. Bu deyimler, LINQ ad alanlarına ve Outlook birincil birlikte çalışma derlemesi (PIA) ad alanına kolay erişim sağlar.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]

6. Aşağıdaki kodu sınıfının içine ekleyin `CustomerRibbon` . Bu kod, Northwind veritabanının Müşteri, siparişler, sipariş ayrıntıları ve ürün tablolarından bilgi depolamak için kullanacağınız veri tablosu ve tablo bağdaştırıcılarını bildirir.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]

7. Aşağıdaki kod bloğunu `CustomerRibbon` sınıfına ekleyin. Bu kod, çalışma zamanında Şerit için denetimler oluşturan üç yardımcı yöntem ekler.

    [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
    [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]

8. `CustomerRibbon_Load`Olay işleyicisi yöntemini aşağıdaki kodla değiştirin. Bu kod, aşağıdaki görevleri gerçekleştirmek için bir LINQ sorgusu kullanır:

   - Northwind veritabanındaki 20 müşterinin KIMLIĞINI ve adını kullanarak **müşteriler** Birleşik giriş kutusunu doldurun.

   - `PopulateSalesOrderInfo`Yardımcı yöntemini çağırır. Bu yöntem, **ProductsPurchased** menüsünü Şu anda seçili müşteriyle ilgili satış siparişi numaralarıyla güncelleştirir.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]

9. Sınıfına aşağıdaki kodu ekleyin `CustomerRibbon` . Bu kod, aşağıdaki görevleri gerçekleştirmek için LINQ sorgularını kullanır:

   - Seçili müşteriyle ilgili her satış siparişi için **ProductsPurchased** menüsüne bir alt menü ekler.

   - Satış siparişiyle ilgili ürünlerin her alt menüsüne düğme ekler.

   - Her düğmeye olay işleyicileri ekler.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]

10. **Çözüm Gezgini**, Şerit kod dosyasına çift tıklayın.

     Şerit Tasarımcısı açılır.

11. Şerit tasarımcısında **müşteriler** Birleşik giriş kutusuna çift tıklayın.

     Şerit kod dosyası kod düzenleyicisinde açılır ve `ComboBox1_TextChanged` olay işleyicisi görünür.

12. `ComboBox1_TextChanged`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

    - `PopulateSalesOrderInfo`Yardımcı yöntemini çağırır. Bu yöntem, **satın alınan ürünler** menüsünü Seçili müşteriyle ilgili satış siparişleriyle güncelleştirir.

    - `PopulateMailItem`Yardımcı yöntemini çağırır ve seçilen müşteri adı olan geçerli metinde geçirir. Bu yöntem, yeni posta iletilerinin, konu ve gövde alanlarını doldurur.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]

13. Aşağıdaki `Click` olay işleyicisini `CustomerRibbon` sınıfına ekleyin. Bu kod, seçilen ürünlerin adını yeni posta iletilerinin gövde alanına ekler.

     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]

14. Sınıfına aşağıdaki kodu ekleyin `CustomerRibbon` . Bu kod aşağıdaki görevleri gerçekleştirir:

    - Şu anda seçili olan müşterinin e-posta adresini kullanarak yeni posta iletilerinin satırına doldurur.

    - Yeni posta iletilerinin konu ve gövde alanlarına metin ekler.

      [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
      [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]

## <a name="test-the-controls-in-the-custom-group"></a>Özel gruptaki denetimleri test etme

Outlook 'ta yeni bir posta formu açtığınızda, şeridin **iletiler** sekmesinde **müşteri satın alımları** adlı özel bir grup görüntülenir.

Bir müşteri takip e-posta iletisi oluşturmak için bir müşteri seçin ve müşteri tarafından satın alınan ürünleri seçin. **Müşteri satınalmaları** grubundaki denetimler, Northwind veritabanındaki verilerle çalışma zamanında güncelleştirilir.

### <a name="to-test-the-controls-in-the-custom-group"></a>Özel gruptaki denetimleri test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

     Outlook başlatılır.

2. Outlook 'ta, **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **posta iletisi**' ne tıklayın.

     Aşağıdaki eylemler gerçekleşir:

    - Yeni bir posta iletisi Denetçisi penceresi görüntülenir.

    - Şeridin **ileti** sekmesinde, **müşteri satın alımları** grubu **Pano** grubundan önce görüntülenir.

    - Gruptaki **müşteriler** açılan kutusu, Northwind veritabanındaki müşterilerin adlarıyla güncelleştirilir.

3. Şeridin **ileti** sekmesinde, **Müşteri satınalmaları** grubunda, **müşteriler** Birleşik giriş kutusundan bir müşteri seçin.

     Aşağıdaki eylemler gerçekleşir:

    - **Satın alınan ürünler** menüsü, seçilen müşteriye ait her satış siparişini gösterecek şekilde güncelleştirilir.

    - Her satış siparişi alt menüsü, söz konusu sırada satın alınan ürünleri gösterecek şekilde güncelleştirilir.

    - Seçilen müşterinin e-posta adresi posta iletisinin **to** satırına eklenir ve posta iletisinin konusu ve gövdesi metinle doldurulur.

4. **Ürünler satın** alma menüsü ' ne tıklayın, herhangi bir satış siparişi üzerine gelin ve ardından satış siparişinden bir ürüne tıklayın.

     Ürün adı e-posta iletisinin gövdesine eklenir.

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki konulardan Office Kullanıcı arabirimini özelleştirme hakkında daha fazla bilgi edinebilirsiniz:

- Herhangi bir belge düzeyi özelleştirmesine bağlam tabanlı kullanıcı arabirimi ekleyin. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

- Bir standart veya özel Microsoft Office Outlook formunu genişletin. Daha fazla bilgi için bkz. [Izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Outlook 'a özel bir görev bölmesi ekleyin. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Dil ile Tümleşik Sorgu (LINQ)](/dotnet/csharp/linq/index)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
- [Outlook için şerit özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Nasıl yapılır: Şerit Tasarımcısından Şerit XML 'ine şerit aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)