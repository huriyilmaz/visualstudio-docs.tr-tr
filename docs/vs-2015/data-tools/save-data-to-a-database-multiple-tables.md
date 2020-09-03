---
title: Verileri bir veritabanına kaydetme (birden çok tablo) | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655457"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Bir veritabanına (birden çok tablo) veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama geliştirmenin en yaygın senaryolarından biri, verileri bir Windows uygulamasında form üzerinde göstermek, verileri düzenlemek ve güncelleştirilmiş verileri veritabanına geri göndermek için kullanılır. Bu izlenecek yol, iki ilişkili tablodaki verileri görüntüleyen ve kayıtları nasıl düzenleydiğini ve değişiklikleri veritabanına geri kaydetmeyi gösteren bir form oluşturur. Bu örnekte, `Customers` `Orders` Northwind örnek veritabanındaki ve tabloları kullanılmaktadır.

 Bir TableAdapter metodunu çağırarak, uygulamanızdaki verileri veritabanına geri kaydedebilirsiniz `Update` . Tabloları **veri kaynakları** penceresinden bir form üzerine sürüklediğinizde, verileri kaydetmek için gereken kod otomatik olarak eklenir. Bir forma eklenen ek tablolar, bu kodun el ile eklenmesini gerektirir. Bu izlenecek yol, birden fazla tablodan güncelleştirmeleri kaydetmek için nasıl kod ekleneceğini gösterir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya kullandığınız sürüme bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Bu izlenecek yolda gösterilen görevler şunlardır:

- Yeni bir **Windows uygulaması** projesi oluşturma.

- [Veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)ile uygulamanızda bir veri kaynağı oluşturma ve yapılandırma.

- [Veri kaynakları penceresindeki](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)öğelerin denetimlerini ayarlama. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- **Veri kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimler oluşturma.

- Veri kümesindeki her tabloda birkaç kaydı değiştirme.

- Veri kümesindeki güncelleştirilmiş verileri veritabanına geri göndermek için kodu değiştirme.

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind örnek veritabanına erişim.

## <a name="create-the-windows-application"></a>Windows uygulaması oluşturma
 İlk adım bir **Windows uygulaması**oluşturmaktır. Bu adım sırasında projeye bir ad atanması isteğe bağlıdır, ancak daha sonra kaydetmeyi planladığımız için buna bir ad vereceğiz.

#### <a name="to-create-the-new-windows-application-project"></a>Yeni Windows uygulaması projesi oluşturmak için

1. **Dosya** menüsünde Yeni bir proje oluşturun.

2. Projeyi adlandırın `UpdateMultipleTablesWalkthrough` .

3. **Windows uygulaması**' nı seçin ve ardından **Tamam**' ı seçin. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     **UpdateMultipleTablesWalkthrough** projesi oluşturulup **Çözüm Gezgini**eklenir.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma
 Bu adım, **veri kaynağı Yapılandırma Sihirbazı**'Nı kullanarak Northwind veritabanından bir veri kaynağı oluşturur. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir.

#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde**veri kaynaklarını göster**' i seçin.

2. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için**Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin**ekranında **veritabanı**' nı seçin ve ardından **İleri**' yi seçin.

4. **Veri bağlantınızı seçin**ekranında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         -veya-

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu açın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet**sayfasında **İleri**' yi seçin.

7. **Veritabanı nesnelerinizi seçin**ekranında **Tablolar** düğümünü genişletin.

8. **Müşteriler** ve **siparişler** tablolarını seçip **son**' u seçin.

     **NorthwindDataSet** , projenize eklenir ve tablolar **veri kaynakları** penceresinde görüntülenir.

## <a name="set-the-controls-to-be-created"></a>Oluşturulacak denetimleri ayarlayın
 Bu kılavuzda, tablodaki veriler, `Customers` verilerin tek tek denetimlerde görüntülendiği bir **Ayrıntılar** düzeninde yer verilir. Tablodaki veriler, `Orders` denetimde görüntülenen **kılavuz** düzenidir <xref:System.Windows.Forms.DataGridView> .

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Veri kaynakları penceresinde öğelerin bırakma türünü ayarlamak için

