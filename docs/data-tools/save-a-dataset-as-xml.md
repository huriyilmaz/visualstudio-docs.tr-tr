---
title: Bir veri kümesini XML olarak kaydetme
description: Veri kümelerini XML olarak kaydedin. Veri kümesinde GetXml veya WriteXml gibi kullanılabilir XML yöntemlerini çağırarak bir veri kümesinde XML verilerine erişin.
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
ms.openlocfilehash: 127e97c92d9b331fe3cc461c585fb3240482fbd0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067093"
---
# <a name="save-a-dataset-as-xml"></a>Bir veri kümesini XML olarak kaydetme

Veri kümesinde kullanılabilir XML yöntemlerini çağırarak bir veri kümesinde XML verilerine erişin. Verileri XML biçiminde kaydetmek için yöntemini veya yöntemini <xref:System.Data.DataSet.GetXml%2A> <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet> çağırabilirsiniz.

yönteminin çağrılsı, XML olarak biçimlendirilmiş veri kümesinde yer alan tüm veri <xref:System.Data.DataSet.GetXml%2A> tablolarından verileri içeren bir dize döndürür.

yönteminin <xref:System.Data.DataSet.WriteXml%2A> çağrılsı XML biçimli verileri belirttiğiniz bir dosyaya gönderir.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Verileri bir veri kümesinde XML olarak bir değişkene kaydetmek için

- yöntemi <xref:System.Data.DataSet.GetXml%2A> bir <xref:System.String> döndürür. türünde bir değişken <xref:System.String> bildirin ve yöntemin sonuçlarını <xref:System.Data.DataSet.GetXml%2A> buna at uygun şekilde attayin.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet12":::

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Verileri bir veri kümesinde XML olarak bir dosyaya kaydetmek için

- yönteminde <xref:System.Data.DataSet.WriteXml%2A> çeşitli aşırı yüklemeler vardır. Bir değişken bildirin ve dosyayı kaydetmek için geçerli bir yol attayabilirsiniz. Aşağıdaki kod, verileri bir dosyaya kaydetmeyi gösterir:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet13":::

## <a name="see-also"></a>Ayrıca bkz.

- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
