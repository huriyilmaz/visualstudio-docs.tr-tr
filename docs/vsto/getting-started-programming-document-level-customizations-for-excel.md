---
title: 'Excel: belge düzeyinde özelleştirmeler programlama ile çalışmaya başlama'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c1ff264eb1a4ca7afdc424cef7edf15bae06554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66402152"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Excel için belge düzeyi özelleştirmelerini Programlamaya Başlama
  Visual Studio 'Yu kullanarak Microsoft Office Excel için belge düzeyi özelleştirmeleri oluşturmaya başladıysanız, bilmeniz gerekenler aşağıda verilmiştir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Excel için belge düzeyi özelleştirmelerinin nasıl çalıştığını anlama
 Excel için belge düzeyi özelleştirmesi tek bir çalışma kitabını temel alarak. Özelleştirmeyi kullanmaya başlamak için, son kullanıcı çalışma kitabını açar veya bir Excel şablonundan çalışma kitabını oluşturur. Çalışma kitabındaki olaylar, örneğin hücrelere yazma veya düğme ve menü öğelerini tıklatma, derlemede olay işleme yöntemlerini çağırabilir. Çalışma kitabı kapatıldığında, özelleştirme tarafından sağlanan özellikler artık Excel 'de yalnızca bunları içeren belgede kullanılamaz.

 Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Excel için belge düzeyi projeleri oluşturma
 Excel 'de belge düzeyinde bir özelleştirme oluşturmak için **Yeni proje** Iletişim kutusundaki Excel çalışma kitabı veya Excel Şablonu proje şablonunu kullanın. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir.

 Excel için belge düzeyi projesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md). Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Konak öğelerini ve konak denetimlerini kullanarak Excel çalışma kitaplarını programlama
 *Konak öğeleri* ve *konak denetimleri* , Visual Studio kullanılarak oluşturulan belge düzeyi özelleştirmeleri için programlama modeli sağlayan sınıflardır.

 Konak öğeleri kodunuz için bir giriş noktası sağlar ve ayrıca konak denetimleri ve Windows Forms denetimleri için kapsayıcılar olarak davranabilir. Excel için belge düzeyi projelerinde, bu konak öğeleri,,, `ThisWorkbook` `Sheet1` `Sheet2` ve sınıfları tarafından temsil edilir `Sheet3` .

 Konak denetimleri liste nesneleri ve aralıklar gibi yerel Excel nesnelerini temel alır. Konak denetimleri, yerel Excel nesnelerine benzer işlevler sağlar, ancak aynı zamanda yeni olaylara, tasarımcı desteğine ve veri bağlama özelliğine sahiptir. Bunlar, proje kodunuzda ve IntelliSense 'de ilk sınıf nesneler olarak görünürler, bu da Excel nesne modelinde gezinmek zorunda kalmadan kodunuzda belirli nesnelere doğrudan başvurmayı kolaylaştırır.

 Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)

- [Genişletilmiş nesneleri kullanarak Excel 'i otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)

- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Excel 'in Kullanıcı arabirimini özelleştirme
 Çoğu Microsoft Office çözüm, kullanıcıların çözümle etkileşim kurması için bir yol sağlamak üzere Office uygulamasının Kullanıcı arabirimini (UI) değiştirir. Belge düzeyi özelleştirmesi kullanarak Excel 'in Kullanıcı arabirimini değiştirebilmenin birçok yolu vardır. Örneğin, şerit 'e denetimler ekleyebilir veya bir eylemler bölmesini görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

 Ayrıca, projenizle doğrudan Visual Studio 'da ilişkili çalışma kitabını da açabilirsiniz. Çalışma kitabı Visual Studio 'da açıldığında, çalışma kitabını Excel Kullanıcı arabirimini kullanarak değiştirebilirsiniz. Çalışma kitabını tasarım yüzeyi olarak da kullanabilirsiniz ve bu sayede denetimleri çalışma sayfalarına sürükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Veri bağlamayı kullanma
 Konak denetimleri, **veri kaynakları** penceresinden sürükleyebileceğiniz denetimler listesinde de bulunur. Konak denetimlerini bu şekilde eklemek, pencereyi kullanarak ayarladığınız veri kaynağına otomatik olarak bağlar. Herhangi bir kod yazmadan, veritabanlarından, Web hizmetlerinden ve iş nesnelerinden verileri görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Sonraki adımlar
 Excel için belge düzeyi özelleştirmesi oluşturmayı öğrenmek için bkz. [Izlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Bu kılavuzda, Visual Studio 'da Office geliştirme araçları ve Excel belge düzeyi özelleştirmeleri için programlama modeli açıklanır.

 Excel projelerindeki yaygın görevlerden bazıları boyunca size kılavuzluk eden konuların listesi için bkz. [Office programlamada ortak görevler](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Excel çözümleri](../vsto/excel-solutions.md)
- [İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
- [Excel nesne modeline genel bakış](../vsto/excel-object-model-overview.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
