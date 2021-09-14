---
title: Bir veritabanına (birden çok tablo) veri kaydetme
description: Bu kılavuzda, veri kümesinde DataSet araçlarını kullanarak birden çok tablodan veritabanına Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 772a4001ad999ce4c585eeac5bf5ea9b3ba97ab1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631190"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Bir veritabanına (birden çok tablo) veri kaydetme

Uygulama geliştirmenin en yaygın senaryolarından biri, verileri bir Windows uygulamasındaki bir formda görüntülemek, verileri düzenlemek ve güncelleştirilmiş verileri veritabanına geri göndermektir. Bu kılavuz, iki ilişkili tablodan verileri görüntüleyen ve kayıtları düzenlemeyi ve değişiklikleri veritabanına geri kaydetmeyi gösteren bir form oluşturur. Bu örnekte `Customers` `Orders` Northwind örnek veritabanındaki ve tabloları kullanılır.

TableAdapter yöntemini çağırarak uygulamanıza verileri `Update` veritabanına geri kaydedebilirsiniz. Veri Kaynakları penceresindeki **tabloları bir** forma sürüklerken, verileri kaydetmek için gereken kod otomatik olarak eklenir. Forma eklenen tüm ek tablolar, bu kodun el ile eklerini gerektirir. Bu kılavuzda, birden fazla tablodan güncelleştirmeleri kaydetmek için kod ekleme adımlarını gösterir.

Bu kılavuzda gösterilen görevler şunlardır:

- Veri Kaynağı Yapılandırma Sihirbazı ile uygulamanıza bir veri [kaynağı oluşturma ve yapılandırma.](../data-tools/media/data-source-configuration-wizard.png)

- Veri Kaynakları penceresinde öğelerin [denetimlerini ayarlama.](add-new-data-sources.md#data-sources-window) Daha fazla bilgi için [bkz. Veri Kaynakları penceresinden sürüklenrken oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

- Veri Kaynakları penceresindeki öğeleri form üzerine **sürükleyerek veriye bağlı** denetimler oluşturma.

- Veri kümesinde her bir tablodaki birkaç kaydı değiştirme.

- Veri kümesinde güncelleştirilmiş verileri veritabanına geri göndermek için kodu değiştirme.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi,** yerel SQL Server Express veri depolama ve işleme iş yükünün bir parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz. 

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün bir parçası olarak** Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturma

C# **veya Windows için yeni** bir FormLar Uygulaması projesi Visual Basic. Projeye **UpdateMultipleTablesWalkthrough adını girin.**

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Bu adım, Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak Northwind **veritabanından bir veri kaynağı oluşturur.** Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Örnek veritabanlarını yükleme.](../data-tools/installing-database-systems-tools-and-samples.md)

1. Veri menüsünde **Veri** Kaynaklarını **Göster'i seçin.**

   Veri **Kaynakları** penceresi açılır.

2. Veri Kaynakları **penceresinde Yeni** Veri Kaynağı **Ekle'yi seçerek** Veri Kaynağı **Yapılandırma Sihirbazı'nı başlatın.**

3. Veri Kaynağı **Türü Seçin ekranında Veritabanı'ı** **ve ardından** Sonraki'yi **seçin.**

4. Veri **Bağlantınızı Seçin** ekranında, aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         -veya-

    - Bağlantı **Ekle/Değiştir** iletişim **kutusunu açmak için Yeni Bağlantı'ya** tıklayın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etmek için seçeneğini belirtin ve ardından Sonraki seçeneğini **belirleyin.**

6. Bağlantı **dizesini Uygulama Yapılandırma dosyasına kaydet'de, Sonraki'yi** **seçin.**

7. Veritabanı **Nesnelerinizi seçin ekranında** Tablolar **düğümünü** genişletin.

8. **Customers** ve **Orders tablolarını** ve ardından Son'ı **seçin.**

     **NorthwindDataSet** projenize eklenir ve tablolar Veri Kaynakları **penceresinde** görüntülenir.

## <a name="set-the-controls-to-be-created"></a>Oluşturulacak denetimleri ayarlama

Bu kılavuzda, tablodaki `Customers` veriler, tek tek **denetimlerde** verilerin görüntülendiğinde bir Ayrıntılar düzenindedir. Tablodaki `Orders` veriler, **denetimde** görüntülenen bir Kılavuz düzenindedir. <xref:System.Windows.Forms.DataGridView>

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Veri Kaynakları penceresindeki öğelerin bırakma türünü ayarlamak için

