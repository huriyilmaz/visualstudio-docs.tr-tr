---
title: WPF uygulamalarında arama tabloları oluşturma
description: WPF uygulamalarında arama tabloları oluşturma. Arama tablosu, bir veri tablosundan, diğer bir tablodaki yabancı anahtar alan değerine göre bilgi gösteren bir denetimdir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: cc390642155d33f75bf5c4a69236945658845639
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867106"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF uygulamalarında arama tabloları oluşturma

Terim *arama tablosu* (bazen *arama bağlaması* denir), bir veri tablosundan, başka bir tablodaki yabancı anahtar alanının değerine göre bilgi görüntüleyen bir denetimi açıklar. Bir üst tablonun veya nesnenin ana **düğümünü, ilgili** alt tablodaki bir sütuna veya özelliğe zaten bağımlı olan bir denetimin üzerine sürükleyerek bir arama tablosu oluşturabilirsiniz.

Örneğin, `Orders` bir satış veritabanındaki tablosunu düşünün. Tablodaki her kayıt `Orders` `CustomerID` , siparişi hangi müşterinin yaptığını belirten bir içerir. , `CustomerID` Tablodaki bir müşteri kaydına işaret eden bir yabancı anahtardır `Customers` . Tablodan siparişlerin bir listesini görüntülediğinizde, `Orders` yerine gerçek müşteri adını göstermek isteyebilirsiniz `CustomerID` . Müşteri adı `Customers` tabloda olduğundan, müşteri adını göstermek için bir arama tablosu oluşturmanız gerekir. Arama tablosu, `CustomerID` `Orders` ilişkide gezinmek için kayıttaki değeri kullanır ve müşteri adını döndürür.

## <a name="to-create-a-lookup-table"></a>Arama tablosu oluşturmak için

1. Projenize ilgili verileri içeren aşağıdaki veri kaynağı türlerinden birini ekleyin:

    - Veri kümesi veya Varlık Veri Modeli.

    - WCF veri hizmeti, WCF hizmeti veya Web hizmeti. Daha fazla bilgi için bkz. [nasıl yapılır: bir hizmette verilere bağlanma](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Nesneyi. Daha fazla bilgi için bkz. [Visual Studio 'da nesnelere bağlama](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Bir arama tablosu oluşturabilmeniz için önce iki ilişkili tablo veya nesne, proje için bir veri kaynağı olarak bulunmalıdır.

2. **WPF tasarımcısını** açın ve tasarımcı 'Nın **veri kaynakları** penceresindeki öğeler için geçerli bir bırakma hedefi olan bir kapsayıcı içerdiğinden emin olun.

     Geçerli bırakma hedefleri hakkında daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3. Veri **kaynakları** penceresini açmak için **veri** menüsünde **veri kaynaklarını göster** ' e tıklayın.

4. Üst tabloyu veya nesneyi ve ilgili alt tabloyu veya nesneyi görene kadar **veri kaynakları** penceresinde düğümleri genişletin.

    > [!NOTE]
    > İlişkili alt tablo veya nesne, üst tablo veya nesne altında genişletilebilen bir alt düğüm olarak görünen düğümdür.

5. Alt düğümün açılan menüsüne tıklayın ve **Ayrıntılar**' ı seçin.

6. Alt düğümü genişletin.

7. Alt düğüm altında, alt ve üst verileri ilişkilendiren öğenin açılan menüsüne tıklayın. (Önceki örnekte, bu **CustomerID** düğümüdür.) Arama bağlamasını destekleyen aşağıdaki denetim türlerinden birini seçin:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > **ListBox** veya **ListView** denetimi listede görünmezse, bu denetimleri listeye ekleyebilirsiniz. Bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Öğesinden türetilen herhangi bir özel denetim <xref:System.Windows.Controls.Primitives.Selector> .

        > [!NOTE]
        > **Veri kaynakları** penceresinde öğeler için seçebileceğiniz denetim listesine özel denetimler ekleme hakkında bilgi için, bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Alt düğümü **veri kaynakları** penceresinden WPF Tasarımcısı 'ndaki bir kapsayıcıya sürükleyin. (Önceki örnekte, alt düğüm **Orders** düğümüdür.)

     Visual Studio, sürüklediğiniz öğelerin her biri için yeni veri bağlantılı denetimler oluşturan XAML oluşturur. XAML ayrıca <xref:System.Windows.Data.CollectionViewSource> bırakma hedefinin kaynaklarına alt tablo veya nesne için yeni bir ekler. Visual Studio, bazı veri kaynaklarında verileri tabloya veya nesneye yüklemek için de kod üretir. Daha fazla bilgi için bkz. [Visual Studio 'DA WPF denetimlerini verilere bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. **Veri kaynakları** penceresinden üst düğümü daha önce oluşturduğunuz arama bağlama denetiminin üzerine sürükleyin. (Önceki örnekte, ana düğüm **müşteriler** düğümüdür).

     Visual Studio, arama bağlamasını yapılandırmak için denetimdeki bazı özellikleri ayarlar. Aşağıdaki tabloda, Visual Studio 'Nun değiştirdiği özellikler listelenmiştir. Gerekirse, bu özellikleri XAML 'de veya **Özellikler** penceresinde değiştirebilirsiniz.

    |Özellik|Ayarın açıklaması|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Bu özellik, denetimde görüntülenen verileri almak için kullanılan koleksiyonu veya bağlamayı belirtir. Visual Studio, bu özelliği <xref:System.Windows.Data.CollectionViewSource> denetime sürüklediğiniz ana veriler için olarak ayarlar.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Bu özellik, denetimde görüntülenen veri öğesinin yolunu belirtir. Visual Studio bu özelliği, bir dize veri türüne sahip olan birincil anahtardan sonra ana verilerdeki ilk sütuna veya özelliğe ayarlar.<br /><br /> Üst verilerde farklı bir sütun veya özellik göstermek istiyorsanız, bu özelliği farklı bir özelliğin yolu olarak değiştirin.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio bu özelliği, tasarımcıya sürüklediğiniz alt verilerin sütununa veya özelliğine bağlar. Bu, üst verilerin yabancı anahtarıdır.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio bu özelliği, ana verilere yabancı anahtar olan alt verilerin sütununun veya özelliğinin yoluna ayarlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)
- [İzlenecek yol: bir WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)
