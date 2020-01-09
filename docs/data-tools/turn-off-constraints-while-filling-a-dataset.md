---
title: Bir veri kümesini doldururken kısıtlamaları kapatma
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 13cde04c3a10833c25fdc351d730b866f876e8da
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586139"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Bir veri kümesini doldururken kısıtlamaları kapatma

Bir veri kümesi kısıtlamalar içeriyorsa (örneğin, yabancı anahtar kısıtlamaları), veri kümesinde gerçekleştirilen işlemlerin sırasıyla ilgili hatalar oluşturabilir. Örneğin, ilgili üst kayıtları yüklemeden önce alt kayıtları yükleme bir kısıtlamayı ihlal edebilir ve hataya neden olabilir. Bir alt kayıt yükledikten hemen sonra kısıtlama ilgili üst kaydı denetler ve bir hata oluşturur.

Geçici kısıtlama askıya almaya izin veren bir mekanizma yoksa, alt tabloya bir kayıt yüklemeye her seferinde bir hata oluşur. Bir veri kümesindeki tüm kısıtlamaları askıya almanın bir başka yolu da <xref:System.Data.DataRow.BeginEdit%2A>ve <xref:System.Data.DataRow.EndEdit%2A> özelliklerdir.

> [!NOTE]
> (Örneğin, <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging>) doğrulama olayları, kısıtlamalar devre dışı bırakıldığında oluşturulmaz.

## <a name="to-suspend-update-constraints-programmatically"></a>Güncelleştirme kısıtlamalarını programlı bir şekilde askıya almak için

- Aşağıdaki örnek, bir veri kümesindeki kısıtlama denetiminin geçici olarak nasıl kapatılacağı gösterilmektedir:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Veri Kümesi Tasarımcısı kullanarak güncelleştirme kısıtlamalarını askıya almak için

1. Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için bkz. [Izlenecek yol: veri kümesi Tasarımcısı veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. **Özellikler** penceresinde <xref:System.Data.DataSet.EnforceConstraints%2A> özelliğini `false`olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)
