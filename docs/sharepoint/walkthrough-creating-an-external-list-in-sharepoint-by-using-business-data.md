---
title: İş verileri kullanarak SharePoint 'te dış liste oluşturma
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9f4fe79c3a6f158eb61d624ce6c5e1566925e3fd
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740064"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>İzlenecek yol: iş verileri kullanarak SharePoint 'te dış liste oluşturma

Iş verileri bağlantısı (BDC) hizmeti, SharePoint 'in arka uç sunucu uygulamalarından, Web hizmetlerinden ve veritabanlarından iş verilerini görüntülemesini sağlar.

Bu izlenecek yol, bir örnek veritabanındaki kişiler hakkında bilgi döndüren BDC hizmeti için bir model oluşturmayı gösterir. Bu durumda, SharePoint 'te bu modeli kullanarak bir dış liste oluşturacaksınız.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Proje oluşturma.
- Modele bir varlık ekleniyor.
- Bulucu yöntemi ekleme.
- Belirli bir bulucu yöntemi ekleniyor.
- Projeyi test etme.

## <a name="prerequisites"></a>Ön koşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint sürümleri.

- AdventureWorks örnek veritabanına erişim. AdventureWorks veritabanının nasıl yükleneceği hakkında daha fazla bilgi için bkz. [SQL Server örnek veritabanları](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).

## <a name="create-a-project-that-contains-a-bdc-model"></a>IVB modeli içeren bir proje oluşturma

1. Visual Studio 'daki menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

2. **Visual C#** veya **Visual Basic**altında **SharePoint** düğümünü genişletin ve ardından **2010** öğesini seçin.

3. **Şablonlar** bölmesinde **SharePoint 2010 projesi**' ni seçin, projeyi **AdventureWorksTest**olarak adlandırın ve **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir. Bu sihirbazda, projede hata ayıklamak için kullanacağınız siteyi belirtebilir ve çözümün güven düzeyini ayarlayabilirsiniz.

4. Güven düzeyini ayarlamak için **Grup çözümü olarak dağıt** seçenek düğmesini seçin.

5. Varsayılan yerel SharePoint sitesini kabul etmek için **son** düğmesini seçin.

6. **Çözüm Gezgini**, SharePoint proje düğümünü seçin.

7. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

     **Yeni öğe Ekle** iletişim kutusu açılır.

8. **Şablonlar** bölmesinde, **Iş verileri bağlantı modeli (yalnızca Grup çözümü)** öğesini seçin, projeyi **AdventureWorksContacts**olarak adlandırın ve ardından **Ekle** düğmesini seçin.

## <a name="add-data-access-classes-to-the-project"></a>Projeye veri erişim sınıfları ekleme

1. Menü çubuğunda **Araçlar**  >  **veritabanına Bağlan**' ı seçin.

     **Bağlantı ekle** iletişim kutusu açılır.

2. SQL Server AdventureWorks örnek veritabanına bir bağlantı ekleyin.

     Daha fazla bilgi için bkz. [Bağlantı Ekle/Değiştir (Microsoft SQL Server)](/previous-versions/dxb6fxah(v=vs.140)).

3. **Çözüm Gezgini**, proje düğümünü seçin.

4. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

5. **Yüklü şablonlar** bölmesinde, **veri** düğümünü seçin.

6. **Şablonlar** bölmesinde **LINQ to SQL sınıfları**' nı seçin.

7. **Ad** kutusunda **AdventureWorks**belirtin ve sonra **Ekle** düğmesini seçin.

     Bir. dbml dosyası projeye eklenir ve Nesne İlişkisel Tasarımcısı (O/R Designer) açılır.

8. Menü çubuğunda Sunucu Gezgini **görüntüle**' yi seçin  >  **Server Explorer**.

9. **Sunucu Gezgini**' de, AdventureWorks örnek veritabanını temsil eden düğümü genişletin ve **Tablolar** düğümünü genişletin.

10. **Kişi (kişi)** tablosunu O/R tasarımcısına ekleyin.

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görüntülenir. Varlık sınıfı, Iletişim (kişi) tablosundaki sütunlarla eşlenen özelliklere sahiptir.

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Varsayılan varlığı IVB modelinden kaldır

**Iş verileri bağlantı modeli** projesi, modele Entity1 adlı bir varsayılan varlık ekler. Bu varlığı kaldırın. Daha sonra yeni bir varlık ekleyeceksiniz. Boş bir modelle başlamak, izlenecek yolu tamamlamak için gereken adımların sayısını azaltır.

