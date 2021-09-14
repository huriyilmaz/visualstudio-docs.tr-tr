---
title: Veri bağlama ile Windows Forms kullanıcı denetimi oluşturma
description: ComplexBindingPropertiesAttribute sınıfını kullanarak karmaşık veri bağlamayı destekleyen bir Windows Forms kullanıcı denetimi oluşturma hakkında bilgi.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b179c957320badae098d0f82107d26ebf0859df1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631496"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Karmaşık veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma

Uygulama uygulamalarında formlarda Windows görüntülerken, Araç Kutusundan mevcut denetimleri **seçebilirsiniz.** Veya, uygulamanıza standart denetimlerde mevcut olmayan işlevler gerektiriyorsa özel denetimler de oluşturabilirsiniz. Bu kılavuz, uygulayan bir denetimin nasıl oluşturuldığını <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> gösterir. uygulayan <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> denetimler, `DataSource` verilere `DataMember` bağlanan bir ve özelliği içerir. Bu tür denetimler veya ile <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.ListBox> benzerdir.

Denetim yazma hakkında daha fazla bilgi için [bkz. Tasarım zamanında Windows Forms denetimleri geliştirme.](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)

Veri bağlama senaryolarında kullanmak üzere denetimler yazarken aşağıdaki veri bağlama özniteliklerinden birini uygulamanız gerekir:

|Veri bağlama özniteliği kullanımı|
| - |
|Tek <xref:System.ComponentModel.DefaultBindingPropertyAttribute> bir veri sütunu (veya <xref:System.Windows.Forms.TextBox> özelliği) görüntüleniyor gibi basit denetimler üzerinde uygulaması. Daha fazla bilgi için [bkz. Basit Windows destekleyen bir Formlar kullanıcı denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)|
|Veri <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> listelerini <xref:System.Windows.Forms.DataGridView> (veya tablolarını) görüntülemek için gibi on denetimlerini uygulama. (Bu işlem bu kılavuz sayfasında açıklanmıştır.)|
|Veri <xref:System.ComponentModel.LookupBindingPropertiesAttribute> listelerini (veya tablolarını) görüntülemenin yanı sıra tek bir sütun veya özellik de sun ihtiyacı olan , gibi <xref:System.Windows.Forms.ComboBox> üzerinde denetimlerini uygulama. Daha fazla bilgi için [bkz. Arama Windows destekleyen bir Formlar kullanıcı denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)|

Bu kılavuz, bir tablodaki veri satırlarını görüntüleyen karmaşık bir denetim oluşturur. Bu örnekte `Customers` Northwind örnek veritabanındaki tablo kullanılır. Karmaşık kullanıcı denetimi, özel denetimde customers <xref:System.Windows.Forms.DataGridView> tablosunda görüntülenir.

Bu kılavuzda şunları yapmayı öğrenirsiniz:

- Projenize **yeni bir Kullanıcı** Denetimi ekleyin.

- Kullanıcı denetimi görsel olarak tasarlar.

- özniteliğini `ComplexBindingProperty` uygulama.

- Veri Kaynağı Yapılandırma Sihirbazı ile [bir veri kümesi oluşturun.](../data-tools/media/data-source-configuration-wizard.png)

- Yeni **karmaşık denetimi** kullanmak için [Veri Kaynakları penceresindeKi](add-new-data-sources.md#data-sources-window) Müşteriler tablosuna tıklayın.

- Yeni denetimi Veri Kaynakları penceresinden **Form1'e** **sürükleyerek ekleyin.**

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi,** yerel SQL Server Express veri depolama ve işleme iş yükünün bir parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz. 

1. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün bir parçası olarak** Visual Studio Yükleyicisi.) SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Sorgu düzenleyicisi penceresi açılır.

    1. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    1. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-a-windows-forms-app-project"></a>Windows Forms uygulama projesi oluşturma

İlk adım, C# veya **Windows için** bir Windows Forms Uygulaması projesi Visual Basic. Projeye **ComplexControlWalkthrough adını girin.**

## <a name="add-a-user-control-to-the-project"></a>Projeye kullanıcı denetimi ekleme

Bu kılavuz bir Kullanıcı Denetiminden karmaşık bir veri bağlanabilir denetim **oluşturduğundan,** projeye bir **Kullanıcı Denetimi** öğesi ekleyin:

