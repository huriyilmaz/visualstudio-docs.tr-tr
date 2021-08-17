---
title: Office projelerinde olaylar
description: Her bir Office proje şablonunun birkaç olay işleyicisi oluşturması ve bu olay işleyicileri, VSTO için olay işleyicilerinden biraz farklı olduğunu öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4eee6a66e8cd9d0a9868af75bc68ad249be76827
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038051"
---
# <a name="events-in-office-projects"></a>Office projelerinde olaylar
  Her Office proje şablonu otomatik olarak birkaç olay işleyicisi oluşturur. Belge düzeyi özelleştirmeler için olay işleyicileri, belge düzeyi özelleştirmeler için olay VSTO biraz farklıdır.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Belge düzeyi projeler
 Visual Studio düzeyi özelleştirmelerde yeni veya mevcut belgelerin veya çalışma sayfalarının arkasında oluşturulan kod sağlar. Bu kod iki farklı olay başlatır: **Başlangıç ve** **Kapatma.**

### <a name="startup-event"></a>Startup olayı
 Başlangıç **olayı,** belge çalıştırıldıktan ve derlemedeki tüm başlatma kodu çalıştırıldıktan sonra konak öğelerinin her biri (belge, çalışma kitabı veya çalışma sayfası) için yükseltildi. Bu, kodunuzun içinde çalıştır olduğu sınıfın oluşturucusnda çalıştıracak son şeydir. Konak öğeleri hakkında daha fazla bilgi için bkz. [Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

 Belge düzeyinde bir proje ekleyebilirsiniz Visual Studio kod dosyalarında **Başlangıç** olayı için olay işleyicileri oluşturur:

- Word Microsoft Office için olay işleyicisi olarak `ThisDocument_Startup` adlandırılmıştır.

- Daha Microsoft Office Excel için olay işleyicileri aşağıdaki adlara sahip olur:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown olayı
 Kapatma **olayı,** kodunuzun yük devre dışı olduğu uygulama etki alanının yüklenmek zorunda olduğu konak öğelerinin her biri için (belge veya çalışma sayfası) ortaya çıkar. Bu, kaldırılan sınıfta çağrılılacak son şeydir.

 Belge düzeyinde bir proje ekleyebilirsiniz Visual Studio kod dosyalarında **Shutdown** olayı için olay işleyicileri oluşturur:

- Word Microsoft Office için olay işleyicisi olarak `ThisDocument_Shutdown` adlandırılmıştır.

- Daha Microsoft Office Excel için olay işleyicileri aşağıdaki adlara sahip olur:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Belgenin Kapatma olayı işleyicisi sırasında **program aracılığıyla** denetimleri kaldırabilirsiniz. Kapatma olayı oluştuğunda belgenin kullanıcı arabirimi **öğeleri artık** kullanılamaz. Uygulama kapanmadan önce denetimleri kaldırmak için kodunuzu **BeforeClose** veya BeforeSave gibi başka bir olay **işleyicisine ekleyin.**

### <a name="event-handler-method-declarations"></a>Olay işleyicisi yöntem bildirimleri
 Her olay işleyicisi yöntem bildirimine geçirilen bağımsız değişkenler aynıdır: *gönderen ve* *e*. Bu Excel, *gönderen* bağımsız değişkeni veya gibi bir sayfayı ifade `Sheet1` `Sheet2` eder; Word'de gönderen bağımsız değişkeni belgeye başvurur.  *E bağımsız* değişkeni, bir olay için standart bağımsız değişkenleri ifade eder ve bu durumda kullanılmaz.

 Aşağıdaki kod örneği, Word için belge düzeyi projelerde varsayılan olay işleyicilerini gösterir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet121":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet121":::

 Aşağıdaki kod örneği, belge düzeyi projelerde varsayılan olay işleyicilerini Excel.

> [!NOTE]
> Aşağıdaki kod örneği sınıfındaki olay işleyicilerini `Sheet1` gösterir. Diğer konak öğesi sınıflarında olay işleyicilerinin adları sınıf adına karşılık gelen. Örneğin sınıfında Başlangıç `Sheet2` olay **işleyicisi** olarak adlandırılmıştır. `Sheet2_Startup` sınıfında, `ThisWorkbook` Başlangıç olay **işleyicisi** olarak adlandırılmıştır. `ThisWorkbook_Startup`

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet83":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet83":::

### <a name="order-of-events-in-document-level-excel-projects"></a>Belge düzeyindeki ve projelerde Excel sırası
 Farklı **projelerde** başlangıç Excel işleyicileri şu sırayla çağrılır:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Sırayla diğer sayfalar.

   Çalışma **kitabı** çözümünde Kapatma olayı işleyicileri şu sırayla çağrılır:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Sırayla diğer sayfalar.

    Proje derlenmiş olduğunda sıra belirlenir. Kullanıcı çalışma zamanında sayfaları yeniden yeniden değiştirirse, çalışma kitabı bir sonraki açılabilir veya kapatılacak olay sırasını değiştirmez.

## <a name="vsto-add-in-projects"></a>VSTO Eklenti projeleri
 Visual Studio eklentilerde oluşturulan VSTO sağlar. Bu kod iki farklı olay neden olur: <xref:Microsoft.Office.Tools.AddInBase.Startup> ve <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup olayı
 Olay, VSTO Eklenti yüklendikten ve derlemede tüm başlatma <xref:Microsoft.Office.Tools.AddIn.Startup> kodu çalıştırıldıktan sonra ortaya çıkar. Bu olay, oluşturulan kod `ThisAddIn_Startup` dosyasındaki yöntemi tarafından ele alındı.

 Olay işleyicisinde kod, eklentiniz yöntemi geçersiz kılmadıkça `ThisAddIn_Startup` VSTO ilk kullanıcı <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> kodudur. Bu durumda, olay `ThisAddIn_Startup` işleyicisi sonrasında <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> çağrılır.

 Kodun bir belgenin açık `ThisAdd-In_Startup` olması gerekirse olay işleyiciye kod ekleme. Bunun yerine, kullanıcı belge oluşturduğunda veya açtığında Office uygulamanın oluşturduğu bir olayına bu kodu ekleyin. Daha fazla bilgi için [bkz. Uygulama başlatıldığında Office erişme.](../vsto/programming-vsto-add-ins.md#AccessingDocuments)

 Uygulama Eklentilerinin başlangıç sırası hakkında daha fazla VSTO için [bkz. VSTO Eklentilerinin Mimarisi.](../vsto/architecture-of-vsto-add-ins.md)

### <a name="shutdown-event"></a>Shutdown olayı
 Olay, <xref:Microsoft.Office.Tools.AddInBase.Shutdown> kodunuzun yükleniyor olduğu uygulama etki alanı kaldırılacak olduğunda ortaya çıkar. Bu olay, oluşturulan kod `ThisAddIn_Shutdown` dosyasındaki yöntemi tarafından ele alındı. Bu olay işleyicisi, Eklenti yüklemesi kaldır VSTO çalıştırılacak son kullanıcı kodudur.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Eklentilerde Outlook VSTO olayı
 Olay yalnızca kullanıcı eklentiyi devre dışı VSTO com eklentileri iletişim kutusu kullanılarak <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Outlook. Bu, çıkış Outlook yükseltlanmaz. Çıkışta çalışması gereken kodunuz Outlook aşağıdaki olaylardan birini işle:

- <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit>Nesnesinin <xref:Microsoft.Office.Interop.Outlook.Application> olayı.

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close>Nesnesinin <xref:Microsoft.Office.Interop.Outlook.Explorer> olayı.

> [!NOTE]
> Kayıt defterini Outlook çıkışta <xref:Microsoft.Office.Tools.AddInBase.Shutdown> olayı yükseltmeye zorlarsınız. Ancak, bir yönetici bu ayarı geri döndürse, yönteme ekleyseniz herhangi bir kod, `ThisAddIn_Shutdown` çıkışta Outlook çalışır. Daha fazla bilgi için [bkz. Outlook 2010 için değişiklikleri kapatma.](/previous-versions/office/developer/office-2010/ee720183(v=office.14))

## <a name="see-also"></a>Ayrıca bkz.
- [Yeni Office geliştirme](../vsto/developing-office-solutions.md)
- [Nasıl Office: Visual Studio'da Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program belge düzeyi özelleştirmeleri](../vsto/programming-document-level-customizations.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)
- [Office şablonlarına genel bakış](../vsto/office-project-templates-overview.md)
