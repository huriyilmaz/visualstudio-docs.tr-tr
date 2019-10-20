---
title: TableAdapter DBDirect yöntemleriyle verileri kaydetme | Microsoft Docs
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655416"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect metotlarıyla veri kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, bir TableAdapter 'ın DBDirect yöntemlerini kullanarak SQL deyimlerini doğrudan bir veritabanına karşı çalıştırmaya yönelik ayrıntılı yönergeler sağlar. Bir TableAdapter 'ın DBDirect yöntemleri, veritabanı güncelleştirmeleriniz üzerinde ince bir denetim düzeyi sağlar. Uygulamanızı gerektiği gibi bireysel `Insert`, `Update` ve `Delete` yöntemlerini çağırarak belirli SQL deyimlerini ve saklı yordamları çalıştırmak için bunları kullanabilirsiniz (GÜNCELLEŞTIRMEYI gerçekleştiren aşırı yüklenmiş `Update` yönteminin aksine, Ekle ve deyimleri tek bir çağrıda sıler).

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Yeni bir **Windows uygulaması**oluşturun.

- [Veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)ile bir veri kümesi oluşturun ve yapılandırın.

- **Veri kaynakları** penceresinden öğeleri sürüklerken form üzerinde oluşturulacak denetimi seçin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- **Veri kaynakları** penceresinden forma öğe sürükleyerek veri bağlantılı bir form oluşturun.

- Veritabanına doğrudan erişmek ve ekleme, güncelleştirme ve silme işlemleri gerçekleştirmek için yöntemler ekleyin.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind örnek veritabanına erişim.

## <a name="create-a-windows-application"></a>Windows uygulaması oluşturma
 İlk adım bir **Windows uygulaması**oluşturmaktır.

#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için

1. Visual Studio 'da, **Dosya** menüsünde Yeni bir **Proje**oluşturun.

2. Projeyi **TableAdapterDbDirectMethodsWalkthrough**olarak adlandırın.

3. **Windows uygulaması**' nı seçin ve ardından **Tamam**' ı seçin. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     **TableAdapterDbDirectMethodsWalkthrough** projesi oluşturulup **Çözüm Gezgini**eklenir.

## <a name="create-a-data-source-from-your-database"></a>Veritabanınızdan bir veri kaynağı oluşturun
 Bu adım, Northwind örnek veritabanındaki `Region` tablosuna dayalı bir veri kaynağı oluşturmak için **veri kaynağı Yapılandırma Sihirbazı** ' nı kullanır. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir.

#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde **veri kaynaklarını göster**' i seçin.

2. Veri **kaynakları** penceresinde, **veri kaynağı Yapılandırma Sihirbazı**' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seçin** ekranında **veritabanı**' nı seçin ve ardından **İleri**' yi seçin.

4. **Veri bağlantınızı seçin** ekranında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

         veya

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' yi seçin.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** ekranında, **İleri**' yi seçin.

7. **Veritabanı nesnelerinizi seçin** ekranında **Tablolar** düğümünü genişletin.

8. @No__t_0 tablosunu seçip **son**' u seçin.

     **NorthwindDataSet** , projenize eklenir ve `Region` tablosu **veri kaynakları** penceresinde görünür.

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Verileri göstermek için forma addcontrols
 Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimler oluşturun.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows formunda veriye bağlı denetimler oluşturmak için

- Ana **bölge** düğümünü **veri kaynakları** penceresinden form üzerine sürükleyin.

     Kayıtlar üzerinde gezinmek için bir <xref:System.Windows.Forms.DataGridView> denetimi ve araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) formda görüntülenir. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), regiontableadapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Bireysel TableAdapter DbDirect yöntemlerini çağıran düğmeler eklemek için

1. **Araç kutusundan** üç <xref:System.Windows.Forms.Button> denetimini **Form1** üzerine sürükleyin ( **RegionDataGridView**altında).

2. Her düğme için aşağıdaki **ad** ve **metin** özelliklerini ayarlayın.

    |Name|Metin|
    |----------|----------|
    |`InsertButton`|**Ekleyin**|
    |`UpdateButton`|**Güncelleştir**|
    |`DeleteButton`|**Delete**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Veritabanına yeni kayıtlar eklemek üzere kod eklemek için

1. Tıklama olayı için bir olay işleyicisi oluşturmak ve kod düzenleyicisinde formunuzu açmak için **InsertButton** öğesini seçin.

2. @No__t_0 olay işleyicisini aşağıdaki kodla değiştirin:

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Veritabanındaki kayıtları güncelleştirmek üzere kod eklemek için

1. Tıklama olayı için bir olay işleyicisi oluşturmak ve formunuzu Kod düzenleyicisinde açmak için **UpdateButton** öğesine çift tıklayın.

2. @No__t_0 olay işleyicisini aşağıdaki kodla değiştirin:

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Veritabanından kayıtları silmek üzere kod eklemek için

1. Tıklama olayı için bir olay işleyicisi oluşturmak üzere **DeleteButton** ' ı seçin ve formunuzu Kod düzenleyicisinde açın.

2. @No__t_0 olay işleyicisini aşağıdaki kodla değiştirin:

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

- Uygulamayı çalıştırmak için **F5** ' i seçin.

- **Ekle** düğmesini seçin ve yeni kaydın kılavuzda göründüğünü doğrulayın.

- **Güncelleştir** düğmesini seçin ve kaydın kılavuzda güncelleştirildiğinden emin olun.

- **Sil** düğmesini seçin ve kaydın kılavuzdan kaldırıldığını doğrulayın.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, verilere bağlı bir form oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bu izlenecek yolda yapabileceğiniz bazı geliştirmeler şunlardır:

- Forma arama işlevleri ekleniyor. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms uygulamasına Parametreli sorgu ekleme](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- **Veri kaynakları** penceresi Içinden veri **kümesini sihirbaz ile yapılandır** ' a seçerek veri kümesine ek tablolar ekleme. İlgili düğümleri form üzerine sürükleyerek ilgili verileri görüntüleyen denetimler ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
