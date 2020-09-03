---
title: IntelliTrace | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4cbe14e1bf8c3a5e010e3c9e887a208b7e045b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85536519"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>Visual Studio Enterprise için IntelliTrace (C#, Visual Basic, C++)

Kodunuzun yürütme geçmişini kaydetmek ve izlemek için IntelliTrace 'i kullandığınızda uygulamanızda hata ayıklamaya daha az zaman ayırabilirsiniz. IntelliTrace size izin sağladığından hataları kolayca bulabilirsiniz:

- Belirli olayları kaydetme

- Hata ayıklayıcı olayları sırasında ilgili kodu, **Yerel öğeler** penceresinde görünen verileri ve işlev çağrısı bilgilerini inceleyin

- Yeniden oluşturulması zor olan veya dağıtımda gerçekleşen hatalarda hata ayıkla

IntelliTrace 'i Visual Studio Enterprise sürümünde (ancak Professional veya Community sürümlerinde kullanamazsınız) kullanabilirsiniz.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

|Senaryo|Başlık|
|-|-|
|**IntelliTrace ile uygulamamda hata ayıkla:**<br /><br /> -Geçmiş olayları göster.<br />-Geçmiş olaylarla çağrı bilgilerini göster.<br />-IntelliTrace Oturumumu Kaydet.<br />-IntelliTrace 'in topladığı verileri kontrol edin.|- [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md)<br />- [İzlenecek yol: IntelliTrace kullanma](../debugger/walkthrough-using-intellitrace.md)<br />- [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)<br />- [Geçmiş hata ayıklama](../debugger/historical-debugging.md)|
|**Dağıtılan uygulamalardan IntelliTrace verileri toplama**|- [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**IntelliTrace günlük dosyasından (. iTrace dosyası) hata ayıklamayı Başlat.**|- [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)|

## <a name="what-apps-can-i-debug-with-intellitrace"></a><a name="IntelliTraceSupport"></a> IntelliTrace ile hangi uygulamalarda hata ayıklayabilirim?

| Destek düzeyi| Uygulama türleri |
|---------------------| - |
| **Tam destek** | -Visual Basic ve .NET Framework 2,0 veya daha yüksek sürümleri kullanan Visual C# uygulamaları.<br/>ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Iş akışı, SharePoint 2010, SharePoint 2013 ve 64 bit uygulamalar dahil olmak üzere çoğu uygulamada hata ayıklaması yapabilirsiniz.<br/>IntelliTrace ile SharePoint uygulamalarında hata ayıklamak için bkz. [Izlenecek yol: IntelliTrace 'ı kullanarak SharePoint uygulamasında hata ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> IntelliTrace ile Microsoft Azure uygulamalarda hata ayıklamak için bkz. [IntelliTrace ve Visual Studio Ile yayımlanan bulut hizmetinde hata ayıklama](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md). |
| **Sınırlı destek** | -Windows 'un hedeflediği C++ uygulamaları IntelliTrace adım geri 'yi kullanarak anlık görüntüleri görüntülemeyi destekler. Yalnızca hata ayıklayıcı ve özel durum olayları desteklenir.<br />-Yerel hata ayıklamada yalnızca belirli olaylar (MVC denetleyicisi, ADO.NET ve HTTPClient olayları) için desteklenen uygulamalar .NET Core ve ASP.NET Core. Tek başına toplayıcı, .NET Core veya ASP.NET Core uygulamaları için desteklenmez.<br />-Deneysel temelinde-F # uygulamaları<br />-Yalnızca olaylar için desteklenen UWP uygulamaları |
| **Desteklenmiyor** | -Diğer diller ve betik<br />-Windows Hizmetleri, Silverlight, Xbox veya Windows mobil uygulamaları |

> [!NOTE]
> Zaten çalışmakta olan bir işlemde hata ayıklamak istiyorsanız, yalnızca IntelliTrace olayları toplayabilirsiniz (çağrı bilgisi yok). Yalnızca yerel makinede 32 bit veya 64 bit işleme ekleyebilirsiniz. İşleme iliştirmadan önce oluşan olaylar toplanmaz.

## <a name="why-debug-with-intellitrace"></a><a name="IntelliTraceVSTraditional"></a> IntelliTrace ile hata ayıklama neden?

Geleneksel veya *canlı* hata ayıklama, geçmiş olaylar hakkında sınırlı verilerle yalnızca uygulamanızın geçerli durumunu gösterir. Bu olayları uygulamanın geçerli durumuna göre çıkarmalıyız ya da uygulamanızı yeniden çalıştırarak bu olayları yeniden oluşturmanız gerekir.

IntelliTrace bu zamanlardaki belirli olayları ve verileri kaydederek bu geleneksel hata ayıklama deneyimini genişletir. Bu, özellikle de hatanın nerede olduğunu gördüğünüzde, uygulamanızı yeniden başlatmadan uygulamanızda ne olduğunu görmenizi sağlar. IntelliTrace geleneksel hata ayıklama işlemi sırasında varsayılan olarak açıktır ve görünmez ve otomatik olarak veri toplar. Bu, geleneksel hata ayıklama ve IntelliTrace hata ayıklama arasında kaydedilen bilgileri görmek için kolayca geçiş yapmanızı sağlar. [IntelliTrace özelliklerine](../debugger/intellitrace-features.md) ve [IntelliTrace 'in hangi verileri toplayacağını görün?](#WhatData)

IntelliTrace yeniden oluşturulması zor olan veya dağıtımda gerçekleşen hataları ayıklamaya da yardımcı olabilir. IntelliTrace verisi toplayabilir ve bir IntelliTrace günlük dosyasına (.iTrace dosyası) kaydedebilirsiniz. Bir .iTrace dosyası özel durumlar, performans olayları, Web istekleri, test verileri, iş parçacıkları, modüller ve diğer sistem bilgileri ile ilgili ayrıntıları içerir. Bu dosyayı Visual Studio Enterprise açabilir, bir öğe seçebilir ve IntelliTrace ile hata ayıklamaya başlayabilirsiniz. Bu, dosyada herhangi bir olaya gitmenizi ve o anda uygulamanız hakkındaki özel ayrıntıları görmenizi sağlar.

Bu kaynaklardan IntelliTrace verisi kaydedebilirsiniz:

- Visual Studio 2015 Enterprise veya sonraki sürümlerinde veya önceki Visual Studio Ultimate sürümlerinde bir IntelliTrace oturumu.

- IIS'de barındırılan ASP.NET web uygulamaları ya da Microsoft Monitoring Agent kullandığınızda dağıtımda tek başına ya da System Center 2012 ile birlikte çalışan SharePoint 2010 ve SharePoint 2013 uygulamaları. Bkz. [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md) ve [Microsoft Monitoring Agent ile izleme](https://technet.microsoft.com/library/dn465153.aspx).

IntelliTrace'in hata ayıklamada yardımcı olması ile ilgili bazı örnekler aşağıdadır:

- Uygulamanız bir veri dosyasını bozdu, ancak bu olayın nerede oluştuğunu bilemezsiniz.

  IntelliTrace olmadan, tüm olası dosya erişimlerini bulmak, bu erişimlerde kesme noktaları koymak ve sorunu nerede meydana geldiğini bulmak için uygulamanızı yeniden çalıştırmanız gerekir. IntelliTrace ile her olay meydana geldiğinde uygulamanız hakkında toplanan dosya erişimi olaylarını ve belirli ayrıntıları görebilirsiniz.

- Bir özel durum gerçekleşir.

  IntelliTrace olmadan, bir özel durum hakkında bir ileti alırsınız ancak özel duruma yol gösteren olaylar hakkında çok fazla bilgiye sahip değilsiniz. Özel duruma yol eden çağrıların zincirini görmek için çağrı yığınını inceleyebilirsiniz ancak bu çağrılar sırasında gerçekleşen olayların sırasını göremezsiniz. IntelliTrace ile özel durumdan önce meydana gelen olayları inceleyebilirsiniz.

- Dağıtılan bir uygulamada hata veya kilitlenme oluşur.

  Microsoft Azure tabanlı uygulamalarda, uygulamayı yayımlamadan önce IntelliTrace veri toplamayı yapılandırabilirsiniz. Uygulamanız çalışırken, IntelliTrace verileri bir. iTrace dosyasına kaydeder. Bkz. [IntelliTrace ve Visual Studio Ile yayınlanmış bir bulut hizmetinde hata ayıklama](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).

  IIS 7.0, 7.5 ve 8.0'da barındırılan ASP.NET web uygulamaları ve SharePoint 2010 ya da SharePoint 2013 uygulamalarında, IntelliTrace verisini bir .iTrace dosyasına kaydetmek için Microsoft İzleme Aracısı'nı tek başına ya da System Center 2012 ile birlikte kullanın.

  Bu, dağıtımdaki uygulamalarla ilgili sorunları tanılamak istediğinizde kullanışlıdır. Bkz. [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="what-data-does-intellitrace-collect"></a><a name="WhatData"></a> IntelliTrace hangi verileri toplar?

**Olay bilgilerini topla**

Varsayılan olarak, IntelliTrace yalnızca IntelliTrace olaylarını kaydeder: hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve hata ayıklamanıza yardımcı olabilecek diğer sistem olayları. Hata ayıklayıcı olayları ve her zaman toplanan özel durumlar dışında toplamak istediğiniz IntelliTrace olaylarının türlerini seçebilirsiniz. [IntelliTrace özelliklerine](../debugger/intellitrace-features.md)bakın.

- **Hata ayıklayıcı olayları**

  IntelliTrace her zaman Visual Studio hata ayıklayıcıda gerçekleşen olayları kaydeder. Örneğin, uygulamanızı başlatmak bir hata ayıklayıcı olayıdır. Diğer hata ayıklayıcı olayları, uygulamanızın yürütmeyi kesmesine neden olan olayları durduruyor. Örneğin, programınız bir kesme noktasına rastlayın, bir izleme noktası arar veya bir **adım** komutu yürütür.

  Varsayılan olarak, performans sağlamaya yardımcı olmak için IntelliTrace bir hata ayıklayıcı olayı için olası her değeri kaydetmez. Bunun yerine, bu değerleri kaydeder:

  - **Yereller** penceresindeki değerler. Bu değerleri görmek için **Yerel öğeler** penceresini açık tutun.

  - Yalnızca **oto** penceresi açıksa, **oto** penceresindeki değerler

  - Kaynak penceresinde değerini görmek için bir değişkenin üzerine fare işaretçisini getirdiğinizde görüntülenen DataTips değerleri. IntelliTrace sabitlenmiş DataTips değerlerini toplamaz.

    IntelliTrace olayları ve anlık görüntü modu etkinleştirildiğinde, IntelliTrace her hata ayıklayıcı **kesme noktası** ve **adım** olayında uygulamanın işleminin anlık görüntüsünü alır. Bu işlem, Windows 'un açık olup olmamasına bakılmaksızın **Yereller**, **oto**ve pencereleri **izlemek** için değerleri kaydeder. Sabitlenmiş veri ipuçlarında bulunan değerler de toplanacak.

- **Özel durumlar**

  IntelliTrace özel durum türünü ve iletisini bu tür özel durumlar için kaydeder:

  - Özel durumun ortaya çıktığı ve yakalandığı yönetilen özel durumlar

  - İşlenmeyen özel durumlar

- **.NET Framework olaylar**

  Varsayılan olarak, IntelliTrace en sık görülen .NET Framework olaylarını kaydeder. Örneğin, bir olay için <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> IntelliTrace onay kutusunun durumunu ve metnini toplar.

- **SharePoint 2010 ve SharePoint 2013 uygulama olayları**

  Kullanıcı profili olayları ve SharePoint 2010 ile Visual Studio dışında çalışan 2013 uygulamaları için birleşik Günlük Kaydetme Sistemi (ULS) olaylarının alt kümesini kaydedebilirsiniz. Bu olayları bir .iTrace dosyasına kaydedebilirsiniz. Visual Studio Enterprise 2015 veya sonraki sürümleri, önceki bir Visual Studio Ultimate sürümü veya **izleme** modunda çalışan [Microsoft Monitoring Agent](https://www.microsoft.com/download/details.aspx?id=40316) gerektirir.

  .iTrace dosyasını açtığınızda, eşleşen web isteğini bulmak için bir SharePoint bağıntı kimliği girin, kayıtlı olayları görüntüleyin ve belirli bir olaydan hata ayıklamaya başlayın. Dosya işlenmeyen özel durumlar içeriyorsa, bir bağıntı kimliği seçerek bir özel durumu hata ayıklamaya başlayabilirsiniz.

  Bkz.

  - [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)

  - [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

  - [İzlenecek yol: IntelliTrace'i Kullanarak SharePoint Uygulamasında Hata Ayıklama](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Anlık görüntüleri yakala**

IntelliTrace 'i, her kesme noktasında ve hata ayıklayıcı adım olayında anlık görüntüleri yakalamak üzere yapılandırabilirsiniz. IntelliTrace, her anlık görüntüde tam uygulama durumunu kaydeder ve bu da karmaşık değişkenleri görüntülemenize ve ifadeleri değerlendirmenize olanak tanır.

> [!NOTE]
> [IntelliTrace tek başına toplayıcısı](../debugger/using-the-intellitrace-stand-alone-collector.md) , anlık görüntüleri yakalamayı desteklemez.

Bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md).

**İşlev çağrı bilgilerini topla**

İşlev çağrı bilgilerini toplamak için IntelliTrace'i yapılandırabilirsiniz. Bu bilgiler çağrı yığını geçmişini görmenizi sağlar ve koddaki çağrılarda geri veya ileri hareket edebilmenize izin verir. Her işlev çağrısı için IntelliTrace bu verileri kaydeder:

- İşlev adı
- İşlev giriş noktalarında parametre olarak gönderilen ve işlev çıkış noktalarında döndürülen temel veri türlerinin değerleri
- Okunduklarında veya değiştirildiklerinde otomatik özelliklerin değerleri
- Birinci düzey alt nesnelerin işaretçileri, ancak değerleri yalnızca boş veya değil şeklinde verilir

> [!NOTE]
> IntelliTrace yalnızca dizilerdeki ilk 256 nesneyi ve dizelerdeki ilk 256 karakteri toplar.

Bkz. [geçmiş hata ayıklama ile uygulamanızı İnceleme](../debugger/historical-debugging-inspect-app.md).

**Modül bilgilerini topla**

IntelliTrace'in ne kadar çağrı bilgisi topladığını denetlemek için, yalnızca istediğiniz modülleri belirtin. Bu, koleksiyon sırasında uygulamanızın performansını artırmaya yardımcı olabilir. IntelliTrace özelliklerinde [ne kadar bilgi IntelliTrace 'In topladığı](../debugger/intellitrace-features.md#ControlCallData) bölümüne bakın.

## <a name="will-intellitrace-slow-down-my-application"></a><a name="AffectPerformance"></a> IntelliTrace uygulamamı yavaşlatacak mı?

Varsayılan olarak, IntelliTrace yalnızca seçili IntelliTrace olaylarının verilerini toplar. Bu, kodunuzun yapısına ve kuruluşuna bağlı olarak uygulamanızı yavaşlatabilecek ya da yavaşlatmayabilir. Örneğin, IntelliTrace bir olayı sıklıkla kaydediyorsa, bu durum uygulamanızı yavaşlatabilir. Uygulamanızı yeniden düzenlemeyi de düşünebilirsiniz.

Çağrı bilgilerinin toplanması uygulamanızı önemli ölçüde yavaşlatabilir. Diske kaydettiğiniz IntelliTrace herhangi bir günlük dosyasının (.iTrace dosyaları) boyutunu da artırabilir. Bu etkileri en aza indirmek için yalnızca ilginiz dahilinde olan modüller için çağrı bilgilerini toplayın.  . İTrace dosyalarınızın en büyük boyutunu değiştirmek için **Araçlar**, **Seçenekler**, **IntelliTrace**, **Gelişmiş**öğesine gidin.

### <a name="blogs"></a>Bloglar

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Forumlar

[Visual Studio tanılama](https://social.msdn.microsoft.com/Forums/en-US/home)
