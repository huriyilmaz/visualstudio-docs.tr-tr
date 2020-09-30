---
title: Word için belge düzeyi özelleştirmeleri Programlamaya Başlama
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4cf54dcdd08e7c44e8318973a3653dbe9c5ea1b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585673"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Word için belge düzeyi özelleştirmeleri Programlamaya Başlama
  Visual Studio 'Yu kullanarak Microsoft Office Word için belge düzeyi özelleştirmeleri oluşturmaya başladıysanız, bilmeniz gerekenler aşağıda verilmiştir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Word için belge düzeyi özelleştirmelerinin nasıl çalıştığını anlama
 Oluşturduğunuz her sözcük özelleştirmesi tek bir belgeyi temel alarak. Özelleştirmeyi kullanmaya başlamak için, Son Kullanıcı belgeyi açar veya bir Word şablonundan belgeyi oluşturur. Belgedeki olaylar, örneğin imleci belirli alanlara taşımak veya düğme ve menü öğelerini tıklatmak, derlemede olay işleme yöntemlerini çağırabilir. Belge kapatıldığında özelleştirme tarafından sağlanan özellikler artık Word 'de kullanılamaz.

 Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Word için belge düzeyi projeler oluşturma
 Word için belge düzeyi özelleştirmesi oluşturmak için **Yeni proje** Iletişim kutusundaki Word belgesi veya Word şablonu proje şablonunu kullanın. Bu şablonlar gerekli derleme başvurularını ve proje dosyalarını içerir.

 Word için belge düzeyi projesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md). Proje şablonları hakkında daha fazla bilgi için bkz. [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Konak öğeleri konak denetimlerini kullanarak program Word belgeleri
 *Konak öğeleri* ve *konak denetimleri* , belge düzeyi özelleştirmeleri için programlama modeli sağlayan sınıflardır.

 Konak öğeleri kodunuz için bir giriş noktası sağlar ve ayrıca konak denetimleri ve Windows Forms denetimleri için kapsayıcılar olarak davranabilir. Word için belge düzeyi projelerinde, konak öğesi sınıfı tarafından temsil edilir `ThisDocument` .

 Konak denetimleri, içerik denetimleri, yer işaretleri ve XML düğümleri gibi yerel Word nesnelerini temel alır. Konak denetimleri, yerel Word nesnelerine benzer işlevler sağlar, ancak yeni olaylar, tasarımcı desteği ve veri bağlama özelliğine de sahiptir. Bunlar, proje kodunuzda ve IntelliSense 'de ilk sınıf nesneler olarak görünürler, bu da Word nesne modelinde gezinmek zorunda kalmadan kodunuzda belirli nesnelere doğrudan başvurmayı kolaylaştırır.

 Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)

- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)

- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Word 'ün Kullanıcı arabirimini özelleştirme
 Çoğu Microsoft Office çözüm, kullanıcıların çözümle etkileşim kurması için bir yol sağlamak üzere Office uygulamasının Kullanıcı arabirimini (UI) değiştirir. Belge düzeyi özelleştirmesi kullanarak Word 'ün Kullanıcı arabirimini değiştirebilmenin birçok yolu vardır. Örneğin, şerit 'e denetimler ekleyebilir ve bir eylemler bölmesi görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [OFFICE UI özelleştirmesi](../vsto/office-ui-customization.md).

 Ayrıca, projenizle doğrudan Visual Studio 'da ilişkili belgeyi açabilirsiniz. Belge Visual Studio 'da açıldığında, Word Kullanıcı arabirimini kullanarak belgeyi değiştirebilirsiniz. Ayrıca, denetimleri üzerine sürüklemenize olanak sağlayan tasarım yüzeyi olarak belgeyi de kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio ortamında Office projeleri](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Denetimleri verilere bağlama
 İçerik denetimleri ve denetim, <xref:Microsoft.Office.Tools.Word.Bookmark> **veri kaynakları** penceresinden sürükleyebileceğiniz denetim listesidir. İçerik denetimleri ve yer işaretleri bu şekilde eklendiğinde, pencereyi kullanarak ayarladığınız veri kaynağına otomatik olarak bağlanır. Herhangi bir kod yazmadan, veritabanlarından, hizmetlerden ve iş nesnelerinden verileri görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Sonraki adımlar
 Word için belge düzeyi özelleştirmesi oluşturmayı öğrenmek için bkz. [Izlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Bu izlenecek yol, Visual Studio 'da Office geliştirme araçları ve Word belge düzeyi özelleştirmeleri için programlama modeli sağlar.

 Word projelerindeki yaygın görevlerden bazıları boyunca size kılavuzluk eden konuların listesi için bkz. [Office programlamada ortak görevler](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Word çözümleri](../vsto/word-solutions.md)
- [İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Word kullanarak izlenecek yollar](../vsto/walkthroughs-using-word.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md)
