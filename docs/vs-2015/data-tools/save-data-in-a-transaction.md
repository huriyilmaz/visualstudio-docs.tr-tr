---
title: Verileri bir işlemde kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671083"
---
# <a name="save-data-in-a-transaction"></a>İşleme veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, ad alanını kullanarak bir işlemde nasıl veri kaydedileceğini gösterir <xref:System.Transactions> . Bu örnekte, `Customers` `Orders` Northwind örnek veritabanındaki ve tabloları kullanılmaktadır.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yol, Northwind örnek veritabanına erişim gerektirir.

## <a name="create-a-windows-application"></a>Windows uygulaması oluşturma
 İlk adım bir **Windows uygulaması**oluşturmaktır.

#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için

1. Visual Studio 'da, **Dosya** menüsünde Yeni bir **Proje**oluşturun.

2. Projeyi **SavingDataInATransactionWalkthrough**olarak adlandırın.

3. **Windows uygulaması**' nı seçin ve ardından **Tamam**' ı seçin. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     **SavingDataInATransactionWalkthrough** projesi oluşturulup **Çözüm Gezgini**eklenir.

## <a name="create-a-database-data-source"></a>Veritabanı veri kaynağı oluşturma
 Bu adım, Northwind örnek veritabanındaki ve tablolarını temel alan bir veri kaynağı oluşturmak için [veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) ' nı kullanır `Customers` `Orders` .

#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde**veri kaynaklarını göster**' i seçin.

2. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin**ekranında **veritabanı**' nı seçin ve ardından **İleri**' yi seçin.

4. **Veri bağlantınızı seçin**ekranında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         -veya-

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** Iletişim kutusunu başlatın ve Northwind veritabanına bir bağlantı oluşturun.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** ekranında, **İleri**' yi seçin.

7. **Veritabanı nesnelerinizi seçin** ekranında **Tablolar** düğümünü genişletin.

8. `Customers`Ve tablolarını seçip `Orders` **son**' u seçin.

     **NorthwindDataSet** , projenize eklenir ve `Customers` `Orders` Tablolar **veri kaynakları** penceresinde görünür.

## <a name="addcontrols-to-the-form"></a>Form için addcontrols
 Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows formunda veriye bağlı denetimler oluşturmak için

- **Veri kaynakları** penceresinde, **müşteriler** düğümünü genişletin.

- Ana **müşteriler** düğümünü **veri kaynakları** penceresinden **Form1**üzerine sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir denetim ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) formda görüntülenir. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

- İlgili **siparişler** düğümünü (ana **siparişler** düğümünü değil, **Faks** sütununun altındaki Ilişkili alt tablo düğümünü) **CustomersDataGridView**altında bulunan form üzerine sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Form üzerinde görünür. Bir OrdersTableAdapter ve <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görünür.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System. Transactions derlemesine bir başvuru ekleyin
 İşlemler <xref:System.Transactions> ad alanını kullanır. System. Transactions derlemesine bir proje başvurusu varsayılan olarak eklenmez, bu yüzden el ile eklemeniz gerekir.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System. Transactions DLL dosyasına bir başvuru eklemek için

1. **Proje** menüsünde,**Başvuru Ekle**' yi seçin.

2. **System. Transactions**( **.net** sekmesinde) öğesini seçin ve ardından **Tamam**' ı seçin.

     **System. Transactions** öğesine bir başvuru projeye eklenir.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator 'ın saveItem düğmesindeki kodu Değiştir
 Formunuza bırakılan ilk tablo için, kod varsayılan olarak `click` , üzerinde Kaydet düğmesinin olayına eklenir <xref:System.Windows.Forms.BindingNavigator> . Ek tabloları güncelleştirmek için el ile kod eklemeniz gerekir. Bu izlenecek yol için, Kaydet düğmesinin tıklama olay işleyicisindeki mevcut kaydetme kodunu yeniden tasarlıyoruz. Ayrıca, satırın eklenmesi veya silinmesi gerektiğine bağlı olarak belirli güncelleştirme işlevlerini sağlamak için birkaç yöntem de oluşturacağız.

#### <a name="to-modify-the-auto-generated-save-code"></a>Otomatik olarak oluşturulan kaydetme kodunu değiştirmek için

1. **CustomersBindingNavigator** (disket simgesini içeren düğme) üzerinde **Kaydet** düğmesini seçin.

2. `CustomersBindingNavigatorSaveItem_Click` yöntemini aşağıdaki kod ile değiştirin:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   İlgili verilerde yapılan değişiklikleri mutabık kılma sırası aşağıdaki gibidir:

- Alt kayıtları silin. (Bu durumda, tablodaki kayıtları silin `Orders` .)

- Üst kayıtları silin. (Bu durumda, tablodaki kayıtları silin `Customers` .)

- Üst kayıtları ekleyin. (Bu durumda, kayıtları `Customers` tablosuna ekleyin.)

- Alt kayıtları ekleyin. (Bu durumda, kayıtları `Orders` tablosuna ekleyin.)

#### <a name="to-delete-existing-orders"></a>Mevcut siparişleri silmek için

- Aşağıdaki `DeleteOrders` yöntemi **Form1**öğesine ekleyin:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Mevcut müşterileri silmek için

- Aşağıdaki `DeleteCustomers` yöntemi **Form1**öğesine ekleyin:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Yeni müşteriler eklemek için

- Aşağıdaki `AddNewCustomers` yöntemi **Form1**öğesine ekleyin:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Yeni siparişler eklemek için

- Aşağıdaki `AddNewOrders` yöntemi **Form1**öğesine ekleyin:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

- Uygulamayı çalıştırmak için **F5** ' i seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
