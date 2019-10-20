---
title: Basit veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturun | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf30a38384863c9ba5a8af35af3326a51058d831
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668765"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Basit veri bağlama modelini destekleyen bir Windows Forms kullanıcı denetimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows uygulamalarındaki formlarda verileri görüntülerken, **araç kutusundan**varolan denetimleri seçebilir veya uygulamanız standart denetimlerde kullanılamayan işlevselliği gerektiriyorsa özel denetimleri yazabilirsiniz. Bu izlenecek yol, <xref:System.ComponentModel.DefaultBindingPropertyAttribute> uygulayan bir denetimin nasıl oluşturulacağını gösterir. @No__t_0 uygulayan denetimler, verilere bağlanabilen bir özellik içerebilir. Bu tür denetimler <xref:System.Windows.Forms.TextBox> veya <xref:System.Windows.Forms.CheckBox> benzerdir.

 Denetim yazma hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Veri bağlama senaryolarında kullanılacak denetimleri yazarken, aşağıdaki veri bağlama özniteliklerinden birini uygulamalısınız:

|Veri bağlama özniteliği kullanımı|
|-----------------------------------|
|Verilerin tek bir sütununu (veya özelliği) görüntüleyen <xref:System.Windows.Forms.TextBox> gibi basit denetimlerde <xref:System.ComponentModel.DefaultBindingPropertyAttribute> uygulayın. (Bu işlem Bu izlenecek yol sayfasında açıklanmaktadır.)|
|Denetimlerin listesini (veya tabloları) görüntüleyen <xref:System.Windows.Forms.DataGridView> gibi denetimlerde <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> uygulayın. Daha fazla bilgi için bkz. [karmaşık veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Verilerin listelerini (veya tabloları) görüntüleyen ancak tek bir sütun veya özellik sunması gereken <xref:System.Windows.Forms.ComboBox> gibi denetimlerde <xref:System.ComponentModel.LookupBindingPropertiesAttribute> uygulayın. Daha fazla bilgi için bkz. [arama verisi bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Bu izlenecek yol, tablodaki tek bir sütundan verileri görüntüleyen basit bir denetim oluşturur. Bu örnek, Northwind örnek veritabanındaki `Customers` tablosunun `Phone` sütununu kullanır. Basit Kullanıcı denetimi, müşterilerin telefon numaralarını bir <xref:System.Windows.Forms.MaskedTextBox> kullanarak ve maskeyi bir telefon numarasına ayarlayarak standart telefon numarası biçiminde görüntüler.

 Bu izlenecek yol sırasında şunları yapmayı öğreneceksiniz:

- Yeni bir **Windows uygulaması**oluşturun.

- Projenize yeni bir **Kullanıcı denetimi** ekleyin.

- Kullanıcı denetimini görsel olarak tasarlayın.

- @No__t_0 özniteliğini uygulayın.

- **Veri kaynağı yapılandırma** Sihirbazı ile bir veri kümesi oluşturun.

- **Veri kaynakları** penceresindeki **Telefon** sütununu yeni denetimi kullanacak şekilde ayarlayın.

- Yeni denetimdeki verileri göstermek için bir form oluşturun.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için şunlar gerekir:

- Northwind örnek veritabanına erişim.

## <a name="create-a-windows-application"></a>Windows uygulaması oluşturma
 İlk adım bir **Windows uygulaması**oluşturmaktır.

#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için

1. Visual Studio 'da, **Dosya** menüsünden Yeni bir **Proje**oluşturun.

2. Projeyi **SimpleControlWalkthrough**olarak adlandırın.

3. **Windows uygulaması** ' nı seçin ve **Tamam**' a tıklayın. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     **SimpleControlWalkthrough** projesi oluşturulur ve **Çözüm Gezgini**eklenir.

## <a name="add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi Ekle
 Bu izlenecek yol, bir **Kullanıcı denetiminden**basit bir veri bağlanabilir denetim oluşturur, bu nedenle **SimpleControlWalkthrough** projesine bir **Kullanıcı denetim** öğesi ekleyin.

#### <a name="to-add-a-user-control-to-the-project"></a>Projeye Kullanıcı denetimi eklemek için

1. **Proje** menüsünden **Kullanıcı denetimi Ekle**' yi seçin.

2. Ad alanına `PhoneNumberBox` yazın ve **Ekle**' ye tıklayın.

     **PhoneNumberBox** denetimi **Çözüm Gezgini**eklenir ve tasarımcıda açılır.

## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox denetimini tasarlama
 Bu izlenecek yol, `PhoneNumberBox` denetimini oluşturmak için var olan <xref:System.Windows.Forms.MaskedTextBox> üzerine genişletilir.

#### <a name="to-design-the-phonenumberbox-control"></a>PhoneNumberBox denetimini tasarlamak için

1. **Araç kutusundan** bir <xref:System.Windows.Forms.MaskedTextBox> Kullanıcı denetiminin tasarım yüzeyine sürükleyin.

2. Yeni sürüklediğiniz <xref:System.Windows.Forms.MaskedTextBox> akıllı etiketini seçin ve **maskeyi ayarla**' yı seçin.

3. **Giriş maskesi** Iletişim kutusunda **telefon numarası** ' nı seçin ve maskeyi ayarlamak için **Tamam** ' ı tıklatın.

## <a name="add-the-required-data-binding-attribute"></a>Gerekli veri bağlama özniteliğini ekleyin
 Veri bağlamayı destekleyen basit denetimler için <xref:System.ComponentModel.DefaultBindingPropertyAttribute> uygulayın.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>DefaultBindingProperty özniteliğini uygulamak için

1. @No__t_0 denetimini kod görünümüne geçirin. ( **Görünüm** menüsünde **kod**öğesini seçin.)

2. @No__t_0 kodundaki kodu aşağıdaki kodla değiştirin:

     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]

3. **Build** menüsünde **Build Solution**öğesini seçin.

## <a name="create-a-data-source-from-your-database"></a>Veritabanınızdan bir veri kaynağı oluşturun
 Bu adım, Northwind örnek veritabanındaki `Customers` tablosuna dayalı bir veri kaynağı oluşturmak için **veri kaynağı yapılandırma** Sihirbazı ' nı kullanır. Bağlantıyı oluşturmak için Northwind örnek veritabanına erişiminizin olması gerekir.

#### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri** menüsünde **veri kaynaklarını göster**' e tıklayın.

2. Veri **kaynakları** penceresinde, **veri kaynağı yapılandırma** Sihirbazı ' nı başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veri kaynağı türü seç** sayfasında, **veritabanı**' nı seçin ve ardından **İleri**' ye tıklayın.

4. **Veri bağlantınızı seçin** sayfasında aşağıdakilerden birini yapın:

    - Northwind örnek veritabanıyla kurulan veri bağlantısı aşağı açılan listede kullanılabilir durumdaysa bunu seçin.

    - **Yeni bağlantı** ' yı seçerek **Bağlantı Ekle/Değiştir** iletişim kutusunu başlatın.

5. Veritabanınız parola gerektiriyorsa, hassas verileri dahil etme seçeneğini belirleyin ve ardından **İleri**' ye tıklayın.

6. **Bağlantı dizesini uygulama yapılandırma dosyasına kaydet** sayfasında, **İleri**' ye tıklayın.

7. **Veritabanı nesnelerinizi seçin** sayfasında **Tablolar** düğümünü genişletin.

8. @No__t_0 tablosunu seçin ve ardından **son**' a tıklayın.

     **NorthwindDataSet** , projenize eklenir ve `Customers` tablosu **veri kaynakları** penceresinde görünür.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Telefon sütununu PhoneNumberBox denetimini kullanacak şekilde ayarlama
 **Veri kaynakları** penceresinde, öğeleri formunuza sürüklemeden önce oluşturulacak denetimi ayarlayabilirsiniz.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Telefon sütununu PhoneNumberBox denetimine bağlanacak şekilde ayarlamak için

1. Tasarımcıda **Form1** ' i açın.

2. **Veri kaynakları** penceresindeki **müşteriler** düğümünü genişletin.

3. **Müşteriler** düğümündeki açılan oka tıklayın ve denetim listesinden **Ayrıntılar** ' ı seçin.

4. **Telefon** sütunundaki açılan oka tıklayın ve **Özelleştir**' i seçin.

5. **Veri Kullanıcı arabirimi özelleştirme seçenekleri** Iletişim kutusunda **Ilişkili denetimler** listesinden **PhoneNumberBox** ' ı seçin.

6. **Telefon** sütunundaki açılan oka tıklayın ve **PhoneNumberBox**' ı seçin.

## <a name="addcontrols-to-the-form"></a>Form için addcontrols
 Veri **kaynakları** penceresinden forma öğe sürükleyerek veri bağlantılı denetimleri oluşturabilirsiniz.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Form üzerinde veri bağlama denetimleri oluşturmak için

- Ana **müşteriler** düğümünü **veri kaynakları** penceresinden form üzerine sürükleyin ve `PhoneNumberBox` denetiminin verileri `Phone` sütununda göstermek için kullanıldığını doğrulayın.

     Açıklayıcı etiketlere sahip veriye bağlı denetimler, formda gezinmek için bir araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) ile birlikte görüntülenir. Bir [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

## <a name="run-the-application"></a>Uygulamayı çalıştırma

#### <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

- Uygulamayı çalıştırmak için F5 tuşuna basın.

## <a name="next-steps"></a>Sonraki Adımlar
 Uygulama gereksinimlerinize bağlı olarak, veri bağlamayı destekleyen bir denetim oluşturduktan sonra gerçekleştirmek isteyebileceğiniz birkaç adım vardır. Bazı tipik sonraki adımlar şunlardır:

- Özel denetimlerinizi, diğer uygulamalarda yeniden kullanabilmek için bir denetim kitaplığına yerleştirme.

- Daha karmaşık veri bağlama senaryolarını destekleyen denetimler oluşturma. Daha fazla bilgi için bkz. [karmaşık veri bağlamayı destekleyen Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) ve [Arama veri bağlamayı destekleyen bir Windows Forms Kullanıcı denetimi oluşturma](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'daki verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlayın](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
