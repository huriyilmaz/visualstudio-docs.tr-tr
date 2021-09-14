---
title: Windows Forms uygulamalarında arama tabloları oluşturma
description: Windows Forms uygulamalarında arama tabloları oluşturma makalelerini okuyun. Arama tablosu, iki ilişkili veri tablosuna bağlı denetimleri açıklar.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4d8bfc94d98c56d525d0d2d1c7f16f98cffbc7d0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631467"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows Forms uygulamalarında arama tabloları oluşturma

Arama *tablosu terimi,* iki ilişkili veri tablosuna bağlı denetimleri açıklar. Bu arama denetimleri, ikinci tabloda seçilen bir değere göre ilk tablodan verileri görüntüler.

Bir üst tablonun ana düğümünü (Veri Kaynakları [penceresinden)](add-new-data-sources.md#data-sources-window)form üzerinde ilgili alt tablodaki sütuna zaten bağlı olan bir denetime sürükleyerek arama tabloları oluşturabilirsiniz.

Örneğin, satış veritabanındaki `Orders` bir tablosu düşünün. Tablodaki her `Orders` kayıt, siparişi `CustomerID` hangi müşterinin yerleştiren bir içerir. `CustomerID`, tablodaki bir müşteri kaydını işaret alan yabancı bir `Customers` anahtardır. Bu senaryoda, Veri Kaynakları `Orders` penceresindeki **tabloyu genişletecek ve ana** düğümü Ayrıntılar olarak **ayarlayabilirsiniz.** Ardından sütunu bir (veya arama bağlamayı destekleyen başka bir denetim) kullanmak üzere `CustomerID` ayarlayın ve düğümü form üzerine <xref:System.Windows.Forms.ComboBox> `Orders` sürükleyin. Son olarak, düğümü ilgili sütuna (bu durumda sütununa bağlı) bağlı `Customers` <xref:System.Windows.Forms.ComboBox> olan denetime `CustomerID` sürükleyin.

## <a name="to-databind-a-lookup-control"></a>Arama denetimine veri bindirma

1. Projeniz açıkken Veri Kaynakları penceresini **açmak için** Diğer Kaynakları   >  **Görüntüle'Windows**  >  **Seçin.**

    > [!NOTE]
    > Arama tabloları, veri kaynakları penceresinde iki ilişkili tablo veya nesne **kullanılabilir gerektirir.** Daha fazla bilgi için [bkz. Veri kümelerini ilişkileri.](relationships-in-datasets.md)

2. Üst tabloyu ve  tüm sütunlarını, ilişkili alt tabloyu ve tüm sütunlarını görene kadar Veri Kaynakları penceresindeki düğümleri genişletin.

    > [!NOTE]
    > Alt tablo düğümü, üst tabloda genişletilebilir bir alt düğüm olarak görünen düğüm olur.

3. Alt tablonun düğümünde denetim **listesinden Ayrıntılar'ı**  seçerek alt tablonun bırakma türünü Ayrıntılar olarak değiştirebilirsiniz. Daha fazla bilgi için [bkz. Veri Kaynakları penceresinden sürüklenrken oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

4. İki tabloyla (önceki örnekteki `CustomerID` düğüm) ilgili düğümü bulun. Denetim listesinden <xref:System.Windows.Forms.ComboBox> **ComboBox'ı** seçerek bırakma türünü olarak değiştirebilirsiniz.

5. Ana alt tablo düğümünü Veri Kaynakları **penceresinden** form üzerine sürükleyin.

     Formda veriye bağlı denetimler (açıklayıcı etiketlerle) ve bir araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) görüntülenir. Bir [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> ve bileşen <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir.

6. Şimdi ana üst tablo düğümünü Veri Kaynakları **penceresinden doğrudan** arama denetimine <xref:System.Windows.Forms.ComboBox> ().

     Arama bağlamaları artık kurulur. Denetimde ayarlanmış belirli özellikler için aşağıdaki tabloya bakın.

    |Özellik|Ayarın açıklaması|
    |--------------| - |
    |**Datasource**|Visual Studio, denetimin üzerine sürükleyip (denetim oluşturulduğunda oluşturulan tablosu yerine) için oluşturulan bu özelliği <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource> olarak ayarlar.<br /><br /> Ayarlama yapmak gerekirse, bunu görüntülemek istediğiniz <xref:System.Windows.Forms.BindingSource> sütunu içeren tablonun sütunu olarak ayarlayın.|
    |**Displaymember**|Visual Studio özelliği, denetime sürüklersiniz tablosu için dize veri türüne sahip birincil anahtardan sonra ilk sütuna ayarlar.<br /><br /> Ayarlama yapmak gerekirse, bunu görüntülemek istediğiniz sütun adı olarak ayarlayın.|
    |**Valuemember**|Visual Studio özelliği birincil anahtara katılan ilk sütuna veya tanımlanmamışsa tablodaki ilk sütuna ayarlar.<br /><br /> Bir ayarlama yapmak gerekirse, bunu görüntülemek istediğiniz sütunu içeren tablodaki birincil anahtar olarak ayarlayın.|
    |**Selectedvalue**|Visual Studio özelliği Veri Kaynakları penceresinden bırakılan özgün **sütuna** ayarlar.<br /><br /> Ayarlama yapmak gerekirse, bunu ilgili tablodaki yabancı anahtar sütununa ayarlayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
