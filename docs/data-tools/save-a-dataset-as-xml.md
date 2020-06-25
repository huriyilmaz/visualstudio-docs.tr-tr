---
title: Bir veri kümesini XML olarak kaydetme
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8854581903ab58a327ff18be7b3b7c0f860a3b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281740"
---
# <a name="save-a-dataset-as-xml"></a>Bir veri kümesini XML olarak kaydetme

Veri kümesindeki kullanılabilir XML yöntemlerini çağırarak bir veri kümesindeki XML verilerine erişin. Verileri XML biçiminde kaydetmek için, <xref:System.Data.DataSet.GetXml%2A> yöntemini ya da <xref:System.Data.DataSet.WriteXml%2A> bir yöntemini çağırabilirsiniz <xref:System.Data.DataSet> .

Yöntemi çağırmak, <xref:System.Data.DataSet.GetXml%2A> XML olarak biçimlendirilen veri kümesindeki tüm veri tablolarından verileri içeren bir dize döndürür.

Yöntemi çağırmak, <xref:System.Data.DataSet.WriteXml%2A> XML biçimli verileri belirttiğiniz bir dosyaya gönderir.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Bir veri kümesindeki verileri bir değişkene XML olarak kaydetmek için

- <xref:System.Data.DataSet.GetXml%2A>Yöntemi bir döndürür <xref:System.String> . Türünde bir değişken bildirin <xref:System.String> ve yöntemin sonuçlarını atayın <xref:System.Data.DataSet.GetXml%2A> .

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Veri kümesindeki verileri bir dosyaya XML olarak kaydetmek için

- <xref:System.Data.DataSet.WriteXml%2A>Yönteminde birkaç aşırı yükleme vardır. Bir değişken bildirin ve dosyayı kaydetmek için geçerli bir yol atayın. Aşağıdaki kod, verilerin bir dosyaya nasıl kaydedileceğini gösterir:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
