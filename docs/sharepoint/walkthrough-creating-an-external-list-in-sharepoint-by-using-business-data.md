---
title: İş verilerini kullanarak SharePoint listesi oluşturma
description: BDC hizmeti için bir iş veritabanındaki kişiler hakkında bilgi döndüren bir model oluşturun ve ardından bu modeli kullanarak SharePoint bir dış liste oluşturun.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a265a80116da0d1d2ffac469f7193c737a65a93a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075911"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>Adım adım kılavuz: İş verilerini kullanarak SharePoint dış liste oluşturma

İş Verileri Bağlantısı (BDC) hizmeti, SharePoint sunucu uygulamaları, Web hizmetleri ve veritabanlarından iş verilerini görüntülemesini sağlar.

Bu kılavuzda, örnek veritabanındaki kişiler hakkında bilgi döndüren BDC hizmeti için bir model oluşturma adımlarını gösterir. Daha sonra bu modeli kullanarak SharePoint bir dış liste oluşturabilirsiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Proje oluşturma.
- Modele varlık ekleme.
- Bulıcı yöntemi ekleme.
- Belirli bir Bulıcı yöntemi ekleme.
- Projeyi test etme.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Desteklenen Windows ve SharePoint.

- AdventureWorks örnek veritabanına erişim. AdventureWorks veritabanını yükleme hakkında daha fazla bilgi için bkz. [SQL Server Veritabanları.](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

## <a name="create-a-project-that-contains-a-bdc-model"></a>BDC modeli içeren bir proje oluşturma

1. dosya menüsündeki menü çubuğunda Dosya **Visual Studio'yi**  >  **seçin**  >  **Project.**

     Yeni **Project** iletişim kutusu açılır.

2. Visual **C# veya** **Visual Basic** altında, SharePoint **düğümünü** genişletin ve ardından **2010 öğesini** seçin.

3. Şablonlar **bölmesinde** **2010'SharePoint 2010'Project** seçin, projeye **AdventureWorksTest** adını ve ardından **Tamam düğmesini** seçin.

     SharePoint **Özelleştirme Sihirbazı** görüntülenir. Bu sihirbazda, projede hata ayıklamak ve çözümün güven düzeyini ayarlamak için kullanabileceğiniz siteyi belirtebilirsiniz.

4. Güven düzeyini **ayarlamak için Grup çözümü** olarak dağıt seçeneğini belirleyin.

5. Varsayılan yerel **siteyi** kabul etmek için Son SharePoint seçin.

6. Bu **Çözüm Gezgini** proje düğümünü SharePoint seçin.

7. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

     Yeni **Öğe Ekle iletişim** kutusu açılır.

8. Şablonlar bölmesinde **İş** Verileri Bağlantı Modeli **(Yalnızca** Grup Çözümü) 'ni seçin, projeye **AdventureWorksContacts** adını ve ardından Ekle **düğmesini** seçin.

## <a name="add-data-access-classes-to-the-project"></a>Projeye veri erişim sınıfları ekleme

1. Menü çubuğunda Araçlar ve **Veritabanı'Bağlan**  >  **seçin.**

     Bağlantı **Ekle** iletişim kutusu açılır.

2. SQL Server AdventureWorks örnek veritabanına bağlantı ekleyin.

     Daha fazla bilgi için [bkz. Bağlantı Ekleme/Değiştirme (Microsoft SQL Server)](/previous-versions/dxb6fxah(v=vs.140)).

3. Bu **Çözüm Gezgini** proje düğümünü seçin.

4. Menü çubuğunda Yeni Öğe **Ekle'Project**  >  **seçin.**

5. Yüklü **Şablonlar bölmesinde Veri** **düğümünü** seçin.

6. Şablonlar **bölmesinde Sınıfları** seçin LINQ to SQL **seçin.**

7. Ad **kutusunda** **AdventureWorks'i belirtin** ve ardından Ekle **düğmesini** seçin.

     Projeye bir .dbml dosyası eklenir ve Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) açılır.

