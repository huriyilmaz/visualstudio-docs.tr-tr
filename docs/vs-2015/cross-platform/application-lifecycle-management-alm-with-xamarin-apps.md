---
title: Xamarin uygulamalarıyla uygulama yaşam döngüsü yönetimi (ALM) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: 1a0ea4f611c5312331fa0e2f2f467b4189778f30
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300034"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Xamarin uygulamalarıyla Uygulama Yaşam Döngüsü Yönetimi (ALM)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin, .net ve Visual Studio kullanarak C#Android, IOS ve Windows 'u hedefleyen platformlar arası mobil uygulamalar oluşturmanıza olanak sağlar. Xamarin, büyük bir kod bölümünün platformlar arasında paylaşılmasını sağlar ve yalnızca platforma özgü olması gereken küçük bir yüzdedir. Xamarin 'in kendisi hakkında daha fazla bilgi için bkz. [Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Modern platformlar için uygulama geliştirme, yalnızca koddan çok daha fazla etkinlik içerir. DevOps (geliştirme + işlemler) olarak adlandırılan bu etkinlikler, uygulamanın tamamlanma yaşam döngüsünü yayın ve planlama ve izleme işi, kod tasarlama ve uygulama, bir kaynak kodu deposunu yönetme, yapıları çalıştırma, sürekli tümleştirmeler yönetme ve dağıtımlar, test (birim testleri ve UI testleri dahil), hem geliştirme hem de üretim ortamlarında çeşitli tanılama biçimlerini çalıştırıp uygulama performansını ve kullanıcı davranışlarını telemetri ve analiz aracılığıyla gerçek zamanlı olarak izleyin.  
  
 Visual Studio Team Services ve Team Foundation Server ile birlikte Visual Studio, uygulama yaşam döngüsü yönetimi veya ALM olarak da adlandırılan çeşitli DevOps özellikleri sağlar. Bunların birçoğu platformlar arası projelere uygulanabilir.  
  
 Bu, özellikle de bazı ALM araçlarının oluşturulduğu ve .NET ile C# oluşturulduğundan Xamarin uygulamalarıyla doğru bir şekilde geçerlidir. Diğer araçlar, derleme ve çalışma zamanı ortamları ile sıkı tümleştirme gerektirir. Xamarin uygulamaları Windows dışı platformlarda çalıştığı ve .NET 'in mono uygulamasını kullandığından, Xamarin belirli gereksinimler için özelleştirilmiş araçlar sağlar.  
  
 Aşağıdaki tablolarda, Xamarin projesiyle hangi Visual Studio ALM özelliklerinin düzgün çalıştığını ve hangilerinin sınırlamaları olduğunu tanımlanmaktadır. Özelliklerin kendileri hakkındaki ayrıntılar için bağlantılı belgelere başvurun.  
  
