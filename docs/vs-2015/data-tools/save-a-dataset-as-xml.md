---
title: Veri kümesini XML olarak kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652859"
---
# <a name="save-a-dataset-as-xml"></a>Bir veri kümesini XML olarak kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veri kümesindeki XML verilerine veri kümesindeki kullanılabilir XML yöntemleri çağırarak erişilebilir. Verileri XML biçiminde kaydetmek için, bir <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetXml%2A> yöntemini ya da <xref:System.Data.DataSet.WriteXml%2A> yöntemini çağırabilirsiniz.

 @No__t_0 yöntemini çağırmak, XML olarak biçimlendirilen veri kümesindeki tüm veri tablolarından verileri içeren bir dize döndürür.

 @No__t_0 yöntemini çağırmak, XML biçimli verileri belirttiğiniz bir dosyaya gönderir.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Bir veri kümesindeki verileri bir değişkene XML olarak kaydetmek için

- @No__t_0 yöntemi bir <xref:System.String> döndürür. Bu, <xref:System.String> türünde bir değişken bildirdiğiniz ve <xref:System.Data.DataSet.GetXml%2A> yönteminin sonuçlarını atayan anlamına gelir.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Veri kümesindeki verileri bir dosyaya XML olarak kaydetmek için

- @No__t_0 yönteminde birkaç aşırı yükleme vardır. Aşağıdaki kod, verilerin bir dosyaya nasıl kaydedileceğini gösterir. Bir değişken bildirin ve dosyayı kaydetmek için geçerli bir yol atayın.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Ayrıca Bkz.
 [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