1. Veri **Kaynakları penceresinde** Müşteriler **düğümünü** genişletin.

2. Müşteriler **düğümünde** denetim **listesinden** Ayrıntılar'ı seçerek **Customers** tablosuna ilişkin denetimi tek tek denetimler olarak değiştirebilirsiniz. Daha fazla bilgi için [bkz. Veri Kaynakları penceresinden sürüklenrken oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

## <a name="create-the-data-bound-form"></a>Veriye bağlı formu oluşturma

Veri Kaynakları penceresindeki öğeleri form üzerine sürükleyerek **veriye bağlı** denetimler oluşturabilirsiniz.

1. Ana Müşteriler **düğümünü** Veri Kaynakları **penceresinden** **Form1'e sürükleyin.**

     Formda, kayıtlarda gezinmek için bir araç şeridi ( ) ile birlikte açıklayıcı <xref:System.Windows.Forms.BindingNavigator> etiketlere sahip veriye bağlı denetimler görüntülenir. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , ve bileşenleri bileşen <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

2. İlgili Siparişler **düğümünü** Veri Kaynakları **penceresinden** **Form1'e sürükleyin.**

    > [!NOTE]
    > İlgili **Siparişler** düğümü Faks sütunlarının **altında** bulunur ve Müşteriler düğümünün bir alt **düğümü** olur.

     Formda <xref:System.Windows.Forms.DataGridView> kayıtlarda gezinmek için bir denetim ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) görüntülenir. ve, `OrdersTableAdapter` <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görüntülenir.

## <a name="add-code-to-update-the-database"></a>Veritabanını güncelleştirmek için kod ekleme

Customers ve `Update` Orders TableAdapters yöntemlerini  çağırarak **veritabanını** güncelleştirebilirsiniz. Varsayılan olarak, veritabanına güncelleştirme **göndermek için** formun koduna Kaydet düğmesi için bir <xref:System.Windows.Forms.BindingNavigator> olay işleyicisi eklenir. Bu yordam, güncelleştirmeleri doğru sırada göndermek için kodu değiştiren bir yordamdır. Bu, bilgi tutarlılığı hataları olasılığını ortadan kaldırıyor. Kod ayrıca güncelleştirme çağrısını try-catch bloğuna sarmalamayla hata işlemeyi de uygulamaya alır. Kodu, uygulamanın ihtiyaçlarına uyacak şekilde değiştirebilirsiniz.

> [!NOTE]
> Netlik sağlamak için bu kılavuzda işlem kullanmaz. Ancak, iki veya daha fazla ilişkili tablo güncelleştiriyorsanız, bir işlem içindeki tüm güncelleştirme mantığını ekleyin. İşlem, herhangi bir değişiklik işlenmeden önce veritabanında yapılan tüm ilgili değişikliklerin başarılı olduğunu garanti eden bir işlemdir. Daha fazla bilgi için [bkz. İşlemler ve Eşzamanlılık.](/dotnet/framework/data/adonet/transactions-and-concurrency)

### <a name="to-add-update-logic-to-the-application"></a>Uygulamaya güncelleştirme mantığı eklemek için

1. üzerinde **Kaydet** düğmesini <xref:System.Windows.Forms.BindingNavigator> seçin. Bu, Kod Düzenleyicisi'ni olay `bindingNavigatorSaveItem_Click` işleyicisinde açar.

2. İlgili TableAdapter'ların yöntemlerini çağıracak olay `Update` işleyicisi kodunu değiştirin. Aşağıdaki kod önce her biri ( , ve ) için güncelleştirilmiş bilgileri tutmak için üç <xref:System.Data.DataRowState> <xref:System.Data.DataRowState.Deleted> geçici veri tablosu <xref:System.Data.DataRowState.Added> <xref:System.Data.DataRowState.Modified> oluşturur. Güncelleştirmeler doğru sırada çalıştır. Kodun aşağıdaki gibi olması gerekir:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs" id="Snippet10":::

## <a name="test-the-application"></a>Uygulamayı test edin

1. **F5 tuşuna basın.**

2. Her tablodaki bir veya daha fazla kaydın verisinde bazı değişiklikler yapın.

3. **Kaydet** düğmesini seçin.

4. Değişikliklerin kaydedilebilir olduğunu doğrulamak için veritabanındaki değerleri kontrol edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
