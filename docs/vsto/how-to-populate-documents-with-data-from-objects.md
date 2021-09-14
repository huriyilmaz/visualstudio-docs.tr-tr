---
title: 'Nasıl yapılır: belgeleri nesnelerden verilerle doldurma'
description: çözümünüzdeki bir nesneden verileri nasıl kullanabileceğinizi öğrenin ve verileri bir belge içinde göstermek için Windows Forms denetimleri kullanabilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cba1869353071be287f244c7783964b010fff91d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634022"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Nasıl yapılır: belgeleri nesnelerden verilerle doldurma

veri nesnesindeki verileri erişen, Windows Forms projelerinde yaptığı gibi Microsoft Office Word için belge düzeyi projelerde aynı şekilde çalışmaktadır. aynı araçları ve kodu kullanarak verileri bir nesneden çözümünüze taşıyın ve verileri görüntülemek için Windows Forms denetimleri kullanabilirsiniz. Bunlara ek olarak, konak denetimlerini kullanarak verileri görüntüleyebilirsiniz. konak denetimleri, Microsoft Office Word 'de olaylar ve veri bağlama özelliğiyle geliştirilmiş yerel nesnelerdir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Belgeyi bir nesneden alınan verilerle doldurmak için üç temel adımı tamamlamalısınız:

- Veriye bağlayacağınız belgeye bir denetim ekleyin.

- Belgeye bir veri nesnesi ekleyin.

- veri nesnesini BindingSource 'a Bağlan.

## <a name="to-add-a-data-object"></a>Veri nesnesi eklemek için

Veri nesnesi eklemek için **veri kaynakları** penceresini açın ve nesnesinden bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>veri nesnesini BindingSource 'a Bağlan

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