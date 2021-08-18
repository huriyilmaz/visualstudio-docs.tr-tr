---
title: Bir veri kümesini XML olarak kaydetme
description: Veri kümesini XML olarak kaydetme. Veri kümesinde, GetXml veya WriteXml gibi kullanılabilir XML yöntemlerini çağırarak bir veri kümesindeki XML verilerine erişin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 144412b8e738391e1c0122efaef3dee658010422556541987f09b2ca31881697
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346940"
---
# <a name="save-a-dataset-as-xml"></a>Bir veri kümesini XML olarak kaydetme

Veri kümesindeki kullanılabilir XML yöntemlerini çağırarak bir veri kümesindeki XML verilerine erişin. Verileri XML biçiminde kaydetmek için, <xref:System.Data.DataSet.GetXml%2A> yöntemini ya da <xref:System.Data.DataSet.WriteXml%2A> bir yöntemini çağırabilirsiniz <xref:System.Data.DataSet> .

Yöntemi çağırmak, <xref:System.Data.DataSet.GetXml%2A> XML olarak biçimlendirilen veri kümesindeki tüm veri tablolarından verileri içeren bir dize döndürür.

Yöntemi çağırmak, <xref:System.Data.DataSet.WriteXml%2A> XML biçimli verileri belirttiğiniz bir dosyaya gönderir.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Bir veri kümesindeki verileri bir değişkene XML olarak kaydetmek için

- <xref:System.Data.DataSet.GetXml%2A>Yöntemi bir döndürür <xref:System.String> . Türünde bir değişken bildirin <xref:System.String> ve yöntemin sonuçlarını atayın <xref:System.Data.DataSet.GetXml%2A> .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet12":::

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Veri kümesindeki verileri bir dosyaya XML olarak kaydetmek için

- <xref:System.Data.DataSet.WriteXml%2A>Yönteminde birkaç aşırı yükleme vardır. Bir değişken bildirin ve dosyayı kaydetmek için geçerli bir yol atayın. Aşağıdaki kod, verilerin bir dosyaya nasıl kaydedileceğini gösterir:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
