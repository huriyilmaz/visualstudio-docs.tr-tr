---
title: Çalışma zamanında form bölgesine erişme
description: Çalışma zamanında Microsoft Office çeşitli proje türlerinde ve sürümlerinde form bölgesine erişmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dbd60f5773392af2066e4693751dd6fff99128b9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827974"
---
# <a name="access-a-form-region-at-run-time"></a>Çalışma zamanında form bölgesine erişme

|Şunlara uygulanır|
|----------------|
|Bu konunun içerdiği bilgiler, yalnızca Microsoft Office'in aşağıdaki proje türleri ve sürümleri için geçerlidir. Daha fazla bilgi için bkz. [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Proje türü**<br /><br /> -VSTO eklenti projeleri<br /><br /> **Microsoft Office sürümü**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 `Globals`Form bölgelerine Outlook projenizin içinden herhangi bir yerden erişmek için sınıfını kullanın. Sınıfı hakkında daha fazla bilgi için `Globals` bkz. [Office Projelerindeki Nesnelere Genel erişim](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Belirli bir Outlook Inspector penceresinde görünen erişim formu bölgeleri
 Belirli bir Outlook denetçisinde görünen tüm form bölgelerine erişmek için, `FormRegions` sınıfının özelliğini çağırın `Globals` ve <xref:Microsoft.Office.Interop.Outlook.Inspector> denetçisi temsil eden bir nesneyi geçirin.

 Aşağıdaki örnek, şu anda odağa sahip olan Inspector 'da görünen form bölgelerinin koleksiyonunu alır. Bu örnek daha sonra adlı koleksiyondaki bir form bölgesine erişir `formRegion1` ve metin kutusunda görüntülenen metni olarak ayarlar `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet2":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet2":::

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Belirli bir Outlook Explorer penceresinde görünen erişim formu bölgeleri
 Belirli bir Outlook Explorer 'da görünen tüm form bölgelerine erişmek için, `FormRegions` sınıfının özelliğini çağırın `Globals` ve <xref:Microsoft.Office.Interop.Outlook.Explorer> Gezgini temsil eden bir nesneyi geçirin.

 Aşağıdaki örnek, Gezgin 'de Şu anda odaklanmış olan form bölgelerinin koleksiyonunu alır. Bu örnek daha sonra adlı koleksiyondaki bir form bölgesine erişir `formRegion1` ve metin kutusunda görüntülenen metni olarak ayarlar `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet3":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet3":::

## <a name="access-all-form-regions"></a>Tüm form bölgelerine erişin
 Tüm araştırıcılar ve tüm Denetçilerde görünen tüm form bölgelerine erişmek için, `FormRegions` sınıfının özelliğini çağırın `Globals` .

 Aşağıdaki örnek, tüm araştırıcılar ve tüm Denetçilerde görünen form bölgelerinin koleksiyonunu alır. Bu örnekte, adlı bir form bölgesine erişilir `formRegion1` ve metin kutusunda görüntülenen metin olarak ayarlanır `Hello World` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs" id="Snippet1":::

## <a name="access-controls-on-a-form-region"></a>Form bölgesindeki erişim denetimleri
 Sınıfını kullanarak form bölgesindeki denetimlere erişmek için `Globals` , denetimleri form bölgesi kod dosyası dışındaki kod için erişilebilir yapmanız gerekir.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Form bölgesi tasarımcısında tasarlanan form bölgeleri
 C# için, erişmek istediğiniz her denetimin değiştiricisini değiştirin. Bunu yapmak için, form bölgesi tasarımcısında her bir denetimi seçin ve **Özellikler** penceresinde **değiştiriciler** özelliğini **iç** veya **ortak** olarak değiştirin. Örneğin, öğesinin **değiştirici** özelliğini `textBox1` **iç** olarak değiştirirseniz `textBox1` yazarak erişebilirsiniz `Globals.FormRegions.FormRegion1.textBox1` .

 Visual Basic için değiştiriciyi değiştirmenize gerek yoktur.

### <a name="imported-form-regions"></a>İçeri aktarılan form bölgeleri
 Outlook 'ta tasarlanan bir form bölgesini içeri aktardığınızda, form bölgesindeki her bir denetimin erişim değiştiricisi Private olur. İçe aktarılan bir form bölgesini değiştirmek için form bölgesi tasarımcısını kullanamadığı için, **Özellikler** penceresinde bir denetimin değiştiricisini değiştirmenin bir yolu yoktur.

 Form bölgesi kod dosyası dışından bir denetime erişimi etkinleştirmek için, bu denetimi döndürmek üzere form bölgesi kod dosyasında bir özellik oluşturun.

 C# ' de özellikler oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: okuma yazma özelliklerini bildirme ve kullanma &#40;C&#35; programlama kılavuzu&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Visual Basic özellikler oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Özellik oluşturma (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Ayrıca bkz.
- [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)
- [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [İzlenecek yol: Outlook 'ta tasarlanan form bölgesini Içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)
- [Çalışma zamanında Şerite erişin](../vsto/accessing-the-ribbon-at-run-time.md)
