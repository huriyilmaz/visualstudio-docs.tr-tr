---
title: Verilere Windows Forms denetimleri bağlama | Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf93d96594b65b06670567e8c23cd83ccb7f1ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672973"
---
# <a name="bind-windows-forms-controls-to-data"></a>Verilere Windows Forms denetimleri bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri **kaynakları** penceresinden bir Windows formuna veya bir formdaki mevcut bir denetime nesneleri sürükleyerek veri kaynaklarını denetimlere bağlayabilirsiniz. Öğeleri sürüklemeden önce, bağlamak istediğiniz denetim türünü ayarlayabilirsiniz. Farklı değerler tablonun kendisini mi yoksa tek bir sütun mı seçtiğinize bağlı olarak görünür.  Ayrıca, özel değerler de ayarlayabilirsiniz. Bir tablo için, "Ayrıntılar" her sütunun ayrı bir denetime bağlandığı anlamına gelir.

 ![Veri kaynağını DataGridView 'a bağlama](../data-tools/media/raddata-bind-data-source-to-datagridview.png "radveri kaynağına veri kaynağını DataGridView 'a bağlama")

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="bind-to--data-in-a-datagridview-control"></a>DataGridView Denetimindeki verilere bağlama
 DataGridView için tüm tablo bu tek denetime bağlanır. Forma bir DataGridView sürüklediğinizde, kayıtlar () içinde gezinmek için bir araç şeridi <xref:System.Windows.Forms.BindingNavigator> de görüntülenir. Bir [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür. Aşağıdaki çizimde, Customers tablosunun Orders tablosuyla bir ilişkisi olduğundan, bir TableAdapterManager de eklenir. Bu değişkenlerin hepsi, otomatik olarak oluşturulan kodda form sınıfında özel Üyeler olarak bildirilmiştir. DataGridView 'in doldurulmasıyla ilgili otomatik oluşturulan kod form_load olay işleyicisinde bulunur. Veritabanını güncelleştirmek için verileri kaydetme kodu, BindingNavigator için Save olay işleyicisinde bulunur. Gerektiğinde bu kodu taşıyabilir veya değiştirebilirsiniz.

 ![BindingNavigator ile GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "BindingNavigator ile radveri GridView")

 DataGridView ve BindingNavigator davranışını özelleştirmek için sağ üst köşedeki akıllı etikete tıklayın:

 ![DataGridView ve Binding Navigator akıllı etiketleri](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "radveri DataGridView ve bağlama Gezgini akıllı etiketleri")

 Uygulamanızın ihtiyaç duyacağı denetimler **veri kaynakları** penceresinde yoksa, denetimler ekleyebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

 Ayrıca, denetimi verilere bağlamak için **veri kaynakları** penceresinden öğeleri zaten bir form üzerinde bulunan denetimlere sürükleyebilirsiniz. Veriye zaten bağlanan bir denetimin veri bağlamaları, en son sürüklediğiniz öğeye sıfırlanır. Geçerli bırakma hedefleri olması için, denetimlerin **veri kaynakları** penceresinden üzerine sürüklenen öğenin temel alınan veri türünü görüntülemesi yeterli olmalıdır. Örneğin, bir veri türüne sahip olan bir öğeyi <xref:System.DateTime> bir <xref:System.Windows.Forms.CheckBox> Tarih görüntüleme yeteneğine sahip olmadığından, üzerine sürüklemek için geçerli değildir <xref:System.Windows.Forms.CheckBox> .

## <a name="bind-to--data-in-individual-controls"></a>Tek denetimlerde verilere bağlama
 Bir veri kaynağını "details" öğesine bağladığınızda, veri kümesindeki her bir sütun ayrı bir denetime bağlanır.

 ![Veri kaynağını ayrıntılara bağlama](../data-tools/media/raddata-bind-data-source-to-details.png "veri kaynağını ayrıntılara bağlayan radveri")

> [!IMPORTANT]
> Önceki çizimde, Siparişler tablosundan değil Customers tablosunun Orders özelliğinden sürükleyeceğinizi unutmayın. Customer. Orders özelliğine bağlayarak, DataGridView içinde yapılan Gezinti komutları Ayrıntılar denetimlerinde anında yansıtılır. Siparişler tablosundan sürüklediyseniz denetimler yine de veri kümesine bağlanır, ancak bunlar DataGridView ile eşitlenmez.

 Aşağıdaki çizimde, Müşteriler tablosundaki siparişler özelliği **veri kaynakları** penceresinde "Ayrıntılar" a bağlandığında forma eklenen varsayılan veri bağlantılı denetimler gösterilmektedir.

 ![Ayrıntılar tablosu ile bağlantılı siparişler](../data-tools/media/raddata-orders-table-bound-to-details.png "ayrıntı ile bağlantılı radveri siparişlerinin tablosu")

 Ayrıca, her denetimin akıllı bir etiketi olduğunu unutmayın. Bu etiket yalnızca bu denetim için uygulanan özelleştirmeleri sağlar.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
