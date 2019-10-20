---
title: Verilere Windows Forms denetimleri bağlama
ms.date: 11/03/2017
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 24c3549cf98e49f3419ef0e7387a6c236c15e9e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648836"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere Windows Forms denetimleri bağlama

Verileri Windows Forms 'e bağlayarak uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. Bu veriye dayalı denetimleri oluşturmak için, öğeleri **veri kaynakları** penceresinden Visual Studio 'daki Windows Form Tasarımcısı sürükleyin.

![Veri kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> **Veri kaynakları** penceresi görünür değilse,**diğer Windows**  > **veri kaynaklarını** **görüntüle**  >  seçerek veya **SHIFT** +**alt** +**D**tuşlarına basarak açabilirsiniz. **Veri kaynakları** penceresini görmek Için Visual Studio 'da açık bir projeniz olmalıdır.

Öğeleri sürüklemeden önce, bağlamak istediğiniz denetim türünü ayarlayabilirsiniz. Farklı değerler tablonun kendisini mi yoksa tek bir sütun mı seçtiğinize bağlı olarak görünür.  Ayrıca, özel değerler de ayarlayabilirsiniz. Bir tablo için **Ayrıntılar** , her sütunun ayrı bir denetime bağlandığı anlamına gelir.

![Veri kaynağını DataGridView 'a bağlama](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource ve BindingNavigator denetimleri

@No__t_0 bileşeni iki amaca hizmet eder. İlk olarak, denetimleri verilere bağlarken bir soyutlama katmanı sağlar. Formdaki denetimler doğrudan bir veri kaynağına değil <xref:System.Windows.Forms.BindingSource> bileşenine bağlıdır. İkincisi, bir nesne koleksiyonunu yönetebilir. @No__t_0 bir türü eklemek, bu türün bir listesini oluşturur.

@No__t_0 bileşeni hakkında daha fazla bilgi için bkz.:

- [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource bileşeni mimarisi](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator denetimi](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) bir Windows uygulaması tarafından görünen veriler arasında gezinmek için bir kullanıcı arabirimi sağlar.

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView Denetimindeki verilere bağlama

[DataGridView denetiminde](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), tüm tablo bu tek denetime bağlanır. Forma bir **DataGridView** sürüklediğiniz zaman, kayıtlarda gezinmek için bir araç şeridi (<xref:System.Windows.Forms.BindingNavigator>) de görüntülenir. Bir [veri kümesi](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> ve <xref:System.Windows.Forms.BindingNavigator> bileşen tepsisinde görünür. Aşağıdaki çizimde, Customers tablosunun Orders tablosuyla bir ilişkisi olduğundan, bir [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) de eklenir. Bu değişkenlerin hepsi, otomatik olarak oluşturulan kodda form sınıfında özel Üyeler olarak bildirilmiştir. **DataGridView** 'in doldurulmasıyla ilgili otomatik oluşturulan kod `Form_Load` olay işleyicisinde bulunur. Veritabanını güncelleştirmek için verileri kaydetme kodu, **BindingNavigator**için `Save` olay işleyicisinde bulunur. Gerektiğinde bu kodu taşıyabilir veya değiştirebilirsiniz.

![BindingNavigator ile GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

**DataGridView** ve **BindingNavigator** davranışını özelleştirmek için sağ üst köşedeki akıllı etikete tıklayın:

![DataGridView ve Binding Navigator akıllı etiketleri](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Uygulamanızın ihtiyaç duyacağı denetimler **veri kaynakları** penceresinde yoksa, denetimler ekleyebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Ayrıca, denetimi verilere bağlamak için **veri kaynakları** penceresinden öğeleri zaten bir form üzerinde bulunan denetimlere sürükleyebilirsiniz. Veriye zaten bağlanan bir denetimin veri bağlamaları, en son sürüklediğiniz öğeye sıfırlanır. Geçerli bırakma hedefleri olması için, denetimlerin **veri kaynakları** penceresinden üzerine sürüklenen öğenin temel alınan veri türünü görüntülemesi yeterli olmalıdır. Örneğin, <xref:System.Windows.Forms.CheckBox> bir tarihi görüntüleme yeteneğine sahip olmadığından, veri türü <xref:System.DateTime> olan bir öğeyi bir <xref:System.Windows.Forms.CheckBox> sürüklemek geçerli değildir.

## <a name="bind-to-data-in-individual-controls"></a>Tek denetimlerde verilere bağlama

Bir veri kaynağını **ayrıntılara**bağladığınızda, veri kümesindeki her sütun ayrı bir denetime bağlanır.

![Veri kaynağını ayrıntılara bağlama](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Önceki çizimde, Siparişler tablosundan değil Customers tablosunun Orders özelliğinden sürükleyeceğinizi unutmayın. @No__t_0 özelliğine bağlayarak, **DataGridView** içinde yapılan Gezinti komutları Ayrıntılar denetimlerinde anında yansıtılır. Siparişler tablosundan sürüklediyseniz denetimler yine de veri kümesine bağlanır, ancak bunlar **DataGridView**ile eşitlenmez.

Aşağıdaki çizimde, Müşteriler tablosundaki siparişler özelliği **veri kaynakları** penceresindeki **ayrıntılara** bağlandıktan sonra forma eklenen varsayılan veri bağlantılı denetimler gösterilmektedir.

![Ayrıntılar tablosu ile bağlantılı siparişler](../data-tools/media/raddata-orders-table-bound-to-details.png)

Ayrıca, her denetimin akıllı bir etiketi olduğunu unutmayın. Bu etiket yalnızca bu denetim için uygulanan özelleştirmeleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms veri bağlama (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)