1. Uygulama **menüsünden Project** Denetimi **Ekle'yi seçin.**

1. Ad **alanına ComplexDataGridView** **yazın ve** Ekle'ye **tıklayın.**

    **ComplexDataGridView** denetimi, Çözüm Gezgini eklenir ve tasarımcıda açılır.

## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView denetimini tasarlama

Kullanıcı <xref:System.Windows.Forms.DataGridView> denetimine bir eklemek için Araç <xref:System.Windows.Forms.DataGridView> Kutusundan kullanıcı **denetimi** tasarım yüzeyine bir sürükleyin.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleme

Veri bağlamayı destekleyen karmaşık denetimler için: <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>

1. **ComplexDataGridView denetimini** kod görünümüne değiştirme. (Görünüm menüsünde **Kod'a** **tıklayın.)**

1. içinde kodunu `ComplexDataGridView` aşağıdakiyle değiştirin:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb" id="Snippet4":::

1. Derleme **menüsünden** Çözümü **Derleme'yi seçin.**

## <a name="create-a-data-source-from-your-database"></a>Veritabanınız ile veri kaynağı oluşturma

Northwind **örnek veritabanındaki** tabloyu temel alan bir veri kaynağı oluşturmak `Customers` için Veri Kaynağı Yapılandırma sihirbazını kullanın:

1. Veri Kaynakları **penceresini açmak için** Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

2. Veri Kaynağı **Yapılandırma sihirbazını** başlatmak **için Veri Kaynakları penceresinde** Yeni Veri Kaynağı **Ekle'yi** seçin.

3. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı seçin** ve ardından Sonraki'ye **tıklayın.**

4. Veri **Bağlantınızı Seçin sayfasında,** aşağıdakilerden birini yapın:

   - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

   - Bağlantı **Ekle/Değiştir** iletişim **kutusunu başlatmak için Yeni Bağlantı'ya** tıklayın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etmek için seçeneğini belirleyin ve ardından Sonraki 'ye **tıklayın.**

6. Bağlantı **dizesini Uygulama Yapılandırması dosyasına kaydet sayfasında, Sonraki** 'ye **tıklayın.**

7. Veritabanı **Nesnelerinizi seçin sayfasında** Tablolar **düğümünü** genişletin.

8. Tabloyu `Customers` seçin ve ardından Son'a **tıklayın.**

   **NorthwindDataSet** projenize eklenir ve `Customers` tablo Veri Kaynakları **penceresinde** görüntülenir.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Customers tabloyu ComplexDataGridView denetimini kullanmak üzere ayarlama

Veri **Kaynakları penceresinde,** öğeleri form üzerine sürüklemeden önce oluşturulacak denetimi ayarlayın:

1. Tasarımcıda **Form1'i** açın.

1. Veri **Kaynakları penceresinde** Müşteriler **düğümünü** genişletin.

1. Müşteriler düğümünde açılan oka tıklayın **ve** Özelleştir'i **seçin.**

1. Veri Kullanıcı Arabirimi Özelleştirme Seçenekleri iletişim kutusundaki **İlişkili Denetimler** **listesinden ComplexDataGridView'u** seçin. 

1. Tablodaki açılan oka tıklayın `Customers` ve denetim **listesinden ComplexDataGridView'u** seçin.

## <a name="add-controls-to-the-form"></a>Forma denetimler ekleme

Veri Kaynakları penceresindeki öğeleri form üzerine sürükleyerek **veriye bağlı** denetimler oluşturabilirsiniz. Ana Müşteriler **düğümünü** Veri Kaynakları **penceresinden** forma sürükleyin. **Tablonun verilerini görüntülemek için ComplexDataGridView** denetiminin çalıştığını doğrulayın.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamayı çalıştırmak için **F5**'e basın.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturdukta gerçekleştirmek istediğiniz birkaç adım vardır. Tipik sonraki adımlardan bazıları şunlardır:

- Özel denetimlerinizi başka uygulamalarda yeniden kullanmak için bir denetim kitaplığına yerleştirme.

- Arama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için [bkz. Arama Windows destekleyen bir Formlar kullanıcı denetimi oluşturma.](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Form Denetimleri](/dotnet/framework/winforms/controls/index)
