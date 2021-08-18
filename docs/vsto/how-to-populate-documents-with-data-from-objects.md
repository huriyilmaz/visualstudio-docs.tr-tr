---
title: 'Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak'
description: Çözümünüzde bir nesneden verileri nasıl kullanabileceğinizi ve verileri bir belgede görüntülemek için Windows Forms denetimlerini nasıl kullanabileceğinizi öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046795"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak

Bir veri nesnesine veri tahakkuk etme, Microsoft Office Word için belge düzeyi projelerde, Windows Forms projelerinde olduğu gibi çalışır. Bir nesneden çözümünüze veri getirmek için aynı araçları ve kodu kullanır ve verileri görüntülemek için Windows Forms denetimlerini kullanabilirsiniz. Ayrıca, konak denetimlerini kullanarak verileri görüntüebilirsiniz. Konak denetimleri, Word'Microsoft Office ve veri bağlama özelliğiyle geliştirilmiş yerel nesnelerdir. Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Belgeyi bir nesneden verilerle doldurmak için üç temel adımı tamamlamanız gerekir:

- Belgeye verilere bağlanabilirsiniz bir denetim ekleyin.

- Belgeye bir veri nesnesi ekleyin.

- Bağlan nesnesini BindingSource'a bağlama.

## <a name="to-add-a-data-object"></a>Veri nesnesi eklemek için

Veri nesnesi eklemek için Veri Kaynakları **penceresini açın ve** bir nesneden veri kaynağı oluşturun. Daha fazla bilgi için [bkz. Yeni veri kaynakları ekleme.](../data-tools/add-new-data-sources.md)

## <a name="connect-the-data-object-to-the-bindingsource"></a>Bağlan nesnesini BindingSource'a bağlama

Belge düzeyindeki projelerde, belgenize denetimler ekler ve bunları tasarım zamanında verilere bağlarsınız.

Bu VSTO projelerinde denetimler oluşturabilir ve bunları çalışma zamanında bağlayabilirsiniz.

### <a name="document-level-projects"></a>Belge düzeyi projeler

Veri nesnesini BindingSource'a bağlamak için:

1. Veri Kaynakları penceresinden istediğiniz **veri alanını** belgenize sürükleyin. Bu, otomatik olarak bir denetim oluşturur.

2. Kodunda, veri kaynağı için seçtiğiniz nesne türünün bir örneğini oluşturun.

3. Örneğini <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğinin özelliğine <xref:System.Windows.Forms.BindingSource> attayabilirsiniz.

### <a name="application-level-projects"></a>Uygulama düzeyindeki projeler

Veri nesnesini BindingSource'a bağlamak için:

1. Kodunda, veri kaynağıyla ilişkili nesne türünün bir örneğini oluşturun.

2. Bir <xref:System.Windows.Forms.BindingSource> örneği oluşturun.

3. Veri kaynağı örneğini <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğine attayabilirsiniz. <xref:System.Windows.Forms.BindingSource>

4. Veri kaynağını denetime veri bağlama olarak ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource bileşenine genel bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)