---
title: Office projelerinde hata ayıklama
description: Diğer Visual Studio projeleri için kullandığınız Microsoft Visual Studio araçları kullanarak Office projelerinin hatalarını nasıl ayıklayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1e21a876fd2af04523ae205882463b0f8e0e3f3b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928893"
---
# <a name="debug-office-projects"></a>Office projelerinde hata ayıklama
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Diğer projeler için kullandığınız Microsoft araçlarını kullanarak Office projelerinde hata ayıklaması yapabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata ayıklama özellikleri, örneğin, **Yerel öğeler** penceresinde kesme noktaları ekleme ve değişkenleri görüntüleme özelliği gibi Office projelerinde hata ayıklarken da kullanılabilir. Hata ayıklama araçları hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugger-feature-tour.md).

> [!TIP]
> Hata ayıklamayı basitleştirmek için, derleme ve hata ayıklama yapmadan önce Office uygulamasının tüm açık örneklerini kapatın.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>Hata ayıklayıcıyı başlatma ve durdurma
 Diğer projelere hata ayıklamaya başladığınızda olduğu gibi bir Office projesinde hata ayıklamaya başlayabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Örneğin, **F5** tuşuna basabilirsiniz. VSTO eklenti projesinde hata ayıklamaya başladığınızda, hedeflenen Office uygulaması için yeni bir işlem başlatılır ve VSTO eklentisi yüklenir.

 Belge düzeyindeki bir projede hata ayıklamaya başladığınızda belge veya çalışma kitabı yeni bir kelime veya Excel işleminde açılır.

 Hata ayıklayıcıyı durdurduğunuzda, hata ayıklayıcı uygulama işlemini aniden sonlandırır veya hata ayıklayıcı ayrılmak üzere ayarlandıysa ayırır. Sonlandırılan Office uygulama işleminde açılan diğer tüm belgeler uyarı vermeden da kapatılır ve kaydedilmemiş değişiklikler kaybolur. Bu, hata ayıklayıcı çalışırken açılan tüm belgeleri veya çalışma kitaplarını içerebilir.

 Genellikle, hata ayıklayıcıyı durdurmadan önce işlemden ayrılmak daha iyidir, böylece Office uygulamasından normal şekilde çıkabilirsiniz. Ayrıca, hata ayıklayıcıyı durdurduktan sonra yine de bir açık belge veya çalışma sayfasıyla çalışmak istiyorsanız işlemden ayırabilirsiniz.

 Word için belge düzeyi özelleştirmesi hata ayıklaması yapıyorsanız, hata ayıklayıcıyı sürekli olarak durdurmayı ve Word 'Ün aniden kapatılmasını sağlamak normal şablonun bozulmasına yol açabilir. Bu durumda, bozuk Normal şablonu silebilirsiniz ve Word 'Ü bir sonraki açışınızda otomatik olarak yeniden oluşturulur. Ancak, Normal şablonda depolanan makrolar yeniden oluşturulmaz.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Office 2013 veya Office 2016 kullanarak Office 2013 VSTO Eklentilerini hata ayıklama
 Visual Studio 2015 kullanıyorsanız ve Office sürümlerinin her iki sürümü de yan yana yüklüyse, Visual Studio Office 2016 ' i başlatır. Visual Studio 2013 kullanıyorsanız, Visual Studio Office 2013 ' i başlatır.

 Office 'in farklı bir sürümünü (2013 veya 2016) kullanarak VSTO eklentilerinizi ayıklamak istiyorsanız, **Proje tasarımcısını** açın ve **Hata Ayıkla** sekmesinde **dış program Başlat** seçenek düğmesini seçin. Ardından, uygun Office uygulaması yürütülebilir dosyasının konumuna gidin.

## <a name="f10-and-f11-behavior"></a>F10 ve F11 davranışı
 Office projesinde hata ayıklamaya başladığınızda, **F10** ve **F11** , diğer Visual Basic veya C# projelerinin hatalarını ayıklamaya başladığınızda aynı davranışa sahip değildir. Visual Basic veya C# projelerinde, hata ayıklayıcı ana işlevde duraklar; Office projelerinde, Visual Studio 'nun Office uygulamasının ana işlevi üzerinde denetimi yoktur. Ancak, hata ayıklama sırasında **F10** ve **F11** Işlevleri Visual Basic ve C# projeleriyle aynı işlevlere sahiptir.

