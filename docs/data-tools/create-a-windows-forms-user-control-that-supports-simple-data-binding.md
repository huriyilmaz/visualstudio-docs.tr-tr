---
title: Basit veri bağlamayı destekleyen kullanıcı denetimleri oluşturma
description: Visual Studio'de DefaultBindingPropertyAttribute sınıfını kullanarak basit veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi Visual Studio.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6956740daec7a782bca3d265d7c868dcd7b2c4dec47fde4b0416d4d9d6cd6f5b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347512"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Basit veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Windows uygulamalarında formlarda veri görüntülerken, **Araç** Kutusundan mevcut denetimleri seçebilir veya uygulamanıza standart denetimlerde mevcut olmayan işlevler gerektiriyorsa özel denetimler oluşturabilirsiniz. Bu kılavuz, uygulayan bir denetimin nasıl oluşturuldığını <xref:System.ComponentModel.DefaultBindingPropertyAttribute> gösterir. uygulayan <xref:System.ComponentModel.DefaultBindingPropertyAttribute> denetimler, verilere bağlanan tek bir özellik içerebilir. Bu tür denetimler veya ile <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.CheckBox> benzerdir.

Denetim yazma hakkında daha fazla bilgi için [bkz. Tasarım Zamanında Windows Form Denetimleri Geliştirme.](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)

Veri bağlama senaryolarında kullanmak üzere denetimler yazarken, aşağıdaki veri bağlama özniteliklerinden birini uygulamanız gerekir:

|Veri bağlama özniteliği kullanımı|
| - |
|Tek <xref:System.ComponentModel.DefaultBindingPropertyAttribute> bir veri sütununu (veya özelliğini) görüntülemek için gibi basit <xref:System.Windows.Forms.TextBox> denetimler üzerinde gerçekleştirin. (Bu işlem bu kılavuz sayfasında açıklanmıştır.)|
|Veri <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> listelerini <xref:System.Windows.Forms.DataGridView> (veya tablolarını) görüntülemek için gibi on denetimlerini uygulama. Daha fazla bilgi için [bkz. Karmaşık Windows destekleyen bir Formlar kullanıcı denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)|
|Veri <xref:System.ComponentModel.LookupBindingPropertiesAttribute> listelerini (veya tablolarını) görüntülemenin yanı sıra tek bir sütun veya özellik de sun ihtiyacı olan , gibi <xref:System.Windows.Forms.ComboBox> üzerinde denetimlerini uygulama. Daha fazla bilgi için [bkz. Arama Windows destekleyen bir Formlar kullanıcı denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)|

Bu kılavuz, bir tablodaki tek bir sütundaki verileri görüntüleyen basit bir denetim oluşturur. Bu örnekte `Phone` Northwind örnek `Customers` veritabanındaki tablonun sütunu kullanılır. Basit kullanıcı denetimi, bir kullanarak ve maskeyi bir telefon numarasına ayarerek müşterilerin telefon numaralarını <xref:System.Windows.Forms.MaskedTextBox> standart bir telefon numarası biçiminde görüntüler.

Bu kılavuzda şunları yapmayı öğrenirsiniz:

- Yeni bir form **Windows Forms Uygulaması oluşturun.**

- Projenize **yeni bir Kullanıcı** Denetimi ekleyin.

- Kullanıcı denetimi görsel olarak tasarlar.

- özniteliğini `DefaultBindingProperty` uygulama.

- Veri Kaynağı Yapılandırma sihirbazı ile **bir veri kümesi** oluşturun.

- Yeni **Telefon** kullanmak için **Veri Kaynakları penceresindeki** veri kümesi sütununu ayarlayın.

- Yeni denetimde verileri görüntülemek için bir form oluşturun.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. YerelDB'niz yoksa, SQL Server Express indirme sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi,** yerel SQL Server Express veri depolama ve işleme iş  yükünün bir parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün** bir parçası olarak **Visual Studio Yükleyicisi.)** SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-application"></a>Windows Forms Uygulaması Oluşturma

İlk adım, Windows **Forms Uygulaması oluşturmaktır:**

1. Bu Visual Studio, Dosya menüsünde **Yeni** **dosya'Project.**  >  

2. Sol **bölmede Visual C#** **Visual Basic** görseli genişletin ve ardından Masaüstü'Windows **seçin.**

3. Orta bölmede Windows **Forms Uygulaması proje** türünü seçin.

4. Projeye **SimpleControlWalkthrough adını ve** ardından Tamam'ı **seçin.**

     **SimpleControlWalkthrough** projesi oluşturulur ve **Çözüm Gezgini.**

## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi ekleme

Bu kılavuz, kullanıcı denetiminden basit bir veri bağlanabilir **denetim oluşturur.** **SimpleControlWalkthrough** **projesine** Bir Kullanıcı Denetimi öğesi ekleyin:

1. Uygulama **menüsünden Project** Denetimi **Ekle'yi seçin.**

2. Ad **alanına PhoneNumberBox** yazın ve Ekle'ye **tıklayın.**

     **PhoneNumberBox** denetimi, Çözüm Gezgini eklenir ve tasarımcıda açılır.

## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox denetimi tasarlama

Bu izlenecek yol, <xref:System.Windows.Forms.MaskedTextBox> **PhoneNumberBox** denetimi oluşturmak için var olan ile genişletildi:

1. Araç <xref:System.Windows.Forms.MaskedTextBox> Kutusundan **kullanıcı denetimi** tasarım yüzeyine bir sürükleyin.

2. Az önce sürüklemiş olduğunuz <xref:System.Windows.Forms.MaskedTextBox> akıllı etiketi seçin ve Maske ayarla'ya **seçin.**

3. Giriş **Telefon kutusunda** bir numara **seçin** ve **tamam'a tıklar** ve maskeyi ayarlayın.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleme

Veri bağlamayı destekleyen basit denetimler için: <xref:System.ComponentModel.DefaultBindingPropertyAttribute>

1. **PhoneNumberBox denetimi kod** görünümüne geçiş. (Görünüm menüsünde **Kod'a** **tıklayın.)**

2. **PhoneNumberBox'daki kodu** aşağıdakiyle değiştirin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb" id="Snippet3":::

3. Derleme **menüsünden** Çözümü **Derleme'yi seçin.**

## <a name="create-a-data-source-from-your-database"></a>Veritabanınıza bir veri kaynağı oluşturma

Bu adım, Northwind **örnek veritabanındaki** tabloyu temel alan bir veri kaynağı oluşturmak için Veri Kaynağı `Customers` Yapılandırma sihirbazını kullanır. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminiz olmalıdır. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Örnek veritabanlarını yükleme.](../data-tools/installing-database-systems-tools-and-samples.md)

1. Veri Kaynakları **penceresini açmak** için Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

2. Veri Kaynağı **Yapılandırma sihirbazını** başlatmak **için Veri Kaynakları penceresinde** Yeni Veri Kaynağı **Ekle'yi** seçin.

3. Veri Kaynağı **Türü Seçin sayfasında Veritabanı'yı** **seçin ve** ardından Sonraki'ye **tıklayın.**

4. Veri **Bağlantınızı Seçin** sayfasında, aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - Bağlantı **Ekle/Değiştir** iletişim **kutusunu başlatmak için Yeni Bağlantı'ya** tıklayın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etmek için seçeneğini belirleyin ve ardından Sonraki 'ye **tıklayın.**

6. Bağlantı **dizesini Uygulama Yapılandırması dosyasına kaydet sayfasında, Sonraki** 'ye **tıklayın.**

7. Veritabanı **Nesnelerinizi seçin sayfasında** Tablolar **düğümünü** genişletin.

8. Tabloyu `Customers` seçin ve ardından Son'a **tıklayın.**

     **NorthwindDataSet** projenize eklenir ve `Customers` tablo Veri Kaynakları **penceresinde** görüntülenir.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>PhoneNumberBox denetimi kullanmak için telefon sütununu ayarlama

Veri **Kaynakları penceresinde,** öğeleri form üzerine sürüklemeden önce denetimin oluşturulacak şekilde ayarlayın:

1. Tasarımcıda **Form1'i** açın.

2. Veri **Kaynakları penceresinde** Müşteriler **düğümünü** genişletin.

3. Müşteriler düğümünde açılan oka **tıklayın ve** denetim **listesinden Ayrıntılar'ı** seçin.

4. Telefon sütunundaki **açılan oka tıklayın ve** Özelleştir'i **seçin.**

5. Veri Kullanıcı Arabirimi Özelleştirme Seçenekleri iletişim kutusundaki **İlişkili Denetimler** **listesinden PhoneNumberBox'ı** seçin. 

6. Telefon sütunundaki **açılan oka tıklayın ve** **PhoneNumberBox'ı seçin.**

## <a name="add-controls-to-the-form"></a>Forma denetimler ekleme

Veri Kaynakları penceresindeki öğeleri forma sürükleyerek **veriye bağlı** denetimler oluşturabilirsiniz.

Formda veriye bağlı denetimler oluşturmak  için Ana  Müşteriler düğümünü Veri Kaynakları penceresinden forma sürükleyin ve verileri Veri Kaynakları sütununda görüntülemek için **PhoneNumberBox** Telefon **doğrulayın.**

Formda, kayıtlarda gezinmek için bir araç şeridi ( ) ile birlikte açıklayıcı <xref:System.Windows.Forms.BindingNavigator> etiketlere sahip veriye bağlı denetimler görünür. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource> ve bileşen <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı çalıştırmak için **F5**'e basın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturdukta gerçekleştirmek istediğiniz birkaç adım vardır. Tipik sonraki adımlardan bazıları şunlardır:

- Özel denetimlerinizi başka uygulamalarda yeniden kullanmak için bir denetim kitaplığına yerleştirme.

- Daha karmaşık veri bağlama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için [bkz. Karmaşık veri bağlamayı destekleyen Windows Forms](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) kullanıcı denetimi oluşturma ve arama veri bağlamayı [destekleyen Windows Forms kullanıcı denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
