---
title: Office Projelerindeki Olaylar
description: Her bir Office proje şablonunun çeşitli olay işleyicilerini nasıl ürettireceğinizi ve bu olay işleyicilerinin, VSTO eklentileri için olay işleyicilerinden biraz farklı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7bf4da3f0b2dd9cbab960a779690aa752744cdae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910319"
---
# <a name="events-in-office-projects"></a>Office Projelerindeki Olaylar
  Her Office proje şablonu otomatik olarak birkaç olay işleyicisi oluşturur. Belge düzeyi özelleştirmeleri için olay işleyicileri, VSTO eklentilerine yönelik olay işleyicilerinden biraz farklıdır.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Belge düzeyi projeleri
 Visual Studio, belge düzeyi özelleştirmelerde yeni veya mevcut belge veya çalışma sayfalarının arkasında oluşturulan kod sağlar. Bu kod iki farklı olay oluşturur: **Başlangıç** ve **kapalı**.

### <a name="startup-event"></a>Startup olayı
 **Başlangıç** olayı, belge çalıştıktan sonra ana bilgisayar öğelerinin (belge, çalışma kitabı veya çalışma sayfası) her biri için oluşturulur ve derlemedeki tüm başlatma kodu çalıştırılır. Bu, kodunuzun üzerinde çalıştığı sınıfın oluşturucusunda çalıştırılacak son şeydir. Konak öğeleri hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

 Belge düzeyinde bir proje oluşturduğunuzda, Visual Studio oluşturulan kod dosyalarındaki **Başlangıç** olayı için olay işleyicileri oluşturur:

- Microsoft Office Word projeleri için, olay işleyicisi olarak adlandırılır `ThisDocument_Startup` .

- Microsoft Office Excel projeleri için, olay işleyicileri aşağıdaki adlara sahiptir:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown olayı
 Bir  konak öğesi (belge veya çalışma sayfası), kodunuzun yüklendiği uygulama etki alanının kaldırılması ile ilgili olduğu her bir konak öğesi için (belge veya çalışma sayfası) tetiklenir. Bu,, ' i kaldırdığından, sınıfında çağrılacak son şeydir.

 Belge düzeyinde bir proje oluşturduğunuzda, Visual Studio, oluşturulan kod dosyalarındaki **kapalı** olay için olay işleyicileri oluşturur:

- Microsoft Office Word projeleri için, olay işleyicisi olarak adlandırılır `ThisDocument_Shutdown` .

- Microsoft Office Excel projeleri için, olay işleyicileri aşağıdaki adlara sahiptir:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Belgenin **kapalı** olay işleyicisi sırasında denetimleri program aracılığıyla kaldırmayın. **Kapatmadan** önce belgenin UI öğeleri artık kullanılamaz. Uygulama kapanmadan önce denetimleri kaldırmak istiyorsanız, kodunuzu, **Beforeckaybetme** veya **BeforeSave** gibi başka bir olay işleyicisine ekleyin.

### <a name="event-handler-method-declarations"></a>Olay işleyicisi yöntem bildirimleri
 Her olay işleyicisi yöntemi bildirimi kendisine geçirilen bağımsız değişkenlere sahiptir: *gönderici* ve *e*. Excel 'de *gönderici* bağımsız değişkeni, veya gibi bir sayfaya başvurur, `Sheet1` `Sheet2` *Gönderen* bağımsız değişkeni belgeye başvurur. *E* bağımsız değişkeni, bu durumda kullanılmayan bir olayın standart bağımsız değişkenlerine başvurur.

 Aşağıdaki kod örneği, Word için belge düzeyi projelerindeki varsayılan olay işleyicilerini gösterir.

 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]

 Aşağıdaki kod örneği, Excel için belge düzeyi projelerindeki varsayılan olay işleyicilerini gösterir.

