---
title: Veri aramak için bir Windows formu oluşturun | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81980f38cbd8fb595530cc52b2cf32056feb43a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670057"
---
# <a name="create-a-windows-form-to-search-data"></a>Veri aramak için Windows Form oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sık rastlanan bir uygulama senaryosu seçilen verileri form üzerinde görüntülemektir. Örneğin, belirli bir müşterinin siparişlerini veya belirli bir siparişin ayrıntılarını görüntülemek isteyebilirsiniz. Bu senaryoda, kullanıcı bilgileri forma girer ve sonra kullanıcının girişi parametre olarak kullanılarak bir sorgu yürütülür; diğer bir deyişle veriler parametreli bir sorgu temel alınarak seçilir. Sorgu sadece kullanıcı tarafından girilen ölçütleri karşılayan verileri getirir. Bu kılavuzda, belirli bir şehirdeki müşterileri getiren bir sorgu oluşturma ve kullanıcı arabirimini kullanıcıların şehir adı girip bir düğmeye basarak sorguyu çalıştırabilecekleri şekilde değiştirme işlemleri gösterilmiştir.

 Parametreli sorgular kullanılması, veritabanının kayıtları hızla filtreleyerek işini en iyi şekilde yapmasını sağlayarak uygulamanızın verimli çalışmasına yardımcı olur. Buna karşılık, bir veritabanı tablosunun tamamını ister, ağ üzerinden aktarabilir, sonra da istediğiniz kayıtları bulmak için uygulama mantığını kullanırsanız, uygulamanız yavaş ve verimsiz hale gelebilir.

 **Arama ölçütleri Oluşturucu** iletişim kutusunu kullanarak herhangi bir TableAdapter 'a parametreli sorgular ekleyebilirsiniz (ve parametre değerlerini kabul etmek ve sorguyu yürütmek için denetimler). **Veri** menüsünde (veya herhangi bir TableAdapter akıllı etiketinde) **Sorgu Ekle** komutunu seçerek iletişim kutusunu açın.

 Bu izlenecek yolda gösterilen görevler şunlardır:

- Yeni bir Windows Forms uygulama projesi oluşturuluyor.

- Veri kaynağı **yapılandırma** Sihirbazı ile uygulamanızdaki veri kaynağını oluşturma ve yapılandırma.

- **Veri kaynakları** penceresinde öğelerin bırakma türü ayarlanıyor.

- **Veri kaynakları** penceresinden bir formun üzerine öğe sürükleyerek verileri görüntüleyen denetimler oluşturma.

- Formdaki verileri görüntülemek için denetimler ekleme.

- **Arama ölçütleri Oluşturucu** iletişim kutusu tamamlanıyor.

- Forma parametreler girerek ve parametreli sorgu yürütülüyor.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind örnek veritabanına erişim.

## <a name="create-the-windows-application"></a>Windows uygulaması oluşturma
 İlk adım bir **Windows uygulaması**oluşturmaktır. Bu adımda projeye bir ad atanması isteğe bağlıdır, ancak daha sonra kaydedileceği için buraya bir ad verin.

#### <a name="to-create-the-new-windows-application-project"></a>Yeni bir Windows Uygulaması projesi oluşturmak için

1. **Dosya** menüsünden Yeni bir proje oluşturun.

2. Projeyi adlandırın `WindowsSearchForm` .

3. **Windows uygulaması** ' nı seçin ve **Tamam**' a tıklayın.

     **WindowsSearchForm** projesi oluşturulup **Çözüm Gezgini**eklenir.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma
 Bu adım **veri kaynağı yapılandırma** Sihirbazı 'nı kullanarak bir veritabanından veri kaynağı oluşturur. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [ınstall SQL Server Sample Databases](../data-tools/install-sql-server-sample-databases.md).

#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

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

## <a name="create-the-form"></a>Formu oluşturun
 Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için

1. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

2. **Müşteriler** düğümünü **veri kaynakları** penceresinden formunuza sürükleyin.

     <xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) formda görüntülenir. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="addparameterization-search-functionality-to-the-query"></a>Sorguya addparameterleştirme (arama işlevi)
 **Arama ölçütü Oluşturucu** iletişim kutusunu kullanarak, özgün sorguya bir where yan tümcesi ekleyebilirsiniz.

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Parametreleri girmek üzere parametreli sorgu ve denetimler oluşturmak için

1. Denetimi seçin <xref:System.Windows.Forms.DataGridView> ve ardından **veri** menüsünde **Sorgu Ekle** ' yi seçin.

2. `FillByCity` **Arama ölçütleri Oluşturucu** iletişim kutusunda **Yeni sorgu adı** alanını yazın.

3. Sorgu `WHERE City = @City` **metin** alanındaki sorguya ekleyin.

     Sorgu aşağıdakine benzemelidir:

     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`

     `FROM Customers`

     `WHERE City = @City`

    > [!NOTE]
    > Erişim ve OLE DB veri kaynakları, parametreleri belirtmek için soru işareti ('? ') kullanır, bu nedenle WHERE yan tümcesi şöyle görünür: `WHERE City = ?` .

4. **Tamam** ' a tıklayarak **arama ölçütleri Oluşturucu** iletişim kutusunu kapatın.

     Forma bir **FillByCityToolStrip** eklenir.

## <a name="testing-the-application"></a>Uygulamayı test etme
 Uygulamanın çalıştırılması formunuzu giriş olarak parametreyi almaya hazır olarak açar.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. Uygulamayı çalıştırmak için F5'e basın.

2. **Şehir** metin kutusuna **Londra** yazın ve ardından **FillByCity**' ye tıklayın.

     Veri kılavuzu, ölçütlere uyan müşterilerle doldurulur. Bu örnekte, veri kılavuzu yalnızca, **şehir** sütununda **Londra** değeri olan müşterileri görüntüler.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, parametreli form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- İlgili verileri görüntüleyen denetimler ekleme.

- Veritabanı nesneleri eklemek veya çıkarmak için veri kümesini düzenleme. Daha fazla bilgi için bkz. [veri kümeleri oluşturma ve yapılandırma](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
