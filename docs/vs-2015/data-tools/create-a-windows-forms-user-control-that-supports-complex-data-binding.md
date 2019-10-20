---
title: Karmaşık veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturun | Microsoft Docs
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c4a20939ed2e3a036831930749bb59b5a42315
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670046"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Karmaşık veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows uygulamalarındaki formlarda verileri görüntülerken, **araç kutusundan**varolan denetimleri seçebilir veya uygulamanız standart denetimlerde kullanılamayan işlevselliği gerektiriyorsa özel denetimleri yazabilirsiniz. Bu izlenecek yol, <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> uygulayan bir denetimin nasıl oluşturulacağını gösterir. @No__t_0 uygulayan denetimler, verilere bağlanabilen bir `DataSource` ve `DataMember` özelliği içerir. Bu tür denetimler <xref:System.Windows.Forms.DataGridView> veya <xref:System.Windows.Forms.ListBox> benzerdir.

 Denetim yazma hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Veri bağlama senaryolarında kullanılacak denetimleri yazma sırasında, aşağıdaki veri bağlama özniteliklerinden birini uygulamanız gerekir:

|Veri bağlama özniteliği kullanımı|
|-----------------------------------|
|Verilerin tek bir sütununu (veya özelliği) görüntüleyen <xref:System.Windows.Forms.TextBox> gibi basit denetimlerde <xref:System.ComponentModel.DefaultBindingPropertyAttribute> uygulayın. Daha fazla bilgi için bkz. [basit veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Denetimlerin listesini (veya tabloları) görüntüleyen <xref:System.Windows.Forms.DataGridView> gibi denetimlerde <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> uygulayın. (Bu işlem Bu izlenecek yol sayfasında açıklanmaktadır.)|
|Verilerin listelerini (veya tabloları) görüntüleyen ancak tek bir sütun veya özellik sunması gereken <xref:System.Windows.Forms.ComboBox> gibi denetimlerde <xref:System.ComponentModel.LookupBindingPropertiesAttribute> uygulayın. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Bu izlenecek yol, bir tablodaki veri satırlarını görüntüleyen karmaşık bir denetim oluşturur. Bu örnek, Northwind örnek veritabanındaki `Customers` tablosunu kullanır. Karmaşık kullanıcı denetimi, müşteriler tablosunu özel denetimdeki bir <xref:System.Windows.Forms.DataGridView> görüntüler.

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Yeni bir **Windows uygulaması**oluşturun.

- Projenize yeni bir **Kullanıcı denetimi** ekleyin.

- Kullanıcı denetimini görsel olarak tasarlayın.

- @No__t_0 özniteliğini uygulayın.

- [Veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)ile bir veri kümesi oluşturun.

- Yeni karmaşık denetimi kullanmak için [veri kaynakları penceresinde](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) **Customers** tablosunu ayarlayın.

- **Veri kaynakları penceresinden** **Form1**üzerine sürükleyerek yeni denetim ekleyin.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind örnek veritabanına erişim.

## <a name="create-a-windows-application"></a>Windows uygulaması oluşturma
 İlk adım bir **Windows uygulaması**oluşturmaktır.

#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için

1. Visual Studio 'da, **Dosya** menüsünden Yeni bir **Proje**oluşturun.

2. Projeyi **ComplexControlWalkthrough**olarak adlandırın.

3. **Windows uygulaması**' nı seçin ve **Tamam**' ı tıklatın. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     **ComplexControlWalkthrough** projesi oluşturulur ve **Çözüm Gezgini**eklenir.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle
 Bu izlenecek yol, bir **Kullanıcı denetiminden**karmaşık bir veri bağlanabilir denetim oluşturduğundan, projeye bir **Kullanıcı denetim** öğesi eklemeniz gerekir.

#### <a name="to-add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi eklemek için

1. **Proje** menüsünden **Kullanıcı denetimi Ekle**' yi seçin.

2. **Ad** alanına **ComplexDataGridView** yazın ve ardından **Ekle**' ye tıklayın.

     **ComplexDataGridView** denetimi **Çözüm Gezgini**eklenir ve tasarımcıda açılır.

## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView denetimini tasarlama
 Bu adım kullanıcı denetimine bir <xref:System.Windows.Forms.DataGridView> ekler.

#### <a name="to-design-the-complexdatagridview-control"></a>ComplexDataGridView denetimini tasarlamak için

- **Araç kutusundan** bir <xref:System.Windows.Forms.DataGridView> Kullanıcı denetiminin tasarım yüzeyine sürükleyin.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleyin
 Veri bağlamayı destekleyen karmaşık denetimler için <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> uygulayabilirsiniz.

#### <a name="to-implement-the-complexbindingproperties-attribute"></a>ComplexBindingProperties özniteliğini uygulamak için

1. **ComplexDataGridView** denetimini Code View olarak değiştirin. ( **Görünüm** menüsünde **kod**' i seçin.)

2. @No__t_0 kodundaki kodu aşağıdaki kodla değiştirin:

     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]

3. **Build** menüsünde **Build Solution**öğesini seçin.

## <a name="creating-a-data-source-from-your-database"></a>Veritabanından veri kaynağı oluşturma
 Bu adım, Northwind örnek veritabanındaki `Customers` tablosuna dayalı bir veri kaynağı oluşturmak için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanır. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [ınstall SQL Server Sample Databases](../data-tools/install-sql-server-sample-databases.md).

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

8. @No__t_0 tablosunu seçin ve ardından **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve `Customers` tablosu **veri kaynakları** penceresinde görünür.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Müşteriler tablosunu ComplexDataGridView denetimini kullanacak şekilde ayarlama
 **Veri kaynakları** penceresinde, öğeleri formunuza sürüklemeden önce oluşturulacak denetimi ayarlayabilirsiniz.

#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Müşteriler tablosunu ComplexDataGridView denetimine bağlanacak şekilde ayarlamak için

1. Tasarımcıda **Form1** ' i açın.

2. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

3. **Müşteriler** düğümündeki açılan oka tıklayın ve **Özelleştir**' i seçin.

4. **Veri Kullanıcı arabirimi özelleştirme seçenekleri** Iletişim kutusunda **Ilişkili denetimler** listesinden **ComplexDataGridView** ' i seçin.

5. @No__t_0 tablosundaki aşağı açılan oka tıklayın ve denetim listesinden **ComplexDataGridView** ' i seçin.

## <a name="addcontrols-to-the-form"></a>Form için addcontrols
 Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için

- Ana **müşteriler** düğümünü **veri kaynakları** penceresinden form üzerine sürükleyin. Tablo verilerini göstermek için **ComplexDataGridView** denetiminin kullanıldığını doğrulayın.

## <a name="running-the-application"></a>Uygulamayı çalıştırma

#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

- Uygulamayı çalıştırmak için F5 tuşuna basın.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bazı tipik sonraki adımlar şunlardır:

- Özel denetimlerinizi, diğer uygulamalarda yeniden kullanabilmek için bir denetim kitaplığına yerleştirme.

- Arama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'daki verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [veri kaynakları penceresi Windows Forms Denetimlerinde sürüklerken oluşturulacak denetimi ayarlayın](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) [](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
