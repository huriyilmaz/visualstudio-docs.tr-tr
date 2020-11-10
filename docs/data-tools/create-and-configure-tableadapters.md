---
title: TableAdapter’lar oluşturma ve yapılandırma
description: Visual Studio 'da TableAdapter oluşturma ve yapılandırma konusunu gözden geçirin. TableAdapter, uygulamanızla veritabanı arasındaki iletişimi sağlar.
ms.custom: SEO-VS-2020
ms.date: 09/01/2017
ms.topic: how-to
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6c976f06f105969f1eaa91022607d61251a56008
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436764"
---
# <a name="create-and-configure-tableadapters"></a>TableAdapter’lar oluşturma ve yapılandırma

TableAdapter, uygulamanızla veritabanı arasındaki iletişimi sağlar. Veritabanına bağlanır, sorguları veya saklı yordamları çalıştırır ve yeni bir veri tablosu döndürür ya da döndürülen verilerle var olan verileri doldurur <xref:System.Data.DataTable> . Ayrıca, TableAdapters güncelleştirilmiş verileri uygulamanızdan veritabanına geri gönderebilir.

TableAdapters, aşağıdaki eylemlerden birini gerçekleştirdiğinizde sizin için oluşturulur:

- Veritabanı nesnelerini **Sunucu Gezgini** **veri kümesi Tasarımcısı** sürükleyin.

