---
title: 'İzlenecek yol: bir WPF uygulamasında Ilgili verileri görüntüleme | Microsoft Docs'
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: c44b949daabf587dbca5d8a5d1d932afca2c1f9c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602461"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>İzlenecek Yol: Bir WPF Uygulamasında İlgili Verileri Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda, üst/alt ilişkisi olan veritabanı tablolarından veri görüntüleyen bir WPF uygulaması oluşturacaksınız. Veriler bir Varlık Veri Modeli varlıklarda kapsüllenir. Üst varlık, bir dizi siparişin genel bakış bilgilerini içerir. Bu varlığın her özelliği, uygulamadaki farklı bir denetime bağlanır. Alt varlık her bir siparişin ayrıntılarını içerir. Bu veri kümesi bir <xref:System.Windows.Controls.DataGrid> denetimine bağlanır.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir WPF uygulaması ve AdventureWorksLT örnek veritabanındaki verilerden oluşturulan bir Varlık Veri Modeli oluşturma.

- Bir dizi siparişin genel bakış bilgilerini görüntüleyen bir veri bağlantılı denetimler kümesi oluşturma. Denetimleri, bir üst varlığı **veri kaynakları** penceresinden **WPF tasarımcısına**sürükleyerek oluşturabilirsiniz.

- Seçili her sipariş için ilgili ayrıntıları görüntüleyen bir <xref:System.Windows.Controls.DataGrid> denetimi oluşturma. Bir alt varlığı, **veri kaynakları** penceresinden **WPF Tasarımcısında**bir pencereye sürükleyerek oluşturabilirsiniz.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- AdventureWorksLT örnek veritabanının eklendiği SQL Server veya SQL Server Express çalışan bir örneğine erişim. AdventureWorksLT veritabanını [CodePlex Web sitesinden](http://go.microsoft.com/fwlink/?linkid=87843)indirebilirsiniz.

  Aşağıdaki kavramların önceki bilgileri de yararlı olmakla kalmaz, izlenecek yolu tamamlamak için gerekli değildir:

- Varlık veri modelleri ve ADO.NET Entity Framework. Daha fazla bilgi için bkz. [Entity Framework genel bakış](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- WPF Tasarımcısı ile çalışma. Daha fazla bilgi için bkz. [WPF ve Silverlight tasarımcısına genel bakış](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- WPF veri bağlama. Daha fazla bilgi için bkz. [veri bağlamaya genel bakış](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Projeyi Oluşturma
 Sipariş kayıtlarını göstermek için yeni bir WPF projesi oluşturun.

#### <a name="to-create-a-new-wpf-project"></a>Yeni bir WPF projesi oluşturmak için

1. Visual Studio 'Yu başlatın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **C# Görsel** veya **Visual Basic**öğesini genişletin ve ardından **Windows**' u seçin.

4. İletişim kutusunun üst kısmındaki Birleşik giriş kutusunda **.NET Framework 4** ' ün seçildiğinden emin olun. Bu izlenecek yolda kullandığınız <xref:System.Windows.Controls.DataGrid> denetimi yalnızca .NET Framework 4 ' te kullanılabilir.

5. **WPF uygulaması** proje şablonunu seçin.

6. **Ad** kutusuna `AdventureWorksOrdersViewer` yazın.

7. **Tamam**'a tıklayın.

     Visual Studio `AdventureWorksOrdersViewer` projesi oluşturur.

## <a name="creating-an-entity-data-model-for-the-application"></a>Uygulama için Varlık Veri Modeli oluşturma
 Veriye dayalı denetimler oluşturabilmeniz için önce uygulamanız için bir veri modeli tanımlamanız ve **veri kaynakları** penceresine eklemeniz gerekir. Bu kılavuzda, veri modeli bir Varlık Veri Modeli.

#### <a name="to-create-an-entity-data-model"></a>Varlık Veri Modeli oluşturmak için

1. **Veri menüsünde** **Yeni veri kaynağı Ekle** ' ye tıklayarak **veri kaynağı Yapılandırma Sihirbazı**' nı açın.

2. **Veri kaynağı türü seç** sayfasında, **veritabanı**' na ve ardından **İleri**' ye tıklayın.

3. **Veritabanı modeli seçin** sayfasında, **varlık veri modeli**' a ve ardından **İleri**' ye tıklayın.

4. **Model Içeriğini seçin** sayfasında, **veritabanından oluştur**' u ve ardından **İleri**' yi tıklatın.

5. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

   - Aşağı açılan listede AdventureWorksLT örnek veritabanıyla bir veri bağlantısı varsa, bunu seçin.

      veya

   - **Yeni bağlantı** ' ya tıklayın ve AdventureWorksLT veritabanına bir bağlantı oluşturun.

     **App. config dosyasındaki varlık bağlantısı ayarlarını kaydet** seçeneğinin belirlendiğinden emin olun ve ardından **İleri**' ye tıklayın.

6. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar**' ı genişletin ve ardından aşağıdaki tabloları seçin:

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. **Son**'a tıklayın.

8. Projeyi oluşturun.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Siparişleri görüntüleyen veri bağlantılı denetimler oluşturma
 **Veri kaynakları** penceresinden WPF tasarımcısına `SalesOrderHeaders` varlığını sürükleyerek sıra kayıtlarını görüntüleyen denetimler oluşturun.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Sipariş kayıtlarını görüntüleyen veriye dayalı denetimler oluşturmak için

1. **Çözüm Gezgini**, MainWindow. xaml ' ye çift tıklayın.

    Pencere WPF Tasarımcısı 'nda açılır.

2. **Yükseklik** ve **Genişlik** özelliklerinin 800 olarak ayarlanması için XAML 'yi düzenleyin

3. **Veri kaynakları** penceresinde, **SalesOrderHeaders** düğümünün açılan menüsüne tıklayın ve **Ayrıntılar**' ı seçin.

4. **SalesOrderHeaders** düğümünü genişletin.

5. **SalesOrderID** ' nin yanındaki açılan menüye tıklayın ve **ComboBox**' ı seçin.

6. **SalesOrderHeaders** düğümünün aşağıdaki alt düğümlerinin her biri için, düğümün yanındaki açılan menüye tıklayın ve **hiçbiri**' ni seçin:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **Shiptoadresisıd**

   - **Billtoadresisıd**

   - **CreditCardApprovalCode**

   - **Dikçe**

   - **TaxAmt**

   - **Liye**

   - **rowguid**

   - **ModifiedDate & lt**

     Bu eylem, Visual Studio 'Nun bir sonraki adımda bu düğümler için veri bağlantılı denetimler oluşturmasını engeller. Bu izlenecek yol için, son kullanıcının bu verileri görmesini gerektirmeyen varsayılır.

7. **Veri kaynakları** penceresinde, **SALESORDERHEADERS** düğümünü **WPF Tasarımcısında**pencereye sürükleyin.

    Visual Studio, **SalesOrderHeaders** varlığındaki verilere ve verileri yükleyen koda bağlanan bir denetim KÜMESI oluşturan xaml oluşturur. Oluşturulan XAML ve kod hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. Tasarımcıda **Satış SIPARIŞI kimliği** etiketinin yanındaki açılan kutuya tıklayın.

9. **Özellikler** penceresinde, **IsReadOnly** özelliğinin yanındaki onay kutusunu işaretleyin.

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Sıra ayrıntılarını görüntüleyen bir DataGrid oluşturma
 **Veri kaynakları** penceresinden WPF tasarımcısına `SalesOrderDetails` varlığını sürükleyerek sıra ayrıntılarını görüntüleyen bir <xref:System.Windows.Controls.DataGrid> denetimi oluşturun.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Sıra ayrıntılarını görüntüleyen bir DataGrid oluşturmak için

1. **Veri kaynakları** penceresinde, **SalesOrderHeaders** düğümünün bir alt öğesi olan **SalesOrderDetails** düğümünü bulun.

   > [!NOTE]
   > Ayrıca, **SalesOrderHeaders** düğümünün eşi olan bir **SalesOrderDetails** düğümü de vardır. **SalesOrderHeaders** düğümünün alt düğümünü seçtiğinizden emin olun.

2. Alt **SalesOrderDetails** düğümünü genişletin.

3. **SalesOrderDetails** düğümünün aşağıdaki alt düğümlerinin her biri için, düğümün yanındaki açılan menüye tıklayın ve **hiçbiri**' ni seçin:

   - **SalesOrderID**

   - **Salesorderdetailıd**

   - **rowguid**

   - **ModifiedDate & lt**

     Bu eylem, Visual Studio 'Nun bu verileri bir sonraki adımda oluşturduğunuz <xref:System.Windows.Controls.DataGrid> denetimine eklenmesini engeller. Bu izlenecek yol için, son kullanıcının bu verileri görmesini gerektirmeyen varsayılır.

4. **Veri kaynakları** penceresinde, alt **SALESORDERDETAILS** düğümünü **WPF Tasarımcısında**pencereye sürükleyin.

    Visual Studio, yeni bir veri bağlantılı <xref:System.Windows.Controls.DataGrid> denetimi tanımlamak için XAML oluşturur ve denetim tasarımcıda görünür. Visual Studio Ayrıca, arka plan kod dosyasındaki oluşturulan `GetSalesOrderHeadersQuery` yöntemini, verileri **SalesOrderDetails** varlığına dahil etmek için de güncelleştirir.

## <a name="testing-the-application"></a>Uygulamayı Test Etme
 Sipariş kayıtlarını görüntülediğini doğrulamak için uygulamayı derleyin ve çalıştırın.

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. **F5**tuşuna basın.

     Uygulama oluşturulur ve çalışır. Aşağıdakileri doğrulayın:

    - **Satış SIPARIŞI kimliği** açılan kutusu **71774**görüntüler. Bu, varlıktaki ilk sipariş KIMLIĞIDIR.

    - **Satış SIPARIŞI kimliği** Birleşik giriş kutusunda seçtiğiniz her sipariş için <xref:System.Windows.Controls.DataGrid> ayrıntılı sipariş bilgileri görüntülenir.

2. Uygulamayı kapatın.

## <a name="next-steps"></a>Sonraki Adımlar
 Bu yönergeyi tamamladıktan sonra, Visual Studio 'daki **veri kaynakları** PENCERESINI kullanarak WPF denetimlerini diğer veri kaynağı türlerine bağlamayı öğrenin. Daha fazla bilgi için bkz. bir [WCF veri HIZMETINE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) ve [WPF denetimlerini bir veri kümesine bağlama](../data-tools/bind-wpf-controls-to-a-dataset.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'daki VERILERE WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [WPF uygulamalarında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)