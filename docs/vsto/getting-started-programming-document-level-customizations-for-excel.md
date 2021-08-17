---
title: 'Excel: Kullanmaya başlayın düzeyinde özelleştirmeleri programlama'
description: Microsoft Office Excel kullanarak belge düzeyinde özelleştirmeler oluşturmaya başlamanız için Microsoft Office Excel hakkında Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: fc808765dc4691ea35c8d3fdf91f4af04b4e8efd9221e8b02a98449ab63751d0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424339"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Kullanmaya başlayın için belge düzeyinde özelleştirmeler programlama Excel
  Visual Studio kullanarak Microsoft Office Excel için belge düzeyinde özelleştirmeler oluşturmaya yeni Visual Studio, şu şekilde bilginiz gerekir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>İş için belge düzeyinde özelleştirmelerin nasıl Excel anlama
 Tek bir çalışma kitabına Excel belge düzeyinde özelleştirme. Özelleştirmeyi kullanmaya başlamak için, son kullanıcı çalışma kitabını açar veya çalışma kitabını Excel oluşturur. Çalışma kitabındaki olaylar(örneğin hücrelerde yazma veya düğmelere ve menü öğelerine tıklama) derlemede olay işleme yöntemlerini çağırabilirsiniz. Çalışma kitabı kapatılarak özelleştirme tarafından sağlanan özellikler artık Excel yalnızca bunları içeren belgede kullanılamaz.

 Daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerin mimarisi.](../vsto/architecture-of-document-level-customizations.md)

## <a name="create-document-level-projects-for-excel"></a>Excel için belge düzeyi projeler oluşturma
 Excel için belge düzeyinde özelleştirme oluşturmak Excel Yeni Çalışma Kitabı iletişim kutusundaki Excel Çalışma Kitabı veya Excel Şablonu **Project proje** şablonunu kullanın. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir.

 Excel için belge düzeyi proje oluşturma hakkında daha fazla bilgi için bkz. Nasıl Office [proje oluşturma Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md) Proje şablonları hakkında daha fazla bilgi için bkz. [Office şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Konak Excel ve konak denetimlerini kullanarak çalışma kitaplarını programla
 *Konak öğeleri* ve *konak denetimleri,* bir konak tarafından oluşturulan belge düzeyi özelleştirmeler için programlama modelini sağlayan Visual Studio.

 Konak öğeleri kodunuz için bir giriş noktası sağlar ve bunlar aynı zamanda konak denetimleri ve Windows Forms denetimleri için kapsayıcı Windows davranabilir. Bu konak öğeleri, Excel , , ve sınıfları tarafından temsil edilen belge `ThisWorkbook` `Sheet1` düzeyi `Sheet2` `Sheet3` projelerinde.

 Konak denetimleri, liste nesneleri Excel gibi yerel konak nesnelerine dayalıdır. Konak denetimleri, yerel Excel işlevleri sağlar, ancak yeni olaylar, tasarımcı desteği ve veri bağlama özelliğine de sahiptir. Bunlar, proje kodunuzda ve IntelliSense'te birinci sınıf nesneler olarak görünür. Bu, nesne modelinde gezinmek zorunda kalmadan doğrudan kodunuzda belirli nesnelere Excel kolaylaştırır.

 Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)

- [Genişletilmiş Excel kullanarak otomatikleştirme](../vsto/automating-excel-by-using-extended-objects.md)

- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Uygulamanın kullanıcı arabirimini Excel
 Çoğu Microsoft Office çözümü, kullanıcıların çözümle etkileşim kurması için bir yol sağlamak Office uygulamanın kullanıcı arabirimini (UI) değiştirir. Belge düzeyi özelleştirme kullanarak kullanıcı arabirimini Excel birçok yol vardır. Örneğin, şerite denetimler ekleyebilir veya eylemler bölmesini görüntüleyebilirsiniz. Daha fazla bilgi için [bkz. Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

 Projeniz ile ilişkili çalışma kitabını doğrudan projenizin içinde de Visual Studio. Çalışma kitabı, Visual Studio kullanıcı arabirimini kullanarak Excel değiştirebilirsiniz. Çalışma kitabını tasarım yüzeyi olarak da kullanabilirsiniz. Bu sayede denetimleri çalışma sayfalarına sürükleyebilirsiniz. Daha fazla bilgi için [Office ortamındaki Visual Studio bakın.](../vsto/office-projects-in-the-visual-studio-environment.md)

## <a name="use-data-binding"></a>Veri bağlamayı kullanma
 Konak denetimleri, Veri Kaynakları penceresinden sürükleyebilirsiniz denetim **listesinde de** yer alıyor. Bu şekilde konak denetimleri eklemek, bunları pencereyi kullanarak ayarlayacakları veri kaynağına otomatik olarak bağlar. Kod yazmadan veritabanlarından, web hizmetlerinden ve iş nesnelerinden verileri görüntüebilirsiniz. Daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

## <a name="next-steps"></a>Sonraki adımlar
 Excel için belge düzeyinde özelleştirme oluşturma hakkında bilgi edinmek Excel [bkz. Kılavuz:](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)Excel için ilk belge düzeyi özelleştirmenizi oluşturma. Bu kılavuzda, Office geliştirme araçları ve Visual Studio düzeyinde özelleştirmeler için programlama modeli Excel tanıtabilirsiniz.

 Excel projelerinde sık kullanılan görevlerden bazıları hakkında size yol Office için [bkz. programlamada ortak Office.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Office: Visual Studio'da Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Excel çözümleri](../vsto/excel-solutions.md)
- [Adım adım kılavuz: Belge düzeyi özelleştirmeniz için ilk belge düzeyi özelleştirmenizi Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Excel kullanarak izlenecek yollar](../vsto/walkthroughs-using-excel.md)
- [Excel modeline genel bakış](../vsto/excel-object-model-overview.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
