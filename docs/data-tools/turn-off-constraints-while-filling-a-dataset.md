---
title: Bir veri kümesini doldururken kısıtlamaları kapatma
description: Bir veri kümesi doldururken kısıtlamaları nasıl kapatacaklarını bilmek. Güncelleştirme kısıtlamalarını program aracılığıyla veya Veri Kümesi Tasarımcısı.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ab5ff2fe9702d56ddc2c4b767ac40f3d63ddbe15
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631113"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Bir veri kümesini doldururken kısıtlamaları kapatma

Bir veri kümesi kısıtlamalar (yabancı anahtar kısıtlamaları gibi) içeriyorsa, veri kümesine karşı gerçekleştirilen işlemlerin sırasıyla ilgili hatalar olabilir. Örneğin, ilgili üst kayıtları yüklemeden önce alt kayıtların yüklenmesi kısıtlamayı ihlal etmek ve hataya neden olabilir. Bir alt kaydı yükleyemediklerinden, kısıtlama ilgili üst kaydı denetler ve bir hata döndürür.

Geçici kısıtlamanın askıya alınmasına izin verecek bir mekanizma yoksa, alt tabloya her kayıt yükleme denemesi sırasında bir hata ortaya çıkar. Bir veri kümesinde tüm kısıtlamaları askıya almanın bir diğer yolu, <xref:System.Data.DataRow.BeginEdit%2A> ve <xref:System.Data.DataRow.EndEdit%2A> özellikleridir.

> [!NOTE]
> Kısıtlamalar kapalı olduğunda doğrulama <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> olayları (örneğin, ve ) yükseltlanmaz.

## <a name="to-suspend-update-constraints-programmatically"></a>Güncelleştirme kısıtlamalarını program aracılığıyla askıya almak için

- Aşağıdaki örnekte, bir veri kümesinde kısıtlama denetlemenin nasıl geçici olarak kapatıldığını gösterir:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb" id="Snippet10":::

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>güncelleştirme kısıtlamalarını askıya almak için Veri Kümesi Tasarımcısı

1. veri kümenizi **Veri Kümesi Tasarımcısı.** Daha fazla bilgi için [bkz. Adım adım: Veri kümesi oluşturma Veri Kümesi Tasarımcısı.](walkthrough-creating-a-dataset-with-the-dataset-designer.md)

2. Özellikler **penceresinde** özelliğini olarak <xref:System.Data.DataSet.EnforceConstraints%2A> `false` ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
- [Veri kümelerindeki ilişkiler](../data-tools/relationships-in-datasets.md)
