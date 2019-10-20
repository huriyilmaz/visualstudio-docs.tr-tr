---
title: Bir TableAdapter’ın işlevselliğini genişletme
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e92b820b04913733095645d21ad682bff40acd84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648487"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Bir TableAdapter’ın işlevselliğini genişletme

TableAdapter 'ın kısmi sınıf dosyasına kod ekleyerek bir TableAdapter 'ın işlevselliğini genişletebilirsiniz.

TableAdapter tanımlayan kod, **veri kümesi Tasarımcısı**TableAdapter 'ta herhangi bir değişiklik yapıldığında veya bir sihirbaz bir TableAdapter yapılandırmasını değiştirdiğinde yeniden oluşturulur. Bir TableAdapter 'ın yeniden oluşturulması sırasında kodunuzun silinmesini engellemek için TableAdapter 'ın kısmi sınıf dosyasına kod ekleyin.

Kısmi sınıflar, belirli bir sınıf için kodun birden fazla fiziksel Dosya arasında bölünmesine izin verir. Daha fazla bilgi için bkz. [kısmi](/dotnet/visual-basic/language-reference/modifiers/partial) veya [kısmi (tür)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Kodda TableAdapters bulma

TableAdapters, **veri kümesi Tasarımcısı**ile tasarlanırken, oluşturulan TableAdapter sınıfları <xref:System.Data.DataSet> iç içe geçmiş sınıfları değildir. TableAdapters, TableAdapter 'ın ilişkili veri kümesinin adını temel alan bir ad alanında bulunur. Örneğin, uygulamanız `HRDataSet` adlı bir veri kümesi içeriyorsa, TableAdapters ad alanında yer `HRDataSetTableAdapters` alır. (Adlandırma kuralı şu düzene uyar: *DataSetName*  +  `TableAdapters`).

Aşağıdaki örnek, `NorthwindDataSet` bir projede `CustomersTableAdapter`is adında bir TableAdapter olduğunu varsayar.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>TableAdapter için kısmi bir sınıf oluşturmak için

1. **Proje** menüsüne gidip **Sınıf Ekle**öğesini seçerek projenize yeni bir sınıf ekleyin.

2. @No__t_0 sınıfı adlandırın.

3. **Ekle**' yi seçin.

4. Kodu, projeniz için doğru ad alanı ve kısmi sınıf adı ile aşağıdaki gibi değiştirin:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)