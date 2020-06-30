---
title: 'Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtlarını kaydırma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8127a5f61e292fb777be4854796535bbe01226aa
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545801"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtlarını kaydırma
  Aşağıdaki yordamda, Microsoft Office bir Excel çalışma sayfasındaki veritabanı tablosundan, son kullanıcının tüm kayıtlarda gezindiğini etkinleştiren denetimlerle tek bir alan göstermek için tasarımcının nasıl kullanılacağı gösterilmektedir.

 Tasarımcıyı yalnızca belge düzeyinde projeler içinde kullanabilirsiniz. Bununla birlikte, denetimleri de ekleyebilir ve çalışma zamanında programlı olarak verilere bağlayabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: VSTO eklentisi projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Çalışma sayfasındaki veritabanı kayıtlarını kaydırmak için

1. Visual Studio 'da bir Excel uygulama projesi açın.

2. **Veri kaynakları** penceresini açın ve veritabanından bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. Göstermek istediğiniz verileri içeren tabloyu genişletin ve belirli sütunu seçin.

4. Denetim listesini açın ve **NamedRange**' i seçin.

5. Denetimi, <xref:Microsoft.Office.Tools.Excel.NamedRange> verilerin görünmesini istediğiniz hücreye sürükleyin.

6. **Araç kutusu** **Windows Forms** sekmesinden, <xref:System.Windows.Forms.BindingNavigator> çalışma sayfanıza bir denetim ekleyin ve kullanmak istediğiniz denetimleri ayarlayın. Daha fazla bilgi için bkz. [BindingNavigator denetimine genel bakış &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
