---
title: WPF uygulamalarında arama tabloları oluşturma
description: WPF uygulamaları içinde arama tabloları oluşturun. Arama tablosu, başka bir tablodaki yabancı anahtar alan değerini temel alan bir veri tablosundan bilgileri gösteren bir denetimdir.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b5c1ee368bca523be99074cd3df2ad20dadc99877ea6673fd4bba45ec961f99f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347421"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>WPF uygulamalarında arama tabloları oluşturma

Arama tablosu *terimi* (bazen arama bağlaması olarak da *adlandırılan),* başka bir tablodaki yabancı anahtar alanı değerine göre bir veri tablosundan bilgileri görüntüleyen bir denetimi açıklar. Veri Kaynakları penceresindeki bir üst tablonun veya nesnenin ana  düğümünü ilgili alt tablodaki bir sütuna veya özelle bağlantılı bir denetime sürükleyerek arama tablosu oluşturabilirsiniz.

Örneğin, satış veritabanındaki `Orders` bir tablosu düşünün. Tablodaki her `Orders` kayıt, siparişi `CustomerID` hangi müşterinin yerleştiren bir içerir. `CustomerID`, tablodaki bir müşteri kaydına bakan yabancı bir `Customers` anahtardır. Tablodan bir sipariş listesi `Orders` görüntüleniyorsa, yerine gerçek müşteri adını görüntülemek istiyor `CustomerID` olabilir. Müşteri adı tabloda `Customers` olduğundan, müşteri adını görüntülemek için bir arama tablosu oluşturmanız gerekir. Arama tablosu, `CustomerID` ilişkide `Orders` gezinmek ve müşteri adını iade etmek için kayıtta yer alan değeri kullanır.

## <a name="to-create-a-lookup-table"></a>Arama tablosu oluşturmak için

1. Aşağıdaki veri kaynağı türlerinden birini projenize ilgili verilerle ekleyin:

    - Veri kümesi veya Varlık Veri Modeli.

    - WCF Veri Hizmeti, WCF hizmeti veya web hizmeti. Daha fazla bilgi için, [bkz. How to: Bağlan to Data in a Service](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Nesne. Daha fazla bilgi için [bkz. Visual Studio.](bind-objects-in-visual-studio.md)

    > [!NOTE]
    > Arama tablosu oluşturamadan önce, proje için bir veri kaynağı olarak iki ilişkili tablo veya nesne mevcut olması gerekir.

2. **WPF Tasarımcısını açın** ve tasarımcının Veri Kaynakları penceresinde öğeler için geçerli bir bırakma hedefi olan bir kapsayıcı **içerdiğini emin** olun.

     Geçerli bırakma hedefleri hakkında daha fazla bilgi için [bkz. WPF denetimlerini](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)Visual Studio.

3. Veri menüsünde **Veri** Kaynaklarını **Göster'e tıklayın** ve Veri **Kaynakları penceresini** açın.

4. Üst tabloyu veya nesneyi **ve** ilgili alt tabloyu veya nesneyi görene kadar Veri Kaynakları penceresindeki düğümleri genişletin.

    > [!NOTE]
    > İlgili alt tablo veya nesne, üst tablo veya nesne altında genişletilebilir bir alt düğüm olarak görünen düğüm olur.

5. Alt düğümün açılan menüsüne tıklayın ve Ayrıntılar'ı **seçin.**

6. Alt düğümü genişletin.

7. Alt düğümün altında, alt ve üst verileri ilişkili öğenin açılan menüsüne tıklayın. (Önceki örnekte **customerID düğümü bu** şekildedir.) Arama bağlamayı destekleyen aşağıdaki denetim türlerinden birini seçin:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > **ListBox veya** **ListView** denetimi listede görünmüyorsa, bu denetimleri listeye ekleyebilirsiniz. Bilgi için [bkz. Veri Kaynakları penceresinden sürüklenrken oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

    - 'den türeten herhangi bir özel <xref:System.Windows.Controls.Primitives.Selector> denetim.

        > [!NOTE]
        > Veri Kaynakları penceresinde öğeler için seçebilirsiniz denetim listesine özel denetimler ekleme hakkında bilgi için bkz. Veri Kaynakları  [penceresine özel denetimler ekleme.](../data-tools/add-custom-controls-to-the-data-sources-window.md)

8. Alt düğümü Veri Kaynakları **penceresinden** WPF tasarımcısında bir kapsayıcıya sürükleyin. (Önceki örnekte, alt düğüm Orders **düğümü** olur.)

     Visual Studio sürükleyip her bir öğe için yeni veriye bağlı denetimler oluşturan XAML oluşturur. XAML ayrıca bırakma <xref:System.Windows.Data.CollectionViewSource> hedefinin kaynaklarına alt tablo veya nesne için yeni bir ekler. Bazı veri kaynakları için Visual Studio tabloya veya nesneye veri yüklemek için kod da oluşturur. Daha fazla bilgi için [bkz. WPF denetimlerini Visual Studio.](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)

9. Veri Kaynakları penceresinden üst **düğümü daha** önce oluşturduğunuz arama bağlama denetimine sürükleyin. (Önceki örnekte, üst düğüm Müşteriler **düğümü** olur).

     Visual Studio bağlamayı yapılandırmak için denetimde bazı özellikleri ayarlar. Aşağıdaki tabloda, değişiklik yapılan Visual Studio listele. Gerekirse, bu özellikleri XAML'de veya Özellikler penceresinde **değiştirebilirsiniz.**

    |Özellik|Ayarın açıklaması|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Bu özellik, denetimde görüntülenen verileri almak için kullanılan koleksiyonu veya bağlamayı belirtir. Visual Studio denetimine <xref:System.Windows.Data.CollectionViewSource> sürüklemiş üst veriler için bu özelliği olarak ayarlar.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Bu özellik, denetimde görüntülenen veri öğesinin yolunu belirtir. Visual Studio, bu özelliği birincil anahtardan sonra dize veri türüne sahip ilk sütun veya özellik olarak ayarlar.<br /><br /> Üst verilerde farklı bir sütun veya özellik görüntülemek için bu özelliği farklı bir özelliğin yoluna göre değiştirebilirsiniz.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio, bu özelliği tasarımcıya sürüklenen alt verilerin sütununa veya özelliğine bağlar. Bu, üst verilerin yabancı anahtarıdır.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio, bu özelliği üst verilerin yabancı anahtarı olan alt verilerin sütun veya özelliğinin yoluna ayarlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [WPF uygulamalarındaki ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)
- [Adım adım kılavuz: WPF uygulamasında ilgili verileri görüntüleme](../data-tools/display-related-data-in-wpf-applications.md)