8. Menü çubuğunda Görünüm'e tıklayın **ve Sunucu Gezgini.**  >  

9. Bu **Sunucu Gezgini,** AdventureWorks örnek veritabanını temsil eden düğümü genişletin ve ardından Tablolar **düğümünü** genişletin.

10. Kişi **(Kişi) tablosuna** O/R Tasarımcısı'na ekleyin.

     Bir varlık sınıfı oluşturulur ve tasarım yüzeyinde görünür. Varlık sınıfı, Kişi (Kişi) tablosunda sütunlara eşlene özelliklere sahiptir.

## <a name="remove-the-default-entity-from-the-bdc-model"></a>Varsayılan varlığı BDC modelinden kaldırma

İş **Verileri Bağlantı Modeli projesi,** modele Entity1 adlı bir varsayılan varlık ekler. Bu varlığı kaldırın. Daha sonra yeni bir varlık eksersiniz. Boş bir modelle başlayarak izlenecek yolu tamamlamak için gereken adım sayısı azalır.

1. Bu **Çözüm Gezgini** **BdcModel1 düğümünü** genişletin ve ardından *BdcModel1.bdcm dosyasını* açın.

2. İş Verileri Bağlantısı model dosyası BDC tasarımcısında açılır.

3. Tasarımcıda **Entity1** kısayol menüsünü açın ve Sil'i **seçin.**

