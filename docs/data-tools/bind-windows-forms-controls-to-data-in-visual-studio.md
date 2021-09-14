---
title: Verilere Windows Forms denetimleri bağlama
description: Uygulama Windows görüntülemek için Visual Studio form denetimlerini veriye bağlayın.
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
ms.openlocfilehash: 311bdc7d0bf236f29d09804257aaaa8ce991f32f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631586"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere Windows Forms denetimleri bağlama

Verileri Formlar'a bağarak uygulamanın kullanıcılarına Windows görüntüebilirsiniz. Bu veriye bağlı denetimleri oluşturmak için, öğeleri Veri Kaynakları penceresinden Windows Form Tasarımcısı'nda Visual Studio. 

![Veri Kaynağı sürükleme işlemi](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Veri Kaynakları **penceresi görünmüyorsa** Diğer Veri Kaynaklarını Görüntüle'Windows veya  >    >   **Shift** Alt D tuşlarına basarak +  + **açabilirsiniz.** Veri Kaynakları penceresini görmek için Visual Studio açık bir **projeniz** olması gerekir.

Öğeleri sürüklemeden önce bağlamak istediğiniz denetim türünü ayarlayabilirsiniz. Tablonun kendisini mi yoksa tek bir sütunu mu seçtiğinize bağlı olarak farklı değerler görünür.  Ayrıca özel değerler de oluşturabilirsiniz. Details, bir **tablo için** her sütunun ayrı bir denetime bağlı olduğu anlamına gelir.

![Veri kaynağını DataGridView'a bağlama](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource ve BindingNavigator denetimleri

Bileşen <xref:System.Windows.Forms.BindingSource> iki amaca hizmet eder. İlk olarak, denetimleri verilere bağlarken bir soyutlama katmanı sağlar. Formda denetimler doğrudan bir <xref:System.Windows.Forms.BindingSource> veri kaynağı yerine bileşene bağlı olur. İkincisi, bir nesne koleksiyonunu yönetebilir. 'a bir tür <xref:System.Windows.Forms.BindingSource> eklemek, bu türün bir listesini oluşturur.

Bileşen hakkında daha fazla <xref:System.Windows.Forms.BindingSource> bilgi için bkz:

- [BindingSource bileşeni](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource bileşen mimarisi](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

[BindingNavigator denetimi,](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) bir uygulama tarafından görüntülenen veriler arasında gezinmek için bir kullanıcı Windows sağlar.

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView denetiminde verilere bağlama

[DataGridView denetimi için](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms)tablonun tamamı bu tek denetime bağlı olur. Bir **DataGridView'u** forma sürüklerken, kayıtlarda gezinmeye yönelik bir araç şeridi ( <xref:System.Windows.Forms.BindingNavigator> ) da görünür. Bir [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> ve bileşen <xref:System.Windows.Forms.BindingNavigator> tepsisinde görüntülenir. Aşağıdaki çizimde, Customers tablosu Orders tablosuyla bir ilişkisi olduğundan [TableAdapterManager](/previous-versions/bb384426(v=vs.140)) da eklenmiştir. Bu değişkenlerin hepsi, otomatik olarak oluşturulan kodda form sınıfında özel üyeler olarak bildirildi. **DataGridView'u** doldurmak için otomatik olarak oluşturulan kod olay `Form_Load` işleyicisinde bulunur. Veritabanını güncelleştirmek için verileri kaydetme kodu `Save` BindingNavigator için olay **işleyicisinde bulunur.** Bu kodu gerektiğinde hareket ettirebilirsiniz veya değiştirebilirsiniz.

![BindingNavigator ile GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Her biri sağ üst köşedeki akıllı etikete tıklayarak **DataGridView** ve **BindingNavigator'ın** davranışını özelleştirebilirsiniz:

![DataGridView ve Bağlama Gezgini akıllı etiketleri](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Uygulamanıza gereken denetimler Veri Kaynakları **penceresinden kullanılamıyorsa** denetimler ebilirsiniz. Daha fazla bilgi için [Bkz. Veri Kaynakları penceresine özel denetimler ekleme.](../data-tools/add-custom-controls-to-the-data-sources-window.md)

Ayrıca, denetimi verilere bağlamak **için Veri** Kaynakları penceresindeki öğeleri bir formda zaten var olan denetimlere sürükleyebilirsiniz. Verilere zaten bağlı olan bir denetim, veri bağlamalarının en son sürüklendiği öğeye sıfırlanır. Geçerli bırakma hedefleri olması için denetimler, Veri Kaynakları penceresinden öğenin üzerine sürüklenen öğenin temel veri türünü **görüntüleyeme özelliğine sahip** olmalıdır. Örneğin, veri türüne sahip bir öğeyi üzerine sürüklemek geçerli değildir çünkü bir <xref:System.DateTime> <xref:System.Windows.Forms.CheckBox> tarihi görüntüleme <xref:System.Windows.Forms.CheckBox> özelliğine sahip değildir.

## <a name="bind-to-data-in-individual-controls"></a>Tek tek denetimlerde verilere bağlama

Bir veri kaynağını Ayrıntılar'a **bağ her** sütun ayrı bir denetime bağlı olur.

![Veri kaynağını ayrıntılara bağlama](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Önceki çizimde, Orders tablosundan değil Customers tablonun Orders özelliğinden sürüklemeniz gerekir. özelliğine `Customer.Orders` bağlanarak **DataGridView'da** yapılan gezinti komutları, ayrıntılar denetimlerine hemen yansıtıldı. Orders tablosundan sürüklenen denetimler yine de veri kümesine bağlı olur, ancak **DataGridView ile eşitlenmez.**

Aşağıdaki çizimde, Müşteriler tablosunda Orders özelliği Veri Kaynakları penceresinde Ayrıntılar'a bağlandikten  sonra forma eklenen varsayılan veriye bağlı **denetimler gösterilir.**

![Ayrıntılara bağlı siparişler tablosu](../data-tools/media/raddata-orders-table-bound-to-details.png)

Ayrıca her denetimin bir akıllı etiketi olduğunu unutmayın. Bu etiket yalnızca bu denetim için geçerli olan özelleştirmeleri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Denetimler verilerde Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms'ta veri bağlama (.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)