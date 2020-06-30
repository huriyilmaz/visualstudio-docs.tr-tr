---
title: 'Nasıl yapılır: belgeleri nesnelerden verilerle doldurma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38461fc30f71a811033ea70bfe560a6492f56e12
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547179"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Nasıl yapılır: belgeleri nesnelerden verilerle doldurma

Veri nesnesindeki verileri erişen, Windows Forms projelerinde yaptığı gibi Microsoft Office Word için belge düzeyi projelerde aynı şekilde çalışmaktadır. Aynı araçları ve kodu kullanarak verileri bir nesneden çözümünüze taşıyın ve verileri görüntülemek için Windows Forms denetimleri kullanabilirsiniz. Bunlara ek olarak, konak denetimlerini kullanarak verileri görüntüleyebilirsiniz. Konak denetimleri, Microsoft Office Word 'de olaylar ve veri bağlama özelliğiyle geliştirilmiş yerel nesnelerdir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Belgeyi bir nesneden alınan verilerle doldurmak için üç temel adımı tamamlamalısınız:

- Veriye bağlayacağınız belgeye bir denetim ekleyin.

- Belgeye bir veri nesnesi ekleyin.

- Veri nesnesini BindingSource 'a bağlayın.

## <a name="to-add-a-data-object"></a>Veri nesnesi eklemek için

Veri nesnesi eklemek için **veri kaynakları** penceresini açın ve nesnesinden bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Veri nesnesini BindingSource 'a bağlama

Belge düzeyi projelerinde, belgenize denetimler ekler ve bunları tasarım zamanında verilere bağlarsınız.

VSTO eklenti projelerinde, denetimler oluşturur ve bunları çalışma zamanında bağlarsınız.

### <a name="document-level-projects"></a>Belge düzeyi projeleri

Veri nesnesini BindingSource 'a bağlamak için:

1. **Veri kaynakları** penceresinden istediğiniz veri alanını belgenize sürükleyin. Bu otomatik olarak bir denetim oluşturur.

2. Kodunuzda, veri kaynağı için seçtiğiniz nesnenin türünün bir örneğini oluşturun.

3. Örneğini <xref:System.Windows.Forms.BindingSource.DataSource%2A> öğesinin özelliğine atayın <xref:System.Windows.Forms.BindingSource> .

### <a name="application-level-projects"></a>Uygulama düzeyi projeleri

Veri nesnesini BindingSource 'a bağlamak için:

1. Kodunuzda, veri kaynağıyla ilişkili nesne türünün bir örneğini oluşturun.

2. Bir <xref:System.Windows.Forms.BindingSource> örneği oluşturun.

3. Veri kaynağı örneğini <xref:System.Windows.Forms.BindingSource.DataSource%2A> öğesinin özelliğine atayın <xref:System.Windows.Forms.BindingSource> .

4. Veri kaynağını denetime veri bağlama olarak ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)