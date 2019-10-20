---
title: Bir veritabanına (birden çok tablo) veri kaydetme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bcb551cdcd5b2505c6ac536a440fcc3e70464bfb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648203"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Bir veritabanına (birden çok tablo) veri kaydetme

Uygulama geliştirmenin en yaygın senaryolarından biri, verileri bir Windows uygulamasında form üzerinde göstermek, verileri düzenlemek ve güncelleştirilmiş verileri veritabanına geri göndermek için kullanılır. Bu izlenecek yol, iki ilişkili tablodaki verileri görüntüleyen ve kayıtları nasıl düzenleydiğini ve değişiklikleri veritabanına geri kaydetmeyi gösteren bir form oluşturur. Bu örnekte, Northwind örnek veritabanındaki `Customers` ve `Orders` tabloları kullanılmaktadır.

Bir TableAdapter 'ın `Update` yöntemini çağırarak, uygulamanızdaki verileri veritabanına geri kaydedebilirsiniz. Tabloları **veri kaynakları** penceresinden bir form üzerine sürüklediğinizde, verileri kaydetmek için gereken kod otomatik olarak eklenir. Bir forma eklenen ek tablolar, bu kodun el ile eklenmesini gerektirir. Bu izlenecek yol, birden fazla tablodan güncelleştirmeleri kaydetmek için nasıl kod ekleneceğini gösterir.

Bu izlenecek yolda gösterilen görevler şunlardır:

- [Veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)ile uygulamanızda bir veri kaynağı oluşturma ve yapılandırma.

- [Veri kaynakları penceresindeki](add-new-data-sources.md#data-sources-window)öğelerin denetimlerini ayarlama. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- **Veri kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimler oluşturma.

- Veri kümesindeki her tabloda birkaç kaydı değiştirme.

- Veri kümesindeki güncelleştirilmiş verileri veritabanına geri göndermek için kodu değiştirme.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturma

Ya da C# Visual Basic için yeni bir **Windows Forms uygulama** projesi oluşturun. Projeyi **UpdateMultipleTablesWalkthrough**olarak adlandırın.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Bu adım, **veri kaynağı Yapılandırma Sihirbazı**'Nı kullanarak Northwind veritabanından bir veri kaynağı oluşturur. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanlarını kurma](../data-tools/installing-database-systems-tools-and-samples.md).

1. **Veri** menüsünde **veri kaynaklarını göster**' i seçin.

   **Veri kaynakları** penceresi açılır.

2. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** ekranında **veritabanı**' nı seçin ve ardından **İleri**' yi seçin.

4. **Veri bağlantınızı seçin** ekranında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu açın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet**sayfasında **İleri**' yi seçin.

7. **Veritabanı nesnelerinizi seçin** ekranında **Tablolar** düğümünü genişletin.

8. **Müşteriler** ve **siparişler** tablolarını seçip **son**' u seçin.

     **NorthwindDataSet** , projenize eklenir ve tablolar **veri kaynakları** penceresinde görüntülenir.

## <a name="set-the-controls-to-be-created"></a>Oluşturulacak denetimleri ayarlayın

Bu izlenecek yol için `Customers` tablosundaki veriler, verilerin ayrı denetimlerde görüntülendiği bir **Ayrıntılar** düzeninde yer aldığı yerdir. @No__t_0 tablodaki veriler, <xref:System.Windows.Forms.DataGridView> denetiminde görüntülenen **kılavuz** düzenidir.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Veri kaynakları penceresinde öğelerin bırakma türünü ayarlamak için

1. **Veri kaynakları** penceresinde, **müşteriler** düğümünü genişletin.

2. **Müşteriler düğümünde,** **müşteriler** tablosunun denetimini ayrı denetimler olarak değiştirmek için denetim listesinden **Ayrıntılar** ' ı seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Veri bağlantılı formu oluşturma

Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

1. Ana **müşteriler** düğümünü **veri kaynakları** penceresinden **Form1**üzerine sürükleyin.

     Açıklayıcı etiketlere sahip veriye bağlı denetimler, formda gezinmek için bir araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) ile birlikte görüntülenir. Bileşen tepsisinde bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> görüntülenir.

2. İlgili **siparişler** düğümünü **veri kaynakları** penceresinden **Form1**üzerine sürükleyin.

    > [!NOTE]
    > İlişkili **siparişler** düğümü, **Faks** sütununun altında bulunur ve **müşteriler** düğümünün bir alt düğümüdür.

     Kayıtlar üzerinde gezinmek için bir <xref:System.Windows.Forms.DataGridView> denetimi ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) formda görüntülenir. Bileşen tepsisinde bir `OrdersTableAdapter` ve <xref:System.Windows.Forms.BindingSource> görüntülenir.

## <a name="add-code-to-update-the-database"></a>Veritabanını güncelleştirmek için kod ekleme

**Müşteriler** ve **siparişler** TableAdapters `Update` yöntemlerini çağırarak veritabanını güncelleştirebilirsiniz. Varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator> **Kaydet** düğmesine yönelik bir olay işleyicisi, güncelleştirmeleri veritabanına göndermek için formun koduna eklenir. Bu yordam, güncelleştirmeleri doğru sırada göndermek için kodu değiştirir. Bu, başvurusal bütünlük hataları oluşturma olasılığını ortadan kaldırır. Kod ayrıca, bir try-catch bloğunda güncelleştirme çağrısını sarmalayarak hata işleme uygular. Kodu uygulamanızın gereksinimlerine uyacak şekilde değiştirebilirsiniz.

> [!NOTE]
> Netlik için bu izlenecek yol bir işlem kullanmaz. Ancak, iki veya daha fazla ilişkili tabloyu güncelleştiriyorsanız, tüm güncelleştirme mantığını bir işlem içine dahil edin. İşlem, herhangi bir değişiklik kaydedilmeden önce bir veritabanında yapılan tüm değişikliklerin başarılı olmasını sağlayan bir işlemdir. Daha fazla bilgi için bkz. [işlemler ve eşzamanlılık](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Uygulamaya güncelleştirme mantığı eklemek için

1. @No__t_1 **Kaydet** düğmesini seçin. Bu, kod düzenleyicisini `bindingNavigatorSaveItem_Click` olay işleyicisine açar.

2. Olay işleyicisindeki kodu, ilgili TableAdapters `Update` yöntemlerini çağırmak için değiştirin. Aşağıdaki kod ilk olarak her bir <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> ve <xref:System.Data.DataRowState.Modified>) güncelleştirilmiş bilgileri tutmak için üç geçici veri tablosu oluşturur. Güncelleştirmeler doğru sırada çalıştırılır. Kod aşağıdaki gibi görünmelidir:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Uygulamayı test etme

1. **F5**tuşuna basın.

2. Her tablodaki bir veya daha fazla kaydın verilerinde bazı değişiklikler yapın.

3. **Kaydet** düğmesini seçin.

4. Değişikliklerin kaydedildiğini doğrulamak için veritabanındaki değerleri kontrol edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)