---
title: Verilere Windows Forms denetimleri bağlama
description: uygulamanızın kullanıcılarına veri görüntüleyebilmeniz için Windows Forms denetimleri Visual Studio veriye bağlayın.
ms.custom: SEO-VS-2020
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d891cc83008c844ddc694b958be6314c9f2de63a7c8383a541fc3ccd265d00bc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240646"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere Windows Forms denetimleri bağlama

verileri Windows Forms 'e bağlayarak uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. bu veri bağlantılı denetimleri oluşturmak için, öğeleri **veri kaynakları** penceresinden Visual Studio Windows Form Tasarımcısı üzerine sürükleyin.

![Veri kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> **veri kaynakları** penceresi görünür değilse,   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek veya **shıft** + **Alt** + **D** tuşlarına basarak dosyayı açabilirsiniz. **veri kaynakları** penceresini görmek için Visual Studio bir projenizin açık olması gerekir.

Öğeleri sürüklemeden önce, bağlamak istediğiniz denetim türünü ayarlayabilirsiniz. Farklı değerler tablonun kendisini mi yoksa tek bir sütun mı seçtiğinize bağlı olarak görünür.  Ayrıca, özel değerler de ayarlayabilirsiniz. Bir tablo için **Ayrıntılar** , her sütunun ayrı bir denetime bağlandığı anlamına gelir.

![Veri kaynağını DataGridView 'a bağlama](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource ve BindingNavigator denetimleri

<xref:System.Windows.Forms.BindingSource>Bileşen iki amaca hizmet eder. İlk olarak, denetimleri verilere bağlarken bir soyutlama katmanı sağlar. Formdaki denetimler <xref:System.Windows.Forms.BindingSource> doğrudan bir veri kaynağına değil, bileşene bağlıdır. İkincisi, bir nesne koleksiyonunu yönetebilir. Bir türü öğesine eklemek, <xref:System.Windows.Forms.BindingSource> Bu türün bir listesini oluşturur.

Bileşen hakkında daha fazla bilgi için <xref:System.Windows.Forms.BindingSource> bkz.

- [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource bileşeni mimarisi](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator denetimi](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) , Windows bir uygulama tarafından görünen veriler arasında gezinmek için bir kullanıcı arabirimi sağlar.

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView Denetimindeki verilere bağlama

[DataGridView denetiminde](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), tüm tablo bu tek denetime bağlanır. Forma bir **DataGridView** sürüklediğinizde, kayıtlar () içinde gezinmek için bir araç şeridi <xref:System.Windows.Forms.BindingNavigator> de görüntülenir. Bir [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür. Aşağıdaki çizimde, Customers tablosunun Orders tablosuyla bir ilişkisi olduğundan, bir [TableAdapterManager](/previous-versions/bb384426(v=vs.140)) de eklenir. Bu değişkenlerin hepsi, otomatik olarak oluşturulan kodda form sınıfında özel Üyeler olarak bildirilmiştir. **DataGridView** 'i doldurmak için otomatik olarak oluşturulan kod `Form_Load` olay işleyicisinde bulunur. Veritabanını güncelleştirmek için verileri kaydetme kodu, `Save` **BindingNavigator** için olay işleyicisinde bulunur. Gerektiğinde bu kodu taşıyabilir veya değiştirebilirsiniz.

![BindingNavigator ile GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

**DataGridView** ve **BindingNavigator** davranışını özelleştirmek için sağ üst köşedeki akıllı etikete tıklayın:

![DataGridView ve Binding Navigator akıllı etiketleri](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Uygulamanızın ihtiyaç duyacağı denetimler **veri kaynakları** penceresinde yoksa, denetimler ekleyebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Ayrıca, denetimi verilere bağlamak için **veri kaynakları** penceresinden öğeleri zaten bir form üzerinde bulunan denetimlere sürükleyebilirsiniz. Veriye zaten bağlanan bir denetimin veri bağlamaları, en son sürüklediğiniz öğeye sıfırlanır. Geçerli bırakma hedefleri olması için, denetimlerin **veri kaynakları** penceresinden üzerine sürüklenen öğenin temel alınan veri türünü görüntülemesi yeterli olmalıdır. Örneğin, bir veri türüne sahip olan bir öğeyi <xref:System.DateTime> bir <xref:System.Windows.Forms.CheckBox> Tarih görüntüleme yeteneğine sahip olmadığından, üzerine sürüklemek için geçerli değildir <xref:System.Windows.Forms.CheckBox> .

## <a name="bind-to-data-in-individual-controls"></a>Tek denetimlerde verilere bağlama

Bir veri kaynağını **ayrıntılara** bağladığınızda, veri kümesindeki her sütun ayrı bir denetime bağlanır.

![Veri kaynağını ayrıntılara bağlama](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Önceki çizimde, Siparişler tablosundan değil Customers tablosunun Orders özelliğinden sürükleyeceğinizi unutmayın. `Customer.Orders`Özelliğine bağlayarak, **DataGridView** 'de yapılan Gezinti komutları Ayrıntılar denetimlerinde anında yansıtılır. Siparişler tablosundan sürüklediyseniz denetimler yine de veri kümesine bağlanır, ancak bunlar **DataGridView** ile eşitlenmez.

Aşağıdaki çizimde, Müşteriler tablosundaki siparişler özelliği **veri kaynakları** penceresindeki **ayrıntılara** bağlandıktan sonra forma eklenen varsayılan veri bağlantılı denetimler gösterilmektedir.

![Ayrıntılar tablosu ile bağlantılı siparişler](../data-tools/media/raddata-orders-table-bound-to-details.png)

Ayrıca, her denetimin akıllı bir etiketi olduğunu unutmayın. Bu etiket yalnızca bu denetim için uygulanan özelleştirmeleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio içindeki verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms veri bağlama (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)