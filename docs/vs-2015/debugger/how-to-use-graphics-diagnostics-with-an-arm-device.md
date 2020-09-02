---
title: 'Nasıl yapılır: ARM cihazındaki Grafik Tanılama kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bbe12449849b656af2658c5bab667b0e611515e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685869"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Nasıl Yapılır: ARM Cihazla Grafik Tanılamayı Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik Tanılama, Windows RT 8,1 veya Windows Phone 8,1 çalıştıran ARM tabanlı cihazlarda Direct3D uygulamalarında uzaktan hata ayıklamayı destekler. Cihazda çalışırken Direct3D uygulamanızdan grafik bilgilerini yakalayabilir veya daha önce yakalanan grafik bilgileri için cihazı kayıttan yürütme makinesi olarak kullanabilirsiniz.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>ARM tabanlı bir cihazla Grafik Tanılama kullanma  
 Visual Studio ARM tabanlı cihazlarda çalıştırılmadığından, üzerinde çalışan bir uygulamayı çözümlemek için uzaktan hata ayıklayıcıyı kullanmanız gerekir. Uzaktan hata ayıklayıcı grafik yakalamayı ve kayıttan yürütmeyi destekler, böylece uygulamanızda hata ayıklayabileceğiniz kadar kolayca bu cihazlarda grafik performansını değerlendirebilmenizi sağlayabilir.  
  
 Grafik Tanılama özelliklerini kullanmak için, öncelikle cihazınızda uzaktan hata ayıklamayı etkinleştirin.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>ARM tabanlı cihazınızda uzaktan hata ayıklamayı etkinleştirmek için  
  
1. ARM tabanlı cihazınıza [ARM setleri ilkesini](https://msdn.microsoft.com/windows/desktop/dn469188) yükler.  
  
2. ARM tabanlı cihazınıza [Uzaktan hata ayıklama araçları](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) 'yi yükler.  
  
> [!IMPORTANT]
> Windows Phone 8,1 cihazlarında, telefonunuzu geliştirme için kaydetmeniz gerekebilir. Bunu yapmak için kayıtlı bir geliştirici olmanız gerekir. Daha fazla bilgi için bkz. [Windows Phone 8 için uygulama dağıtma ve çalıştırma](https://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Cihazınızda uzaktan hata ayıklamayı etkinleştirdikten sonra, hata ayıklama hedefinizi yapın ve Grafik Tanılama başlatın.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Cihazınızda Grafik Tanılama yapılandırmak ve başlatmak için  
  
1. , ARM tabanlı cihazınızın uzak hata ayıklama hedefi olarak kullanılabilmesi için, **çözüm platformları** açılan listesinde **ARM** ' i seçin.  
  
2. **Hata ayıklama hedefi** AÇıLAN listesinde ARM Cihazınızı seçin.  
  
3. Menüde **Hata Ayıkla**, **grafikler**, **Tanılamayı Başlat**' ı seçin. (Klavye: alt + F5)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzak makinede Windows Mağazası uygulamalarını çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Nasıl yapılır: Grafik Tanılama Kayıttan Yürütme Makinesini Değiştirme](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)
