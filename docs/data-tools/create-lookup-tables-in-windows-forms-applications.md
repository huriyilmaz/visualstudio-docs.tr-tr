---
title: Windows Forms uygulamalarında arama tabloları oluşturma
description: Windows Forms uygulamalarında arama tabloları oluşturmayı okuyun. Arama tablosu, iki ilişkili veri tablosuna bağlanan denetimleri açıklar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 57190afba118468b4533ef1ecd30957eb25b08e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859054"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows Forms uygulamalarında arama tabloları oluşturma

Terim *arama tablosu* , iki ilişkili veri tablosuna bağlanan denetimleri açıklar. Bu arama denetimleri, ikinci tabloda seçilen bir değere göre ilk tablodaki verileri görüntüler.

Üst tablonun ana düğümünü ( [veri kaynakları penceresi](add-new-data-sources.md#data-sources-window)), formunuzdaki ilgili alt tablodaki sütuna zaten bağlı olan bir denetime sürükleyerek arama tabloları oluşturabilirsiniz.

Örneğin, `Orders` bir satış veritabanındaki tablosunu düşünün. Tablodaki her kayıt `Orders` `CustomerID` , hangi müşterinin siparişi yerleştirdiğini belirten bir içerir. , `CustomerID` Tablodaki bir müşteri kaydına işaret eden bir yabancı anahtardır `Customers` . Bu senaryoda, `Orders` **veri kaynakları** penceresinde tabloyu genişlettikten sonra ana düğümü **Ayrıntılar** olarak ayarlarsınız. Sonra, `CustomerID` sütununu <xref:System.Windows.Forms.ComboBox> (veya arama bağlamasını destekleyen başka bir denetimi) kullanacak şekilde ayarlayın ve `Orders` düğümü formunuza sürükleyin. Son olarak, `Customers` düğümü ilgili sütuna bağlanan denetime sürükleyin — bu durumda, <xref:System.Windows.Forms.ComboBox> `CustomerID` sütununa bağlanır.

## <a name="to-databind-a-lookup-control"></a>Arama denetimini bağlamak için

1. Projeniz açıkken, diğer Windows   >    >  **veri kaynaklarını** görüntüle ' yi seçerek veri kaynakları penceresini açın.

    > [!NOTE]
    > Arama tabloları, **veri kaynakları** penceresinde iki ilişkili tablonun veya nesnenin kullanılabilir olmasını gerektirir. Daha fazla bilgi için bkz. [veri kümelerinde ilişkiler](relationships-in-datasets.md).

2. Üst tabloyu ve tüm sütunlarını ve ilgili alt tabloyu ve tüm sütunlarını görene kadar **veri kaynakları** penceresindeki düğümleri genişletin.

    > [!NOTE]
    > Alt tablo düğümü, üst tabloda Genişletilebilir alt düğüm olarak görünen düğümdür.

3. Alt tablonun düğümünde denetim listesinden **Ayrıntılar** ' a tıklayarak alt tablonun bırakma türünü **Ayrıntılar** olarak değiştirin. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. İki tabloyla ilişkili düğümü bulun ( `CustomerID` önceki örnekteki düğüm). <xref:System.Windows.Forms.ComboBox>Denetim listesinden **ComboBox** ' i seçerek bırakma türünü bir olarak değiştirin.

5. Ana alt tablo düğümünü **veri kaynakları** penceresinden formunuzun üzerine sürükleyin.

     Veri sınırlama denetimleri (açıklayıcı etiketlerle birlikte) ve formda bir araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) görünür. Bir [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür.

6. Şimdi, ana üst tablo düğümünü **veri kaynakları** penceresinden doğrudan arama denetimine ( <xref:System.Windows.Forms.ComboBox> ) sürükleyin.

     Arama bağlamaları artık oluşturulmuştur. Denetimde ayarlanan belirli özellikler için aşağıdaki tabloya bakın.

    |Özellik|Ayarın açıklaması|
    |--------------| - |
    |**DataSource**|Visual Studio bu özelliği, <xref:System.Windows.Forms.BindingSource> denetimin üzerine sürüklediğiniz tablo için oluşturulan öğesine ayarlar ( <xref:System.Windows.Forms.BindingSource> Denetim oluşturulduğunda oluşturulan ' ın aksine).<br /><br /> Bir ayarlama yapmanız gerekiyorsa, bunu, <xref:System.Windows.Forms.BindingSource> göstermek istediğiniz sütunun bulunduğu tablonun öğesine ayarlayın.|
    |**Alınan**|Visual Studio bu özelliği, denetimin üzerine sürüklediğiniz tablo için bir dize veri türüne sahip birincil anahtardan sonraki ilk sütuna ayarlar.<br /><br /> Bir ayarlama yapmanız gerekiyorsa, bunu, göstermek istediğiniz sütun adına ayarlayın.|
    |**ValueMember**|Visual Studio bu özelliği birincil anahtara katılan ilk sütuna veya anahtar tanımlanmadığında tablodaki ilk sütuna ayarlar.<br /><br /> Bir ayarlama yapmanız gerekiyorsa, bunu tabloda, göstermek istediğiniz sütunu içeren birincil anahtar olarak ayarlayın.|
    |**SelectedValue**|Visual Studio, bu özelliği **veri kaynakları** penceresinden bırakılan özgün sütuna ayarlar.<br /><br /> Bir ayarlama yapmanız gerekiyorsa, bunu ilgili tablodaki yabancı anahtar sütununa ayarlayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
