---
title: IntelliTrace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db7430d03bbce065b75e890736253c6ba05752d0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298928"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konunun en son sürümü [IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) 'de bulunabilir.  
  
Kodunuzun yürütme geçmişini kaydetmek ve izlemek için IntelliTrace 'i kullandığınızda uygulamanızda hata ayıklamaya daha az zaman ayırabilirsiniz. IntelliTrace size izin sağladığından hataları kolayca bulabilirsiniz:  
  
- Belirli olayları kaydetme  
  
   Hata ayıklayıcı olayları sırasında ilgili kodu, **Yerel öğeler** penceresinde görünen verileri ve işlev çağrısı bilgilerini inceleyin  
  
- Yeniden oluşturulması zor olan veya dağıtımda gerçekleşen hatalarda hata ayıkla  
  
  IntelliTrace 'i Visual Studio Enterprise sürümünde (ancak Professional veya Community sürümlerinde kullanamazsınız) kullanabilirsiniz.  
  
## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?  
  
|||  
|-|-|  
|**IntelliTrace ile uygulamamda hata ayıkla:**<br /><br /> -Geçmiş olayları göster.<br />-Geçmiş olaylarla çağrı bilgilerini göster.<br />-IntelliTrace Oturumumu Kaydet.<br />-IntelliTrace 'in topladığı verileri kontrol edin.|-   [Izlenecek yol: IntelliTrace kullanma](../debugger/walkthrough-using-intellitrace.md)<br />     [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)<br />-   [IntelliTrace yapılandırma](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [geçmiş hata ayıklama](../debugger/historical-debugging.md)|  
|**Test Yöneticisi bir test oturumu sırasında IntelliTrace verisi topla**|[el ile testlerde daha fazla tanılama verisi toplama](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) -   |  
|**Dağıtılan uygulamalardan IntelliTrace verileri toplama**|[IntelliTrace tek başına toplayıcıyı kullanarak](../debugger/using-the-intellitrace-stand-alone-collector.md) -   |  
|**IntelliTrace günlük dosyasından (. iTrace dosyası) hata ayıklamayı Başlat.**|[kaydedilen IntelliTrace verilerini kullanarak](../debugger/using-saved-intellitrace-data.md) -   |  
  
## <a name="IntelliTraceSupport"></a>IntelliTrace ile hangi uygulamalarda hata ayıklayabilirim?  
  
|||  
|-|-|  
|**Destek**|-Visual Basic ve .NET Framework C# 2,0 veya daha yüksek sürümleri kullanan görsel uygulamalar.<br />     ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Iş akışı, SharePoint 2010, SharePoint 2013 ve 64 bit uygulamalar dahil olmak üzere çoğu uygulamada hata ayıklaması yapabilirsiniz.<br />     IntelliTrace ile SharePoint uygulamalarında hata ayıklamak için bkz. [Izlenecek yol: IntelliTrace 'ı kullanarak SharePoint uygulamasında hata ayıklama](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     IntelliTrace ile Microsoft Azure uygulamalarda hata ayıklamak için bkz. [IntelliTrace ve Visual Studio Ile yayımlanan bulut hizmetinde hata ayıklama](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).|  
|**Sınırlı destek**|- F# deneysel tabanlı uygulamalar<br />-Yalnızca olaylar için desteklenen Windows Mağazası uygulamaları|  
|**Desteklenmiyor**|- C++, diğer diller ve betik<br />-Windows Hizmetleri, Silverlight, Xbox veya [!INCLUDE[winmobile](../includes/winmobile-md.md)] uygulamaları|  
  
> [!NOTE]
> Zaten çalışan bir işlemde hata ayıklamak istiyorsanız, IntelliTrace kullanamazsınız. IntelliTrace'i işlem başladığında başlatmanız gerekir.  
  
