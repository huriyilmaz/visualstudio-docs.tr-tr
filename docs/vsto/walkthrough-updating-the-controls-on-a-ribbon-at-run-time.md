---
title: 'İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme'
description: şerit Office uygulamasına yüklendikten sonra şeritteki denetimleri güncelleştirmek için şerit nesne modelini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ee3fd72ef1ad75512b87d3fae61efa271c2773ba155663502bb5d489b243b0ee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408194"
---
# <a name="walkthrough-update-the-controls-on-a-ribbon-at-run-time"></a>İzlenecek yol: çalışma zamanında Şeritteki denetimleri güncelleştirme

bu izlenecek yol, şerit 'in Office uygulamasına yüklendikten sonra şeritteki denetimleri güncelleştirmek için şerit nesne modelinin nasıl kullanılacağını gösterir.

[!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

Örnek, Microsoft Office Outlook bir Birleşik giriş kutusu ve menüyü doldurmak için Northwind örnek veritabanından veri çeker. Bu denetimlerde seçtiğiniz öğeler **, ve gibi alanları otomatik olarak bir** e-posta **iletisine doldurur.**

Bu izlenecek yol aşağıdaki görevleri gösterir:

- yeni bir Outlook VSTO eklenti projesi oluşturun.

- Özel bir Şerit grubu tasarlayın.

- Özel grubu yerleşik bir sekmeye ekleyin.

- Çalışma zamanında Şeritteki denetimleri güncelleştirin.

> [!NOTE]
> Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. daha fazla bilgi için bkz. [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-a-new-outlook-vsto-add-in-project"></a>yeni bir Outlook VSTO eklenti projesi oluşturma

ilk olarak, bir Outlook VSTO eklenti projesi oluşturun.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>yeni bir Outlook VSTO eklenti projesi oluşturmak için

1. içinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , **Ribbon_Update_At_Runtime** adında bir Outlook VSTO eklenti projesi oluşturun.

2. **yeni Project** iletişim kutusunda **çözüm için dizin oluştur**' u seçin.

3. Projeyi varsayılan proje dizinine kaydedin.

     daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="design-a-custom-ribbon-group"></a>Özel Şerit grubu tasarlama

Bir Kullanıcı yeni bir posta iletisi yazdığında bu örnek için şerit görüntülenir. Şerit için özel bir grup oluşturmak için, önce projenize bir şerit öğesi ekleyin ve ardından grubu Şerit tasarımcısında tasarlayın. Bu özel grup, bir veritabanından adları ve sıra geçmişlerini çekerek müşterilere yönelik izleme e-posta iletileri oluşturmanıza yardımcı olur.

### <a name="to-design-a-custom-group"></a>Özel bir grup tasarlamak için

1. **Project** menüsünde, **yeni öğe ekle**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusunda **Şerit (görsel Tasarımcı)** öğesini seçin.

3. Yeni şerit 'in adını **CustomerRibbon** olarak değiştirin ve **Ekle**' ye tıklayın.

     *CustomerRibbon. cs* veya *CustomerRibbon. vb* dosyası Şerit Tasarımcısı 'nda açılır ve varsayılan bir sekme ve grup görüntüler.

4. Şerit Tasarımcısına tıklayarak seçin.

5. **özellikler** penceresinde, **ribbontype** özelliğinin yanındaki açılan oka tıklayın ve ardından **Microsoft. Outlook. Mail. Compose**' a tıklayın.

     Bu, Kullanıcı Outlook yeni bir posta iletisi yazdığında şeridin görünmesini sağlar.

6. Şerit tasarımcısında, seçmek için **grup1** ' e tıklayın.

7. **Özellikler** penceresinde, **etiketi** **müşteri satın alımları** olarak ayarlayın.

8. **araç kutusunun** **Office şerit denetimleri** sekmesinden **müşteri harcamaları** grubuna bir **açılan kutu** sürükleyin.

9. Seçmek için **ComboBox1** öğesine tıklayın.

10. **Özellikler** penceresinde, **etiketi** **müşterilere** ayarlayın.

11. **araç kutusunun** **Office şerit denetimleri** sekmesinden bir **menüyü** **müşteri satınalmaları** grubuna sürükleyin.

12. **Özellikler** penceresinde **etiket** ' i **satın alınan ürün** olarak ayarlayın.

13. **Dynamic** **değerini true** olarak ayarlayın.

     bu, şerit Office uygulamasına yüklendikten sonra çalışma zamanında menüdeki denetimleri eklemenize ve kaldırmanıza olanak sağlar.

## <a name="add-the-custom-group-to-a-built-in-tab"></a>Özel grubu yerleşik bir sekmeye ekleme

yerleşik sekme, Outlook gezgin veya ınspector şeridinde zaten bulunan bir sekmedir. Bu yordamda, özel grubu yerleşik bir sekmeye ekleyecek ve sonra sekmede özel grubun konumunu belirtmelisiniz.

### <a name="to-add-the-custom-group-to-a-built-in-tab"></a>Özel grubu yerleşik bir sekmeye eklemek için

1. **TabAddins (yerleşik)** sekmesine tıklayarak seçin.

2. **Özellikler** penceresinde **ControlID** özelliğini genişletin ve ardından **OfficeId** 'yi **TabNewMailMessage** olarak ayarlayın.

     Bu, **müşteri satın alımları** grubunu yeni bir posta iletisinde görünen şeridin **iletiler** sekmesine ekler.

3. **Müşteri satın alımları** grubuna tıklayarak seçin.

4. **Özellikler** penceresinde, **konum** özelliğini genişletin, **PositionType** özelliğinin yanındaki açılan oka tıklayın ve ardından **BeforeOfficeId**' ye tıklayın.

5. **OfficeId** özelliğini **GroupClipboard** olarak ayarlayın.

     Bu, **iletiler** sekmesinin **Pano** grubundan önce **müşterinin satın** alma grubunu konumlandırır.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde **Yeni veri kaynağı Ekle**' ye tıklayın.

     Bu, **veri kaynağı Yapılandırma Sihirbazı 'nı** başlatır.

2. **Veritabanı**' nı seçin ve ardından **İleri**' ye tıklayın.

3. **Veri kümesi**' ni seçin ve ardından **İleri**' ye tıklayın.

4. Northwind örnek Microsoft SQL Server Compact 4,0 veritabanına yönelik bir veri bağlantısı seçin veya **yeni bağlantı** düğmesini kullanarak yeni bir bağlantı ekleyin.

5. Bir bağlantı seçildikten veya oluşturulduktan sonra **İleri**' ye tıklayın.

6. Bağlantı dizesini kaydetmek için **İleri** ' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar**' ı genişletin.

8. Aşağıdaki tabloların yanındaki onay kutusunu işaretleyin:

    1. **Müşteriler**

    2. **Sipariş Ayrıntıları**

    3. **Siparişler**

    4. **Ürünler**

9. **Finish (Son)** düğmesine tıklayın.

## <a name="update-controls-in-the-custom-group-at-run-time"></a>Çalışma zamanında özel gruptaki denetimleri Güncelleştir

Aşağıdaki görevleri gerçekleştirmek için şerit nesne modelini kullanın:

- Müşteri adlarını **müşteriler** Birleşik giriş kutusuna ekleyin.

- Satış siparişlerini ve satılan ürünleri temsil eden **ürünler satın alınan** menüye menü ve düğme denetimleri ekleyin.

- **Müşteriler** Birleşik giriş kutusu ve **satın alınan ürünler** menüsündeki verileri kullanarak yeni posta Iletilerinin ' e, konu ve gövde alanlarını doldurun.

### <a name="to-update-controls-in-the-custom-group-by-using-the-ribbon-object-model"></a>Şerit nesne modelini kullanarak özel gruptaki denetimleri güncelleştirmek için

1. **Project** menüsünde **başvuru ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, **System. Data. LINQ** derlemesini seçin ve ardından **Tamam**' a tıklayın.

    Bu derleme Language-Integrated sorguları (LINQ) kullanmak için sınıflar içerir. Özel gruptaki denetimleri Northwind veritabanındaki verilerle doldurmak için LINQ kullanacaksınız.

3. **Çözüm Gezgini**' de, **CustomerRibbon. cs** veya **CustomerRibbon. vb** ' ye tıklayarak seçin.

4. **Görünüm** menüsünde **kod**' a tıklayın.

    Şerit kod dosyası kod düzenleyicisinde açılır.

5. Aşağıdaki deyimlerini Şerit kod dosyasının en üstüne ekleyin. bu deyimler, lınq ad alanlarına ve Outlook birincil birlikte çalışma derlemesinin (pıa) ad alanına kolay erişim sağlar.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet1":::

6. Aşağıdaki kodu sınıfının içine ekleyin `CustomerRibbon` . Bu kod, Northwind veritabanının Müşteri, siparişler, sipariş ayrıntıları ve ürün tablolarından bilgi depolamak için kullanacağınız veri tablosu ve tablo bağdaştırıcılarını bildirir.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet2":::

7. Aşağıdaki kod bloğunu `CustomerRibbon` sınıfına ekleyin. Bu kod, çalışma zamanında Şerit için denetimler oluşturan üç yardımcı yöntem ekler.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet3":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet3":::

8. `CustomerRibbon_Load`Olay işleyicisi yöntemini aşağıdaki kodla değiştirin. Bu kod, aşağıdaki görevleri gerçekleştirmek için bir LINQ sorgusu kullanır:

   - Northwind veritabanındaki 20 müşterinin KIMLIĞINI ve adını kullanarak **müşteriler** Birleşik giriş kutusunu doldurun.

   - `PopulateSalesOrderInfo`Yardımcı yöntemini çağırır. Bu yöntem, **ProductsPurchased** menüsünü Şu anda seçili müşteriyle ilgili satış siparişi numaralarıyla güncelleştirir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet4":::

9. Aşağıdaki kodu `CustomerRibbon` sınıfına ekleyin. Bu kod, aşağıdaki görevleri gerçekleştirmek için LINQ sorgularını kullanır:

   - Seçili müşteriyle ilgili her satış siparişi için **ProductsPurchased** menüsüne bir alt menü ekler.

   - Satış siparişiyle ilgili ürünlerin her alt menüsüne düğme ekler.

   - Her düğmeye olay işleyicileri ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet6":::

10. **Çözüm Gezgini**, Şerit kod dosyasına çift tıklayın.

     Şerit Tasarımcısı açılır.

11. Şerit tasarımcısında **müşteriler** Birleşik giriş kutusuna çift tıklayın.

     Şerit kod dosyası kod düzenleyicisinde açılır ve `ComboBox1_TextChanged` olay işleyicisi görünür.

12. `ComboBox1_TextChanged`Olay işleyicisini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

    - `PopulateSalesOrderInfo`Yardımcı yöntemini çağırır. Bu yöntem, **satın alınan ürünler** menüsünü Seçili müşteriyle ilgili satış siparişleriyle güncelleştirir.

    - `PopulateMailItem`Yardımcı yöntemini çağırır ve seçilen müşteri adı olan geçerli metinde geçirir. Bu yöntem, yeni posta iletilerinin, konu ve gövde alanlarını doldurur.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet5":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet5":::

13. Aşağıdaki `Click` olay işleyicisini `CustomerRibbon` sınıfına ekleyin. Bu kod, seçilen ürünlerin adını yeni posta iletilerinin gövde alanına ekler.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet8":::

14. Aşağıdaki kodu `CustomerRibbon` sınıfına ekleyin. Bu kod aşağıdaki görevleri gerçekleştirir:

    - Şu anda seçili olan müşterinin e-posta adresini kullanarak yeni posta iletilerinin satırına doldurur.

    - Yeni posta iletilerinin konu ve gövde alanlarına metin ekler.

      :::code language="csharp" source="../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs" id="Snippet7":::
      :::code language="vb" source="../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb" id="Snippet7":::

## <a name="test-the-controls-in-the-custom-group"></a>Özel gruptaki denetimleri test etme

Outlook yeni bir posta formu açtığınızda, şeridin **iletiler** sekmesinde **müşteri satın alımları** adlı özel bir grup görüntülenir.

Bir müşteri takip e-posta iletisi oluşturmak için bir müşteri seçin ve müşteri tarafından satın alınan ürünleri seçin. **Müşteri satınalmaları** grubundaki denetimler, Northwind veritabanındaki verilerle çalışma zamanında güncelleştirilir.

### <a name="to-test-the-controls-in-the-custom-group"></a>Özel gruptaki denetimleri test etmek için

1. Projenizi çalıştırmak için **F5** tuşuna basın.

     Outlook başlar.

2. Outlook, **dosya** menüsünde, **yeni**' nin üzerine gelin ve **posta iletisi**' ne tıklayın.

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

Office kullanıcı arabirimini nasıl özelleştireceğinizi öğrenmek için aşağıdaki konulardan daha fazla bilgi edinebilirsiniz:

- Herhangi bir belge düzeyi özelleştirmesine bağlam tabanlı kullanıcı arabirimi ekleyin. Daha fazla bilgi için bkz. [eylemler bölmesine genel bakış](../vsto/actions-pane-overview.md).

- standart veya özel bir Microsoft Office Outlook formu genişletin. daha fazla bilgi için bkz. [izlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Outlook için özel bir görev bölmesi ekleyin. Daha fazla bilgi için bkz. [özel görev bölmeleri](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
- [Şerite genel bakış](../vsto/ribbon-overview.md)
- [Dil ile Tümleşik Sorgu (LINQ)](/dotnet/csharp/linq/index)
- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Şerit Tasarımcısı](../vsto/ribbon-designer.md)
- [İzlenecek yol: Şerit Tasarımcısını kullanarak özel sekme oluşturma](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Şerit nesne modeline genel bakış](../vsto/ribbon-object-model-overview.md)
- [Outlook için bir şeridi özelleştirme](../vsto/customizing-a-ribbon-for-outlook.md)
- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md)
- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Nasıl yapılır: Şerit Tasarımcısından Şerit XML 'ine şerit aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md)