## <a name="display-exceptions"></a>Özel durumları görüntüle
 Yönetilen kodun yönetilmeyen kodla etkileşime girdiği şekilde, Visual Studio Microsoft Office uygulamalar tarafından oluşturulan hataları görüntülemez. Örneğin, Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan bir VSTO eklentisi bir özel durum oluşturursa Microsoft Office uygulama bir hata görüntülemeden devam eder. Bu hataları görmek için, hata ayıklayıcıyı ortak dil çalışma zamanı özel durumlarını bozmak üzere ayarlayın. Daha fazla bilgi için bkz. [hata ayıklayıcı ile özel durumları yönetme](../debugger/managing-exceptions-with-the-debugger.md).

 Hata ayıklayıcıyı ortak dil çalışma zamanı özel durumlarının kesintiye uğratmak üzere ayarlarsanız, işledikleriniz de dahil olmak üzere tüm özel durumlar artık hata ayıklayıcıya bölünür ve bu da çalışma zamanının kendisinden ilgili olmayabilir. Msosec 'in bulunamamasına başvuran hatalar her projede görünür, ancak yok sayılacak güvenlidir. Bu msosec özel durumları, çözümünüzü etkilemez.

 **TRY... öğesini de kullanabilirsiniz.** Özel durumları yakalamak için yöntemlerinizin çevresindeki catch deyimleri.

 Visual Studio, varsayılan olarak Office projeleri için tam zamanında hata ayıklama hataları göstermez; Ancak, ortaya çıkan hataları görebilmeniz için bu özelliği etkinleştirebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Da tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Komut satırı bağımsız değişkenleri
 **Hata ayıklama** özelliği sayfasında **Başlangıç eylemi** , **projeyi Başlat** olarak ayarlandıysa, Visual Studio, komut satırı bağımsız değişkenlerini başlangıç seçenekleri olarak belirtseniz bile, projenin hata ayıklaması sırasında komut satırı bağımsız değişkenlerini kullanmaz. Hata ayıklamayı başlattığınızda komut satırı bağımsız değişkenlerini kullanmak istiyorsanız, **projeyi Başlat** dışında bir **Başlangıç eylemi** seçmeniz gerekir.

