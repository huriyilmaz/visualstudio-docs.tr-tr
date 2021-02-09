---
title: Basit veri bağlamayı destekleyen Kullanıcı denetimleri oluşturma
description: Visual Studio 'da DefaultBindingPropertyAttribute sınıfını kullanarak basit veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30f6d338b4e27677c14dfa4e5ff8793e67f4c6ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867119"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Basit veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows uygulamalarındaki formlarda verileri görüntülerken, **araç kutusundan** varolan denetimleri seçebilir veya uygulamanız standart denetimlerde kullanılamayan işlevselliği gerektiriyorsa özel denetimleri yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetimin nasıl oluşturulacağını gösterir <xref:System.ComponentModel.DefaultBindingPropertyAttribute> . Uygulayan denetimler, <xref:System.ComponentModel.DefaultBindingPropertyAttribute> verilere bağlanabilen bir özellik içerebilir. Bu tür denetimler veya ile benzerdir <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.CheckBox> .

Denetim yazma hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Veri bağlama senaryolarında kullanılacak denetimleri yazarken, aşağıdaki veri bağlama özniteliklerinden birini uygulamalısınız:

|Veri bağlama özniteliği kullanımı|
| - |
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute> <xref:System.Windows.Forms.TextBox> Verilerin tek bir sütununu (veya özelliğini) görüntüleyen bir gibi basit denetimleri uygulayın. (Bu işlem Bu izlenecek yol sayfasında açıklanmaktadır.)|
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> <xref:System.Windows.Forms.DataGridView> Verilerin listelerini (veya tabloları) görüntüleyen, gibi denetimleri uygulayın. Daha fazla bilgi için bkz. [karmaşık veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute> <xref:System.Windows.Forms.ComboBox> Verilerin listelerini (veya tabloları) görüntüleyen, ancak tek bir sütun veya özellik sunmanız gereken, gibi denetimleri uygulayın. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Bu izlenecek yol, tablodaki tek bir sütundan verileri görüntüleyen basit bir denetim oluşturur. Bu örnek, `Phone` `Customers` Northwind örnek veritabanındaki tablosunun sütununu kullanır. Basit Kullanıcı denetimi, müşterilerin telefon numaralarını kullanarak standart telefon numarası biçiminde görüntüler <xref:System.Windows.Forms.MaskedTextBox> ve maskeyi bir telefon numarası olarak ayarlar.

Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Yeni bir **Windows Forms uygulaması** oluşturun.

- Projenize yeni bir **Kullanıcı denetimi** ekleyin.

- Kullanıcı denetimini görsel olarak tasarlayın.

- Özniteliğini uygulayın `DefaultBindingProperty` .

- **Veri kaynağı yapılandırma** Sihirbazı ile bir veri kümesi oluşturun.

- **Veri kaynakları** penceresindeki **Telefon** sütununu yeni denetimi kullanacak şekilde ayarlayın.

- Yeni denetimdeki verileri göstermek için bir form oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi** aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, **Visual Studio yükleyicisi** **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **Çalıştır** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma

İlk adım **Windows Forms bir uygulama** oluşturmaktır:

1. Visual Studio 'da, **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin.

2. Sol bölmedeki **Visual C#** veya **Visual Basic** genişletip **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **SimpleControlWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **SimpleControlWalkthrough** projesi oluşturulur ve **Çözüm Gezgini** eklenir.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle

Bu izlenecek yol, bir **Kullanıcı denetiminden** basit bir veri bağlanabilir denetim oluşturur. **SimpleControlWalkthrough** projesine bir **Kullanıcı denetim** öğesi ekleyin:

1. **Proje** menüsünden **Kullanıcı denetimi Ekle**' yi seçin.

2. Ad alanına **PhoneNumberBox** yazın ve **Ekle**' ye tıklayın.

     **PhoneNumberBox** denetimi **Çözüm Gezgini** eklenir ve tasarımcıda açılır.

## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox denetimini tasarlama

Bu izlenecek yol, <xref:System.Windows.Forms.MaskedTextBox> **PhoneNumberBox** denetimini oluşturmak için var olan üzerine genişletilir:

1. <xref:System.Windows.Forms.MaskedTextBox> **Araç kutusundan** bir öğesini Kullanıcı denetiminin tasarım yüzeyine sürükleyin.

2. Yeni sürüklediğiniz seçtiğiniz akıllı etiketi seçin <xref:System.Windows.Forms.MaskedTextBox> ve **maskeyi ayarla**' yı seçin.

3. **Giriş maskesi** Iletişim kutusunda **telefon numarası** ' nı seçin ve maskeyi ayarlamak için **Tamam** ' ı tıklatın.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleyin

Veri bağlamayı destekleyen basit denetimler için <xref:System.ComponentModel.DefaultBindingPropertyAttribute> aşağıdakileri uygulayın:

1. **PhoneNumberBox** denetimini kod görünümüne geçirin. ( **Görünüm** menüsünde **kod** öğesini seçin.)

2. **PhoneNumberBox** içindeki kodu aşağıdaki kodla değiştirin:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. **Build** menüsünde **Build Solution** öğesini seçin.

## <a name="create-a-data-source-from-your-database"></a>Veritabanınızdan bir veri kaynağı oluşturun

Bu adım, Northwind örnek veritabanındaki tabloya dayalı bir veri kaynağı oluşturmak için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanır `Customers` . Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanlarını kurma](../data-tools/installing-database-systems-tools-and-samples.md).

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seç** sayfasında, **veritabanı**' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

8. Tabloyu seçin `Customers` ve ardından **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve `Customers` tablo **veri kaynakları** penceresinde görünür.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Telefon sütununu PhoneNumberBox denetimini kullanacak şekilde ayarlama

**Veri kaynakları** penceresinde, öğeleri formunuza sürüklemeden önce oluşturulacak denetimi ayarlayabilirsiniz:

1. Tasarımcıda **Form1** ' i açın.

2. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

3. **Müşteriler** düğümündeki açılan oka tıklayın ve denetim listesinden **Ayrıntılar** ' ı seçin.

4. **Telefon** sütunundaki açılan oka tıklayın ve **Özelleştir**' i seçin.

5. **Veri Kullanıcı arabirimi özelleştirme seçenekleri** Iletişim kutusunda **Ilişkili denetimler** listesinden **PhoneNumberBox** ' ı seçin.

6. **Telefon** sütunundaki açılan oka tıklayın ve **PhoneNumberBox**' ı seçin.

## <a name="add-controls-to-the-form"></a>Forma denetim ekleme

Veri **kaynakları** penceresinden forma öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

Formda veriye bağlı denetimler oluşturmak için, **veri kaynakları** penceresinden ana **müşteriler** düğümünü form üzerine sürükleyin ve **Telefonenumberbox** denetiminin **Telefon** sütunundaki verileri göstermek için kullanıldığını doğrulayın.

Açıklayıcı etiketlere sahip veriye bağlı denetimler, formda gezinmek için bir araç şeridinde () birlikte görüntülenir <xref:System.Windows.Forms.BindingNavigator> . Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı çalıştırmak için **F5**'e basın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bazı tipik sonraki adımlar şunlardır:

- Özel denetimlerinizi, diğer uygulamalarda yeniden kullanabilmek için bir denetim kitaplığına yerleştirme.

- Daha karmaşık veri bağlama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için bkz. [karmaşık veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) ve [Arama veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
