---
title: Veri aramak için Windows Form oluşturma
description: veri aramak için Windows Form oluşturma hakkında bir örnek okuyun. Windows form uygulaması, veri kaynağı ve form oluşturun. Parametreleştirme ekleyin. Uygulamayı test etme.
ms.custom: SEO-VS-2020
ms.date: 06/07/2021
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8236f6c030e70033a77aa9c71d759dedaa453608c20a957fc63e2f8743613e4a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347590"
---
# <a name="create-a-windows-form-to-search-data"></a>Veri aramak için Windows Form oluşturma

Sık rastlanan bir uygulama senaryosu seçilen verileri form üzerinde görüntülemektir. Örneğin, belirli bir müşterinin siparişlerini veya belirli bir siparişin ayrıntılarını görüntülemek isteyebilirsiniz. Bu senaryoda, kullanıcı bilgileri forma girer ve sonra kullanıcının girişi parametre olarak kullanılarak bir sorgu yürütülür; diğer bir deyişle veriler parametreli bir sorgu temel alınarak seçilir. Sorgu sadece kullanıcı tarafından girilen ölçütleri karşılayan verileri getirir. Bu kılavuzda, belirli bir şehirdeki müşterileri getiren bir sorgu oluşturma ve kullanıcı arabirimini kullanıcıların şehir adı girip bir düğmeye basarak sorguyu çalıştırabilecekleri şekilde değiştirme işlemleri gösterilmiştir.

Parametreli sorgular kullanılması, veritabanının kayıtları hızla filtreleyerek işini en iyi şekilde yapmasını sağlayarak uygulamanızın verimli çalışmasına yardımcı olur. Buna karşılık, bir veritabanı tablosunun tamamını ister, ağ üzerinden aktarabilir, sonra da istediğiniz kayıtları bulmak için uygulama mantığını kullanırsanız, uygulamanız yavaş ve verimsiz hale gelebilir.

**Arama ölçütleri Oluşturucu** iletişim kutusunu kullanarak herhangi bir TableAdapter 'a parametreli sorgular ekleyebilirsiniz (ve parametre değerlerini kabul etmek ve sorguyu yürütmek için denetimler). **Veri** menüsünde (veya herhangi bir TableAdapter akıllı etiketinde) **Sorgu Ekle** komutunu seçerek iletişim kutusunu açın.

Bu izlenecek yolda gösterilen görevler şunlardır:

- Veri kaynağı **yapılandırma** Sihirbazı ile uygulamanızdaki veri kaynağını oluşturma ve yapılandırma.

- **Veri kaynakları** penceresinde öğelerin bırakma türü ayarlanıyor.

- **Veri kaynakları** penceresinden bir formun üzerine öğe sürükleyerek verileri görüntüleyen denetimler oluşturma.

- Formdaki verileri görüntülemek için denetimler ekleme.

- **Arama ölçütleri Oluşturucu** iletişim kutusu tamamlanıyor.

- Forma parametreler girerek ve parametreli sorgu yürütülüyor.

> [!NOTE]
> bu makaledeki yordamlar, .net Core Windows Forms projelerine değil, yalnızca .NET Framework Windows Forms projelerine uygulanır.

## <a name="prerequisites"></a>Önkoşullar

**Veri depolama ve işleme** iş yükünün yüklü olması gerekir. Bkz. [Visual Studio değiştirme](../install/modify-visual-studio.md).

bu izlenecek yol, SQL Server Express localdb ve Northwind örnek veritabanını kullanır.

1. SQL Server Express localdb yoksa, [SQL Server Express indirme sayfasından](https://www.microsoft.com/sql-server/sql-server-editions-express)veya **Visual Studio Yükleyicisi** aracılığıyla yükleyin. **Visual Studio Yükleyicisi**, SQL Server Express localdb 'yi **veri depolama ve işleme** iş yükünün parçası olarak veya ayrı bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları izleyerek Northwind örnek veritabanını yüklersiniz:

    1. Visual Studio, **SQL Server Nesne Gezgini** penceresini açın. (SQL Server Nesne Gezgini, **Visual Studio Yükleyicisi** **veri depolama ve işleme** iş yükünün parçası olarak yüklenir.) **SQL Server** düğümünü genişletin. LocalDB örneğinize sağ tıklayıp **Yeni sorgu**' yı seçin.

       Sorgu Düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiğini](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) panonuza kopyalayın. bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verileri veriyle doldurur.

    3. T-SQL betiğini sorgu düzenleyicisine yapıştırın ve sonra **yürüt** düğmesini seçin.

       Kısa bir süre sonra sorgu çalışmayı sonlandırır ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturma

