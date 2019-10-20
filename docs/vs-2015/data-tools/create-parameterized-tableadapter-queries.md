---
title: Parametreleştirilmiş TableAdapter sorguları oluşturma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 560587e70365a485c3391a0623b959f88d417698
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671066"
---
# <a name="create-parameterized-tableadapter-queries"></a>Parametreleştirilmiş TableAdapter sorguları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Parametreli bir sorgu, sorgu içindeki bir WHERE yan tümcesinin koşullarını karşılayan verileri döndürür. Örneğin, bir müşteri listesini, müşterilerin listesini döndüren SQL ifadesinin sonuna `WHERE City = @City` ekleyerek yalnızca belirli bir şehirdeki müşterileri görüntüleyecek şekilde parametreleştirebilirsiniz.

Veri Kümesi Tasarımcısı parametreli TableAdapter sorguları oluşturursunuz. Bunları, **veri** menüsünde **Parametreleştirme veri kaynağı** komutuyla bir Windows uygulamasında da oluşturabilirsiniz. **Parametreleştirme veri kaynağı** komutu, formunuzda parametre değerlerini girebileceğiniz ve sorguyu çalıştıran denetimler oluşturur.

> [!NOTE]
> Parametreli bir sorgu oluştururken, kodlama yaptığınız veritabanına özgü parametre gösterimini kullanın. Örneğin, Access ve OleDb veri kaynakları, parametreleri göstermek için '? ' soru işaretini kullanır, bu nedenle WHERE yan tümcesi şöyle görünür: `WHERE City = ?`.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya kullandığınız sürüme bağlı olarak yardım bölümünde açıklananlardan farklı bir durum içerebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsüne gidin ve **ayarları Içeri ve dışarı aktar '** ı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-parameterized-tableadapter-query"></a>Parametreli bir TableAdapter sorgusu oluşturma

- SQL deyimi için istenen parametrelerle bir WHERE yan tümcesi ekleyerek yeni bir TableAdapter oluşturun. Daha fazla bilgi için bkz. [TableAdapters oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md).

     veya

- Var olan bir TableAdapter 'a bir sorgu ekleyin ve istenen parametrelere sahip WHERE yan tümcesini SQL deyimi 'ne ekleyin.

### <a name="create-a-parameterized-query-while-designing-a-data-bound-form"></a>Veri bağlantılı form tasarlarken parametreli bir sorgu oluşturma

1. Formunuzda zaten bir veri kümesine bağlı olan bir denetim seçin. Daha fazla bilgi için bkz. [Visual Studio 'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2. **Veri** menüsünde**Sorgu Ekle**' yi seçin.

3. **Arama ölçütleri Oluşturucu** iletişim kutusunu doldurun ve istenen PARAMETRELERE sahip WHERE yan tümcesini SQL deyimi 'ne ekleyin.

### <a name="add-a-query-to-an-existing-data-bound-form"></a>Varolan bir veri bağlantılı forma sorgu ekleme

1. **Windows Form Tasarımcısı**formunu açın.

2. **Veri** menüsünde sorgu veya **veri Akıllı Etiketler** **Ekle** ' yi seçin.

   > [!NOTE]
   > **Sorgu Ekle** ' de **veri** menüsünde kullanılabilir değilse, form üzerinde Parametreleştirme eklemek istediğiniz veri kaynağını görüntüleyen bir denetim seçin. Örneğin, form verileri bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntülüyorsa, onu seçin. Form, verileri ayrı denetimlerde görüntülüyorsa, veri bağlantılı herhangi bir denetimi seçin.

3. **Veri kaynağı tablosu seçin** alanında, Parametreleştirme eklemek istediğiniz tabloyu seçin.

4. Yeni bir sorgu oluşturuyorsanız **Yeni sorgu adı** kutusuna bir ad yazın.

    veya

    **Var olan sorgu adı** kutusunda bir sorgu seçin.

5. **Sorgu metin** kutusuna parametreleri alan bir sorgu yazın.

6. **Tamam ' ı**seçin.

    Parametre ve bir **yükleme** düğmesi girmek için bir denetim, <xref:System.Windows.Forms.ToolStrip> denetimindeki forma eklenir.

   TableAdapter parametrelerine, geçerli değeri olmayan kayıtları sorgulamak istediğinizde null değerler atanabilir. Örneğin, `WHERE` yan tümcesinde `ShippedDate` parametresine sahip olan aşağıdaki sorguyu göz önünde bulundurun:

   ```sql
   SELECT CustomerID, OrderDate, ShippedDate
   FROM Orders
   WHERE (ShippedDate = @ShippedDate) OR
   (ShippedDate IS NULL)
   ```

Bu bir TableAdapter üzerinde bir sorgu olsaydı, şu kodla gönderilmeyen tüm siparişleri sorgulayabilirsiniz:

   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]

### <a name="enable-a-query-to-accept-null-values"></a>Sorgunun null değerlerini kabul etmesine izin vermek

1. **Veri kümesi Tasarımcısı**, null parametre değerlerini kabul etmesi gereken TableAdapter sorgusunu seçin.

2. **Özellikler** penceresinde **Parametreler**' i seçin. Ardından, **Parametreler koleksiyonu düzenleyicisini**açmak için üç nokta ( **...** ) düğmesine basın.

3. Null değerlere izin veren parametreyi seçin ve **AllowDBNull** özelliğini `true` olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [TableAdapter'ları kullanarak veri kümelerini doldurma](../data-tools/fill-datasets-by-using-tableadapters.md)