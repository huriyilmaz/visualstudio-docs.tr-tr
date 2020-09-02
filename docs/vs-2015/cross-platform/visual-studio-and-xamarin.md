---
title: Visual Studio ve Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 098d94a1aed9020271db5010e278a4aa8fc68330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64828378"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio ve Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin, ortak bir C#/.NET kod tabanından Yerel iOS, Android ve Windows uygulamaları oluşturmaya yönelik bir mobil uygulama geliştirme platformudur ve platformlar arasında %100 75 oranında kod yeniden kullanımı elde edilir. Xamarin ve C# ile yazılmış uygulamalar, temel alınan platform API 'Lerine ve yerel kullanıcı arabirimleri oluşturma özelliğine ve çalışma zamanı performansı üzerinde çok az etkisi olması için platforma özgü paketlere yönelik olarak tam erişime sahiptir. (Note: Xamarin F # ' ı da destekler, ancak bu belge yalnızca C# ' ye odaklanacaktır. Visual Basic şu anda desteklenmiyor.)  
  
 Artık, C#, .NET ve Visual Studio 'ya alışkın olan geliştiriciler, Android, iOS ve Windows cihazlarında uzaktan hata ayıklama de dahil olmak üzere, hedef-C veya Java gibi yerel kodlama dillerini öğrenmeden, mobil uygulamalar için Xamarin ile çalışırken aynı güç ve verimliliğin avantajlarından yararlanır. Daha kısa bir süre sonra, Xamarin kullanılarak derlenmiş Kullanıcı arabirimleriyle (NASCAR, Aviva ve MixRadio gibi) çok yüksek performanslı uygulamalar oluşturulmuştur.  
  
 Bu belgeler, bu deneyimleri derlemek için **Xamarin Ile Visual Studio** 'nun tam özelliklerini değerlendirmenize yardımcı olur.  
  
- [Kurulum ve yükleme](../cross-platform/setup-and-install.md)ile başlayın (Internet bağlantınızın hızına, zaten yüklü olduğunu ve seçtiğiniz seçeneklere bağlı olarak genellikle 2-4 saat).  
  
- Yükleyiciler çalışırken Xamarin 'in doğası, Xamarin. Forms 'u yerel kullanıcı arabirimine karşılaştırma ve daha fazlasını belirten [Xamarin ile mobil geliştirme hakkında bilgi](../cross-platform/learn-about-mobile-development-with-xamarin.md) edinebilirsiniz.  
  
- Yükleme tamamlandıktan sonra [Xamarin ortamınızı doğrulayın](../cross-platform/verify-your-xamarin-environment.md).  
  
- Öğreticiyi izleyerek [Visual Studio 'Da Xamarin. Forms ile uygulama oluşturma hakkında temel bilgileri öğrenin](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
  [Herhangi bir Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional ve Enterprise) sürümü aracılığıyla tüm Xamarin özellikleriyle çalışabilirsiniz. Ayrıca, 31 2016 Mart itibariyle Xamarin 'in tüm Visual Studio 2015 sürümleriyle dahil edildiğini ve artık ayrı bir lisans gerektirmediğini unutmayın. Visual Studio 2013 için, [Kurulum ve yükleme](../cross-platform/setup-and-install.md) konusunun açıklandığı şekilde Xamarin 'i ayrı olarak yükleyebilirsiniz.  
  
> [!NOTE]
> Bu yönergeler, Windows ve Visual Studio arka planına sahip olanlar için en kolay ve en basit bilgisayar yapılandırmasını anlatmaktadır. Bu yapılandırmayla, genel geliştirme deneyimi basitleştirilmiştir çünkü yalnızca, iOS simülatörü ve tethered cihazını kullanmak için Mac ile etkileşimde bulunmak yeterlidir. Bunun yerine bir Mac arka planında geliyorsa, Visual Studio 'Yu Parallels/VMWare içinde veya Xamarin Studio Community kullanarak çalıştırmayı öneririz. Yönergeler için [Mac kullanıcıları Için kurulum, yükleme ve doğrulama](../cross-platform/setup-install-and-verifications-for-mac-users.md) bilgileri bölümüne bakın.  
  
> [!NOTE]
> HTML ve CSS tabanlı platformlar arası bir geliştirme çözümü arıyorsanız, [Visual Studio 'Da platformlar arası geliştirme](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML)bölümünde açıklandığı gibi Apache Cordova için Visual Studio Araçları inceleyin.
