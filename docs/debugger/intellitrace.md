---
title: IntelliTrace | Microsoft Docs
description: IntelliTrace kullanarak kodunuzun yürütme geçmişini Visual Studio. Belirli olayları kaydetme, ilgili kodu inceleme ve hata ayıklama hataları.
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 539e1e89f31851897adab932d75c0dca170155f9
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129431100"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>Visual Studio Enterprise için IntelliTrace (C#, Visual Basic, C++)

Kodunuzun yürütme geçmişini kaydetmek ve takip etmek için IntelliTrace'i kullanarak uygulamanıza hata ayıklamaya daha az zaman ayırabilirsiniz. IntelliTrace şunları yapabilirsiniz:

- Belirli olayları kaydetme

- İlgili kodu, hata ayıklayıcı olayları **sırasında YerelLer** penceresinde görüntülenen verileri ve işlev çağrısı bilgilerini inceleme

- Yeniden üretilemeyecek veya dağıtımda oluşan hataları ayıklama

IntelliTrace'i Visual Studio Enterprise (ancak Professional veya Community kullanabilirsiniz).

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|Senaryo|Başlık|
|-|-|
|**IntelliTrace ile uygulamamda hata ayıklama:**<br /><br /> - Geçmiş olayları göster.<br />- Bana geçmiş olaylarla ilgili çağrı bilgilerini göster.<br />- IntelliTrace oturumlarımı kaydedin.<br />- IntelliTrace'in toplayan verileri denetleme.|- [IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme](../debugger/view-historical-application-state.md)<br />- [adım adım kılavuz: IntelliTrace kullanma](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)<br />- [Geçmiş Hata Ayıklama](../debugger/historical-debugging.md)|
|**Dağıtılan uygulamalardan IntelliTrace verileri toplama**|- [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**IntelliTrace günlük dosyasından (.iTrace dosyası) hata ayıklamaya başlama.**|- [Kaydedilen IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)|

## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a> IntelliTrace ile hangi uygulamalarda hata ayıklaması olabilirim?

| Destek düzeyi| Uygulama türleri |
|---------------------| - |
| **Tam destek** | - Visual Basic 2.0 veya daha yüksek sürümleri .NET Framework Visual C# uygulamaları.<br/>ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 ve 64 bit uygulamalar dahil olmak üzere çoğu uygulamanın hata ayıklaması sebilirsiniz.<br/>IntelliTrace ile SharePoint ayıklamak için bkz. Adım [adım: IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)Kullanarak SharePoint Uygulamanın Hata Ayıklaması.<br/> IntelliTrace ile Microsoft Azure ayıklamak için bkz. [IntelliTrace](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md)ile Yayımlanan Bulut Hizmetinde Hata Ayıklama ve Visual Studio. |
| **Sınırlı destek** | - IntelliTrace geri Windows anlık görüntüleri görüntülemeyi destekleyen C++ uygulamaları. Yalnızca hata ayıklayıcısı ve özel durum olayları de destekler.<br />- .NET Core ASP.NET Core yerel hata ayıklamada yalnızca belirli olaylar (MVC Denetleyicisi, ADO.NET ve HTTPClient olayları) için desteklenen uygulamalar. Tek Başına Toplayıcı , .NET Core veya ASP.NET Core desteklenmiyor.<br />- Deneysel olarak F# uygulamaları<br />- Yalnızca olaylar için desteklenen UWP uygulamaları |
| **Desteklenmiyor** | - Diğer diller ve betik<br />- Windows Services, Silverlight, Xbox veya Windows Mobile uygulamaları |

> [!NOTE]
> Zaten çalışan bir işlemde hata ayıklamak için Yalnızca IntelliTrace olaylarını toplayabilirsiniz (çağrı bilgisi yok). Yalnızca yerel makinede 32 bit veya 64 bitlik bir işleme iliştirin. İşleme eklemeden önce oluşan olaylar toplanmaz.

## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a> IntelliTrace ile neden hata ayıklaması?

Geleneksel veya *canlı* hata ayıklama yalnızca uygulamanın geçerli durumunu gösterir ve geçmiş olaylarla ilgili sınırlı veri içerir. Bu olayları uygulamanın geçerli durumuna göre çıkararak veya uygulamanızı yeniden çalıştırarak bu olayları yeniden oluşturmanız gerekir.

IntelliTrace bu zamanlardaki belirli olayları ve verileri kaydederek bu geleneksel hata ayıklama deneyimini genişletir. Bu, özellikle hatanın bulunduğu yeri geçmişse, uygulamanıza yeniden başlatmadan neler olduğunu görmenizi sağlar. IntelliTrace geleneksel hata ayıklama işlemi sırasında varsayılan olarak açıktır ve görünmez ve otomatik olarak veri toplar. Bu, geleneksel hata ayıklama ve IntelliTrace hata ayıklama arasında kaydedilen bilgileri görmek için kolayca geçiş yapmanızı sağlar. Bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md) [ve IntelliTrace hangi verileri toplar?](#WhatData)

IntelliTrace yeniden oluşturulması zor olan veya dağıtımda gerçekleşen hataları ayıklamaya da yardımcı olabilir. IntelliTrace verisi toplayabilir ve bir IntelliTrace günlük dosyasına (.iTrace dosyası) kaydedebilirsiniz. Bir .iTrace dosyası özel durumlar, performans olayları, Web istekleri, test verileri, iş parçacıkları, modüller ve diğer sistem bilgileri ile ilgili ayrıntıları içerir. Bu dosyayı dosyada açabilir, Visual Studio Enterprise seçin ve IntelliTrace ile hata ayıklamaya başlayabilirsiniz. Bu, dosyada herhangi bir etkinliğe gitmenizi ve bu noktada uygulamanıza ilişkin belirli ayrıntıları görmenizi sağlar.

Bu kaynaklardan IntelliTrace verisi kaydedebilirsiniz:

- Visual Studio 2015 veya sonraki Enterprise veya önceki sürümlerde IntelliTrace oturumu Visual Studio Ultimate.

- IIS'de barındırılan ASP.NET web uygulamaları ya da Microsoft Monitoring Agent kullandığınızda dağıtımda tek başına ya da System Center 2012 ile birlikte çalışan SharePoint 2010 ve SharePoint 2013 uygulamaları. Bkz. [IntelliTrace tek başına toplayıcıyı ve](../debugger/using-the-intellitrace-stand-alone-collector.md) [İzlemeyi Microsoft Monitoring Agent.](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12))

IntelliTrace'in hata ayıklamada yardımcı olması ile ilgili bazı örnekler aşağıdadır:

- Uygulamanız bir veri dosyasını bozmuş ama bu olayın nerede olduğunu bilmiyorsanız.

  IntelliTrace olmadan tüm olası dosya erişimlerini bulmak, bu erişimlere kesme noktaları koymak ve sorunun nerede olduğunu bulmak için uygulamanızı yeniden çalıştırmanız gerekir. IntelliTrace ile, toplanan tüm dosya erişim olaylarını ve her olay meydana geldiğinde uygulamanıza ilişkin belirli ayrıntıları görebilir.

- Bir özel durum gerçekleşir.

  IntelliTrace olmadan özel durum hakkında bir ileti alırsınız ancak özel durumla ilgili çok fazla bilginiz olmaz. Özel durumuna neden olan çağrı zincirini görmek için çağrı yığınını incelersiniz, ancak bu çağrılar sırasında meydana gelen olayların sırasını göresiniz. IntelliTrace ile özel durumdan önce meydana gelen olayları inceleyebilirsiniz.

- Dağıtılan bir uygulamada hata veya kilitlenme gerçekleşir.

  Daha Microsoft Azure tabanlı uygulamalar için, uygulamayı yayımlamadan önce IntelliTrace veri toplamayı yapılandırabilirsiniz. Uygulamanız çalışırken IntelliTrace verileri bir .iTrace dosyasına kaydeder. Bkz. [IntelliTrace ile Yayımlanan Bulut Hizmeti'nde Hata Ayıklama ve Visual Studio.](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md)

  IIS 7.0, 7.5 ve 8.0'da barındırılan ASP.NET web uygulamaları ve SharePoint 2010 ya da SharePoint 2013 uygulamalarında, IntelliTrace verisini bir .iTrace dosyasına kaydetmek için Microsoft İzleme Aracısı'nı tek başına ya da System Center 2012 ile birlikte kullanın.

  Bu, dağıtımdaki uygulamalarla ilgili sorunları tanılamak istediğinizde kullanışlıdır. Bkz. [IntelliTrace tek başına toplayıcıyı kullanma.](../debugger/using-the-intellitrace-stand-alone-collector.md)

## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a> IntelliTrace hangi verileri toplar?

**Olay bilgilerini toplama**

Varsayılan olarak IntelliTrace yalnızca IntelliTrace olaylarını (hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve hata ayıklamada size yardımcı olacak diğer sistem olaylarını kaydedmektedir. Hata ayıklayıcı olayları ve her zaman toplanan özel durumlar dışında toplamak istediğiniz IntelliTrace olaylarının türlerini seçebilirsiniz. Bkz. [IntelliTrace özellikleri.](../debugger/intellitrace-features.md)

- **Hata ayıklayıcısı olayları**

  IntelliTrace her zaman Visual Studio hata ayıklayıcıda gerçekleşen olayları kaydeder. Örneğin, uygulama başlatan bir hata ayıklayıcı olayıdır. Diğer hata ayıklayıcı olayları, durdurma olaylarıdır ve bu da uygulamanın yürütmeyi durdurmasını sağlar. Örneğin, programınız bir kesme noktası isabet ediyor, bir izleme noktası isabet ediyor veya bir **Step komutu** yürütür.

  Varsayılan olarak, performansa yardımcı olmak için IntelliTrace bir hata ayıklayıcı olayı için mümkün olan her değeri kaydetmez. Bunun yerine, bu değerleri kaydeder:

  - YerelLer **penceresindeki değerler.** Bu değerleri **görmek için** Yereller penceresini açık tutma.

  - Otomatikler **penceresindeki** değerler yalnızca **Otomatikler penceresi** açıksa

  - Kaynak penceresinde değerini görmek için bir değişkenin üzerine fare işaretçisini getirdiğinizde görüntülenen DataTips değerleri. IntelliTrace sabitlenmiş DataTips değerlerini toplamaz.

    IntelliTrace Olayları ve Anlık Görüntüler modu etkinleştirildiğinde, IntelliTrace her hata ayıklayıcısı **Kesme** Noktası ve Adım olayında uygulama işleminin anlık **görüntüsünü** alır. Bu, pencerelerin açık olup **olmadığına**  bakılmaksızın **Yereller,** Otomatikler ve İzleme pencerelerinde değerleri kaydedecek. Sabitlenmiş veri ipuçlarında yer alan değerler de toplanır.

- **Özel durumlar**

  IntelliTrace özel durum türünü ve iletisini bu tür özel durumlar için kaydeder:

  - Özel durumun ortaya çıktığı ve yakalandığı yönetilen özel durumlar

  - İşlenmeyen özel durumlar

- **.NET Framework olayları**

  Varsayılan olarak, IntelliTrace en sık görülen .NET Framework olaylarını kaydeder. Örneğin, bir olay <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> için IntelliTrace onay kutusu durumunu ve metnini toplar.

- **SharePoint 2010 ve SharePoint 2013 uygulama olayları**

  Kullanıcı profili olayları ve SharePoint 2010 ile Visual Studio dışında çalışan 2013 uygulamaları için birleşik Günlük Kaydetme Sistemi (ULS) olaylarının alt kümesini kaydedebilirsiniz. Bu olayları bir .iTrace dosyasına kaydedebilirsiniz. 2015 Visual Studio Enterprise sonraki sürümleri, önceki bir Visual Studio Ultimate sürümünü veya [İzleme](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2015-and-other-products) Microsoft Monitoring Agent **çalıştırmayı** gerektirir.

  .iTrace dosyasını açtığınızda, eşleşen web isteğini bulmak için bir SharePoint bağıntı kimliği girin, kayıtlı olayları görüntüleyin ve belirli bir olaydan hata ayıklamaya başlayın. Dosya işlenmeyen özel durumlar içeriyorsa, bir bağıntı kimliği seçerek bir özel durumu hata ayıklamaya başlayabilirsiniz.

  Bkz.

  - [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

  - [İzlenecek yol: IntelliTrace'i Kullanarak SharePoint Uygulamasında Hata Ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Anlık görüntüleri yakalama**

IntelliTrace'i her kesme noktası ve hata ayıklayıcı adımı olayında anlık görüntüleri yakalayan şekilde yapılandırarak. IntelliTrace, her anlık görüntüde tam uygulama durumunu kaydederek karmaşık değişkenleri görüntülemeye ve ifadeleri değerlendirmeye olanak sağlar.

> [!NOTE]
> [IntelliTrace tek başına toplayıcısı](../debugger/using-the-intellitrace-stand-alone-collector.md) anlık görüntüleri yakalamayı desteklemez.

Bkz. [IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme.](../debugger/view-historical-application-state.md)

**İşlev çağrısı bilgilerini toplama**

İşlev çağrı bilgilerini toplamak için IntelliTrace'i yapılandırabilirsiniz. Bu bilgiler çağrı yığını geçmişini görmenizi sağlar ve koddaki çağrılarda geri veya ileri hareket edebilmenize izin verir. Her işlev çağrısı için IntelliTrace bu verileri kaydeder:

- İşlev adı
- İşlev giriş noktalarında parametre olarak gönderilen ve işlev çıkış noktalarında döndürülen temel veri türlerinin değerleri
- Okunduklarında veya değiştirildiklerinde otomatik özelliklerin değerleri
- Birinci düzey alt nesnelerin işaretçileri, ancak değerleri yalnızca boş veya değil şeklinde verilir

> [!NOTE]
> IntelliTrace yalnızca dizilerdeki ilk 256 nesneyi ve dizelerdeki ilk 256 karakteri toplar.

Bkz. [Geçmiş hata ayıklama ile uygulamanızı inceleme.](../debugger/historical-debugging-inspect-app.md)

**Modül bilgilerini toplama**

IntelliTrace'in ne kadar çağrı bilgisi topladığını denetlemek için, yalnızca istediğiniz modülleri belirtin. Bu, koleksiyon sırasında uygulama performansının iyileştirilmesine yardımcı olabilir. [IntelliTrace özelliklerinde IntelliTrace Collects ne kadar](../debugger/intellitrace-features.md#ControlCallData) bilgi toplayanı denetleme bölümüne bakın.

## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a> IntelliTrace uygulamamı yavaşlatacak mı?

Varsayılan olarak, IntelliTrace yalnızca seçili IntelliTrace olaylarının verilerini toplar. Bu, kodunuzun yapısına ve kuruluşuna bağlı olarak, uygulamalarınızı yavaşlatabilir veya yavaşlatmayabilirsiniz. Örneğin, IntelliTrace bir olayı sık sık kaydedlıyorsa, bu durum uygulamanızı yavaşlatabilirsiniz. Ayrıca, uygulamalarınızı yeniden düzenlemeyi de göz önünde bulundurabilirsiniz.

Çağrı bilgilerini toplamak, uygulamalarınızı önemli ölçüde yavaşlatabilir. Diske kaydettiğiniz IntelliTrace herhangi bir günlük dosyasının (.iTrace dosyaları) boyutunu da artırabilir. Bu etkileri en aza indirmek için yalnızca ilginiz dahilinde olan modüller için çağrı bilgilerini toplayın.  .iTrace dosyalarınızın en büyük boyutunu değiştirmek için Araçlar **,** Seçenekler **,** **IntelliTrace**, Gelişmiş 'e **gidin.**

### <a name="blogs"></a>Bloglar

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Forumlar

[Visual Studio Tanılama](https://social.msdn.microsoft.com/Forums/en-US/home)