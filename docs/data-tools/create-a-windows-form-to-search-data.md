---
title: Veri aramak için Windows Form oluşturma
description: Veri aramak için bir Form oluşturma Windows örneğini okuyun. Form Windows, veri kaynağı ve formu oluşturun. Parametreleştirme ekleyin. Uygulamayı test etme.
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
ms.openlocfilehash: 4d045dcddd1cdebb4308e35bf9060b013216a670
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037089"
---
# <a name="create-a-windows-form-to-search-data"></a>Veri aramak için Windows Form oluşturma

Sık rastlanan bir uygulama senaryosu seçilen verileri form üzerinde görüntülemektir. Örneğin, belirli bir müşterinin siparişlerini veya belirli bir siparişin ayrıntılarını görüntülemek isteyebilirsiniz. Bu senaryoda, kullanıcı bilgileri forma girer ve sonra kullanıcının girişi parametre olarak kullanılarak bir sorgu yürütülür; diğer bir deyişle veriler parametreli bir sorgu temel alınarak seçilir. Sorgu sadece kullanıcı tarafından girilen ölçütleri karşılayan verileri getirir. Bu kılavuzda, belirli bir şehirdeki müşterileri getiren bir sorgu oluşturma ve kullanıcı arabirimini kullanıcıların şehir adı girip bir düğmeye basarak sorguyu çalıştırabilecekleri şekilde değiştirme işlemleri gösterilmiştir.

Parametreli sorgular kullanılması, veritabanının kayıtları hızla filtreleyerek işini en iyi şekilde yapmasını sağlayarak uygulamanızın verimli çalışmasına yardımcı olur. Buna karşılık, veritabanı tablonun tamamını ister, ağ üzerinden aktararak ve ardından istediğiniz kayıtları bulmak için uygulama mantığını kullanırsanız, uygulama yavaş ve verimsiz hale olabilir.

Arama Ölçütleri Oluşturucusu iletişim kutusunu kullanarak herhangi bir TableAdapter'a parametreli sorgular (ve parametre değerlerini kabul etmek ve sorguyu yürütmek için **denetimler)** eklemek için kullanabilirsiniz. Veri menüsünde (veya herhangi  bir TableAdapter akıllı etiketinde) Sorgu Ekle komutunu seçerek iletişim kutusunu açın. 

Bu kılavuzda gösterilen görevler şunlardır:

- Veri Kaynağı Yapılandırma sihirbazı ile uygulamanıza veri kaynağı **oluşturma ve** yapılandırma.

- Veri Kaynakları penceresinde öğelerin bırakma **türünü** ayarlama.

- Veri Kaynakları penceresindeki öğeleri bir forma **sürükleyerek verileri** görüntülüyor denetimler oluşturma.

- Formdaki verileri görüntülemek için denetimler ekleme.

- Arama Ölçütleri **Oluşturucusu iletişim** kutusu tamamlandı.

- Forma parametre girme ve parametreli sorguyu yürütme.

> [!NOTE]
> Bu makaledeki yordamlar yalnızca .NET Core .NET Framework Windows Forms projeleri için değil, Windows Forms projeleri için geçerlidir.

## <a name="prerequisites"></a>Önkoşullar

Veri depolama ve **işleme iş yükünün yüklü** olması gerekir. Bkz. [Visual Studio.](../install/modify-visual-studio.md)

Bu kılavuzda LocalDB SQL Server Express Northwind örnek veritabanı kullanılır.

1. Yerel VERITABANınız yoksa, SQL Server Express sayfasından veya [SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)sayfasından **Visual Studio Yükleyicisi.** Bu **Visual Studio Yükleyicisi,** yerel SQL Server Express veri depolama ve işleme iş  yükünün bir parçası olarak veya tek bir bileşen olarak yükleyebilirsiniz.

2. Aşağıdaki adımları kullanarak Northwind örnek veritabanını yükleyin:

    1. Bu Visual Studio, **SQL Server Nesne Gezgini** açın. (SQL Server Nesne Gezgini, veri depolama ve işleme iş **yükünün** bir parçası olarak **Visual Studio Yükleyicisi.)** SQL Server **genişletin.** LocalDB örneğine sağ tıklayın ve Yeni **Sorgu'yı seçin.**

       Bir sorgu düzenleyicisi penceresi açılır.

    2. [Northwind Transact-SQL betiği panoya](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) kopyalayın. Bu T-SQL betiği, Northwind veritabanını sıfırdan oluşturur ve verilerle doldurmak için kullanılır.

    3. T-SQL betiği sorgu düzenleyicisine yapıştırın ve ardından Yürüt **düğmesini** seçin.

       Kısa bir süre sonra sorgunun çalışıyor ve Northwind veritabanı oluşturulur.

## <a name="create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturma

:::moniker range="vs-2017"

C# veya Windows için yeni .NET Framework Forms Uygulaması **(.NET Framework)** projesi Visual Basic. Projeye **WindowsSearchForm adını girin.**

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Bu adım, Veri Kaynağı Yapılandırma sihirbazını kullanarak **veritabanından bir veri kaynağı** oluşturur:

1. Veri Kaynakları **penceresini açmak** için Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın.**

2. Veri Kaynağı **Yapılandırma sihirbazını** başlatmak **için Veri Kaynakları penceresinde** Yeni Veri Kaynağı **Ekle'yi** seçin.

3. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı seçin** ve ardından Sonraki'ye **tıklayın.**

4. Veri **Bağlantınızı Seçin sayfasında,** aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - Bağlantı **Ekle/Değiştir** iletişim **kutusunu başlatmak için Yeni Bağlantı'ya** tıklayın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etmek için seçeneğini belirleyin ve ardından Sonraki 'ye **tıklayın.**

6. Bağlantı **dizesini Uygulama Yapılandırması dosyasına kaydet sayfasında, Sonraki** 'ye **tıklayın.**

7. Veritabanı **Nesnelerinizi seçin sayfasında** Tablolar **düğümünü** genişletin.

8. Customers **tablosu'u** seçin ve ardından Son'a **tıklayın.**

     **NorthwindDataSet** projenize eklenir ve Veri  Kaynakları penceresinde Müşteriler **tablosu** görüntülenir.

:::moniker-end

:::moniker range=">=vs-2019"

C# veya Windows için yeni .NET Framework Forms Uygulaması **(.NET Framework)** projesi Visual Basic. Projeye **WindowsSearchForm adını girin.**

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma

Bu adım, Veri Kaynağı Yapılandırma sihirbazını kullanarak **veritabanından bir veri kaynağı** oluşturur:

1. Veri Kaynakları **penceresini açmak için** hızlı arama (**Ctrl** Q ) ve Veri Kaynakları araması +  **kullanın.**

1. Veri Kaynağı **Yapılandırma sihirbazını** başlatmak **için Veri Kaynakları penceresinde** Yeni Veri Kaynağı **Ekle'yi** seçin.

1. Veri **Kaynağı** Türü **Seçin sayfasında Veritabanı'ı seçin** ve ardından Sonraki'ye **tıklayın.**

1. Veritabanı Modeli **Seçin ekranında Veri** Kümesi'ne ve **ardından** Sonraki'ye **tıklayın.**

1. Veri **Bağlantınızı Seçin sayfasında,** aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - Bağlantı **Ekle/Değiştir** iletişim **kutusunu başlatmak için Yeni Bağlantı'ya** tıklayın.

1. Bağlantı **dizesini Uygulama Yapılandırması dosyasına kaydet sayfasında, Sonraki** 'ye **tıklayın.**

1. Veritabanı **Nesnelerinizi seçin sayfasında** Tablolar **düğümünü** genişletin.

1. Customers **tablosu'u** seçin ve ardından Son'a **tıklayın.**

     **NorthwindDataSet** projenize eklenir ve Veri  Kaynakları penceresinde Müşteriler **tablosu** görüntülenir.

:::moniker-end

## <a name="create-the-form"></a>Formu oluşturma

Veri Kaynakları penceresindeki öğeleri form üzerine sürükleyerek **veriye bağlı** denetimler oluşturabilirsiniz:

1. Windows Forms tasarımcısının etkin odağında olduğundan ve Veri Kaynakları **penceresinin açık ve** sabitlenmiş olduğundan emin olun.

1. Veri **Kaynakları penceresinde** Müşteriler **düğümünü** genişletin.

1. Veri **Kaynakları** penceresindeki **Müşteriler düğümünü** formuza sürükleyin.

     Formda <xref:System.Windows.Forms.DataGridView> kayıtlarda <xref:System.Windows.Forms.BindingNavigator> gezinmek için bir ve araç şeridi ( ) görüntülenir. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource> ve bileşen <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Sorguya parametreleştirme (arama işlevi) ekleme

Arama Ölçütü Oluşturucusu iletişim kutusunu kullanarak özgün sorguya **WHERE yan tümcesi** ebilirsiniz:

1. Form için tasarım yüzeyinin hemen altında **customersTableAdapter** düğmesini seçin  ve özellikler penceresinde Sorgu **Ekle... öğesini seçin.**

2. Arama Ölçütü Oluşturucusu iletişim **kutusundaki Yeni sorgu** adı alanına **FillByCity** yazın. 

3. sorgusunu `WHERE City = @City` Sorgu Metni **alanında ekleyin.**

     Sorgu aşağıdakine benzemelidir:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Erişim OLE DB veri kaynakları parametreleri ifade etmek için soru işaretini ('?') kullanır, bu nedenle WHERE yan tümcesi şöyle olur: `WHERE City = ?` .

4. Arama **Ölçütleri Oluşturucusu** iletişim **kutusunu kapatmak için Tamam'a** tıklayın.

     Forma **bir FillByCityToolStrip** eklenir.

## <a name="test-the-application"></a>Uygulamayı test edin

Uygulamayı çalıştırma form sayfanızı açar ve parametreyi giriş olarak almaya hazır hale alır:

1. Uygulamayı çalıştırmak için **F5**'e basın.

2. City **metin** kutusuna **Londra yazın** ve **FillByCity'ye tıklayın.**

     Veri kılavuzu, ölçütlere uyan müşterilerle doldurulur. Bu örnekte veri kılavuzunda yalnızca City sütununda Londra **değerine sahip** **müşteriler** görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Uygulama gereksinimlerinize bağlı olarak, parametreli form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- İlgili verileri görüntüleyen denetimler ekleme. Daha fazla bilgi için [bkz. Veri Kümelerde İlişkiler.](relationships-in-datasets.md)

- Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için [bkz. Veri kümeleri oluşturma ve yapılandırma.](../data-tools/create-and-configure-datasets-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