## <a name="source-control"></a>Kaynak denetimi
 Hata ayıklama özellikleri, kaynak denetimi altındaki birden çok kullanıcı arasında paylaşılmaz. Visual Basic ve C# projeleri, hata ayıklama özelliklerini kullanıcıya özgü bir dosyaya (*ProjectName*. vbproj. User veya *ProjectName*. csproj. User) depolar ve bu dosya kaynak denetimi altında değildir. Birden fazla kişinin hata ayıklaması varsa, her bir kişinin hata ayıklama özelliklerini el ile girmesi gerekir.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Belge düzeyindeki bir projede önbelleğe alınmış veri kümelerinde hata ayıklama
 Her proje oluşturduğunuzda veri kümesi boşaltılır ve yeniden oluşturulur. Önbelleğe alınmış bir veri kümesinde hata ayıklamak istiyorsanız, belgeyi Visual Studio dışında açmanız ve ardından hata ayıklayıcıyı eklemeniz gerekir.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Word 97-2003 Document (*. doc) biçimini temel alan Word belge projelerinde hata ayıkla
 Word 97-2003 Document (. doc *) biçimine dayalı bir Word belgesi projesinde hata ayıklamak için */* , proje klasörünü güvenilir klasör listesine eklemeniz gerekir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [belgelere güven verme](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Devre dışı bırakılmış eklentilerde hata ayıkla
 Microsoft Office uygulamalar, beklenmedik şekilde davranan VSTO eklentilerini devre dışı bırakabilir. Microsoft Office uygulaması, uygulama her başlatıldığında sorunlu kodun yüklenmesini engellemek için VSTO eklentilerini devre dışı bırakır. Ancak, tipik hata ayıklama sırasında beklenmeyen davranışa de kolayca yol açabilir. VSTO Eklentilerini yeniden etkinleştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: BIR VSTO eklentisini yeniden etkinleştirme devre dışı](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)bırakılmış.

 Microsoft Office uygulamalarının VSTO eklentileri için kullandığı iki tür devre dışı bırakma: sabit devre dışı bırakma ve yumuşak devre dışı bırakma.

### <a name="hard-disabling"></a>Sabit devre dışı bırakma
 Bir VSTO eklentisi uygulamanın beklenmedik şekilde kapatılmasına neden olduğunda, sabit devre dışı bırakma gerçekleşebilir. Ayrıca, <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO eklentiinizdeki olay işleyicisi yürütülürken hata ayıklayıcıyı durdurursanız, geliştirme bilgisayarınızda da meydana gelebilir. Bir VSTO eklentisi sabit devre dışı bırakıldığında, uygulama içindeki **devre dışı öğeler** listesinde görünür.

 Office uygulaması, Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan bir VSTO eklentisini kalıcı olarak devre dışı bırakırsa, uygulama yalnızca hataya neden olan VSTO eklentisini devre dışı bırakır. Office uygulaması için Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan diğer VSTO eklentileri yüklenmeye devam edecektir.

### <a name="soft-disabling"></a>Geçici devre dışı bırakma
 Bir VSTO eklentisi uygulamanın beklenmedik şekilde kapatılmasına neden olmayan bir hata ürettiğinden, geçici devre dışı bırakma gerçekleşebilir. Örneğin, bir uygulama, olay işleyicisi yürütülürken işlenmeyen bir özel durum oluşturursa, VSTO eklentisini geçici olarak devre dışı bırakabilir <xref:Microsoft.Office.Tools.AddIn.Startup> . Bir VSTO eklentisi geçici olarak devre dışı bırakıldığında, uygulamanın **etkin olmayan uygulama eklentileri** listesinde görünür ve uygulama, bir VSTO **eklentisinin, kaldırılan bir kayıt defteri** girdisinin değerini değiştirir. **LoadBehavior** kayıt defteri girişi hakkında daha fazla bilgi için bkz. [VSTO eklentileri için kayıt defteri girişleri](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Olay Görüntüleyicisi kullanarak yükleme hatalarını giderme
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Office çözümlerini yüklerken veya kaldırdığınızda oluşturulan tüm özel durumlar Için Windows 'daki Olay Görüntüleyicisi iletileri yazar. Bu iletileri, yükleme ve dağıtım sorunlarını çözmek için kullanabilirsiniz.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Günlük dosyası ve hata iletileri kullanarak başlatma hatalarını giderme
 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Başlangıç sırasında oluşan tüm hataları bir günlük dosyasına yazabilir veya her hatayı bir ileti kutusunda görüntüler. Varsayılan olarak, bu seçenekler kapalıdır. Ortam değişkenleri oluşturarak seçenekleri açabilirsiniz.

 Her hatayı bir ileti kutusunda göstermek için adlı bir ortam değişkeni oluşturun `VSTO_SUPPRESSDISPLAYALERTS` ve 0 (sıfır) olarak ayarlayın. Ortam değişkenini silerek veya 1 (bir) olarak ayarlayarak iletileri gizleyebilirsiniz.

 Hataları bir günlük dosyasına yazmak için adlı bir ortam değişkeni oluşturun `VSTO_LOGALERTS` ve bunu 1 (bir) olarak ayarlayın. , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] VSTO eklentisinin dağıtım bildirimini içeren klasörde veya özelleştirmeyle ilişkili belge veya çalışma kitabını içeren klasörde, günlük dosyasını oluşturur. Başarısız olursa, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yerel *% Temp%* klasöründe günlük dosyasını oluşturur. Uygulama düzeyi VSTO eklentileri için varsayılan ad *eklenti adı*. VSTO. log ' dır. Belge düzeyi projeleri için, günlük dosyasının adı *belge adı* olur. ExcelWorkbook1.xlsx. log gibi. log *Uzantısı*. Günlüğe kaydetme hatalarını durdurmak için, ortam değişkenini silin veya 0 (sıfır) olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri oluşturma](../vsto/building-office-solutions.md)
- [Nasıl yapılır: devre dışı bırakılmış bir VSTO eklentisini yeniden etkinleştirme](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md)