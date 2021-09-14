---
title: Bir TableAdapter’ın işlevselliğini genişletme
description: TableAdapter'ın kısmi sınıf dosyasına kod ekleyerek TableAdapter işlevselliğini genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 29c7d9924d822cabdb28c9d3048e457cd7b88d64
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631400"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Bir TableAdapter’ın işlevselliğini genişletme

TableAdapter'ın kısmi sınıf dosyasına kod ekleyerek TableAdapter işlevselliğini genişletebilirsiniz.

TableAdapter tanımlayan kod, **Veri Kümesi Tasarımcısı** veya sihirbaz Bir TableAdapter'ın yapılandırmasını değiştirirken TableAdapter'da herhangi bir değişiklik olduğunda yeniden oluşturulur. TableAdapter'ın yeniden oluşturulması sırasında kodunuzun silinmesini önlemek için TableAdapter'ın kısmi sınıf dosyasına kod ekleyin.

Kısmi sınıflar, belirli bir sınıfın birden çok fiziksel dosya arasında bölünmesine olanak sağlar. Daha fazla bilgi için [bkz. Kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) [veya kısmi (Tür)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Kodda TableAdapter'ları bulma

TableAdapter'lar, Veri Kümesi Tasarımcısı **ile** tasarlansa da, oluşturulan TableAdapter sınıfları iç içe sınıfları <xref:System.Data.DataSet> değildir. TableAdapter'lar, TableAdapter'ın ilişkili veri kümesi adına göre bir ad alanı içinde bulunur. Örneğin, uygulamanız adlı bir veri kümesi içeriyorsa `HRDataSet` TableAdapter'lar ad alanına `HRDataSetTableAdapters` yer alır. (Adlandırma kuralı şu desene uyar: *DatasetName*  +  `TableAdapters` ).

Aşağıdaki örnekte, adlı bir TableAdapter'ın `CustomersTableAdapter` ile bir projede olduğu varsayıldı. `NorthwindDataSet`

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>TableAdapter için kısmi bir sınıf oluşturmak için

1. Project menüsüne gidip Sınıf **Ekle'yi seçerek** projenize yeni **bir sınıf ekleyin.**

2. sınıfını olarak `CustomersTableAdapterExtended` adlar.

3. **Add (Ekle)** seçeneğini belirleyin.

4. Kodu projeniz için doğru ad alanı ve kısmi sınıf adıyla aşağıdaki gibi değiştirin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb" id="Snippet2":::

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