1. **Veri kaynakları** penceresinde, **müşteriler** düğümünü genişletin.

2. **Müşteriler düğümünde,** **müşteriler** tablosunun denetimini ayrı denetimler olarak değiştirmek için denetim listesinden **Ayrıntılar** ' ı seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Veri bağlantılı formu oluşturma
 Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için

1. Ana **müşteriler** düğümünü **veri kaynakları** penceresinden **Form1**üzerine sürükleyin.

     Açıklayıcı etiketlere sahip veriye bağlı denetimler, formda gezinmek için bir araç şeridinde () birlikte görüntülenir <xref:System.Windows.Forms.BindingNavigator> . Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

2. İlgili **siparişler** düğümünü **veri kaynakları** penceresinden **Form1**üzerine sürükleyin.

    > [!NOTE]
    > İlişkili **siparişler** düğümü, **Faks** sütununun altında bulunur ve **müşteriler** düğümünün bir alt düğümüdür.

     <xref:System.Windows.Forms.DataGridView>Kayıtlar üzerinde gezinmek için bir denetim ve araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) formda görüntülenir. Bir OrdersTableAdapter ve <xref:System.Windows.Forms.BindingSource> bileşen tepsisinde görünür.

## <a name="addcode-to-update-the-database"></a>Veritabanını güncelleştirmek için AddCode
 `Update` **Müşteriler** ve **siparişler** TableAdapters yöntemlerini çağırarak veritabanını güncelleştirebilirsiniz. Varsayılan olarak, ' ın **Kaydet** düğmesine ait bir olay işleyicisi, <xref:System.Windows.Forms.BindingNavigator> güncelleştirmeleri veritabanına göndermek için formun koduna eklenir. Bu yordam, güncelleştirmeleri doğru sırada göndermek için kodu değiştirir. Bu, başvurusal bütünlük hataları oluşturma olasılığını ortadan kaldırır. Kod ayrıca, bir try-catch bloğunda güncelleştirme çağrısını sarmalayarak hata işleme uygular. Kodu uygulamanızın gereksinimlerine uyacak şekilde değiştirebilirsiniz.

> [!NOTE]
> Netlik için bu izlenecek yol bir işlem kullanmaz. Ancak, iki veya daha fazla ilişkili tabloyu güncelleştiriyorsanız, tüm güncelleştirme mantığını bir işlem içine dahil edin. İşlem, herhangi bir değişiklik kaydedilmeden önce bir veritabanında yapılan tüm değişikliklerin başarılı olmasını sağlayan bir işlemdir. Daha fazla bilgi için bkz. [işlemler ve eşzamanlılık](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).

#### <a name="to-add-update-logic-to-the-application"></a>Uygulamaya güncelleştirme mantığı eklemek için

1. Üzerinde **Kaydet** düğmesini seçin <xref:System.Windows.Forms.BindingNavigator> . Bu, kod düzenleyicisini `bindingNavigatorSaveItem_Click` olay işleyicisine açar.

2. Olay işleyicisindeki kodu, `Update` Ilgili TableAdapters yöntemlerini çağırmak için değiştirin. Aşağıdaki kod, her bir <xref:System.Data.DataRowState> ( <xref:System.Data.DataRowState> , <xref:System.Data.DataRowState> , ve) için güncelleştirilmiş bilgileri tutmak üzere üç geçici veri tablosu oluşturur <xref:System.Data.DataRowState> . Sonra güncelleştirmeler doğru sırada çalıştırılır. Kod aşağıdaki gibi görünmelidir:

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>Uygulamayı test etme

#### <a name="to-test-the-application"></a>Uygulamayı test etmek için

1. **F5**' i seçin.

2. Her tablodaki bir veya daha fazla kaydın verilerinde bazı değişiklikler yapın.

3. **Kaydet** düğmesini seçin.

4. Değişikliklerin kaydedildiğini doğrulamak için veritabanındaki değerleri kontrol edin.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, Windows uygulamanızda bir veri bağlantılı form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- Forma arama işlevleri ekleniyor. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms uygulamasına Parametreli sorgu ekleme](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Veritabanı nesneleri eklemek veya kaldırmak için veri kaynağını Düzenle. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesini düzenleme](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