:::moniker range="vs-2017"

C# veya Visual Basic için yeni bir **Windows Forms App (.NET Framework)** projesi oluşturun. Projeyi **WindowsSearchForm** olarak adlandırın.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Bu adım **veri kaynağı yapılandırma** Sihirbazı 'nı kullanarak bir veritabanından veri kaynağı oluşturur:

1. Veri **kaynakları** penceresini açmak Için, **veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

8. **Müşteriler** tablosunu seçin ve ardından **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve **Customers** tablosu **veri kaynakları** penceresinde görünür.

:::moniker-end

:::moniker range=">=vs-2019"

C# veya Visual Basic için yeni bir **Windows Forms App (.NET Framework)** projesi oluşturun. Projeyi **WindowsSearchForm** olarak adlandırın.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Bu adım **veri kaynağı yapılandırma** Sihirbazı 'nı kullanarak bir veritabanından veri kaynağı oluşturur:

1. **Veri kaynakları** penceresini açmak için hızlı arama ' yı (**CTRL** + **Q**) kullanın ve **veri kaynaklarını** arayın.

1. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

1. **Veri kaynağı türü seçin** sayfasında **veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

1. **Veritabanı modeli seçin** ekranında **veri kümesi**' ni seçin ve ardından **İleri**' ye tıklayın.

1. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

1. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

1. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

1. **Müşteriler** tablosunu seçin ve ardından **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve **Customers** tablosu **veri kaynakları** penceresinde görünür.

:::moniker-end

## <a name="create-the-form"></a>Formu oluşturun

Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz:

1. Windows Forms tasarımcısında etkin odağa sahip olduğundan ve **veri kaynakları** penceresinin açık ve sabitlenmiş olduğundan emin olun.

1. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

1. **Müşteriler** düğümünü **veri kaynakları** penceresinden formunuza sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) formda görüntülenir. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Sorguya Parametreleştirme (arama işlevi) ekleme

**Arama ölçütü Oluşturucu** iletişim kutusunu kullanarak, özgün sorguya bir where yan tümcesi ekleyebilirsiniz:

1. Formunuz için tasarım yüzeyinin hemen altında, **CustomersTableAdapter** düğmesini seçin ve ardından **Özellikler** penceresinde **Sorgu Ekle...** seçeneğini belirleyin.

2. **Arama ölçütü Oluşturucu** Iletişim kutusundaki **Yeni sorgu adı** alanına **FillByCity** yazın.

3. Sorgu `WHERE City = @City` **metin** alanındaki sorguya ekleyin.

     Sorgu aşağıdakine benzemelidir:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Erişim ve OLE DB veri kaynakları, parametreleri belirtmek için soru işareti ('? ') kullanır, bu nedenle WHERE yan tümcesi şöyle görünür: `WHERE City = ?` .

4. **Tamam** ' a tıklayarak **arama ölçütleri Oluşturucu** iletişim kutusunu kapatın.

     Forma bir **FillByCityToolStrip** eklenir.

## <a name="test-the-application"></a>Uygulamayı test edin

Uygulamayı çalıştırmak formunuzu açar ve parametreyi giriş olarak almaya başlamaya çalışır:

1. Uygulamayı çalıştırmak için **F5**'e basın.

2. **Şehir** metin kutusuna **Londra** yazın ve ardından **FillByCity**' ye tıklayın.

     Veri kılavuzu, ölçütlere uyan müşterilerle doldurulur. Bu örnekte, veri kılavuzu yalnızca, **şehir** sütununda **Londra** değeri olan müşterileri görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, parametreli form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- İlgili verileri görüntüleyen denetimler ekleme. Daha fazla bilgi için bkz. [veri kümelerinde ilişkiler](relationships-in-datasets.md).

- Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
