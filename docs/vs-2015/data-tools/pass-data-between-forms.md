---
title: Formlar arasında veri geçirme | Microsoft Docs
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e14165ba2111f40898c00b3d01950425c042070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652909"
---
# <a name="pass-data-between-forms"></a>Formlar arasında veri geçirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, verileri bir formdan diğerine geçirmek için adım adım yönergeler sağlar. Northwind 'deki Customers ve Orders tablolarını kullanarak, bir form kullanıcıların bir müşteriyi seçmesini sağlar ve ikinci bir form seçili müşterinin siparişlerini görüntüler. Bu izlenecek yol, ikinci formda ilk formdan veri alan bir yöntemin nasıl oluşturulacağını gösterir.

> [!NOTE]
> Bu izlenecek yol, formlar arasında veri geçirmenin yalnızca bir yolunu gösterir. Verileri almak için ikinci bir Oluşturucu oluşturma veya ilk formdan verilerle ayarlanalabilen ortak bir özellik oluşturma dahil olmak üzere bir forma veri geçirmek için başka seçenekler vardır.

 Bu izlenecek yolda gösterilen görevler şunlardır:

- Yeni bir **Windows uygulaması** projesi oluşturma.

- [Veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)ile bir veri kümesi oluşturma ve yapılandırma.

- **Veri kaynakları** penceresinden öğeleri sürüklerken formda oluşturulacak denetimi seçme. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- **Veri kaynakları** penceresinden bir forma öğe sürükleyerek veri bağlantılı denetim oluşturma.

- Verileri göstermek için kılavuza sahip ikinci bir form oluşturma.

- Belirli bir müşteri için sipariş getirmek üzere TableAdapter sorgusu oluşturma.

- Formlar arasında veri geçirme.

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind örnek veritabanına erişim.

## <a name="create-the-windows-application"></a>Windows uygulaması oluşturma

#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için

1. **Dosya** menüsünden Yeni bir proje oluşturun.

2. Projeyi adlandırın `PassingDataBetweenForms` .

3. **Windows Forms uygulama**' yı seçin ve **Tamam**' ı tıklatın. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     **PassingDataBetweenForms** projesi oluşturulur ve **Çözüm Gezgini**eklenir.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Bir veritabanı modeli seçin** sayfasında, **veri kümesinin** belirtildiğinden emin olun ve ardından **İleri**' ye tıklayın.

5. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

6. Veritabanınız parola gerektiriyorsa ve hassas verileri dahil etme seçeneği etkinse, seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

7. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

8. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

9. **Müşteriler** ve **siparişler** tablolarını seçip **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve **müşteriler** ve **siparişler** tabloları **veri kaynakları** penceresinde görünür.

## <a name="create-the-first-form-form1"></a>İlk formu oluşturma (Form1)
 <xref:System.Windows.Forms.DataGridView> **Müşteriler** düğümünü **veri kaynakları** penceresinden form üzerine sürükleyerek veriye dayalı bir kılavuz (bir denetim) oluşturabilirsiniz.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Formda veriye bağlı bir kılavuz oluşturmak için

- Ana **müşteriler** düğümünü **veri kaynakları** penceresinden **Form1**üzerine sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Kayıt gezinmek için bir ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) **Form1**üzerinde görünür. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="create-the-second-form-form2"></a>İkinci formu oluşturma (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Verilerin iletilmesi için ikinci bir form oluşturmak için

1. **Proje** menüsünden **Windows formu Ekle**' yi seçin.

2. Varsayılan **Form2**adını bırakın ve **Ekle**' ye tıklayın.

3. Ana **siparişler** düğümünü **veri kaynakları** penceresinden **Form2**üzerine sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) **Form2**üzerinde görünür. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

4. Bileşen tepsisinden **OrdersBindingNavigator** öğesini silin.

     **OrdersBindingNavigator** **Form2**öğesinden kayboluyor.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Form1 üzerinde seçilen müşteri için Form2 'ye bir TableAdapter sorgusu ekleyin

#### <a name="to-create-a-tableadapter-query"></a>TableAdapter sorgusu oluşturmak için

1. **Çözüm Gezgini** **NorthwindDataSet. xsd** dosyasını çift tıklayın.

2. **OrdersTableAdapter**öğesine sağ tıklayın ve **Sorgu Ekle**' yi seçin.

3. **SQL deyimlerini kullan**varsayılan seçeneğini bırakın ve ardından **İleri**' ye tıklayın.

4. **Satırları döndüren Seç**varsayılan seçeneğini bırakın ve ardından **İleri**' ye tıklayın.

5. Temelinde döndürmek için sorguya bir WHERE yan tümcesi ekleyin `Orders` `CustomerID` . Sorgu aşağıdakine benzemelidir:

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Veritabanınız için doğru parametre söz dizimini doğrulayın. Örneğin, Microsoft Access 'te WHERE yan tümcesi şöyle görünür: `WHERE CustomerID = ?` .

6. **İleri**’ye tıklayın.

7. **DataTableMethod adı doldur**için yazın `FillByCustomerID` .

8. **Bir DataTable döndürün** seçeneğinin işaretini kaldırın ve ardından **İleri**' ye tıklayın.

9. **Son**'a tıklayın.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Verileri iletmek için Form2 üzerinde bir yöntem oluşturma

#### <a name="to-create-a-method-to-pass-data-to"></a>Verileri geçirmek için bir yöntem oluşturmak için

1. **Form2**' e sağ tıklayın ve **Kod Düzenleyicisi**'nde **Form2** ' yi açmak için **kodu görüntüle** ' yi seçin.

2. Aşağıdaki kodu yönteminden sonra **Form2** öğesine ekleyin `Form2_Load` :

     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Veri geçirmek ve Form2 göstermek için Form1 üzerinde bir yöntem oluşturun

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Verileri Form2 'e geçirmek için bir yöntem oluşturmak için

1. **Form1**' te, müşteri verileri kılavuzuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellikler** penceresinde **Olaylar**' a tıklayın.

3. **CellDoubleClick** olayına çift tıklayın.

     Kod Düzenleyicisi görünür.

4. Yöntem tanımını aşağıdaki örnekle eşleşecek şekilde güncelleştirin:

     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

- Uygulamayı çalıştırmak için F5'e basın.

- Bu müşterinin siparişleriyle **Form2** açmak için **Form1** içindeki bir müşteri kaydına çift tıklayın.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, formlar arasında veri geçirmeden sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- Veritabanı nesneleri eklemek veya kaldırmak için veri kümesini düzenleyebilirsiniz. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Verileri veritabanına geri kaydetme işlevselliği ekleme. Daha fazla bilgi için bkz. [verileri veritabanına geri kaydetme](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