## <a name="agile-tools"></a>Çevik Araçlar  
 Başvuru bağlantısı: **[iş](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (Team Explorer Everywhere dahil VISUAL STUDIO Team SERVICES veya TFS kullanarak)  
  
 Genel Açıklama: tüm planlama ve izleme özellikleri proje türü ve kodlama dillerinden bağımsızdır.  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Biriktirme listeleri ve Sprint 'leri yönetme|Evet||  
|Çalışma izleme|Evet||  
|Takım odası işbirliği|Evet||  
|Kanban panoları|Evet||  
|İlerlemeyi raporla ve görselleştirin|Evet||  
  
## <a name="modeling"></a>Modelleme  
 Başvuru bağlantısı:  **[mimari çözümleme ve modelleme](../modeling/analyze-and-model-your-architecture.md)**  
  
 Tasarım özellikleri kodlama dilinden bağımsızdır veya gibi C#.NET dilleri ile birlikte çalışır. Kod ile ilgili hangi yönleri öğrenmek için [yazılım geliştirmede mimari ve modelleme şemaları rollerine](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) bakın.  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Sıralı diyagramlar|Evet||  
|Bağımlılık grafikleri|Evet||  
|Çağrı hiyerarşisi|Evet||  
|Sınıf Tasarımcısı|Evet||  
|Mimari Gezgini|Evet||  
|UML diyagramları (kullanım örneği, etkinlik, sınıf, bileşen, dizi ve DSL)|Evet||  
|Katman diyagramları|Evet||  
|Katman doğrulama|Evet||  
  
## <a name="code"></a>Kod  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|[Team Foundation sürüm denetimi](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) veya Visual Studio Team Services kullanın|Evet||  
|[Team Services 'da git 'i kullanmaya başlama](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Evet||  
|[Kod Analizi/kod kalitesini geliştirme (başvurular, önerilen değişiklikler vb.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Evet||  
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Evet|Uygulamanın çalışma zamanına kadar çözümlenmediği platforma özgü sınırlar haricinde.|  
|[Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Evet||  
  
## <a name="build"></a>Derleme  
 Başvuru bağlantısı:  **[derleme](/azure/devops/pipelines/index)**  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Şirket içi TFS sunucusu|Evet|Derleme makinelerinde Xamarin yüklü olmalıdır ve iOS için derlemek üzere bir OSX bilgisayarına bağlanabilir. Bkz. [Xamarin IÇIN TFS 'Yi yapılandırma](https://docs.microsoft.com/azure/devops/repos/tfvc/overview?view=azure-devops) (Xamarin Web sitesi)|  
|Visual Studio Team Services bağlı şirket içi derleme sunucusu|Evet|Yönergeler için bkz. [yapı sunucusu](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) .|  
|Visual Studio Team Services barındırılan denetleyici hizmeti|Evet|Bkz. [Xamarin uygulamanızı oluşturma](https://www.visualstudio.com/docs/build/apps/mobile/xamarin).|  
|Ön ve son betiklerle derleme tanımları|Evet||  
|Geçitli iadeler dahil sürekli tümleştirme|Evet|TFVC için geçitli iadeler, yalnızca git, iadeler yerine bir çekme isteği modelinde çalışmaktadır.|  
  
## <a name="testing"></a>Sınama  
 Başvuru bağlantısı:  **[uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Testleri planlama, test çalışmaları oluşturma ve test paketlerini düzenleme|Evet||  
|El ile test|Evet||  
|Test Yöneticisi (kaydı ve kayıttan yürütme testleri)|Evet|Windows cihazları ve Android öykünücüleri yalnızca Visual Studio 'dan. Tüm cihazlar için kayıt, [Xamarin test kaydedicisi](https://www.xamarin.com/test-cloud/recorder)ile mümkündür.|  
|Kod kapsamı|yok||  
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Evet|Windows ve Android hedefleri için yerleşik MSTest araçları kullanılabilir. Windows, Android ve iOS 'da birim testlerini çalıştırmak için Xamarin NUnit önerir. Bkz. [Xamarin IÇIN TFS 'Yi yapılandırma](https://docs.microsoft.com/azure/devops/repos/tfvc/overview?view=azure-devops) (Xamarin Web sitesi).|  
|[Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)|Yalnızca Windows|Visual Studio 'nun UI test kaydedicisi yalnızca Windows. Tüm platformlar için bkz. [Xamarin test kaydedicisi](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Kod kalitesini geliştirme  
 Başvuru bağlantısı:  **[kod kalitesini geliştirme](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|[Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Evet||  
|[Kod kopyası algılamayı kullanarak yinelenen kodu bulma](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Evet||  
|[Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Evet||  
|[Performans Gezgini](../profiling/performance-explorer.md)|Hayır|Bunun yerine Xamarin Studio [Xamarin Profiler](https://docs.microsoft.com/xamarin/cross-platform/deploy-test/) kullanın. Xamarin Profiler Şu anda önizleme aşamasındadır ve henüz Windows hedefleri için çalışmadığına bakın.|  
|[.NET Framework bellek sorunlarını analiz etme](../misc/analyze-dotnet-framework-memory-issues.md)|Hayır|Visual Studio Araçları, profil oluşturma için mono Framework 'e kancalar içermez.|  
  
## <a name="release-management"></a>Yayın yönetimi  
 Başvuru bağlantısı:  **[Release Management Ile dağıtımları otomatikleştirin](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Yayın süreçlerini yönetme|Evet||  
|Betikler aracılığıyla dışarıdan yükleme için sunuculara dağıtım|Evet||  
|App Store 'a yükle|Kısmi|Bazı uygulama mağazalarında bu işlemi otomatik hale getirebilen uzantılar vardır.  [Visual Studio Team Services Için uzantılara](https://marketplace.visualstudio.com/VSTS)bakın; Örneğin, [Google Play için uzantı](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>HockeyApp ile izleme  
 Başvuru bağlantısı:  **[HockeyApp ile izleme](https://www.hockeyapp.net/features/)**  
  
|Özellik|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Kilitlenme Analizi, telemetri ve Beta dağıtımı|Evet||
