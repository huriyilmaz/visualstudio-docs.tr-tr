---
title: Veri bağlama ile Windows Forms Kullanıcı denetimi oluşturma
description: ComplexBindingPropertiesAttribute 'e sınıfını uygulayarak karmaşık veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturmayı anlayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 465636b2b5bbf1a47752b4f0917258e264172abd
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436790"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Karmaşık veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows uygulamalarındaki formlarda verileri görüntülerken **araç kutusundan** varolan denetimleri seçebilirsiniz. Ya da uygulamanız standart denetimlerde kullanılamayan işlevselliği gerektiriyorsa özel denetimler yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetimin nasıl oluşturulacağını gösterir <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> . , <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> `DataSource` Verilerine bağlanabilen ve özelliğini içeren denetimler `DataMember` . Bu tür denetimler veya ile benzerdir <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.ListBox> .

Denetim yazma hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Veri bağlama senaryolarında kullanılacak denetimleri yazma sırasında, aşağıdaki veri bağlama özniteliklerinden birini uygulamanız gerekir:

|Veri bağlama özniteliği kullanımı|
| - |
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute> <xref:System.Windows.Forms.TextBox> Verilerin tek bir sütununu (veya özelliğini) görüntüleyen bir gibi basit denetimleri uygulayın. Daha fazla bilgi için bkz. [basit veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> <xref:System.Windows.Forms.DataGridView> Verilerin listelerini (veya tabloları) görüntüleyen, gibi denetimleri uygulayın. (Bu işlem Bu izlenecek yol sayfasında açıklanmaktadır.)|
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute> <xref:System.Windows.Forms.ComboBox> Verilerin listelerini (veya tabloları) görüntüleyen, ancak tek bir sütun veya özellik sunmanız gereken, gibi denetimleri uygulayın. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Bu izlenecek yol, bir tablodaki veri satırlarını görüntüleyen karmaşık bir denetim oluşturur. Bu örnek, `Customers` Northwind örnek veritabanındaki tablosunu kullanır. Karmaşık kullanıcı denetimi, içindeki Customers tablosunu <xref:System.Windows.Forms.DataGridView> özel denetimde görüntüler.

Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Projenize yeni bir **Kullanıcı denetimi** ekleyin.

- Kullanıcı denetimini görsel olarak tasarlayın.

- Özniteliğini uygulayın `ComplexBindingProperty` .

- [Veri kaynağı Yapılandırma Sihirbazı](../data-tools/media/data-source-configuration-wizard.png)ile bir veri kümesi oluşturun.

- Yeni karmaşık denetimi kullanmak için [veri kaynakları penceresinde](add-new-data-sources.md#data-sources-window) **Customers** tablosunu ayarlayın.

- **Veri kaynakları** penceresinden **Form1** üzerine sürükleyerek yeni denetim ekleyin.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi** aracılığıyla yükleyin. **Visual Studio yükleyicisi** , SQL Server Express LocalDB 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

1. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu** ' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    1. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    1. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-app-project"></a>Windows Forms uygulama projesi oluşturma

İlk adım, C# veya Visual Basic için **Windows Forms bir uygulama** projesi oluşturmaktır. Projeyi **ComplexControlWalkthrough** olarak adlandırın.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle

Bu izlenecek yol, **Kullanıcı denetiminden** karmaşık bir veri bağlanabilir denetim oluşturduğundan, projeye bir **Kullanıcı denetim** öğesi ekleyin:

1. **Proje** menüsünden **Kullanıcı denetimi Ekle** ' yi seçin.

1. **Ad** alanına **ComplexDataGridView** yazın ve ardından **Ekle** ' ye tıklayın.

    **ComplexDataGridView** denetimi **Çözüm Gezgini** eklenir ve tasarımcıda açılır.

## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView denetimini tasarlama

Kullanıcı denetimine bir eklemek için <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView> **araç kutusundan** bir öğesini Kullanıcı denetiminin tasarım yüzeyine sürükleyin.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleyin

Veri bağlamayı destekleyen karmaşık denetimler için şunları uygulayabilirsiniz <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> :

1. **ComplexDataGridView** denetimini Code View olarak değiştirin. ( **Görünüm** menüsünde **kod** ' i seçin.)

1. İçindeki kodu aşağıdaki gibi değiştirin `ComplexDataGridView` :

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. **Build** menüsünde **Build Solution** öğesini seçin.

## <a name="create-a-data-source-from-your-database"></a>Veritabanınızdan bir veri kaynağı oluşturun

Northwind örnek veritabanındaki tabloya dayalı bir veri kaynağı oluşturmak için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanın `Customers` :

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster** ' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri** ' ye tıklayın.

4. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

   - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

   - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri** ' ye tıklayın.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri** ' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

8. Tabloyu seçin `Customers` ve ardından **son** ' a tıklayın.

   **NorthwindDataSet** , projenize eklenir ve `Customers` tablo **veri kaynakları** penceresinde görünür.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Müşteriler tablosunu ComplexDataGridView denetimini kullanacak şekilde ayarlama

**Veri kaynakları** penceresinde, öğeleri formunuza sürüklemeden önce oluşturulacak denetimi ayarlayabilirsiniz:

1. Tasarımcıda **Form1** ' i açın.

1. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

1. **Müşteriler** düğümündeki açılan oka tıklayın ve **Özelleştir** ' i seçin.

1. **Veri Kullanıcı arabirimi özelleştirme seçenekleri** Iletişim kutusunda **Ilişkili denetimler** listesinden **ComplexDataGridView** ' i seçin.

1. Tablodaki açılan oka tıklayın `Customers` ve denetim listesinden **ComplexDataGridView** ' i seçin.

## <a name="add-controls-to-the-form"></a>Forma denetim ekleme

Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz. Ana **müşteriler** düğümünü **veri kaynakları** penceresinden form üzerine sürükleyin. Tablo verilerini göstermek için **ComplexDataGridView** denetiminin kullanıldığını doğrulayın.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı çalıştırmak için **F5** 'e basın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bazı tipik sonraki adımlar şunlardır:

- Özel denetimlerinizi, diğer uygulamalarda yeniden kullanabilmek için bir denetim kitaplığına yerleştirme.

- Arama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/index)