- Veri kaynağı Yapılandırma Sihirbazı 'nı çalıştırın ve **veritabanı** ya da **Web hizmeti** veri kaynağı türünü seçin.

   ![Visual Studio 'da veri kaynağı Yapılandırma Sihirbazı](media/data-source-configuration-wizard.png)

Ayrıca yeni bir TableAdapter oluşturup bir TableAdapter 'ı **araç kutusundan** **veri kümesi Tasarımcısı** yüzeyinde boş bir bölgeye sürükleyerek bir veri kaynağıyla yapılandırabilirsiniz.

TableAdapters 'e giriş için bkz. [TableAdapters kullanarak veri kümelerini doldur](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>TableAdapter Yapılandırma Sihirbazı 'nı kullanma

TableAdapters ve ilişkili DataTable değerlerini oluşturmak veya düzenlemek için **TableAdapter Yapılandırma sihirbazını** çalıştırın. Mevcut bir TableAdapter 'ı **veri kümesi Tasarımcısı** sağ tıklayarak yapılandırabilirsiniz.

![radveri tablo bağdaştırıcısı yapılandırma Sihirbazı](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Araç kutusundan yeni bir TableAdapter sürükleyip **veri kümesi Tasarımcısı** odak edildiğinde sihirbaz başlatılır ve TableAdapter 'ın hangi veri kaynağını bağlanacağı belirtmenizi ister. Bir sonraki sayfada, sihirbaz, SQL deyimleri ya da saklı yordamlar veritabanıyla iletişim kurmak için kullanması gereken komut türlerini ister. (Zaten bir veri kaynağıyla ilişkilendirilmiş bir TableAdapter yapılandırıyorsanız bunu göremezsiniz.)

- Veritabanı için doğru izinleriniz varsa, temel alınan veritabanında yeni bir saklı yordam oluşturma seçeneğiniz vardır. Bu izinlere sahip değilseniz bu bir seçenek değildir.

- Ayrıca, TableAdapter 'ın **Select** , **Insert** , **Update** ve **Delete** komutları için mevcut saklı yordamları çalıştırmayı da tercih edebilirsiniz. **Update** komutuna atanan saklı yordam, örneğin, `TableAdapter.Update()` yöntemi çağrıldığında çalıştırılır.

Seçili saklı yordamdaki parametreleri veri tablosundaki karşılık gelen sütunlara eşleyin. Örneğin, saklı yordamınız tablodaki sütuna geçtiğinde adlı bir parametreyi kabul ediyorsa `@CompanyName` `CompanyName` , parametresinin **kaynak sütununu** `@CompanyName` olarak ayarlayın `CompanyName` .

> [!NOTE]
> SELECT komutuna atanan saklı yordam, sihirbazın bir sonraki adımında adı ettiğiniz TableAdapter 'ın yöntemi çağırarak çalıştırılır. Varsayılan yöntem ise `Fill` , genellıkle Select yordamını çalıştırmak için kullanılan kod `TableAdapter.Fill(tableName)` . Varsayılan adı ' dan değiştirirseniz `Fill` , `Fill` atadığınız adla değiştirin ve "TableAdapter" öğesini TableAdapter 'ın gerçek adıyla değiştirin (örneğin, `CustomersTableAdapter` ).

- **Güncelleştirmeleri doğrudan veritabanına göndermek Için oluşturma yöntemlerini** seçme `GenerateDBDirectMethods` özelliği true olarak ayarlanmasına eşdeğerdir. Özgün SQL açıklaması yeterli bilgi sağlamıyorsa veya sorgu güncelleştirilebilir bir sorgu olmadığında bu seçenek kullanılamaz. Bu durum, örneğin, bir tek (skaler) değer döndüren sorguları ve sorguları **birleştirmek** gibi meydana gelebilir.

Sihirbazdaki **Gelişmiş Seçenekler** şunları sağlar:

- **Generate SQL deyimleri** SAYFASıNDA tanımlanan select deyimini temel alan INSERT, Update ve delete deyimlerini oluştur
- İyimser eşzamanlılığı kullanma
- INSERT ve UPDATE deyimlerinin çalıştırıldıktan sonra veri tablosunun yenilenip yenilenmeyeceğini belirtin

## <a name="configure-a-tableadapters-fill-method"></a>TableAdapter 'ın Fill metodunu yapılandırma

Bazen TableAdapter tablosunun şemasını değiştirmek isteyebilirsiniz. Bunu yapmak için, TableAdapter 'ın birincil `Fill` yöntemini değiştirirsiniz. TableAdapters, `Fill` ilişkili veri tablosunun şemasını tanımlayan bir birincil yöntemle oluşturulur. Birincil `Fill` Yöntem, TableAdapter 'ı ilk kez yapılandırdığınızda girdiğiniz sorguyu veya saklı yordamı temel alır. Veri kümesi Tasarımcısı ' nda veri tablosu altındaki ilk (en üst) yöntemdir.

![Birden çok sorguya sahip TableAdapter](../data-tools/media/tableadapter.gif)

TableAdapter 'ın Main yönteminde yaptığınız tüm değişiklikler, `Fill` ilişkili veri tablosunun şemasına yansıtılır. Örneğin, ana yöntemdeki sorgudan bir sütunu kaldırmak, `Fill` sütunu ilişkili veri tablosundan da kaldırır. Ayrıca, sütunun Main yönteminden kaldırılması, `Fill` sütunu o TableAdapter için ek sorgulardan kaldırır.

TableAdapter sorgu Yapılandırma Sihirbazı 'nı kullanarak TableAdapter için ek sorgular oluşturabilir ve düzenleyebilirsiniz. Bu ek sorgular, skaler bir değer döndürmedikleri müddetçe tablo şemasına uymalıdır.  Her ek sorgunun belirttiğiniz bir adı vardır.

Aşağıdaki örnek, adlı ek bir sorgunun nasıl çağrılacağını göstermektedir `FillByCity` :

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>TableAdapter sorgu Yapılandırma Sihirbazı 'nı yeni bir sorgu ile başlatmak için

1. Veri kümenizi **veri kümesi Tasarımcısı** açın.

2. Yeni bir sorgu oluşturuyorsanız, bir **sorgu** nesnesini **Toolbox** 'ın **DataSet** sekmesinden bir nesne üzerine sürükleyin <xref:System.Data.DataTable> veya TableAdapter 'ın kısayol menüsünden **Sorgu Ekle** ' yi seçin. Ayrıca, ilişkili olmayan bir TableAdapter oluşturan **veri kümesi Tasarımcısı** boş bir alanına bir **sorgu** nesnesi sürükleyebilirsiniz <xref:System.Data.DataTable> . Bu sorgular yalnızca tek (skaler) değerler döndürebilir veya veritabanına karşı UPDATE, INSERT veya DELETE komutlarını çalıştırabilir.

3. **Veri bağlantınızı seçin** ekranında, sorgunun kullanacağı bağlantıyı seçin veya oluşturun.

    > [!NOTE]
    > Bu ekran yalnızca Tasarımcı kullanılacak uygun bağlantıyı belirleyeleyemiyorsa veya hiçbir bağlantı yoksa görüntülenir.

4. **Bir komut türü seçin** ekranında, veritabanından veri getirme yöntemlerinden aşağıdaki yöntemlerden birini seçin:

    - **SQL deyimlerini kullanın** , veritabanınızdaki verileri seçmek IÇIN bir SQL deyimi yazmanız sağlar.

    - **Yeni saklı yordam oluştur** , SIHIRBAZıN belirtilen SELECT ifadesine göre yeni bir saklı yordam (veritabanında) oluşturmasını sağlar.

    - **Mevcut saklı yordamları Kullan** , sorguyu çalıştırırken mevcut bir saklı yordamı çalıştırmanızı sağlar.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Mevcut bir sorguda TableAdapter sorgu Yapılandırma Sihirbazı 'nı başlatmak için

- Mevcut bir TableAdapter sorgusunu düzenliyorsanız, sorguyu sağ tıklatın ve ardından kısayol menüsünden **Yapılandır** ' ı seçin.

    > [!NOTE]
    > TableAdapter 'ın ana sorgusuna sağ tıklamak TableAdapter ve Schema 'yı yeniden yapılandırır <xref:System.Data.DataTable> . TableAdapter üzerinde ek bir sorguya sağ tıklanması, ancak yalnızca seçili sorguyu yapılandırır. TableAdapter **Yapılandırma Sihirbazı** TableAdapter tanımını yeniden yapılandırır, ancak **TableAdapter sorgu Yapılandırma Sihirbazı** yalnızca seçili sorguyu yeniden yapılandırır.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>TableAdapter 'a genel sorgu eklemek için

- Genel sorgular, tek (skaler) bir değer veya değer döndürmeyen SQL sorgulardır. Genellikle, genel işlevler ekleme, güncelleştirme ve silme gibi veritabanı işlemleri gerçekleştirir. Ayrıca, bir tablodaki müşterilerin sayısı veya belirli bir sırada tüm öğeler için toplam ücretler gibi bilgileri toplar.

     Bir **sorgu** nesnesini **araç** **kümesi** sekmesinden **veri kümesi Tasarımcısı** boş bir alana sürükleyerek genel sorgular eklersiniz.

- İstenen görevi gerçekleştiren bir sorgu sağlayın, örneğin, `SELECT COUNT(*) AS CustomerCount FROM Customers` .

    > [!NOTE]
    > Bir **sorgu** nesnesini doğrudan **veri kümesi Tasarımcısı** sürüklemek yalnızca skaler (tek) bir değer döndüren bir yöntem oluşturur. Seçtiğiniz sorgu veya saklı yordam tek bir değerden daha fazla döndürebileceğinden, sihirbaz tarafından oluşturulan yöntem yalnızca tek bir değer döndürür. Örneğin, sorgu döndürülen verilerin ilk satırının ilk sütununu döndürebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
