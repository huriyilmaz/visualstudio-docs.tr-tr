---
title: TableAdapter’lar oluşturma ve yapılandırma
description: Bir tablo içinde TableAdapter oluşturma ve yapılandırmayı Visual Studio. TableAdapter, uygulamanızla veritabanı arasındaki iletişimi sağlar.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5f08a8c6d441a8b38f367ecfbdab95e1eabc113a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052973"
---
# <a name="create-and-configure-tableadapters"></a>TableAdapter’lar oluşturma ve yapılandırma

TableAdapter, uygulamanızla veritabanı arasındaki iletişimi sağlar. Veritabanına bağlanıyor, sorgular veya saklı yordamlar çalıştırıyor ve yeni bir veri tablosu iade ediyor veya var olan verileri döndürülen <xref:System.Data.DataTable> verilerle doldurıyor. TableAdapter'lar, güncelleştirilmiş verileri uygulamanıza geri gönderebilir.

TableAdapter'lar aşağıdaki eylemlerden birini gerçekleştirecek olurken sizin için oluşturulur:

- Veritabanı nesnelerini **Sunucu Gezgini** veritabanına **Veri Kümesi Tasarımcısı.**

- Veri Kaynağı Yapılandırma Sihirbazı'nı çalıştırın ve Veritabanı **veya** Web Hizmeti **veri kaynağı** türünü seçin.

   ![Visual Studio'de Veri Kaynağı Yapılandırma Sihirbazı](media/data-source-configuration-wizard.png)

Ayrıca yeni bir TableAdapter oluşturabilir ve **araç** kutusundan bir TableAdapter'i veri kaynağıyla birlikte, tablo yüzeyindeki boş bir **bölgeye sürükleyerek Veri Kümesi Tasarımcısı yapılandırabilirsiniz.**

TableAdapter'lara giriş için [bkz. TableAdapters kullanarak veri kümelerini doldurma.](../data-tools/fill-datasets-by-using-tableadapters.md)

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>TableAdapter Yapılandırma Sihirbazı'nı kullanma

**TableAdapter'ları ve ilişkili** DataTable'ları oluşturmak veya düzenlemek için TableAdapter Yapılandırma Sihirbazı'nı çalıştırın. Var olan bir TableAdapter'ı yapılandırmak için, **Veri Kümesi Tasarımcısı.**

![raddata Tablo Bağdaştırıcısı Yapılandırma Sihirbazı](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

**Veri Kümesi Tasarımcısı** odaktayken araç kutusundan yeni bir TableAdapter sürüklersanız sihirbaz başlatılır ve TableAdapter'ın bağlanması gereken veri kaynağını belirtmenizi istenir. Sonraki sayfada sihirbaz, veritabanıyla iletişim kurmak için ne tür komutlar (deyimler veya saklı yordamlar) SQL gerektiğini sorar. (Zaten bir veri kaynağıyla ilişkilendirilmiş bir TableAdapter yapılandırıyorsanız bunu görmeyebilirsiniz.)

- Veritabanı için doğru izinlere sahipseniz temel alınan veritabanında yeni bir saklı yordam oluşturma seçeneğiniz vardır. Bu izinlere sahip değilseniz bu bir seçenek olmayacak.

- TableAdapter'ın **SELECT**, **INSERT**, **UPDATE** ve **DELETE** komutları için mevcut saklı yordamları çalıştırmayı da seçebilirsiniz. Örneğin, **Update** komutuna atanan saklı yordam, yöntem çağrıldıkta `TableAdapter.Update()` çalıştır.

Seçilen saklı yordamdaki parametreleri veri tablosunda karşılık gelen sütunlara eşler. Örneğin saklı yordamınız tablodaki sütuna geçtiği adlı bir parametre kabul ediyorsa parametrenin Kaynak Sütunu'na `@CompanyName` `CompanyName`  `@CompanyName` `CompanyName` ayarlayın.

> [!NOTE]
> SELECT komutuna atanan saklı yordam, sihirbazın sonraki adımlarında adınız olan TableAdapter yöntemini çağırarak çalıştırıldı. Varsayılan `Fill` yöntemdir, bu nedenle GENELLIKLE SELECT yordamını çalıştırmak için kullanılan kod `TableAdapter.Fill(tableName)` olur. varsayılan adını yerine atadığınız adı yazın ve `Fill` `Fill` "TableAdapter" ifadesini TableAdapter'ın gerçek adıyla (örneğin, `CustomersTableAdapter` ) değiştirin.

- Güncelleştirmeleri **doğrudan veritabanına göndermek için Yöntemleri** oluştur seçeneği, özelliğini true olarak `GenerateDBDirectMethods` ayarlamaya eşdeğerdir. Özgün SQL deyimi yeterli bilgi sağlamasa veya sorgu güncelleştirilebilir bir sorgu olmadığı zaman seçeneği kullanılamaz. Bu durum, örneğin JOIN **sorgularında** ve tek bir (skaler) değer dönüşen sorgularda oluşabilir.

Sihirbazda **Gelişmiş** Seçenekler şunları yapabilirsiniz:

- Generate **SQL deyimleri** sayfasında tanımlanan SELECT deyimini temel alan INSERT, UPDATE ve DELETE deyimleri oluşturma
- İyimser eşzamanlılığı kullanma
- INSERT ve UPDATE deyimleri çalıştırıldıktan sonra veri tablosu yenilemenin gerekip gerek olmadığını belirtin

## <a name="configure-a-tableadapters-fill-method"></a>TableAdapter'ın Fill yöntemini yapılandırma

Bazen TableAdapter'ın tablosu şemasını değiştirmek istiyor olabilir. Bunu yapmak için TableAdapter'ın birincil yöntemini `Fill` değiştirirsiniz. TableAdapter'lar, ilişkili `Fill` veri tablosu şemasını tanımlayan birincil bir yöntem ile oluşturulur. Birincil `Fill` yöntem, TableAdapter'i ilk yapılandırıldığında girdiğiniz sorguyu veya saklı yordamı temel alır. Bu, DataSet Designer'daki veri tablosu altındaki ilk (en üstteki) yöntemdir.

![Birden çok sorgu içeren TableAdapter](../data-tools/media/tableadapter.gif)

TableAdapter'ın ana yönteminde yaptığınız tüm değişiklikler ilişkili veri `Fill` tablosu şemasına yansıtıldı. Örneğin, main yönteminde sorgudan bir sütunu kaldırmak, sütunu ilişkili `Fill` veri tablosundan da kaldırır. Buna ek olarak, main yönteminden sütunu kaldırmak, bu `Fill` TableAdapter için ek sorgulardan sütunu kaldırır.

TableAdapter için ek sorgular oluşturmak ve düzenlemek üzere TableAdapter Sorgu Yapılandırma Sihirbazı'nı kullanabilirsiniz. Skaler değer dönmediği sürece bu ek sorguların tablo şemasına uygun olması gerekir.  Her ek sorgunun belirttiğiniz bir adı olur.

Aşağıdaki örnekte adlı ek bir sorgunun nasıl çağrıl olduğu `FillByCity` gösterir:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>TableAdapter Sorgu Yapılandırma Sihirbazı'nı yeni bir sorguyla başlatmak için

1. veri kümenizi **Veri Kümesi Tasarımcısı.**

2. Yeni bir sorgu oluşturuyorsanız,  Araç Kutusunun **DataSet** sekmesinden  bir Sorgu nesnesini üzerine sürükleyin veya <xref:System.Data.DataTable> TableAdapter'ın kısayol menüsünden Sorgu Ekle'yi seçin.  Sorgu nesnesini, ilişkili **bir** olmadan TableAdapter **oluşturan Veri Kümesi Tasarımcısı** boş bir alana da <xref:System.Data.DataTable> sürükleyebilirsiniz. Bu sorgular yalnızca tek (skaler) değerler veya veritabanında UPDATE, INSERT veya DELETE komutları çalıştırabilirsiniz.

3. Veri **Bağlantınızı Seçin ekranında** sorgunun kullanabileceği bağlantıyı seçin veya oluşturun.

    > [!NOTE]
    > Bu ekran yalnızca tasarımcının kullanmak için uygun bağlantıyı belirleyene kadar veya kullanılabilir bağlantı yoksa görünür.

4. Komut **Türü Seçin ekranında,** veritabanından veri getirmek için aşağıdaki yöntemlerden birini seçin:

    - **Veritabanı SQL kullanarak** veri seçmek için SQL deyimi yazmanıza olanak sağlar.

    - **Yeni saklı yordam oluşturma,** sihirbazın belirtilen SELECT deyimini temel alan yeni bir saklı yordam (veritabanında) oluşturmanızı sağlar.

    - **Mevcut saklı yordamları** kullanma, sorguyu çalıştırarak mevcut bir saklı yordamı çalıştırmaya olanak sağlar.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Mevcut bir sorguda TableAdapter Sorgu Yapılandırması sihirbazını başlatmak için

- Mevcut bir TableAdapter sorgusunu düzenliyorsanız, sorguya sağ tıklayın ve kısayol **menüsünden Yapılandır'ı** seçin.

    > [!NOTE]
    > TableAdapter'ın ana sorgusuna sağ tıklarken TableAdapter ve şemayı yeniden <xref:System.Data.DataTable> yapılandırabilirsiniz. Ancak TableAdapter'da ek bir sorguya sağ tıkıldığında yalnızca seçili sorgu yapılandırılır. **TableAdapter Yapılandırma Sihirbazı** TableAdapter tanımını yeniden yapılandırırken **TableAdapter** Sorgu Yapılandırma Sihirbazı yalnızca seçili sorguyu yeniden yapılandırıyor.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>TableAdapter'a genel sorgu eklemek için

- Genel sorgular, SQL (skaler) değer veya değer getirmiyor olan sorgulardır. Genel işlevler genellikle ekleme, güncelleştirme ve silme gibi veritabanı işlemlerini gerçekleştirir. Ayrıca, bir tablodaki müşterilerin sayısı veya belirli bir siparişte yer alan tüm öğelerin toplam ücretleri gibi bilgileri de toplar.

     Araç Kutusunun **DataSet** **sekmesinden** sorgunun boş bir  alanına bir Sorgu nesnesi sürükleyerek genel **sorgular Veri Kümesi Tasarımcısı.**

- İstenen görevi gerçekleştiren bir sorgu (örneğin, ) `SELECT COUNT(*) AS CustomerCount FROM Customers` sağlar.

    > [!NOTE]
    > Bir **Sorgu nesnesini** doğrudan Veri Kümesi Tasarımcısı **yalnızca** skaler (tek) değer döndüren bir yöntem oluşturur. Seçen sorgu veya saklı yordam tek bir değerden fazla döndürene kadar, sihirbaz tarafından oluşturulan yöntem yalnızca tek bir değer döndürür. Örneğin sorgu, döndürülen verilerin ilk satırına karşılık gelen ilk sütunu döndürüldü.

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