1. **Çözüm Gezgini**' de, **BdcModel1** düğümünü genişletin ve ardından *BdcModel1. bdcm* dosyasını açın.

2. Iş verileri bağlantı modeli dosyası BDC Tasarımcısı 'nda açılır.

3. Tasarımcıda **Entity1**için kısayol menüsünü açın ve **Sil**' i seçin.

4. **Çözüm Gezgini**' de, *Entity1. vb* (Visual Basic) veya *Entity1.cs* (C# ' de) için kısayol menüsünü açın ve **Sil**' i seçin.

5. *Entity1Service. vb* (Visual Basic) veya *Entity1Service.cs* (C# ' de) için kısayol menüsünü açın ve **Sil**' i seçin.

## <a name="add-an-entity-to-the-model"></a>Modele bir varlık ekleyin

Modele bir varlık ekleyin. Visual Studio **araç kutusu** 'ndan bdc Tasarımcısı üzerine varlık ekleyebilirsiniz.

1. Menü çubuğunda **Görünüm**  >  **araç kutusunu**seçin.

2. **Araç kutusunun** **BUSINESSDATACONNECTIVITY** sekmesinde, İVB tasarımcısına bir **varlık** ekleyin.

     Yeni varlık tasarımcıda görünür. Visual Studio, projeye *EntityService. vb* (Visual Basic) veya *EntityService.cs* (C# ' de) adlı bir dosya ekler.

3. Menü çubuğunda **View**  >  **Özellikler**  >  **penceresini**görüntüle ' yi seçin.

4. **Özellikler** penceresinde, **ad** özellik değerini **iletişim**olarak ayarlayın.

5. Tasarımcıda varlık için kısayol menüsünü açın, **Ekle**' yi seçin ve **tanımlayıcı**' yı seçin.

     Varlıkta yeni bir tanımlayıcı belirir.

6. **Özellikler** penceresinde, tanımlayıcının adını, **kişi**kimliği olarak değiştirin.

7. **Tür adı** listesinde, **System. Int32**' yi seçin.

## <a name="add-a-specific-finder-method"></a>Belirli bir bulucu yöntemi ekleme

BDC hizmetinin belirli bir kişiyi göstermesini sağlamak için belirli bir bulucu yöntemi eklemeniz gerekir. Bir Kullanıcı listede bir öğe seçtiğinde ve sonra Şeritteki **öğeyi görüntüle** düğmesini SEÇTIĞINDE, BDC hizmeti belirli Bulucu yöntemini çağırır.

**BDC Yöntem ayrıntıları** penceresini kullanarak ilgili kişi varlığına belirli bir bulucu yöntemi ekleyin. Belirli bir varlığı döndürmek için yöntemine kod ekleyin.

1. IVB tasarımcısında, **iletişim** varlığını seçin.

2. Menü çubuğunda, **View**  >  **diğer Windows**  >  **bdc yöntemi ayrıntılarını**görüntüle ' yi seçin.

     IVB yöntemi ayrıntıları penceresi açılır.

3. **Yöntem Ekle** listesinde, **belirli bulucu yöntemi oluştur**' u seçin.

     Visual Studio, modele aşağıdaki öğeleri ekler. Bu öğeler **BDC Yöntem ayrıntıları** penceresinde görüntülenir.

    - ReadItem adlı bir yöntem.

    - Yöntemi için bir giriş parametresi.

    - Yöntemi için bir dönüş parametresi.

    - Her parametre için bir tür tanımlayıcısı.

    - Yöntemi için bir yöntem örneği.

4. **BDC Yöntem ayrıntıları** penceresinde, **kişi** türü tanımlayıcısı için görüntülenen listeyi açın ve ardından **Düzenle**' yi seçin.

     **IVB Gezgini** açılır ve modelin hiyerarşik bir görünümünü sağlar.

5. **Özellikler** penceresinde, **TypeName** özelliğinin yanındaki listeyi açın, **geçerli proje** sekmesini seçin ve ardından **iletişim** özelliğini seçin.

6. **IVB Gezgini**' nde, **kişinin**kısayol menüsünü açın ve **tür tanımlayıcısı Ekle**' yi seçin.

     **TypeDescriptor1** adlı yeni bir tür tanımlayıcısı **BDC Gezgini**'nde görünür.

7. **Özellikler** penceresinde, **ad** özelliği değerini, **bir.**

8. **TypeName** özelliğinin yanındaki listeyi açın ve ardından **Int32**öğesini seçin.

9. **Tanımlayıcı** özelliğinin yanındaki listeyi açın ve ardından, Ilgili **kişi kimliği**' ni seçin.

10. Aşağıdaki alanların her biri için bir tür tanımlayıcısı oluşturmak üzere 6. adımı tekrarlayın.

    |Ad|Tür adı|
    |----------|---------------|
    |FirstName|System. String|
    |LastName|System. String|
    |Telefon|System. String|
    |EmailAddress|System. String|
    |Emailpromosyonu|System. Int32|
    |NameStyle|System. Boolean|
    |PasswordHash|System. String|
    |Passwordanahtar|System. String|

11. IVB tasarımcısında, **kişi** varlığında **ReadItem** yöntemini açın.

     Iletişim hizmeti kod dosyası kod düzenleyicisinde açılır.

12. Sınıfında, `ContactService` `ReadItem` yöntemini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

    - AdventureWorks veritabanının kişi tablosundan bir kayıt alır.

    - BDC hizmetine bir Iletişim varlığı döndürür.

    > [!NOTE]
    > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Bulucu yöntemi ekleme

BDC hizmetinin kişileri bir listede görüntülemesini sağlamak için bir bulucu yöntemi eklemeniz gerekir. **BDC Yöntem ayrıntıları** penceresini kullanarak kişi varlığına bir bulucu yöntemi ekleyin. BDC hizmetine bir varlık koleksiyonu döndürmek için yöntemine kod ekleyin.

1. IVB tasarımcısında, **iletişim** varlığını seçin.

2. **BDC Yöntem ayrıntıları** penceresinde **ReadItem** düğümünü daraltın.

3. **ReadList** yönteminin altındaki **Yöntem Ekle** listesinde **bulucu yöntemi oluştur**' u seçin.

     Visual Studio bir yöntem, dönüş parametresi ve bir tür tanımlayıcısı ekler.

4. IVB tasarımcısında, **kişi** varlığında **ReadList** yöntemini açın.

     Iletişim hizmeti için kod dosyası kod düzenleyicisinde açılır.

5. Sınıfında, `ContactService` `ReadList` yöntemini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - AdventureWorks veritabanının kişiler tablosundan verileri alır.

   - BDC hizmetine Iletişim varlıklarının bir listesini döndürür.

     > [!NOTE]
     > `ServerName`Alanın değerini sunucunuzun adıyla değiştirin.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>Projeyi test etme

Projeyi çalıştırdığınızda, SharePoint sitesi açılır ve Visual Studio modelinizi Iş verileri bağlantı hizmetine ekler. SharePoint 'te kişi varlığına başvuran bir dış liste oluşturun. AdventureWorks veritabanındaki kişilerin verileri listede görüntülenir.

> [!NOTE]
> Çözümünüzde Hata ayıklayabilmeniz için SharePoint 'teki güvenlik ayarlarınızı değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

1. **F5** tuşunu seçin.

     SharePoint sitesi açılır.

2. **Site eylemleri** menüsünde, **diğer seçenekler** komutunu seçin.

3. **Oluştur** sayfasında, **dış liste** şablonunu seçin ve ardından **Oluştur** düğmesini seçin.

4. Özel liste **kişilerini**adlandırın.

5. **Dış Içerik türü** alanının yanındaki Git düğmesini seçin.

6. **Dış Içerik türü Seçicisi** Iletişim kutusunda **AdventureWorksContacts. BdcModel1. Contact** öğesini seçin ve ardından **Oluştur** düğmesini seçin.

     SharePoint, AdventureWorks örnek veritabanındaki kişileri içeren bir dış liste oluşturur.

7. Belirli Bulucu yöntemini test etmek için listeden bir kişi seçin.

8. Şeritte, **öğeler** sekmesini seçin ve ardından **öğeyi görüntüle** komutunu seçin.

     Seçtiğiniz kişinin ayrıntıları bir formda görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

SharePoint 'te BDC hizmeti modellerini nasıl tasarlayacağınızı öğrenmek için aşağıdaki konulardan daha fazla bilgi edinebilirsiniz:

- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md).
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md).
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Ayrıca bkz.

[İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md) 
 [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md) 
 [İVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md) 
 [İş verilerini SharePoint Ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)