4. Bu **Çözüm Gezgini** *Entity1.vb* (Visual Basic) veya *Entity1.cs* (C# içinde) kısayol menüsünü açın ve Sil'i **seçin.**

5. *Entity1Service.vb* (Visual Basic) veya *Entity1Service.cs* (C# içinde) kısayol menüsünü açın ve Sil'i **seçin.**

## <a name="add-an-entity-to-the-model"></a>Modele varlık ekleme

Modele bir varlık ekleyin. Visual Studio **Toolbox'tan** BDC tasarımcısına varlıklar ekleme.

1. Menü çubuğunda Görünüm Araç **Kutusu'nı**  >  **seçin.**

2. Araç Kutusunun **BusinessDataConnectivity** **sekmesinde,** BDC **tasarımcısına** bir Varlık ekleyin.

     Yeni varlık tasarımcıda görünür. Visual Studio *EntityService.vb* (Visual Basic) veya *EntityService.cs* (C# içinde) adlı bir dosyayı projeye ekler.

3. Menü çubuğunda Özellikler Penceresini **Görüntüle'yi**  >    >  **seçin.**

4. Özellikler **penceresinde Ad** özellik değerini **Kişi** olarak **ayarlayın.**

5. Tasarımcıda varlığın kısayol menüsünü açın, Ekle'yi **ve ardından** Tanımlayıcı'yı **seçin.**

     Varlığa yeni bir tanımlayıcı görünür.

6. Özellikler **penceresinde** tanımlayıcının adını **ContactID olarak değiştirin.**

7. Tür Adı listesinde **System.Int32'yi seçin.** 

## <a name="add-a-specific-finder-method"></a>Belirli bir Bulıcı yöntemi ekleme

BDC hizmetinin belirli bir kişi görüntülemesi için Belirli Bir Bulıcı yöntemi eklemeniz gerekir. BDC hizmeti, bir kullanıcı listede bir öğe seçtiklerde Ve şeritteki Öğeyi Görüntüle düğmesini seçerse Belirli **Bulıcı** yöntemini çağıran bir yöntemdir.

BDC Yöntem Ayrıntıları penceresini kullanarak Kişi varlığa Belirli bir **Bulıcı yöntemi** ekleyin. Belirli bir varlığı geri dönmek için yöntemine kod ekleyin.

1. BDC tasarımcısında Kişi **varlığını** seçin.

2. Menü çubuğunda BDC Yöntem **Ayrıntıları'Windows**  >    >  **Diğer Öğeleri Görüntüle'yi seçin.**

     BDC Yöntem Ayrıntıları penceresi açılır.

3. Yöntem **Ekle listesinde Belirli** Bulıcı **Yöntemi Oluştur'a tıklayın.**

     Visual Studio aşağıdaki öğeleri modele ekler. Bu öğeler **BDC Yöntem Ayrıntıları penceresinde** görünür.

    - ReadItem adlı bir yöntem.

    - yöntemi için bir giriş parametresi.

    - yöntemi için bir dönüş parametresi.

    - Her parametre için bir tür tanımlayıcısı.

    - yöntemi için bir yöntem örneği.

4. **BDC Yöntem Ayrıntıları penceresinde** Kişi türü tanımlayıcısı için görüntülenen listeyi açın **ve düzenle'yi** **seçin.**

     **BDC Gezgini** açılır ve modelin hiyerarşik bir görünümünü sağlar.

5. Özellikler **penceresinde** **TypeName** özelliğinin yanındaki listeyi açın, Geçerli Project **sekmesini** ve ardından **Kişi özelliğini** seçin.

6. **BDC Gezgini'nde** Kişi kısayol menüsünü açın **ve Ardından** Tür Tanımlayıcısı **Ekle'yi seçin.**

     BDC Gezgini'nde **TypeDescriptor1** adlı yeni bir **tür tanımlayıcısı görüntülenir.**

7. Özellikler **penceresinde Name** özellik **değerini** **ContactID olarak ayarlayın.**

8. **TypeName** özelliğinin yanındaki listeyi açın ve **Ardından Int32'yi seçin.**

9. Tanımlayıcı özelliğinin yanındaki listeyi **açın ve** **ContactID'yi seçin.**

10. Aşağıdaki alanların her biri için bir tür tanımlayıcısı oluşturmak için 6. adımı tekrarlayın.

    |Name|Tür Adı|
    |----------|---------------|
    |FirstName|System|
    |LastName|System|
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

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

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

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet2":::

## <a name="test-the-project"></a>Projeyi test etme

projeyi çalıştırdığınızda, SharePoint site açılır ve Visual Studio modelinizi iş verileri bağlantı hizmetine ekler. SharePoint, iletişim varlığına başvuran bir dış liste oluşturun. AdventureWorks veritabanındaki kişilerin verileri listede görüntülenir.

> [!NOTE]
> çözümünüzde hata ayıklayabilmeniz için SharePoint güvenlik ayarlarınızı değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).

1. **F5** tuşunu seçin.

     SharePoint site açılır.

2. **Site eylemleri** menüsünde, **diğer seçenekler** komutunu seçin.

3. **Oluştur** sayfasında, **dış liste** şablonunu seçin ve ardından **Oluştur** düğmesini seçin.

4. Özel liste **kişilerini** adlandırın.

5. **Dış Içerik türü** alanının yanındaki Git düğmesini seçin.

6. **Dış Içerik türü Seçicisi** Iletişim kutusunda **AdventureWorksContacts. BdcModel1. Contact** öğesini seçin ve ardından **Oluştur** düğmesini seçin.

     SharePoint, AdventureWorks örnek veritabanındaki kişileri içeren bir dış liste oluşturur.

7. Belirli Bulucu yöntemini test etmek için listeden bir kişi seçin.

8. Şeritte, **öğeler** sekmesini seçin ve ardından **öğeyi görüntüle** komutunu seçin.

     Seçtiğiniz kişinin ayrıntıları bir formda görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

aşağıdaki konulardan SharePoint BDC hizmeti için model tasarlama hakkında daha fazla bilgi edinebilirsiniz:

- [Nasıl yapılır: bir Oluşturucu yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md).
- [Nasıl yapılır: Güncelleştirici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md).
- [Nasıl yapılır: bir silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md).

## <a name="see-also"></a>Ayrıca bkz.

[İş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md) 
 [İş verileri bağlantı modeli oluşturma](../sharepoint/creating-a-business-data-connectivity-model.md) 
 [İVB modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md) 
 [İş verilerini SharePoint Ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)