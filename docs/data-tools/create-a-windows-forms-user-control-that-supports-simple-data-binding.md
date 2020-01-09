---
title: Basit veri bağlamayı destekleyen bir kullanıcı denetimi oluşturma
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ace5f9dd2781697525e7041be6cbd8df050bca97
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586834"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Basit veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows uygulamalarındaki formlarda verileri görüntülerken, **araç kutusundan**varolan denetimleri seçebilir veya uygulamanız standart denetimlerde kullanılamayan işlevselliği gerektiriyorsa özel denetimleri yazabilirsiniz. Bu izlenecek yol, <xref:System.ComponentModel.DefaultBindingPropertyAttribute>uygulayan bir denetimin nasıl oluşturulacağını gösterir. <xref:System.ComponentModel.DefaultBindingPropertyAttribute> uygulayan denetimler, verilere bağlanabilen bir özellik içerebilir. Bu tür denetimler <xref:System.Windows.Forms.TextBox> veya <xref:System.Windows.Forms.CheckBox>benzerdir.

Denetim yazma hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Veri bağlama senaryolarında kullanılacak denetimleri yazarken, aşağıdaki veri bağlama özniteliklerinden birini uygulamalısınız:

|Veri bağlama özniteliği kullanımı|
| - |
|Verilerin tek bir sütununu (veya özelliği) görüntüleyen <xref:System.Windows.Forms.TextBox>gibi basit denetimlerde <xref:System.ComponentModel.DefaultBindingPropertyAttribute> uygulayın. (Bu işlem Bu izlenecek yol sayfasında açıklanmaktadır.)|
|Denetimlerin listesini (veya tabloları) görüntüleyen <xref:System.Windows.Forms.DataGridView>gibi denetimlerde <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> uygulayın. Daha fazla bilgi için bkz. [karmaşık veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Verilerin listelerini (veya tabloları) görüntüleyen ancak tek bir sütun veya özellik sunması gereken <xref:System.Windows.Forms.ComboBox>gibi denetimlerde <xref:System.ComponentModel.LookupBindingPropertiesAttribute> uygulayın. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Bu izlenecek yol, tablodaki tek bir sütundan verileri görüntüleyen basit bir denetim oluşturur. Bu örnek, Northwind örnek veritabanındaki `Customers` tablosunun `Phone` sütununu kullanır. Basit Kullanıcı denetimi, müşterilerin telefon numaralarını bir <xref:System.Windows.Forms.MaskedTextBox> kullanarak ve maskeyi bir telefon numarasına ayarlayarak standart telefon numarası biçiminde görüntüler.

Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Yeni bir **Windows Forms uygulaması**oluşturun.

- Projenize yeni bir **Kullanıcı denetimi** ekleyin.

- Kullanıcı denetimini görsel olarak tasarlayın.

- `DefaultBindingProperty` özniteliğini uygulayın.

- **Veri kaynağı yapılandırma** Sihirbazı ile bir veri kümesi oluşturun.

- **Veri kaynakları** penceresindeki **Telefon** sütununu yeni denetimi kullanacak şekilde ayarlayın.

- Yeni denetimdeki verileri göstermek için bir form oluşturun.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yol, SQL Server Express LocalDB ve Northwind örnek veritabanını kullanır.

1. SQL Server Express LocalDB yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio yükleyicisi**aracılığıyla yükleyin. **Visual Studio yükleyicisi**, SQL Server Express LocalDB 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio 'da **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, **Visual Studio yükleyicisi** **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiği sorgu düzenleyiciye yapıştırın ve ardından **yürütme** düğmesi.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Windows Forms uygulaması oluşturma

İlk adım **Windows Forms bir uygulama**oluşturmaktır:

1. Visual Studio 'da, **Dosya** menüsünde **Yeni** > **projesi**' ni seçin.

2. Sol bölmedeki **görsel C#**  veya **Visual Basic** ' i genişletin ve ardından **Windows Masaüstü**' nü seçin.

3. Orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **SimpleControlWalkthrough**olarak adlandırın ve ardından **Tamam**' ı seçin.

     **SimpleControlWalkthrough** projesi oluşturulur ve **Çözüm Gezgini**eklenir.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle

Bu izlenecek yol, bir **Kullanıcı denetiminden**basit bir veri bağlanabilir denetim oluşturur. **SimpleControlWalkthrough** projesine bir **Kullanıcı denetim** öğesi ekleyin:

1. **Proje** menüsünden **Kullanıcı denetimi Ekle**' yi seçin.

2. Ad alanına **PhoneNumberBox** yazın ve **Ekle**' ye tıklayın.

     **PhoneNumberBox** denetimi **Çözüm Gezgini**eklenir ve tasarımcıda açılır.

## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox denetimini tasarlama

Bu izlenecek yol, **PhoneNumberBox** denetimini oluşturmak için mevcut <xref:System.Windows.Forms.MaskedTextBox> üzerine genişletilir:

1. **Araç kutusundan** bir <xref:System.Windows.Forms.MaskedTextBox> Kullanıcı denetiminin tasarım yüzeyine sürükleyin.

2. Yeni sürüklediğiniz <xref:System.Windows.Forms.MaskedTextBox> akıllı etiketini seçin ve **maskeyi ayarla**' yı seçin.

3. **Giriş maskesi** Iletişim kutusunda **telefon numarası** ' nı seçin ve maskeyi ayarlamak için **Tamam** ' ı tıklatın.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleyin

Veri bağlamayı destekleyen basit denetimler için <xref:System.ComponentModel.DefaultBindingPropertyAttribute>uygulayın:

1. **PhoneNumberBox** denetimini kod görünümüne geçirin. ( **Görünüm** menüsünde **kod**öğesini seçin.)

2. **PhoneNumberBox** içindeki kodu aşağıdaki kodla değiştirin:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. Gelen **derleme** menüsünde seçin **Çözümü Derle**.

## <a name="create-a-data-source-from-your-database"></a>Veritabanınızdan bir veri kaynağı oluşturun

Bu adım, Northwind örnek veritabanındaki `Customers` tablosuna dayalı bir veri kaynağı oluşturmak için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanır. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: örnek veritabanlarını kurma](../data-tools/installing-database-systems-tools-and-samples.md).

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seç** sayfasında, **veritabanı**' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

8. `Customers` tablosunu seçin ve ardından **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve `Customers` tablosu **veri kaynakları** penceresinde görünür.

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

Açıklayıcı etiketlere sahip veriye bağlı denetimler, formda gezinmek için bir araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) ile birlikte görüntülenir. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="run-the-application"></a>Uygulamayı çalıştırın

Uygulamayı çalıştırmak için **F5**'e basın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bazı tipik sonraki adımlar şunlardır:

- Özel denetimlerinizi, diğer uygulamalarda yeniden kullanabilmek için bir denetim kitaplığına yerleştirme.

- Daha karmaşık veri bağlama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için bkz. [karmaşık veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) ve [Arama veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Deneti veri kaynakları penceresinden sürüklendiğinde oluşturulacak şekilde ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
