---
title: veri bağlamada arama tablolarını kullanma-Windows Forms
description: Visual Studio sınıfının LookupBindingPropertiesAttribute sınıfını kullanarak arama veri bağlamayı destekleyen Windows Forms bir kullanıcı denetimi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 279d45c46d42f1df2011e7164e66f5aa7fa8eecb543eed8eea3970edcf625765
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347525"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Arama veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows Forms verileri görüntülerken, **araç kutusundan** var olan denetimleri seçebilir veya uygulamanız standart denetimlerde kullanılamayan işlevselliği gerektiriyorsa özel denetimleri yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetimin nasıl oluşturulacağını gösterir <xref:System.ComponentModel.LookupBindingPropertiesAttribute> . ' İ uygulayan denetimler, <xref:System.ComponentModel.LookupBindingPropertiesAttribute> verilere bağlanabilen üç özellik içerebilir. Bu tür denetimler öğesine benzerdir <xref:System.Windows.Forms.ComboBox> .

denetim yazma hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Veri bağlama senaryolarında kullanım denetimleri yazma sırasında, aşağıdaki veri bağlama özniteliklerinden birini uygulamanız gerekir:

|Veri bağlama özniteliği kullanımı|
| - |
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute> <xref:System.Windows.Forms.TextBox> Verilerin tek bir sütununu (veya özelliğini) görüntüleyen bir gibi basit denetimleri uygulayın. daha fazla bilgi için bkz. [basit veri bağlamayı destekleyen Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> <xref:System.Windows.Forms.DataGridView> Verilerin listelerini (veya tabloları) görüntüleyen, gibi denetimleri uygulayın. daha fazla bilgi için bkz. [karmaşık veri bağlamayı destekleyen Windows Forms kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute> <xref:System.Windows.Forms.ComboBox> Verilerin listelerini (veya tabloları) görüntüleyen, ancak aynı zamanda tek bir sütun veya özellik sunmanız gereken denetimleri ' de uygulayın. (Bu işlem Bu izlenecek yol sayfasında açıklanmaktadır.)|

Bu izlenecek yol, iki tablodaki verilere bağlanan bir arama denetimi oluşturur. Bu örnekte, `Customers` `Orders` Northwind örnek veritabanındaki ve tabloları kullanılmaktadır. Arama denetimi, `CustomerID` tablodaki alana bağlanır `Orders` . Tablodan aramak için bu değeri kullanır `CompanyName` `Customers` .

Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- yeni bir **Windows Forms uygulaması** oluşturun.

- Projenize yeni bir **Kullanıcı denetimi** ekleyin.

- Kullanıcı denetimini görsel olarak tasarlayın.

- Özniteliğini uygulayın `LookupBindingProperty` .

- **Veri kaynağı yapılandırma** Sihirbazı ile bir veri kümesi oluşturun.

- Yeni denetimi kullanmak için, **veri kaynakları** penceresinde **Orders** tablosundaki **CustomerID** sütununu ayarlayın.

- Yeni denetimdeki verileri göstermek için bir form oluşturun.

## <a name="prerequisites"></a>Önkoşullar

bu izlenecek yol, SQL Server Express localdb ve Northwind örnek veritabanını kullanır.

1. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio Yükleyicisi** aracılığıyla yükleyin. **Visual Studio Yükleyicisi**, SQL Server Express localdb 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio, **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, Visual Studio Yükleyicisi **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **yürüt** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-app-project"></a>Windows Forms uygulama projesi oluşturma

ilk adım **Windows Forms bir uygulama** projesi oluşturmaktır.

1. Visual Studio, **dosya** menüsünde **yeni**  >  **Project**' yi seçin.

2. sol bölmedeki **Visual C#** ' ı veya **Visual Basic** genişletin ve sonra **Windows masaüstü**' nü seçin.

3. orta bölmede **Windows Forms uygulama** proje türünü seçin.

4. Projeyi **LookupControlWalkthrough** olarak adlandırın ve ardından **Tamam**' ı seçin.

     **LookupControlWalkthrough** projesi oluşturulur ve **Çözüm Gezgini** eklenir.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle

Bu izlenecek yol, **Kullanıcı denetiminden** bir arama denetimi oluşturur, bu nedenle **LookupControlWalkthrough** projesine bir **Kullanıcı denetim** öğesi ekleyin.

1. **Project** menüsünde **kullanıcı denetimi ekle**' yi seçin.

2. `LookupBox` **Ad** alanına yazın ve ardından **Ekle**' ye tıklayın.

     **LookupBox** denetimi **Çözüm Gezgini** eklenir ve tasarımcıda açılır.

## <a name="design-the-lookupbox-control"></a>LookupBox denetimini tasarlama

LookupBox denetimini tasarlamak için, <xref:System.Windows.Forms.ComboBox> **araç kutusundan** bir öğesini Kullanıcı denetiminin tasarım yüzeyine sürükleyin.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleyin

Veri bağlamayı destekleyen arama denetimleri için, uygulamasını uygulayabilirsiniz <xref:System.ComponentModel.LookupBindingPropertiesAttribute> .

1. **LookupBox** denetimini kod görünümüne geçirin. ( **Görünüm** menüsünde **kod** öğesini seçin.)

2. İçindeki kodu aşağıdaki gibi değiştirin `LookupBox` :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs" id="Snippet5":::

3. **Build** menüsünde **Build Solution** öğesini seçin.

## <a name="create-a-data-source-from-your-database"></a>Veritabanınızdan bir veri kaynağı oluşturun

Bu adım,  `Customers` `Orders` Northwind örnek veritabanındaki ve tabloları temel alan veri kaynağı Yapılandırma Sihirbazı 'nı kullanarak bir veri kaynağı oluşturur.

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

8. `Customers`Ve tablolarını seçip `Orders` **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve `Customers` `Orders` Tablolar **veri kaynakları** penceresinde görünür.

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>LookupBox denetimini kullanmak için Orders tablosunun CustomerID sütununu ayarlayın

**Veri kaynakları** penceresinde, öğeleri formunuza sürüklemeden önce oluşturulacak denetimi ayarlayabilirsiniz.

1. Tasarımcıda **Form1** ' i açın.

2. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

3. **Orders** düğümünü ( **Faks** sütununun altındaki **müşteriler** düğümünde bir düğüm) genişletin.

4. **Siparişler** düğümündeki açılan oka tıklayın ve denetim listesinden **Ayrıntılar** ' ı seçin.

5. **MüşteriNo** sütunundaki açılan oka tıklayın ( **siparişler** düğümünde) ve **Özelleştir**' i seçin.

6. **Veri Kullanıcı arabirimi özelleştirme seçenekleri** Iletişim kutusunda **Ilişkili denetimler** listesinden **LookupBox** ' ı seçin.

7. **Tamam**'a tıklayın.

8. **MüşteriNo** sütunundaki açılan oka tıklayın ve **LookupBox**' ı seçin.

## <a name="add-controls-to-the-form"></a>Forma denetim ekleme

Veri **kaynakları** penceresinden **Form1** üzerine sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

Windows formunda veriye bağlı denetimler oluşturmak için, **veri kaynakları** penceresinden **Orders** düğümünü Windows Form üzerine sürükleyin ve **lookupbox** denetiminin sütunda verileri göstermek için kullanıldığını doğrulayın `CustomerID` .

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Müşteriler tablosundan ara CompanyName 'e denetim bağlama

Arama bağlamalarını ayarlamak için **veri kaynakları** penceresinde ana **müşteriler** düğümünü seçin ve **Form1'in** içindeki **CustomerIDLookupBox** içindeki Birleşik giriş kutusuna sürükleyin.

Bu, tablodaki değeri koruyarak, tablosundan görüntülenecek veri bağlamayı ayarlar `CompanyName` `Customers` `CustomerID` `Orders` .

## <a name="run-the-application"></a>Uygulamayı çalıştırma

- Uygulamayı çalıştırmak için **F5**'e basın.

- Bazı kayıtlar arasında ilerleyin ve `CompanyName` `LookupBox` denetimin denetimde göründüğünü doğrulayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
