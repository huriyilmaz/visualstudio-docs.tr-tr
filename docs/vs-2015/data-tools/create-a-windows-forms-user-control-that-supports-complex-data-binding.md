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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670046"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Karmaşık veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows uygulamalarındaki formlarda verileri görüntülerken, **araç kutusundan**varolan denetimleri seçebilir veya uygulamanız standart denetimlerde kullanılamayan işlevselliği gerektiriyorsa özel denetimleri yazabilirsiniz. Bu izlenecek yol, uygulayan bir denetimin nasıl oluşturulacağını gösterir <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> . , <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> `DataSource` Verilerine bağlanabilen ve özelliğini içeren denetimler `DataMember` . Bu tür denetimler veya ile benzerdir <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.ListBox> .

 Denetim yazma hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Veri bağlama senaryolarında kullanılacak denetimleri yazma sırasında, aşağıdaki veri bağlama özniteliklerinden birini uygulamanız gerekir:

|Veri bağlama özniteliği kullanımı|
|-----------------------------------|
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute> <xref:System.Windows.Forms.TextBox> Verilerin tek bir sütununu (veya özelliğini) görüntüleyen bir gibi basit denetimleri uygulayın. Daha fazla bilgi için bkz. [basit veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute> <xref:System.Windows.Forms.DataGridView> Verilerin listelerini (veya tabloları) görüntüleyen, gibi denetimleri uygulayın. (Bu işlem Bu izlenecek yol sayfasında açıklanmaktadır.)|
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute> <xref:System.Windows.Forms.ComboBox> Verilerin listelerini (veya tabloları) görüntüleyen, ancak tek bir sütun veya özellik sunmanız gereken, gibi denetimleri uygulayın. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Bu izlenecek yol, bir tablodaki veri satırlarını görüntüleyen karmaşık bir denetim oluşturur. Bu örnek, `Customers` Northwind örnek veritabanındaki tablosunu kullanır. Karmaşık kullanıcı denetimi, içindeki Customers tablosunu <xref:System.Windows.Forms.DataGridView> özel denetimde görüntüler.

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Yeni bir **Windows uygulaması**oluşturun.

- Projenize yeni bir **Kullanıcı denetimi** ekleyin.

- Kullanıcı denetimini görsel olarak tasarlayın.

- Özniteliğini uygulayın `ComplexBindingProperty` .

- [Veri kaynağı Yapılandırma Sihirbazı](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)ile bir veri kümesi oluşturun.

- Yeni karmaşık denetimi kullanmak için [veri kaynakları penceresinde](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) **Customers** tablosunu ayarlayın.

- **Veri kaynakları penceresinden** **Form1**üzerine sürükleyerek yeni denetim ekleyin.

## <a name="prerequisites"></a>Önkoşullar
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
 Bu adım <xref:System.Windows.Forms.DataGridView> Kullanıcı denetimine bir ekler.

#### <a name="to-design-the-complexdatagridview-control"></a>ComplexDataGridView denetimini tasarlamak için

- <xref:System.Windows.Forms.DataGridView> **Araç kutusundan** bir öğesini Kullanıcı denetiminin tasarım yüzeyine sürükleyin.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleyin
 Veri bağlamayı destekleyen karmaşık denetimler için, uygulamasını uygulayabilirsiniz <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> .

#### <a name="to-implement-the-complexbindingproperties-attribute"></a>ComplexBindingProperties özniteliğini uygulamak için

1. **ComplexDataGridView** denetimini Code View olarak değiştirin. ( **Görünüm** menüsünde **kod**' i seçin.)

2. İçindeki kodu aşağıdaki gibi değiştirin `ComplexDataGridView` :

     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]

3. **Build** menüsünde **Build Solution**öğesini seçin.

## <a name="creating-a-data-source-from-your-database"></a>Veritabanından veri kaynağı oluşturma
 Bu adım, Northwind örnek veritabanındaki tabloya dayalı bir veri kaynağı oluşturmak için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanır `Customers` . Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir. Northwind örnek veritabanını ayarlama hakkında daha fazla bilgi için bkz. [ınstall SQL Server Sample Databases](../data-tools/install-sql-server-sample-databases.md).

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

8. Tabloyu seçin `Customers` ve ardından **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve `Customers` tablo **veri kaynakları** penceresinde görünür.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Müşteriler tablosunu ComplexDataGridView denetimini kullanacak şekilde ayarlama
 **Veri kaynakları** penceresinde, öğeleri formunuza sürüklemeden önce oluşturulacak denetimi ayarlayabilirsiniz.

#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Müşteriler tablosunu ComplexDataGridView denetimine bağlanacak şekilde ayarlamak için

1. Tasarımcıda **Form1** ' i açın.

2. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

3. **Müşteriler** düğümündeki açılan oka tıklayın ve **Özelleştir**' i seçin.

4. **Veri Kullanıcı arabirimi özelleştirme seçenekleri** Iletişim kutusunda **Ilişkili denetimler** listesinden **ComplexDataGridView** ' i seçin.

5. Tablodaki açılan oka tıklayın `Customers` ve denetim listesinden **ComplexDataGridView** ' i seçin.

## <a name="addcontrols-to-the-form"></a>Form için addcontrols
 Veri **kaynakları** penceresinden formunuza öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için

- Ana **müşteriler** düğümünü **veri kaynakları** penceresinden form üzerine sürükleyin. Tablo verilerini göstermek için **ComplexDataGridView** denetiminin kullanıldığını doğrulayın.

## <a name="running-the-application"></a>Uygulamayı çalıştırma

#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

- Uygulamayı çalıştırmak için F5'e basın.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bazı tipik sonraki adımlar şunlardır:

- Özel denetimlerinizi, diğer uygulamalarda yeniden kullanabilmek için bir denetim kitaplığına yerleştirme.

- Arama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'daki verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [veri kaynakları penceresi Windows Forms Denetimlerinde sürüklerken oluşturulacak denetimi ayarlayın](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) [Windows Forms Controls](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
