---
title: 'Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtlarını kaydırma'
description: tasarımcı kullanarak Microsoft Excel çalışma sayfasındaki veritabanı tablosundan tek bir alan görüntüleme hakkında bilgi edinin
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: abe1ff62b651c8f8456eea0e3a5ca83e37b70d9d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032686"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtlarını kaydırma
  aşağıdaki yordamda, bir Microsoft Office Excel çalışma sayfasındaki veritabanı tablosundan tek bir alanı göstermek için tasarımcının nasıl kullanılacağı gösterilmektedir. bu, son kullanıcının tüm kayıtlarda kaymasını sağlayan denetimlerle birlikte.

 Tasarımcıyı yalnızca belge düzeyinde projeler içinde kullanabilirsiniz. Bununla birlikte, denetimleri de ekleyebilir ve çalışma zamanında programlı olarak verilere bağlayabilirsiniz. daha fazla bilgi için bkz. [izlenecek yol: VSTO eklentisi projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Çalışma sayfasındaki veritabanı kayıtlarını kaydırmak için

1. Visual Studio bir Excel uygulama projesi açın.

2. **Veri kaynakları** penceresini açın ve veritabanından bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. Göstermek istediğiniz verileri içeren tabloyu genişletin ve belirli sütunu seçin.

4. Denetim listesini açın ve **NamedRange**' i seçin.

5. Denetimi, <xref:Microsoft.Office.Tools.Excel.NamedRange> verilerin görünmesini istediğiniz hücreye sürükleyin.

6. **araç kutusu** **Windows Forms** sekmesinden, <xref:System.Windows.Forms.BindingNavigator> çalışma sayfanıza bir denetim ekleyin ve kullanmak istediğiniz denetimleri ayarlayın. daha fazla bilgi için bkz. [BindingNavigator denetimine genel bakış &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