## <a name="IntelliTraceVSTraditional"></a>IntelliTrace ile hata ayıklama neden?  
 Geleneksel veya *canlı* hata ayıklama, geçmiş olaylar hakkında sınırlı verilerle yalnızca uygulamanızın geçerli durumunu gösterir. Bu olayları uygulamanın geçerli durumuna göre çıkarmalıyız ya da uygulamanızı yeniden çalıştırarak bu olayları yeniden oluşturmanız gerekir.  
  
 IntelliTrace bu zamanlardaki belirli olayları ve verileri kaydederek bu geleneksel hata ayıklama deneyimini genişletir. Bu, özellikle de hatanın nerede olduğunu gördüğünüzde, uygulamanızı yeniden başlatmadan uygulamanızda ne olduğunu görmenizi sağlar. IntelliTrace geleneksel hata ayıklama işlemi sırasında varsayılan olarak açıktır ve görünmez ve otomatik olarak veri toplar. Bu, geleneksel hata ayıklama ve IntelliTrace hata ayıklama arasında kaydedilen bilgileri görmek için kolayca geçiş yapmanızı sağlar. [IntelliTrace özelliklerine](../debugger/intellitrace-features.md) ve [IntelliTrace 'in hangi verileri toplayacağını görün?](#WhatData)  
  
 IntelliTrace yeniden oluşturulması zor olan veya dağıtımda gerçekleşen hataları ayıklamaya da yardımcı olabilir. IntelliTrace verisi toplayabilir ve bir IntelliTrace günlük dosyasına (.iTrace dosyası) kaydedebilirsiniz. Bir .iTrace dosyası özel durumlar, performans olayları, Web istekleri, test verileri, iş parçacıkları, modüller ve diğer sistem bilgileri ile ilgili ayrıntıları içerir. Bu dosyayı Visual Studio Enterprise açabilir, bir öğe seçebilir ve IntelliTrace ile hata ayıklamaya başlayabilirsiniz. Bu, dosyada herhangi bir olaya gitmenizi ve o anda uygulamanız hakkındaki özel ayrıntıları görmenizi sağlar.  
  
 Bu kaynaklardan IntelliTrace verisi kaydedebilirsiniz:  
  
- Visual Studio 2015 Enterprise veya önceki Visual Studio Ultimate sürümlerindeki IntelliTrace oturumu.  
  
- Microsoft Test Yöneticisi bir test oturumu  
  
- IIS'de barındırılan ASP.NET web uygulamaları ya da Microsoft Monitoring Agent kullandığınızda dağıtımda tek başına ya da System Center 2012 ile birlikte çalışan SharePoint 2010 ve SharePoint 2013 uygulamaları. Bkz. [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md) ve [Microsoft Monitoring Agent ile izleme](https://technet.microsoft.com/library/dn465153.aspx).  
  
  IntelliTrace'in hata ayıklamada yardımcı olması ile ilgili bazı örnekler aşağıdadır:  
  
- Uygulamanız bir veri dosyasını bozdu, ancak bu olayın nerede oluştuğunu bilemezsiniz.  
  
   IntelliTrace olmadan, tüm olası dosya erişimlerini bulmak, bu erişimlerde kesme noktaları koymak ve sorunu nerede meydana geldiğini bulmak için uygulamanızı yeniden çalıştırmanız gerekir. IntelliTrace ile her olay meydana geldiğinde uygulamanız hakkında toplanan dosya erişimi olaylarını ve belirli ayrıntıları görebilirsiniz.  
  
- Bir özel durum gerçekleşir.  
  
   IntelliTrace olmadan, bir özel durum hakkında bir ileti alırsınız ama özel duruma yol açan olaylar hakkında fazla bilgi almazsınız. Özel duruma yol açan çağrı zincirini görmek için çağrı yığınını inceleyebilirsiniz ancak bu çağrılar sırasında gerçekleşen olayların sırasını göremezsiniz. IntelliTrace ile özel durumdan önce meydana gelen olayları inceleyebilirsiniz.  
  
- Uygulamanız bir sınama bilgisayarında kilitleniyor, ancak bir geliştirme bilgisayarında başarıyla çalışıyor.  
  
   Microsoft Test Yöneticisi'nden IntelliTrace verisi toplayabilir, verileri .iTrace dosyasına kaydedebilir ve bu dosyayı daha sonra incelemek için Team Foundation Server çalışma öğesine ekleyebilirsiniz. Bkz. [el ile testlerde daha fazla tanılama verisi toplama](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) ve [kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md).  
  
- Dağıtılan bir uygulamada hata veya kilitlenme oluşur.  
  
   Microsoft Azure tabanlı uygulamalarda, uygulamayı yayımlamadan önce IntelliTrace veri toplamayı yapılandırabilirsiniz. Uygulamanız çalışırken, IntelliTrace verileri bir. iTrace dosyasına kaydeder. Bkz. [IntelliTrace ve Visual Studio Ile yayınlanmış bir bulut hizmetinde hata ayıklama](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).  
  
   IIS 7.0, 7.5 ve 8.0'da barındırılan ASP.NET web uygulamaları ve SharePoint 2010 ya da SharePoint 2013 uygulamalarında, IntelliTrace verisini bir .iTrace dosyasına kaydetmek için Microsoft İzleme Aracısı'nı tek başına ya da System Center 2012 ile birlikte kullanın.  
  
   Bu, dağıtımdaki uygulamalarla ilgili sorunları tanılamak istediğinizde kullanışlıdır. Bkz. [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## <a name="WhatData"></a>IntelliTrace hangi verileri toplar?  
 **Olay bilgilerini toplama**  
  
 Varsayılan olarak, IntelliTrace yalnızca IntelliTrace olaylarını kaydeder: hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve hata ayıklamanıza yardımcı olabilecek diğer sistem olayları. Hata ayıklayıcı olayları ve her zaman toplanan özel durumlar dışında toplamak istediğiniz IntelliTrace olaylarının türlerini seçebilirsiniz. Bkz. [IntelliTrace 'ı yapılandırma](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Hata ayıklayıcı olayları**  
  
   IntelliTrace her zaman Visual Studio hata ayıklayıcıda gerçekleşen olayları kaydeder. Örneğin, uygulamanızı başlatmak bir hata ayıklayıcı olayıdır. Diğer hata ayıklayıcı olayları, uygulamanızın yürütmeyi kesmesine neden olan olayları durduruyor. Örneğin, programınız bir kesme noktasına rastlayın, bir izleme noktası arar veya bir **adım** komutu yürütür.  
  
   IntelliTrace, performansa yardımcı olmak için bir hata ayıklayıcı olayında olası her değeri kaydetmez. Bunun yerine, bu değerleri kaydeder:  
  
  - **Yereller** penceresindeki değerler. Bu değerleri görmek için **Yerel öğeler** penceresini açık tutun.  
  
  - Yalnızca **oto** penceresi açıksa, **oto** penceresindeki değerler  
  
  - Kaynak penceresinde değerini görmek için bir değişkenin üzerine fare işaretçisini getirdiğinizde görüntülenen DataTips değerleri. IntelliTrace sabitlenmiş DataTips değerlerini toplamaz.  
  
- **Özel Durumlar**  
  
   IntelliTrace özel durum türünü ve iletisini bu tür özel durumlar için kaydeder:  
  
  - Özel durumun ortaya çıktığı ve yakalandığı yönetilen özel durumlar  
  
  - Yönetilmeyen özel durumlar  
  
- **.NET Framework olaylar**  
  
   Varsayılan olarak, IntelliTrace en sık görülen .NET Framework olaylarını kaydeder. Örneğin:  
  
  - Bir dosya erişim olayında IntelliTrace dosya adını toplar.  
  
  - Bir Onay Kutusu Denetimi olayında IntelliTrace onay kutusunun durumunu ve metnini toplar.  
  
- **SharePoint 2010 ve SharePoint 2013 uygulama olayları**  
  
   Kullanıcı profili olayları ve SharePoint 2010 ile Visual Studio dışında çalışan 2013 uygulamaları için birleşik Günlük Kaydetme Sistemi (ULS) olaylarının alt kümesini kaydedebilirsiniz. Bu olayları bir .iTrace dosyasına kaydedebilirsiniz. Visual Studio Enterprise 2015, önceki bir Visual Studio Ultimate sürümü veya **izleme** modunda çalışan [Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkId=320384) gerektirir.  
  
   .iTrace dosyasını açtığınızda, eşleşen web isteğini bulmak için bir SharePoint bağıntı kimliği girin, kayıtlı olayları görüntüleyin ve belirli bir olaydan hata ayıklamaya başlayın. Dosya işlenmeyen özel durumlar içeriyorsa, bir bağıntı kimliği seçerek bir özel durumu hata ayıklamaya başlayabilirsiniz.  
  
   Bkz.  
  
  - [IntelliTrace tek başına toplayıcısını kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  - [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)  
  
  - [İzlenecek yol: IntelliTrace'i Kullanarak SharePoint Uygulamasında Hata Ayıklama](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **İşlev çağrısı bilgilerini toplama**  
  
  İşlev çağrı bilgilerini toplamak için IntelliTrace'i yapılandırabilirsiniz. Bu bilgiler çağrı yığını geçmişini görmenizi sağlar ve koddaki çağrılarda geri veya ileri hareket edebilmenize izin verir. Her işlev çağrısı için IntelliTrace bu verileri kaydeder:  
  
- İşlev adı  
  
- İşlev giriş noktalarında parametre olarak gönderilen ve işlev çıkış noktalarında döndürülen temel veri türlerinin değerleri  
  
- Okunduklarında veya değiştirildiklerinde otomatik özelliklerin değerleri  
  
- Birinci düzey alt nesnelerin işaretçileri, ancak değerleri yalnızca boş veya değil şeklinde verilir  
  
> [!NOTE]
> IntelliTrace yalnızca dizilerdeki ilk 256 nesneyi ve dizelerdeki ilk 256 karakteri toplar.  
  
 Bkz. [IntelliTrace 'ı yapılandırma](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Modül bilgilerini toplama**  
  
 IntelliTrace'in ne kadar çağrı bilgisi topladığını denetlemek için, yalnızca istediğiniz modülleri belirtin. Bu, koleksiyon sırasında uygulamanızın performansını artırmaya yardımcı olabilir. Bkz. [IntelliTrace 'ı yapılandırma](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="AffectPerformance"></a>IntelliTrace uygulamamı yavaşlatacak mı?  
 Varsayılan olarak, IntelliTrace yalnızca seçili IntelliTrace olaylarının verilerini toplar. Bu, kodunuzun yapısına ve kuruluşuna bağlı olarak uygulamanızı yavaşlatabilecek ya da yavaşlatmayabilir. Örneğin, IntelliTrace bir olayı sıklıkla kaydediyorsa, bu durum uygulamanızı yavaşlatabilir. Uygulamanızı yeniden düzenlemeyi de düşünebilirsiniz.  
  
 Çağrı bilgilerinin toplanması uygulamanızı önemli ölçüde yavaşlatabilir. Diske kaydettiğiniz IntelliTrace herhangi bir günlük dosyasının (.iTrace dosyaları) boyutunu da artırabilir. Bu etkileri en aza indirmek için yalnızca ilginiz dahilinde olan modüller için çağrı bilgilerini toplayın.  . İTrace dosyalarınızın en büyük boyutunu değiştirmek için **Araçlar**, **Seçenekler**, **IntelliTrace**, **Gelişmiş**öğesine gidin. Bkz. [IntelliTrace 'ı yapılandırma](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>Bu bölümde  
 [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)  
  
 [IntelliTrace 'i yapılandırma](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Yeniden oluşturulması zor olan hatalarla tanılama Izleme verilerini dahil etme](https://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md)  
  
 [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Bloglar  
 [Visual Studio ALM + Team Foundation Server](https://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Forumlar  
 [Visual Studio tanılama](https://go.microsoft.com/fwlink/?LinkId=262263)
