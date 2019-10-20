---
title: Veri kümesini doldururken kısıtlamaları kapatma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6646f669bf2c465d8e0f705f8fba956b979952ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667162"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>Bir veri kümesini doldururken kısıtlamaları kapatma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veri kümesi kısıtlamalar içeriyorsa (örneğin, yabancı anahtar kısıtlamaları), bu, veri kümesinde gerçekleştirilen işlemlerin sırasıyla ilgili hatalar oluşturabilir. Örneğin, loadingrelated üst kayıtlarından önce alt kayıtları yükleme bir kısıtlamayı ihlal edebilir ve hataya neden olabilir. Bir alt kayıt yükledikten hemen sonra kısıtlama ilgili üst kaydı denetler ve bir hata oluşturur.

 Geçici kısıtlama askıya almaya izin veren bir mekanizma yoksa, alt tabloya bir kayıt yüklemeye her seferinde bir hata oluşur. Bir veri kümesindeki tüm kısıtlamaları askıya almanın bir başka yolu da <xref:System.Data.DataRow.BeginEdit%2A> ve <xref:System.Data.DataRow.EndEdit%2A> özelliklerdir.

> [!NOTE]
> (Örneğin, <xref:System.Data.DataTable.ColumnChanging> ve <xref:System.Data.DataTable.RowChanging>) doğrulama olayları, kısıtlamalar devre dışı bırakıldığında oluşturulmaz.

### <a name="to-suspend-update-constraints-programmatically"></a>Güncelleştirme kısıtlamalarını programlı bir şekilde askıya almak için

- Aşağıdaki örnek, bir veri kümesindeki kısıtlama denetiminin geçici olarak nasıl kapatılacağı gösterilmektedir:

     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]

### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>Veri Kümesi Tasarımcısı kullanarak güncelleştirme kısıtlamalarını askıya almak için

1. Veri kümenizi Veri Kümesi Tasarımcısı açın. Daha fazla bilgi için bkz. [nasıl yapılır: veri kümesi Tasarımcısı veri kümesini açma](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. **Özellikler** penceresinde <xref:System.Data.DataSet.EnforceConstraints%2A> özelliğini `false` olarak ayarlayın.

## <a name="see-also"></a>Ayrıca Bkz.
 Veri kümelerinde TableAdapters [ilişkilerini](../data-tools/relationships-in-datasets.md) [kullanarak veri kümelerini doldur](../data-tools/fill-datasets-by-using-tableadapters.md)
