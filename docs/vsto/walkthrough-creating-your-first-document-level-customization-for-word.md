---
title: Word için ilk belge düzeyi özelleştirmeyi oluşturma
description: Microsoft Word için belge düzeyi özelleştirmesi oluşturun. Bu tür çözümde oluşturduğunuz özellikler yalnızca belirli bir belge açık olduğunda kullanılabilir.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7c039abd3a6637afe56e80164cb3add830dc44ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155492"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>İzlenecek yol: Word için ilk belge düzeyi özelleştirmeyi oluşturma

  bu açıklayıcı izlenecek yol, Microsoft Office Word için belge düzeyi özelleştirmesi oluşturmayı gösterir. Bu tür çözümde oluşturduğunuz özellikler yalnızca belirli bir belge açık olduğunda kullanılabilir. Belge düzeyinde özelleştirmeyi uygulama genelinde değişiklikler yapmak için kullanamazsınız, örneğin, herhangi bir belge açıkken yeni bir şerit sekmesi görüntüleme.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Word belgesi projesi oluşturma.

- Visual Studio tasarımcısında barındırılan belgeye metin ekleme.

- Açıldığında özelleştirilmiş belgeye metin eklemek için Word nesne modelini kullanan kod yazma.

- Test etmek için projeyi oluşturma ve çalıştırma.

- Gereksiz derleme dosyalarını ve güvenlik ayarlarını geliştirme bilgisayarınızdan kaldırmak için projeyi Temizleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar

 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Proje oluşturma

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Visual Studio yeni bir Word belge projesi oluşturmak için

1. Başlatın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Project**' ye tıklayın.
::: moniker range="vs-2017"
3. şablonlar bölmesinde, **Visual C#** veya **Visual Basic**' i genişletin ve ardından **Office/SharePoint**' yı genişletin.

4. genişletilmiş **Office/SharePoint** düğümü altında **VSTO eklentileri** düğümünü seçin.

5. proje şablonları listesinde bir Word VSTO belge projesi seçin.

6. **Ad** kutusuna **FirstDocumentCustomization** yazın.

7. **Tamam**'a tıklayın.

8. **Office için Visual Studio Araçları Project sihirbazından** **yeni belge oluştur** ' u seçin ve **tamam**' ı tıklatın.
::: moniker-end
::: moniker range=">=vs-2019"
3. **yeni Project oluştur** iletişim kutusunda **Word VSTO belge** projesini seçin.

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. **İleri**’ye tıklayın.

5. **Yeni projenizi yapılandırma** Iletişim kutusundaki **ad** kutusuna **FirstWorkbookCustomization** yazın ve **Oluştur**' a tıklayın.

6. **Office için Visual Studio Araçları Project sihirbazından** **yeni belge oluştur** ' u seçin ve **tamam**' ı tıklatın.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**FirstDocumentCustomization** projesini oluşturur ve **FirstDocumentCustomization** belgesini ve ThisDocument kod dosyasını projeye ekler. **FirstDocumentCustomization** belgesi tasarımcıda otomatik olarak açılır.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Tasarımcıdaki belgeyi kapatın ve yeniden açın

 Projenizi geliştirirken tasarımcı içindeki belgeyi kasıtlı olarak veya yanlışlıkla kapatırsanız yeniden açabilirsiniz.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Belgeyi tasarımcıda kapatmak ve yeniden açmak için

1. Tasarımcı penceresinin **Kapat** düğmesine (X) tıklayarak belgeyi kapatın.

2. **Çözüm Gezgini**, **ThisDocument** kod dosyasına sağ tıklayın ve **Görünüm Tasarımcısı**' na tıklayın.

     \- veya

     **Çözüm Gezgini**, **ThisDocument** kod dosyasına çift tıklayın.

## <a name="add-text-to-the-document-in-the-designer"></a>Tasarımcıdaki belgeye metin ekleme

 Özelleştirmenizin Kullanıcı arabirimini (UI) Tasarımcıda açık olan belgeyi değiştirerek tasarlayabilirsiniz. Örneğin, metin, tablo veya Word denetimleri ekleyebilirsiniz. tasarımcıyı kullanma hakkında daha fazla bilgi için, [Visual Studio ortamında Office projeler](../vsto/office-projects-in-the-visual-studio-environment.md)bölümüne bakın.

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Tasarımcıyı kullanarak belgenize metin eklemek için

1. Tasarımcıda açık olan belgede aşağıdaki metni yazın.

     **Bu metin, tasarımcı kullanılarak eklenmiştir.**

## <a name="add-text-to-the-document-programmatically"></a>Belgeye programlı metin ekleme

 Ardından, ThisDocument kod dosyasına kod ekleyin. Yeni kod, metnin ikinci paragrafını belgeye eklemek için Word nesne modelini kullanır. Varsayılan olarak, ThisDocument kod dosyası aşağıdaki oluşturulan kodu içerir:

- `ThisDocument`Belgenin programlama modelini temsil eden ve Word nesne modeline erişim sağlayan sınıfının kısmi bir tanımı. Daha fazla bilgi için bkz. [belge konak öğesi](../vsto/document-host-item.md) ve [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md). Sınıfın geri kalanı, `ThisDocument` değiştirmemelisiniz bir gizli kod dosyasında tanımlanır.

- `ThisDocument_Startup`Ve `ThisDocument_Shutdown` olay işleyicileri. Bu olay işleyicileri belge açılıp kapatıldığında çağrılır. Belge açıldığında özelleştirmenizin başlatılması ve belge kapatıldığında özelleştirme tarafından kullanılan kaynakları temizlemek için bu olay işleyicilerini kullanın. daha fazla bilgi için bkz. [Office projelerindeki olaylar](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Kodu kullanarak belgeye ikinci bir metin paragrafı eklemek için

1. **Çözüm Gezgini**, **ThisDocument** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

     Kod dosyası Visual Studio açılır.

2. `ThisDocument_Startup`Olay işleyicisini aşağıdaki kodla değiştirin. Belge açıldığında, bu kod bir metnin ikinci paragrafını belgeye ekler.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs" id="Snippet1":::

    > [!NOTE]
    > Bu kod, özelliğindeki ilk paragrafa erişmek için 1 dizin değerini kullanır <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> . Visual Basic ve Visual C# 0 tabanlı diziler kullanmasına karşın, Word nesne modelindeki çoğu koleksiyonun alt dizi sınırları 1 ' dir. daha fazla bilgi için bkz. [Office çözümlerinde kod yazma](../vsto/writing-code-in-office-solutions.md).

## <a name="test-the-project"></a>Projeyi test etme

### <a name="to-test-your-document"></a>Belgenizi test etmek için

1. Projenizi derlemek ve çalıştırmak için **F5** tuşuna basın.

     Projeyi derlediğinizde, kod belgeyle ilişkili bir derlemeye derlenir. Visual Studio, belgenin ve derlemenin kopyasını projenin yapı çıkış klasörüne koyar ve özelleştirmeyi çalıştırmak için geliştirme bilgisayarındaki güvenlik ayarlarını yapılandırır. daha fazla bilgi için bkz. [derleme Office çözümleri](../vsto/building-office-solutions.md).

2. Belgesinde, aşağıdaki metni gördiğinizi doğrulayın.

     **Bu metin, tasarımcı kullanılarak eklenmiştir.**

     **Bu metin kod kullanılarak eklenmiştir.**

3. Belgeyi kapatın.

## <a name="clean-up-the-project"></a>Projeyi temizle

 Projeyi geliştirmeyi bitirdiğinizde derleme çıkış klasöründeki dosyaları ve yapı işlemi tarafından oluşturulan güvenlik ayarlarını kaldırmanız gerekir.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Geliştirme bilgisayarınızda tamamlanmış projeyi temizlemek için

1. Visual Studio, **yapı** menüsünde **çözümü temizle**' ye tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

 Word için temel bir belge düzeyi özelleştirmesi oluşturduğumıza göre, şu konulardan nasıl özelleştirme geliştirileceği hakkında daha fazla bilgi edinebilirsiniz:

- Belge düzeyi özelleştirmelerde gerçekleştirebileceğiniz genel programlama görevleri: [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md).

- Word için belge düzeyi özelleştirmelerine özgü programlama görevleri: [Word çözümleri](../vsto/word-solutions.md).

- Word nesne modelini kullanma: [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md).

- Word 'ün kullanıcı arabirimini özelleştirme, örneğin, şerit 'e özel bir sekme ekleme veya kendi eylemler bölmesini oluşturma: [uı özelleştirmesi Office](../vsto/office-ui-customization.md).

- word nesne modeli kullanılarak mümkün olmayan görevleri gerçekleştirmek için Visual Studio Office çözümleri tarafından sunulan genişletilmiş Word nesnelerini kullanma (örneğin, belgelerde yönetilen denetimleri barındırma ve Windows Forms veri bağlama modelini kullanarak word denetimlerini verilere bağlama): [genişletilmiş nesneleri kullanarak word 'ü otomatikleştirin](../vsto/automating-word-by-using-extended-objects.md).

- Word için belge düzeyi özelleştirmeleri oluşturma ve hata ayıklama: [derleme Office çözümleri](../vsto/building-office-solutions.md).

- Word için belge düzeyi özelleştirmeleri dağıtma: [bir Office çözümü dağıtın](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri geliştirmeye genel bakış &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Word çözümleri](../vsto/word-solutions.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Word nesne modeline genel bakış](../vsto/word-object-model-overview.md)
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [Office UI özelleştirmesi](../vsto/office-ui-customization.md)
- [Office çözümleri oluşturun](../vsto/building-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
