---
title: Projelerde Office ayıklama
description: Diğer projelerde kullanılan Office araçlarıyla aynı Microsoft Visual Studio projelerinde hata ayıklamayı Visual Studio öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0fbd7623cac8acddcbea3265ed3d4da125d3638b16e7f94e240b199118c3e0e8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394764"
---
# <a name="debug-office-projects"></a>Projelerde Office ayıklama
  Diğer projeler için Office Microsoft araçlarını kullanarak [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projelerde hata [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıkabilirsiniz. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Yereller penceresinde kesme noktası ekleme ve değişkenleri görüntüleme gibi  hata ayıklayıcı özellikleri, projelerde hata ayıklaması Office kullanılabilir. Hata ayıklama araçları hakkında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] daha fazla bilgi için [bkz.](../debugger/debugger-feature-tour.md)Visual Studio.

> [!TIP]
> Hata ayıklamayı basitleştirmek için derlemeden ve hata ayıklamadan önce Office uygulamanın açık örneklerini kapatın.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>Hata ayıklayıcıyı başlatma ve durdurma
 Diğer projelerde hata ayıklamaya Office gibi bir projesinde hata ayıklamaya [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **başlayabilirsiniz; örneğin, F5 tuşuna basarak.** VSTO Eklenti projesinde hata ayıklamaya başlarken, hedeflenen Office uygulaması için yeni bir işlem başlar ve VSTO Eklenti yüklenir.

 Belge düzeyi projede hata ayıklamaya başlarken, belge veya çalışma kitabı yeni bir Word veya Excel açılır.

 Hata ayıklayıcıyı durdursanız, hata ayıklayıcı uygulama işlemini aniden sonlandırılır veya hata ayıklayıcıyı ayırmak için ayarlanmışsa ayırır. Sonlandırılan uygulama işlemi sırasında açılan Office tüm belgeler de uyarı olmadan kapatılır ve tüm unsaved değişiklikleri kaybolur. Bu, hata ayıklayıcı çalışırken açılan tüm belgeleri veya çalışma kitaplarını içerebilir.

 Normalde, hata ayıklayıcıyı durdurmadan önce işlemden ayırmak daha iyidir, böylece uygulamanın Office şekilde çıkabilirsiniz. Hata ayıklayıcıyı durdurduktan sonra açık bir belge veya çalışma sayfasıyla çalışmak istemeniz de ilk olarak işlemden ayrılabilirsiniz.

 Word için belge düzeyi özelleştirmede hata ayıklarsanız, hata ayıklayıcıyı tekrar tekrar durdurmak ve Word'in aniden kapanmasına neden olmak Normal şablonun bozulmasına neden olabilir. Bu durumda, bozuk Normal şablonunu silebilirsiniz ve Word'i bir sonraki aç açsanız otomatik olarak yeniden oluşturulur. Ancak, Normal şablonda depolanan tüm makrolar yeniden oluşturulmz.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>2013 Office 2013 VSTO 2013 veya 2016'Office kullanarak Office ayıklama
 Visual Studio 2015 kullanıyorsanız ve her iki Office sürümünüz de yan yana yüklüyse, Visual Studio 2016'Office başlar. Visual Studio 2013 2013 Visual Studio Office.

 VSTO Eklentinizin hata ayıklamak için farklı bir Office (2013 veya 2016) sürümünü kullanmak, **Project Tasarımcısı'nda** açın  ve Hata Ayıkla sekmesinde Dış programı başlat seçeneği **düğmesini** seçin. Ardından, uygulama yürütülebilir dosyası için uygun Office göz atabilirsiniz.

## <a name="f10-and-f11-behavior"></a>F10 ve F11 davranışı
 Bir Office projesinde hata ayıklamaya başlarken, **F10** ve **F11** diğer Visual Basic veya C# projelerinde hata ayıklamaya başlarken aynı davranışa sahip olmaz. Hata Visual Basic veya C# projelerinde hata ayıklayıcı ana işlevde durur; Office projelerinde Visual Studio uygulamanın ana işlevi üzerinde Office sahip değildir. Ancak, hata ayıklama sırasında **F10** ve **F11,** Visual Basic ve C# projelerinde aynı işlevlere sahiptir.

## <a name="display-exceptions"></a>Özel durumları görüntüleme
 Yönetilen kodun yönetilemeyen kodla etkileşim kurma Visual Studio uygulamalar tarafından oluşan hataları Microsoft Office. Örneğin, VSTO geliştirme araçları kullanılarak oluşturulan Office bir Visual Studio özel durum oluşturursa, Microsoft Office uygulama hata görüntülemeden devam eder. Bu hataları görmek için hata ayıklayıcısını ortak dil çalışma zamanı özel durumlarına göre bozacak şekilde ayarlayın. Daha fazla bilgi için [bkz. Hata ayıklayıcısı ile özel durumları yönetme.](../debugger/managing-exceptions-with-the-debugger.md)

 Hata ayıklayıcısını ortak dil çalışma zamanı özel durumlarına göre ayıracak şekilde ayarsanız, artık işleneler ve çalışma zamanının kendisiyle ilgili olmayan bazı ilk şans özel durumları da dahil olmak üzere tüm özel durumlar artık hata ayıklayıcısına dahil olur. Msosec'in bulunamayarak ilgili hatalar her projede görünür, ancak yoksaymak güvenlidir. Bu msosec özel durumları çözümlerinizi etkilemez.

 Ayrıca **Deneyin... Özel** durumları yakalamak için yöntemlerinizin çevresindeki catch deyimleri.

 Varsayılan olarak, Visual Studio projelerde Tam Zamanında hata ayıklama hataları da Office; ancak, oluşan hataları görmek için bu özelliği etkinleştirebilirsiniz. Daha fazla bilgi için, [bkz. In-Time hata ayıklama Visual Studio.](../debugger/just-in-time-debugging-in-visual-studio.md)

## <a name="command-line-arguments"></a>Komut satırı bağımsız değişkenleri
 Hata **Ayıklama** özellik  sayfasındaKi Eylemi Başlat Project **olarak** ayarlanırsa, Visual Studio başlangıç seçenekleri olarak komut satırı bağımsız değişkenlerini belirtse bile projede hata ayıklarken komut satırı bağımsız değişkenlerini kullanmaz. Hata ayıklamaya başlarken komut satırı bağımsız değişkenlerini kullanmak için Start **Project** dışında **bir Başlangıç Eylemi seçmeniz gerekir.**

## <a name="source-control"></a>Kaynak denetimi
 Hata ayıklama özellikleri, kaynak denetimi altındaki birden çok kullanıcı arasında paylaşılmaz. Visual Basic ve C# projeleri hata ayıklama özelliklerini kullanıcıya özgü bir dosyada (*ProjectName*.vbproj.user veya *ProjectName*.csproj.user) depolar ve bu dosya kaynak denetimi altında değildir. Birden fazla kişi hata ayıklarken, her kişinin hata ayıklama özelliklerini el ile girmesi gerekir.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Belge düzeyi projesinde önbelleğe alınmış veri kümelerini ayıklama
 Her proje derlemeniz için veri kümesi boşaltılır ve yeniden oluşturulur. Önbelleğe alınmış bir veri kümesine hata ayıklamak için belgeyi dosyanın dışında Visual Studio sonra hata ayıklayıcıyı ekleyebilirsiniz.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Word 97-2003 Belgesi (*.doc) biçimine göre Word belge projelerinde hata ayıklama
 Word 97-2003 Belge (.doc*) biçimini temel alan bir Word Belgesi projesinde hata ayıklamak için proje klasörünü güvenilen klasör */* listesine eklemeniz gerekir. Bunun nasıl olduğu hakkında daha fazla bilgi için bkz. [Belgelere güven izni ver.](../vsto/granting-trust-to-documents.md)

## <a name="debug-disabled-add-ins"></a>Devre dışı bırakılmış eklentilerde hata ayıklama
 Microsoft Office uygulamaları beklenmedik VSTO eklentileri devre dışı bırakabilirsiniz. Bir Microsoft Office uygulama, VSTO her başlatıldığında sorunlu kodun yüklenmesini önlemek için eklentileri devre dışı bırakıyor. Ancak, tipik hata ayıklama sırasında beklenmeyen davranışlara neden olmak da kolaydır. Eklentilerini yeniden etkinleştirme hakkında VSTO için, bkz. Nasıl 2014' VSTO devre dışı bırakılmış bir [eklentiyi yeniden etkinleştirme.](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)

 Uygulamaların eklentilerde kullanabileceği iki tür Microsoft Office vardır: VSTO devre dışı bırakma ve devre dışı bırakma.

### <a name="hard-disabling"></a>Sabit devre dışı bırakma
 Bir eklenti eklenti uygulamanın beklenmedik VSTO kapatmaya neden olduğunda sabit devre dışı bırakma oluşabilir. Hata ayıklayıcıyı, eklentinizin olay işleyicisi yürütmektedirken <xref:Microsoft.Office.Tools.AddIn.Startup> VSTO bilgisayarınızda da oluşabilir. Bir VSTO sabit devre dışı bırakılmıştır, uygulamadaki Devre **Dışı Öğeler** listesinde görünür.

 Bir Office VSTO Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan bir VSTO Eklentisini devre dışı bırakıyorsa, uygulama yalnızca hataya neden olan VSTO eklentisini devre dışı bırakıyor. Bu VSTO için Visual Studio geliştirme Office kullanılarak oluşturulan diğer Office eklentiler yüklenmeye devam eder.

### <a name="soft-disabling"></a>Yumuşak devre dışı bırakma
 Uygulamanın bir eklenti VSTO uygulamanın beklenmedik şekilde kapanmasını neden olmayan bir hata ürettiğinde, yazılım devre dışı bırakılama oluşabilir. Örneğin, bir uygulama, olay işleyicisi yürüt VSTO işleyicisi işleyicisi tarafından işsiz bir özel durum oluşturursa eklenti eklentisini <xref:Microsoft.Office.Tools.AddIn.Startup> geçici olarak devre dışı bırakabilirsiniz. Bir VSTO eklentinin yazılımdan devre dışı bırakılmış  olması, uygulamanın Etkin Olmayan Uygulama Eklentileri listesinde görünür ve uygulama, yüklemenin kaldırılmış olduğunu belirtmek için VSTO Eklentisinde **LoadBehavior** kayıt defteri girişinin değerini değiştirir. **LoadBehavior** kayıt defteri girişi hakkında daha fazla bilgi için bkz. Eklentilerini [VSTO kayıt defteri girdileri.](../vsto/registry-entries-for-vsto-add-ins.md)

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Olay Görüntüleyicisi kullanarak yükleme hatalarını giderme
 Bu, çözümleri Olay Görüntüleyicisi kaldırdığınız Windows özel durumlar için iletileri Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yazar. Yükleme ve dağıtım sorunlarını çözmek için bu iletileri kullanabilirsiniz.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Günlük dosyası ve hata iletileri kullanarak başlatma hatalarını giderme
 , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] başlatma sırasında oluşan tüm hataları bir günlük dosyasına yazabilir veya her hatayı bir ileti kutusunda görüntüler. Varsayılan olarak, bu seçenekler kapalıdır. Ortam değişkenleri oluşturarak seçenekleri açabilirsiniz.

 Her hatayı bir ileti kutusunda görüntülemek için adlı bir ortam değişkeni oluşturun `VSTO_SUPPRESSDISPLAYALERTS` ve 0 (sıfır) olarak ayarlayın. Ortam değişkenlerini silerek veya 1 (bir) olarak ayarerek iletileri bastırabilirsiniz.

 Hataları bir günlük dosyasına yazmak için adlı bir ortam değişkeni oluşturun `VSTO_LOGALERTS` ve 1 (bir) olarak ayarlayın. , VSTO Eklenti için dağıtım bildirimini içeren klasörde veya özelleştirmeyle ilişkili belge veya çalışma kitabını içeren klasörde günlük [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dosyasını oluşturur. Bu başarısız olursa, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] günlük dosyasını yerel *%TEMP% klasöründe* oluşturur. Uygulama düzeyindeki VSTO eklentileri için varsayılan ad *add-in name*.vsto.log'dır. Belge düzeyindeki projeler için günlük dosyasının adı belge *adıdır.* *extension*.log, örneğin ExcelWorkbook1.xlsx.log. Hataları günlüğe kaydetmeyi durdurmak için ortam değişkenlerini silin veya 0 (sıfır) olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni Office oluşturma](../vsto/building-office-solutions.md)
- [Nasıl: Devre dışı bırakılmış VSTO Eklentiyi yeniden etkinleştirme](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Program VSTO Eklentileri](../vsto/programming-vsto-add-ins.md)