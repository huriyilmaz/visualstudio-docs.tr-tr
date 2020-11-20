---
title: Bir veri kümesini doldururken kısıtlamaları kapatma
description: Bir veri kümesini doldururken kısıtlamaların nasıl kapatılacağı hakkında bilgi. Güncelleştirme kısıtlamalarını programlama yoluyla veya Veri Kümesi Tasarımcısı kullanarak askıya alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 8a4d1e17d2f6a0159a9c0187d5e1a3d16216d0ba
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998323"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Bir veri kümesini doldururken kısıtlamaları kapatma

Bir veri kümesi kısıtlamalar içeriyorsa (örneğin, yabancı anahtar kısıtlamaları), veri kümesinde gerçekleştirilen işlemlerin sırasıyla ilgili hatalar oluşturabilir. Örneğin, ilgili üst kayıtları yüklemeden önce alt kayıtları yükleme bir kısıtlamayı ihlal edebilir ve hataya neden olabilir. Bir alt kayıt yükledikten hemen sonra kısıtlama ilgili üst kaydı denetler ve bir hata oluşturur.

Geçici kısıtlama askıya almaya izin veren bir mekanizma yoksa, alt tabloya bir kayıt yüklemeye her seferinde bir hata oluşur. Bir veri kümesindeki tüm kısıtlamaları askıya almanın başka bir yolu <xref:System.Data.DataRow.BeginEdit%2A> , ve <xref:System.Data.DataRow.EndEdit%2A> özellikleridir.

> [!NOTE]
> Kısıtlamalar devre dışı bırakıldığında doğrulama olayları (örneğin, <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging> ) oluşturulmaz.

## <a name="to-suspend-update-constraints-programmatically"></a>Güncelleştirme kısıtlamalarını programlı bir şekilde askıya almak için

- Aşağıdaki örnek, bir veri kümesindeki kısıtlama denetiminin geçici olarak nasıl kapatılacağı gösterilmektedir:

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Veri Kümesi Tasarımcısı kullanarak güncelleştirme kısıtlamalarını askıya almak için

1. Veri kümenizi **veri kümesi Tasarımcısı** açın. Daha fazla bilgi için bkz. [Izlenecek yol: veri kümesi Tasarımcısı veri kümesi oluşturma](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. **Özellikler** penceresinde, <xref:System.Data.DataSet.EnforceConstraints%2A> özelliğini olarak ayarlayın `false` .

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)
