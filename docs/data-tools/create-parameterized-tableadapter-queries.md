---
title: Parametreleştirilmiş TableAdapter sorguları oluşturma
description: Parametreli TableAdapter sorguları oluşturma hakkında bilgi. Parametreli sorgu, sorgu içindeki WHERE yan tümcesi koşullarını karşılayacak verileri döndürür.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631460"
---
# <a name="create-parameterized-tableadapter-queries"></a>Parametreleştirilmiş TableAdapter sorguları oluşturma

Parametreli sorgu, sorgu içindeki WHERE yan tümcesi koşullarını karşılayacak verileri döndürür. Örneğin, bir müşteri listesini bir müşteri listesi döndüren SQL deyiminin sonuna ekleyerek yalnızca belirli bir şehirde müşterileri görüntülemek için `WHERE City = @City` parametreli hale getirebilirsiniz.

parametreli TableAdapter sorguları oluşturmak için **Veri Kümesi Tasarımcısı.** Ayrıca, veri menüsündeki Windows Kaynağı Parametreleştir **komutuyla** bunları bir uygulama içinde **de oluşturabilirsiniz.** Veri **Kaynağını Parametreleştir** komutu, form üzerinde parametre değerlerini girebilirsiniz ve sorguyu çalıştırabilirsiniz denetimleri oluşturur.

> [!NOTE]
> Parametreli sorguyu oluştururken, kodlaması yapılan veritabanına özgü parametre notlarını kullanın. Örneğin, Access ve OleDb veri kaynakları parametreleri ifade etmek için '?' soru işaretini kullanır, bu nedenle WHERE yan tümcesi şöyle olur: `WHERE City = ?` .

## <a name="create-a-parameterized-tableadapter-query"></a>Parametreli TableAdapter sorgusu oluşturma

### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Sorguda parametreli sorgu oluşturmak Veri Kümesi Tasarımcısı

- Yeni bir TableAdapter oluşturun ve SQL deyimine istenen parametrelerle WHERE yan tümcesi ekler. Daha fazla bilgi için [bkz. TableAdapters oluşturma ve yapılandırma.](../data-tools/create-and-configure-tableadapters.md)

     -veya-

- Mevcut TableAdapter'a sorgu ekleyin ve SQL deyimine istenen parametrelerle WHERE yan tümcesi ekleyin.

### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Veriye bağlı form tasarlarken parametreli sorgu oluşturmak için

1. Form üzerinde zaten bir veri kümesine bağlı olan bir denetim seçin. Daha fazla bilgi için [bkz. Windows Forms denetimlerini Visual Studio.](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

2. Veri menüsünde **Sorgu** **Ekle'yi seçin.**

3. Arama Ölçütleri **Oluşturucusu iletişim** kutusunu tamamlar ve istenen parametrelerle where yan tümcesini SQL ekleyin.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Mevcut bir veriye bağlı forma sorgu eklemek için

1. Form Tasarımcısı'nda **Windows açın.**

2. Veri menüsünde **Sorgu** Ekle'yi **veya Veri Akıllı** **Etiketleri'yi seçin.**

    > [!NOTE]
    > Veri **menüsünde** Sorgu Ekle seçeneği **kullanılamıyorsa,** formda parametreleştirmeyi eklemek istediğiniz veri kaynağını görüntüleyen bir denetim seçin. Örneğin, form bir denetimde veri <xref:System.Windows.Forms.DataGridView> görüntülerse, seçin. Form verileri tek tek denetimlerde görüntülese, veriye bağlı herhangi bir denetimi seçin.

3. Veri **kaynağı tablosu seçin** alanında parametreleştirme eklemek istediğiniz tabloyu seçin.

4. Yeni sorgu **oluşturuyorsanız Yeni sorgu** adı kutusuna bir ad yazın.

     -veya-

     Mevcut sorgu adı **kutusunda bir sorgu** seçin.

5. Sorgu **Metni kutusuna** parametre alan bir sorgu yazın.

6. **Tamam**’ı seçin.

     Bir denetimde forma **parametresini ve** Yükle düğmesini <xref:System.Windows.Forms.ToolStrip> girebilirsiniz.

### <a name="query-for-null-values"></a>Null değerleri sorgulama

Geçerli değeri olmayan kayıtları sorgulamak istediğinizde TableAdapter parametrelerine null değerler atanabilir. Örneğin, yan tümcesinde parametresi olan aşağıdaki `ShippedDate` sorguyu `WHERE` düşünün:

```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

Bu bir TableAdapter sorgusu ise, aşağıdaki kodla birlikte göndernemeyen tüm siparişleri sorgularsınız:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb" id="Snippet8":::

Bir sorgunun null değerleri kabul etmelerini sağlamak için:

1. Aşağıdaki **Veri Kümesi Tasarımcısı** null parametre değerlerini kabul eden TableAdapter sorgusunu seçin.

2. Özellikler **penceresinde Parametreler'i** **seçin** ve ardından üç nokta (**...**) düğmesine tıklayarak Parametre **Koleksiyonu Düzenleyicisi'ni açın.**

3. Null değerlere izin veren parametreyi seçin ve **AllowDbNull özelliğini** olarak `true` ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)