> [!NOTE]
> Aşağıdaki kod örneği, sınıfındaki olay işleyicilerini gösterir `Sheet1` . Diğer konak öğesi sınıflarında bulunan olay işleyicilerinin adları, sınıf adına karşılık gelir. Örneğin, `Sheet2` sınıfında, **Başlangıç** olayı işleyicisi adlandırılır `Sheet2_Startup` . `ThisWorkbook`Sınıfında, **Başlangıç** olayı işleyicisi adlandırılır `ThisWorkbook_Startup` .

 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]

### <a name="order-of-events-in-document-level-excel-projects"></a>Belge düzeyindeki Excel projelerinde olay sırası
 Excel projelerindeki **Başlangıç** olayı işleyicileri şu sırada çağrılır:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Sırayla diğer sayfalar.

   Çalışma kitabı çözümündeki **kapalı** olay işleyicileri şu sırada çağrılır:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Sırayla diğer sayfalar.

    Sıra, proje derlendiğinde belirlenir. Kullanıcı çalışma zamanında sayfaları yeniden düzenler, çalışma kitabının bir sonraki açılışında veya kapatılışında olayların oluşturulma sırasını değiştirmez.

## <a name="vsto-add-in-projects"></a>VSTO eklenti projeleri
 Visual Studio, VSTO eklentilerinde oluşturulan kodu sağlar. Bu kod iki farklı olay oluşturur: <xref:Microsoft.Office.Tools.AddInBase.Startup> ve <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup olayı
 <xref:Microsoft.Office.Tools.AddIn.Startup>Olay, VSTO eklentisi yüklendikten sonra ve derlemedeki tüm başlatma kodları çalıştırıldıktan sonra tetiklenir. Bu olay, `ThisAddIn_Startup` oluşturulan kod dosyasındaki yöntemi tarafından işlenir.

 `ThisAddIn_Startup`VSTO eklentisi yöntemi geçersiz kılmadığı takdirde olay işleyicisindeki kod, çalıştırılacak ilk kullanıcı kodudur <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> . Bu durumda, `ThisAddIn_Startup` olay işleyicisi öğesinden sonra çağrılır <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> .

 `ThisAdd-In_Startup`Kod bir belgenin açık olmasını gerektiriyorsa olay işleyicisine kod eklemeyin. Bunun yerine, bir Kullanıcı bir belge oluşturduğunda veya açtığında Office uygulamasının oluşturduğu bir olaya bu kodu ekleyin. Daha fazla bilgi için bkz. [Office uygulaması başladığında belgeye erişme](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 VSTO eklentilerinin başlangıç dizisi hakkında daha fazla bilgi için bkz. [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown olayı
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown>Olay, kodunuzun yüklendiği uygulama etki alanı boşaltılacak şekilde olduğunda tetiklenir. Bu olay, `ThisAddIn_Shutdown` oluşturulan kod dosyasındaki yöntemi tarafından işlenir. Bu olay işleyicisi, VSTO eklentisi kaldırıldığında çalıştırılacak son kullanıcı kodudur.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Outlook VSTO Eklentilerindeki kapalı olayı
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown>Olay yalnızca Kullanıcı Outlook 'TA com eklentileri iletişim kutusunu kullanarak VSTO eklentisini devre dışı bıraktığında tetiklenir. Outlook çıktığında bu değildir. Outlook 'Tan çıkıldığında çalışması gereken bir kodunuz varsa, aşağıdaki olaylardan birini işleyin:

- <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> <xref:Microsoft.Office.Interop.Outlook.Application> Nesnesinin olayı.

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> <xref:Microsoft.Office.Interop.Outlook.Explorer> Nesnesinin olayı.

> [!NOTE]
> Outlook 'U <xref:Microsoft.Office.Tools.AddInBase.Shutdown> , çıkış sırasında kayıt defteri 'ni değiştirerek olayı daha sonra tetikleyerek uygulamayı zorlayabilirsiniz. Ancak, bir yönetici bu ayarı geri döndürüyorsa, yönteme eklediğiniz herhangi bir kod `ThisAddIn_Shutdown` artık Outlook 'tan çıkıldığında çalışmaz. Daha fazla bilgi için bkz. [Outlook 2010 için değişiklikleri kapatır](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office proje şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
