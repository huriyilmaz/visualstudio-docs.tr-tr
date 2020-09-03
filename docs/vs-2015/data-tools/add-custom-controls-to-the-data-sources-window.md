---
title: Veri Kaynakları penceresine özel denetimler ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 402e62602d99492730d3094965e76964cd5f8218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673089"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Veri kaynakları penceresine özel denetimler ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veriye dayalı bir denetim oluşturmak için **veri kaynakları** penceresinden tasarım yüzeyine bir öğe sürüklediğinizde, oluşturduğunuz denetim türünü seçebilirsiniz. Penceredeki her öğe, aralarından seçim yapabileceğiniz denetimleri görüntüleyen bir açılan liste içerir. Her öğeyle ilişkili denetimlerin kümesi, öğenin veri türüne göre belirlenir. Oluşturmak istediğiniz denetim listede görünmüyorsa, denetimi listeye eklemek için bu konudaki yönergeleri izleyebilirsiniz...

 **Veri kaynakları** penceresinde öğeler için oluşturmak üzere veri bağlantılı denetimleri seçme hakkında daha fazla bilgi için, bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları**' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="customize-the-list-of-bindable-controls-for-a-data-type"></a><a name="customizinglist"></a> Veri türü için bağlanabilir denetimlerin listesini özelleştirme
 **Veri kaynakları** penceresinde belirli bir veri türüne sahip öğeler için kullanılabilir denetimler listesine denetim eklemek veya kaldırmak için aşağıdaki adımları gerçekleştirin.

#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Bir veri türü için listelenecek denetimleri seçmek için

1. WPF Tasarımcısı veya Windows Form Tasarımcısı açık olduğundan emin olun.

2. **Veri kaynakları** penceresinde, pencereye eklediğiniz bir veri kaynağının parçası olan bir öğeye tıklayın ve sonra öğenin açılan menüsüne tıklayın.

3. Açılan menüde, **Özelleştir**' e tıklayın. Aşağıdaki iletişim kutularından biri açılır:

    - Windows Form Tasarımcısı açıksa, **Seçenekler** Iletişim kutusunun **veri UI özelleştirmesi** sayfası açılır.

    - WPF Tasarımcısı açıksa, **denetimi bağlamayı Özelleştir** iletişim kutusu açılır.

4. İletişim kutusunda, **veri türü** aşağı açılan listesinden bir veri türü seçin.

    - Bir tablo veya nesne için denetim listesini özelleştirmek için **[Liste]** öğesini seçin.

    - Bir tablonun sütunu veya bir nesnenin bir özelliği için denetim listesini özelleştirmek için, temel alınan veri deposundaki sütunun veya özelliğin veri türünü seçin.

    - Denetim listesini Kullanıcı tanımlı şekillere sahip veri nesnelerini görüntüleyecek şekilde özelleştirmek için **[diğer]** seçeneğini belirleyin. Örneğin, uygulamanızda belirli bir nesnenin birden fazla özelliğinden verileri görüntüleyen özel bir denetim varsa **[diğer]** seçeneğini belirleyin.

5. **İlişkili denetimler** kutusunda, seçili veri türü için kullanılabilir olmasını istediğiniz her bir denetimi seçin veya listeden kaldırmak istediğiniz denetimlerin seçimini kaldırın.

    > [!NOTE]
    > Seçmek istediğiniz denetim **ilişkili denetimler** kutusunda görünmezse, denetimi listeye eklemeniz gerekir. Daha fazla bilgi için, bkz. [bir veri türü Için Ilişkili denetimler listesine denetim ekleme](#addingcontrols).

6. **Tamam**’a tıklayın.

7. **Veri kaynakları** penceresinde, yalnızca bir veya daha fazla denetimi ilişkilendirdiğiniz veri türünün bir öğesine tıklayın ve sonra öğenin açılan menüsüne tıklayın.

     **İlişkili denetimler** kutusunda seçtiğiniz denetimler artık öğenin açılan menüsünde görüntülenir.

## <a name="addcontrols-to-the-list-of-associated-controls-for-a-data-type"></a><a name="addingcontrols"></a> Bir veri türü için ilişkili denetimlerin listesine addcontrols
 Bir denetimi veri türüyle ilişkilendirmek istiyorsanız, ancak denetim **ilişkili denetimler** kutusunda görünmüyorsa, denetimi listeye eklemeniz gerekir. Denetim geçerli çözümde veya başvurulan bir derlemede bulunmalıdır. Ayrıca **araç kutusunda**da kullanılabilir olmalıdır ve denetimin veri bağlama davranışını belirten bir özniteliği olmalıdır.

#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>İlişkili denetimler listesine denetim eklemek için

1. Araç kutusuna sağ tıklayıp **öğeleri seç** **' i** seçerek istediğiniz denetimi **araç kutusuna** ekleyin.

     Denetim aşağıdaki özniteliklerden birine sahip olmalıdır.

    |Öznitelik|Açıklama|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Bu özniteliği, gibi verilerin tek bir sütununu (veya özelliğini) görüntüleyen basit denetimlerde uygulayın <xref:System.Windows.Forms.TextBox> .|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Bu özniteliği, gibi verilerin listesini (veya tabloları) görüntüleyen denetimlerde uygulayın <xref:System.Windows.Forms.DataGridView> .|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Bu özniteliği, verilerin listelerini (veya tablolarını) görüntüleyen denetimlerde uygulayın, ancak aynı zamanda tek bir sütun veya bir özelliği (örneğin,) sunmalıdır <xref:System.Windows.Forms.ComboBox> .|

2. Windows Forms için,      **Seçenekler** Iletişim kutusunda **veri UI özelleştirmesi** sayfasını açın. Ya da WPF için **Denetim Bağlamayı Özelleştir** iletişim kutusunu açın. Daha fazla bilgi için, bkz. [veri türü Için bağlanabilir denetimlerin listesini özelleştirme](#customizinglist).

3. **İlişkili denetimler** kutusunda, **araç** kutusuna yeni eklediğiniz denetim artık görünmelidir.

    > [!NOTE]
    > Yalnızca geçerli çözüm içinde veya başvurulan bir derlemede bulunan denetimler, ilişkili denetimler listesine eklenebilir. (Denetimler de önceki tablodaki veri bağlama özniteliklerinden birini uygulamalıdır.) Veri **kaynakları** penceresinde kullanılamayan özel bir denetime veri bağlamak için, denetimi **araç kutusundan** tasarım yüzeyine sürükleyin ve ardından **veri kaynakları** penceresinden denetime bağlamak için öğeyi sürükleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
