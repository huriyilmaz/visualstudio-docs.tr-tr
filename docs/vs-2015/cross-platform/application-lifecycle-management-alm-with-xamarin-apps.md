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
ms.openlocfilehash: 37c855f7940cbed847dcb7d5c6414be436cee993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918370"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Xamarin uygulamalarıyla Uygulama Yaşam Döngüsü Yönetimi (ALM)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin, C#, .NET ve Visual Studio kullanarak Android, iOS ve Windows 'u hedefleyen platformlar arası mobil uygulamalar oluşturmanıza olanak sağlar. Xamarin, büyük bir kod bölümünün platformlar arasında paylaşılmasını sağlar ve yalnızca platforma özgü olması gereken küçük bir yüzdedir. Xamarin 'in kendisi hakkında daha fazla bilgi için bkz. [Visual Studio ve Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Modern platformlar için uygulama geliştirme, yalnızca koddan çok daha fazla etkinlik içerir. DevOps (geliştirme + işlemler) olarak adlandırılan bu etkinlikler, uygulamanın tamamlanma yaşam döngüsünü yayın ve iş planlama ve izleme, kod tasarlama ve uygulama, bir kaynak kodu deposunu yönetme, derleme çalıştırma, sürekli tümleştirmeler ve dağıtımları yönetme, test (birim testleri ve kullanıcı ARABIRIMI testleri dahil), her iki geliştirme ve üretim ortamında çeşitli tanılama biçimlerini çalıştırma, hem geliştirme hem de üretim ortamlarında gerçek zamanlı tanılama ve kullanıcı davranışlarını izleme.  
  
 Visual Studio Team Services ve Team Foundation Server ile birlikte Visual Studio, uygulama yaşam döngüsü yönetimi veya ALM olarak da adlandırılan çeşitli DevOps özellikleri sağlar. Bunların birçoğu platformlar arası projelere uygulanabilir.  
  
 Bu, özellikle de bazı ALM araçlarının oluşturulduğu C# ve .NET ile oluşturulduğundan Xamarin uygulamalarıyla doğru bir şekilde geçerlidir. Diğer araçlar, derleme ve çalışma zamanı ortamları ile sıkı tümleştirme gerektirir. Xamarin uygulamaları Windows dışı platformlarda çalıştığı ve .NET 'in mono uygulamasını kullandığından, Xamarin belirli gereksinimler için özelleştirilmiş araçlar sağlar.  
  
 Aşağıdaki tablolarda, Xamarin projesiyle hangi Visual Studio ALM özelliklerinin düzgün çalıştığını ve hangilerinin sınırlamaları olduğunu tanımlanmaktadır. Özelliklerin kendileri hakkındaki ayrıntılar için bağlantılı belgelere başvurun.  
  
