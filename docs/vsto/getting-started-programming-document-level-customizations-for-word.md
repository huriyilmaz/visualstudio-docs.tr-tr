---
title: Kullanmaya başlayın word için belge düzeyinde özelleştirmeler programlama
description: Microsoft Office Word için belge düzeyinde özelleştirmeler oluşturmaya başlamanız için Microsoft Office gerekenleri Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9142781a7e06e2cf1f2546324551be7b5dc436ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026440"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Kullanmaya başlayın word için belge düzeyinde özelleştirmeler programlama
  Visual Studio kullanarak Microsoft Office Word için belge düzeyinde özelleştirmeler oluşturmaya yeni Visual Studio, şu şekilde bilginiz gerekir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Word için belge düzeyinde özelleştirmelerin nasıl çalışalarını anlama
 Her Word özelleştirmesi tek bir belgeyi temel alan bir özelleştirmedir. Özelleştirmeyi kullanmaya başlamak için son kullanıcı belgeyi açar veya belgeyi bir Word şablonundan oluşturur. Belgedeki olaylar,örneğin imleci belirli alanlara taşıma veya düğmelere ve menü öğelerine tıklama, derlemede olay işleme yöntemlerini çağırabilirsiniz. Belge kapatılan, özelleştirme tarafından sağlanan özellikler artık Word'de kullanılamaz.

 Daha fazla bilgi için [bkz. Belge düzeyinde özelleştirmelerin mimarisi.](../vsto/architecture-of-document-level-customizations.md)

## <a name="create-document-level-projects-for-word"></a>Word için belge düzeyinde projeler oluşturma
 Word için belge düzeyinde özelleştirme oluşturmak üzere Yeni Belge iletişim kutusunda Word Belgesi veya **Word Şablonu proje Project** kullanın. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir.

 Word için belge düzeyi proje oluşturma hakkında daha fazla bilgi için bkz. Nasıl [ekleyebilirsiniz: Office'de Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md) Proje şablonları hakkında daha fazla bilgi için bkz. [Office şablonlarına genel bakış.](../vsto/office-project-templates-overview.md)

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Konak öğeleri konak denetimlerini kullanarak Word belgelerini programla
 *Konak öğeleri* ve *konak denetimleri,* belge düzeyinde özelleştirmeler için programlama modelini sağlayan sınıflardır.

 Konak öğeleri kodunuz için bir giriş noktası sağlar ve bunlar aynı zamanda konak denetimleri ve Windows Forms denetimleri için kapsayıcı Windows davranabilir. Word için belge düzeyi projelerinde, konak öğesi sınıfı tarafından temsil `ThisDocument` edildi.

 Konak denetimleri, içerik denetimleri, yer işaretleri ve XML düğümleri gibi yerel Word nesnelerini temel almaktadır. Konak denetimleri yerel Word nesnelerine benzer işlevler sağlar, ancak yeni olaylar, tasarımcı desteği ve veri bağlama özelliğine de sahiptir. Bunlar proje kodunuzda ve IntelliSense'te birinci sınıf nesneler olarak görünür. Bu, Word nesne modelinde gezinmek zorunda kalmadan doğrudan kodunuzda belirli nesnelere başvurulmanızı kolaylaştırır.

 Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)

- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)

- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Word'in kullanıcı arabirimini özelleştirme
 Çoğu Microsoft Office çözümü, kullanıcıların çözümle etkileşim kurması için bir yol sağlamak Office uygulamanın kullanıcı arabirimini (UI) değiştirir. Belge düzeyinde özelleştirme kullanarak Word kullanıcı arabirimini değiştirmenin birçok yolu vardır. Örneğin, şerite denetimler ekleyebilir ve bir eylemler bölmesi görüntüleyebilirsiniz. Daha fazla bilgi için [bkz. Office kullanıcı arabirimi özelleştirmesi.](../vsto/office-ui-customization.md)

 Projeniz ile ilişkili belgeyi doğrudan projenizin içinde de Visual Studio. Belge yeni bir Visual Studio word kullanıcı arabirimini kullanarak belgeyi değiştirebilirsiniz. Belgeyi tasarım yüzeyi olarak da kullanabilirsiniz. Bu sayede denetimleri üzerine sürükleyebilirsiniz. Daha fazla bilgi için [Office ortamındaki Visual Studio bakın.](../vsto/office-projects-in-the-visual-studio-environment.md)

## <a name="bind-controls-to-data"></a>Verilere denetim bağlama
 İçerik denetimleri ve <xref:Microsoft.Office.Tools.Word.Bookmark> denetim, Veri Kaynakları penceresinden sürükleyebilirsiniz denetim **listesindedir.** bu şekilde içerik denetimleri ve yer işaretleri eklemek, pencereyi kullanarak bunları otomatik olarak ayarmış olduğu veri kaynağına bağlar. Kod yazmadan veritabanlarından, hizmetlerden ve iş nesnelerinden verileri görüntüebilirsiniz. Daha fazla bilgi için [bkz. Veri bağlama çözümlerini Office bağlama.](../vsto/binding-data-to-controls-in-office-solutions.md)

## <a name="next-steps"></a>Sonraki adımlar
 Word için belge düzeyinde özelleştirme oluşturma hakkında bilgi edinmek için bkz. Adım adım [kılavuz: Word için ilk belge düzeyi özelleştirmenizi oluşturma.](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md) Bu kılavuzda, Word belge Office için programlama modeli Visual Studio geliştirme araçları hakkında bilgi edinebilirsiniz.

 Word projelerinde sık kullanılan görevlerden bazıları hakkında size yol gösterir konuların listesi için bkz. Programlamada [Office görevler.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Office: Office projelerini Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Word çözümleri](../vsto/word-solutions.md)
- [Adım adım kılavuz: Word için ilk belge düzeyi özelleştirmenizi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Kod yazma Office yazma](../vsto/writing-code-in-office-solutions.md)
