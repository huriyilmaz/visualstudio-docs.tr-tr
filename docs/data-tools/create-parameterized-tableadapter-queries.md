---
title: Parametreleştirilmiş TableAdapter sorguları oluşturma
description: Parametreli TableAdapter sorguları oluşturmayı anlayın. Parametreli bir sorgu, sorgu içindeki bir WHERE yan tümcesinin koşullarını karşılayan verileri döndürür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 53ede3f31574ec2bbbd9b5cc2ce1f588b4ed5233
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052843"
---
# <a name="create-parameterized-tableadapter-queries"></a>Parametreleştirilmiş TableAdapter sorguları oluşturma

Parametreli bir sorgu, sorgu içindeki bir WHERE yan tümcesinin koşullarını karşılayan verileri döndürür. örneğin, bir müşteri listesini, `WHERE City = @City` müşterilerin listesini döndüren SQL deyimin sonuna ekleyerek yalnızca belirli bir şehirdeki müşterileri görüntüleyecek şekilde parametreleştirebilirsiniz.

**Veri kümesi Tasarımcısı** parametreli TableAdapter sorguları oluşturursunuz. bunları, **veri** menüsündeki **parametreleştirme veri kaynağı** komutuyla bir Windows uygulamasında da oluşturabilirsiniz. **Parametreleştirme veri kaynağı** komutu, formunuzda parametre değerlerini girebileceğiniz ve sorguyu çalıştıran denetimler oluşturur.

> [!NOTE]
> Parametreli bir sorgu oluştururken, kodlama yaptığınız veritabanına özgü parametre gösterimini kullanın. Örneğin, Access ve OleDb veri kaynakları, parametreleri göstermek için '? ' soru işaretini kullanır, bu nedenle WHERE yan tümcesi şöyle görünür: `WHERE City = ?` .

## <a name="create-a-parameterized-tableadapter-query"></a>Parametreli bir TableAdapter sorgusu oluşturma

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Veri Kümesi Tasarımcısı parametreli bir sorgu oluşturmak için

- SQL bildirimine istenen parametrelerle bir where yan tümcesi ekleyerek yeni bir TableAdapter oluşturun. Daha fazla bilgi için bkz. [TableAdapters oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md).

     -veya-

- mevcut bir TableAdapter 'a bir sorgu ekleyin ve istenen parametrelere sahip where yan tümcesini SQL bildirimine ekleyin.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Veri bağlantılı form tasarlarken parametreli bir sorgu oluşturmak için

1. Formunuzda zaten bir veri kümesine bağlı olan bir denetim seçin. daha fazla bilgi için bkz. [Visual Studio verileri Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. **Veri** menüsünde **Sorgu Ekle**' yi seçin.

3. SQL bildirimine istenen parametrelerle bir where yan tümcesi ekleyerek **arama ölçütleri oluşturucu** iletişim kutusunu doldurun.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Varolan bir veri bağlantılı forma bir sorgu eklemek için

1. **Windows Form Tasarımcısı** formunu açın.

2. **Veri** menüsünde sorgu veya **veri Akıllı Etiketler** **Ekle** ' yi seçin.

    > [!NOTE]
    > **Sorgu Ekle** ' de **veri** menüsünde kullanılabilir değilse, form üzerinde Parametreleştirme eklemek istediğiniz veri kaynağını görüntüleyen bir denetim seçin. Örneğin, form verileri bir <xref:System.Windows.Forms.DataGridView> denetimde görüntülüyorsa, onu seçin. Form, verileri ayrı denetimlerde görüntülüyorsa, veri bağlantılı herhangi bir denetimi seçin.

3. **Veri kaynağı tablosu seçin** alanında, Parametreleştirme eklemek istediğiniz tabloyu seçin.

4. Yeni bir sorgu oluşturuyorsanız **Yeni sorgu adı** kutusuna bir ad yazın.

     -veya-

     **Var olan sorgu adı** kutusunda bir sorgu seçin.

5. **Sorgu metin** kutusuna parametreleri alan bir sorgu yazın.

6. **Tamam**’ı seçin.

     Bir denetimde parametre ve bir **yükleme** düğmesi girişi için bir denetim eklenir <xref:System.Windows.Forms.ToolStrip> .

### <a name="query-for-null-values"></a>Null değerler için sorgu

TableAdapter parametrelerine, geçerli değeri olmayan kayıtları sorgulamak istediğinizde null değerler atanabilir. Örneğin, yan tümcesindeki bir parametreye sahip aşağıdaki sorguyu göz önünde bulundurun `ShippedDate` `WHERE` :

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Bu bir TableAdapter üzerinde bir sorgu olsaydı, şu kodla gönderilmeyen tüm siparişleri sorgulayabilirsiniz:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb" id="Snippet8":::

Bir sorguyu null değerlerini kabul edecek şekilde etkinleştirmek için:

1. **Veri kümesi Tasarımcısı**, null parametre değerlerini kabul etmesi gereken TableAdapter sorgusunu seçin.

2. **Özellikler** penceresinde **Parametreler**' i seçin, sonra **Parametreler koleksiyonu düzenleyicisini** açmak için üç nokta (**...**) düğmesini tıklatın.

3. Null değerlere izin veren parametreyi seçin ve **AllowDBNull** özelliğini olarak ayarlayın `true` .

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