## <a name="agile-tools"></a>Çevik Araçlar  
 Başvuru bağlantısı: **[iş](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (Team Explorer Everywhere dahil VISUAL STUDIO Team SERVICES veya TFS kullanarak)  
  
 Genel Açıklama: tüm planlama ve izleme özellikleri proje türü ve kodlama dillerinden bağımsızdır.  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Biriktirme listeleri ve Sprint 'leri yönetme|Yes||  
|Çalışma izleme|Yes||  
|Takım odası işbirliği|Yes||  
|Kanban panoları|Yes||  
|İlerlemeyi raporla ve görselleştirin|Yes||  
  
## <a name="modeling"></a>Modelleme  
 Başvuru bağlantısı: ** [mimari çözümleme ve modelleme](../modeling/analyze-and-model-your-architecture.md)**  
  
 Tasarım özellikleri kodlama dilinden bağımsızdır veya C# gibi .NET dilleri ile birlikte çalışır. Kod ile ilgili hangi yönleri öğrenmek için [yazılım geliştirmede mimari ve modelleme şemaları rollerine](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) bakın.  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Sıralı diyagramlar|Yes||  
|Bağımlılık grafikleri|Yes||  
|Çağrı hiyerarşisi|Yes||  
|Sınıf Tasarımcısı|Yes||  
|Mimari Gezgini|Yes||  
|UML diyagramları (kullanım örneği, etkinlik, sınıf, bileşen, dizi ve DSL)|Yes||  
|Katman diyagramları|Yes||  
|Katman doğrulama|Yes||  
  
## <a name="code"></a>Kod  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|[Team Foundation sürüm denetimi](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) veya Visual Studio Team Services kullanın|Yes||  
|[Team Services 'da git 'i kullanmaya başlama](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Yes||  
|[Kod Analizi/kod kalitesini geliştirme (başvurular, önerilen değişiklikler vb.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Yes||  
|[Kod değişikliklerini ve diğer geçmişi bulma](../ide/find-code-changes-and-other-history-with-codelens.md)|Yes|Uygulamanın çalışma zamanına kadar çözümlenmediği platforma özgü sınırlar haricinde.|  
|[Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)|Yes||  
  
## <a name="build"></a>Oluşturma  
 Başvuru bağlantısı: ** [derleme](/azure/devops/pipelines/index)**  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Şirket içi TFS sunucusu|Yes|Derleme makinelerinde Xamarin yüklü olmalıdır ve iOS için derlemek üzere bir OSX bilgisayarına bağlanabilir. Bkz. [Xamarin IÇIN TFS 'Yi yapılandırma](/azure/devops/repos/tfvc/overview?view=azure-devops) (Xamarin Web sitesi)|  
|Visual Studio Team Services bağlı şirket içi derleme sunucusu|Yes|Yönergeler için bkz. [yapı sunucusu](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) .|  
|Visual Studio Team Services barındırılan denetleyici hizmeti|Yes|Bkz. [Xamarin uygulamanızı oluşturma](https://www.visualstudio.com/docs/build/apps/mobile/xamarin).|  
|Ön ve son betiklerle derleme tanımları|Yes||  
|Geçitli iadeler dahil sürekli tümleştirme|Yes|TFVC için geçitli iadeler, yalnızca git, iadeler yerine bir çekme isteği modelinde çalışmaktadır.|  
  
## <a name="testing"></a>Test Etme  
 Başvuru bağlantısı: ** [uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Testleri planlama, test çalışmaları oluşturma ve test paketlerini düzenleme|Yes||  
|El ile test|Yes||  
|Test Yöneticisi (kaydı ve kayıttan yürütme testleri)|Yes|Windows cihazları ve Android öykünücüleri yalnızca Visual Studio 'dan. Tüm cihazlar için kayıt, [Xamarin test kaydedicisi](https://www.xamarin.com/test-cloud/recorder)ile mümkündür.|  
|Kod kapsamı|yok||  
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Yes|Windows ve Android hedefleri için yerleşik MSTest araçları kullanılabilir. Windows, Android ve iOS 'da birim testlerini çalıştırmak için Xamarin NUnit önerir. Bkz. [Xamarin IÇIN TFS 'Yi yapılandırma](/azure/devops/repos/tfvc/overview?view=azure-devops) (Xamarin Web sitesi).|  
|[Kodunuzu Test Etmek için UI Otomasyonunu Kullanma](../test/use-ui-automation-to-test-your-code.md)|Yalnızca Windows|Visual Studio 'nun UI test kaydedicisi yalnızca Windows. Tüm platformlar için bkz. [Xamarin test kaydedicisi](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Kod kalitesini geliştirme  
 Başvuru bağlantısı: ** [kod kalitesini geliştirme](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|[Yönetilen Kod Kalitesini Analiz Etme](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Yes||  
|[Kod kopyası algılamayı kullanarak yinelenen kodu bulma](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Yes||  
|[Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Yes||  
|[Performans Gezgini](../profiling/performance-explorer.md)|No|Bunun yerine Xamarin Studio [Xamarin Profiler](/xamarin/cross-platform/deploy-test/) kullanın. Xamarin Profiler Şu anda önizleme aşamasındadır ve henüz Windows hedefleri için çalışmadığına bakın.|  
|[.NET Framework bellek sorunlarını çözümleme](../misc/analyze-dotnet-framework-memory-issues.md)|No|Visual Studio Araçları, profil oluşturma için mono Framework 'e kancalar içermez.|  
  
## <a name="release-management"></a>Yayın yönetimi  
 Başvuru bağlantısı: ** [Release Management Ile dağıtımları otomatikleştirin](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Yayın süreçlerini yönetme|Yes||  
|Betikler aracılığıyla dışarıdan yükleme için sunuculara dağıtım|Yes||  
|App Store 'a yükle|Kısmi|Bazı uygulama mağazalarında bu işlemi otomatik hale getirebilen uzantılar vardır.  [Visual Studio Team Services Için uzantılara](https://marketplace.visualstudio.com/VSTS)bakın; Örneğin, [Google Play için uzantı](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>HockeyApp ile izleme  
 Başvuru bağlantısı: ** [HockeyApp ile izleme](https://www.hockeyapp.net/features/)**  
  
|Öne çıkan özelliği|Xamarin ile desteklenir|Ek açıklamalar|  
|-------------|----------------------------|-------------------------|  
|Kilitlenme Analizi, telemetri ve Beta dağıtımı|Yes||
