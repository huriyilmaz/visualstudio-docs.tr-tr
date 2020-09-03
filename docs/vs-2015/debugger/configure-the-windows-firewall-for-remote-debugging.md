---
title: Uzaktan hata ayıklama için Windows güvenlik duvarını yapılandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f232446ed699bd7cc034e4b6d6148b665830cf2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535531"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Windows Güvenlik Duvarı’nı Uzaktan Hata Ayıklama İçin Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, aşağıdaki işletim sistemlerini çalıştıran bilgisayarlarda uzaktan hata ayıklamayı etkinleştirmek üzere güvenlik duvarının nasıl yapılandırılacağı açıklanmaktadır:  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  Hata ayıklamakta olduğunuz ağ bir güvenlik duvarı tarafından korunmadığı takdirde bu yapılandırma gereksizdir. Aksi halde, Visual Studio 'Yu barındıran bilgisayarın ve hata Ayıklanacak uzak bilgisayarın, güvenlik duvarı yapılandırmasında değişiklik olması gerekir.  
  
  **IPSec** Ağınız IPSec kullanarak iletişimin gerçekleştirilmesini gerektiriyorsa, hem Visual Studio ana bilgisayarında hem de uzak bilgisayarda ek bağlantı noktalarını açmanız gerekir.  
  
  **Web sunucusu** Uzak Web sunucusunda hata ayıklaması yapıyorsanız, uzak bilgisayarda ek bir bağlantı noktası açmanız gerekir.  
  
  Her iki bilgisayarın da aynı işletim sistemini çalıştırması gerekmediğini unutmayın. Örneğin, Visual Studio bilgisayarı Windows 10 çalıştırabilir ve uzak bilgisayar Windows Server 2012 R2 çalıştırabilir.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Visual Studio bilgisayarında Windows Güvenlik Duvarı 'nı yapılandırmak için  
 Windows Güvenlik Duvarı 'nı yapılandırmaya yönelik yönergeler farklı işletim sistemlerinde biraz farklılık gösterir. Windows 7 veya Windows Server 2008 ' de Word **programı** kullanılır; Windows 8/8.1, Windows 10 ve Windows Server 2012 ' de Word **uygulaması** kullanılır.  Aşağıdaki adımlarda Word **uygulamasını**kullanacağız.  
  
1. Windows Güvenlik Duvarı sayfasını açın. ( **Başlangıç** menüsü arama kutusuna **Windows Güvenlik Duvarı**yazın).  
  
2. **Windows Güvenlik Duvarı aracılığıyla bir uygulamaya veya özelliğe Izin ver**' e tıklayın.  
  
3. **Izin verilen uygulamalar ve Özellikler** listesinde **Visual Studio uzaktan hata ayıklayıcı bulma**' yı arayın. Listeleniyorsa, seçili olduğundan ve bir veya daha fazla ağ türünün de seçildiğinden emin olun.  
  
4. **Visual Studio uzaktan hata ayıklayıcı bulma** listelenmiyorsa, **başka bir uygulamaya izin ver**' e tıklayın. **Uygulama Ekle** penceresinde yine de görmüyorsanız, **Araştır** ' a tıklayın ve ** \<Visual Studio installation directory> \Common7\IDE\Remote hata ayıklayıcı ' ya**gidin. Uygulama için uygun klasörü bulun (x86, x64, appx) ve **msvsmon.exe**' yi seçin. Daha sonra **Ekle**'ye tıklayın.  
  
5. **Izin verilen uygulamalar ve Özellikler** listesinde **Visual Studio uzaktan hata ayıklama İzleyicisi**seçin. Uzaktan hata ayıklama izleyicisinin iletişim kurmasını istediğiniz bir veya daha fazla ağ türünü (**etki alanı, ev/iş (özel), ortak**) denetleyin. Türler, Visual Studio bilgisayarın bağlı olduğu ağı içermelidir.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>Bulmayı etkinleştirmek için Visual Studio bilgisayarındaki bir bağlantı noktasını açmak için  
 Gelen UDP bağlantı noktası 3702 ' in, uzaktan hata ayıklayıcıyı çalıştıran bilgisayarların bulunmasına izin verecek şekilde izin vermeniz gerekir. Eklemek için bkz. güvenlik duvarında bağlantı noktalarını yapılandırma.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>Uzaktan hata ayıklama için uzak bilgisayarın Windows güvenlik duvarını yapılandırmak için  
 Uzaktan hata ayıklama bileşenleri uzak bilgisayara yüklenebilir veya paylaşılan bir dizinden çalıştırılabilir. Uzak bilgisayarın güvenlik duvarının her iki durumda da yapılandırılması gerekir. Uzaktan hata ayıklama bileşenleri şu konumda bulunur:  
  
 **\<Visual Studio installation directory>\Common7\IDE\Remote hata ayıklayıcı**  
  
 Windows Güvenlik Duvarı 'nı yapılandırmaya yönelik yönergeler farklı işletim sistemlerinde biraz farklılık gösterir. Windows 7 veya Windows Server 2008 ' de Word **programı** kullanılır; Windows 8/8.1, Windows 10 ve Windows Server 2012 ' de Word **uygulaması** kullanılır.  Aşağıdaki adımlarda Word **uygulamasını**kullanacağız.  
  
1. Windows Güvenlik Duvarı sayfasını açın. ( **Başlangıç** menüsü arama kutusuna **Windows Güvenlik Duvarı**yazın.)  
  
2. **Windows Güvenlik Duvarı aracılığıyla bir uygulamaya veya özelliğe Izin ver**' e tıklayın.  
  
3. **Izin verilen uygulamalar ve Özellikler** listesinde, **Visual Studio uzaktan hata ayıklama İzleyicisi**' yi arayın. Listeleniyorsa, seçili olduğundan ve bir veya daha fazla ağ türünün de seçildiğinden emin olun.  
  
4. **Visual Studio uzaktan hata ayıklama İzleyicisi** listelenmiyorsa, **başka bir uygulamaya izin ver**' e tıklayın. **Uygulama Ekle penceresinde**yine de görmüyorsanız, **Araştır** ' a tıklayın ve ** \<Visual Studio installation directory> \Common7\IDE\Remote hata ayıklayıcı ' ya**gidin. Uygulama için uygun klasörü bulun (x86, x64, appx) ve **msvsmon.exe**' yi seçin. Daha sonra **Ekle**'ye tıklayın.  
  
5. **Izin verilen uygulamalar** listesinde **Visual Studio uzaktan hata ayıklama İzleyicisi**seçin. Uzaktan hata ayıklama izleyicisinin iletişim kurmasını istediğiniz bir veya daha fazla ağ türünü (**etki alanı, ev/iş (özel), ortak**) denetleyin. Türler, Visual Studio bilgisayarın bağlı olduğu ağı içermelidir.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Uzak bilgisayarda uzaktan hata ayıklamayı etkinleştiren bağlantı noktaları  
  
|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|  
|-|-|-|-|
|3702|Tarafına|UDP|Uzaktan hata ayıklayıcı keşfi için gereklidir.|  
|4020||TCP|VS 2015 için. Her Visual Studio sürümü için bağlantı noktası numarası 2 ile artırılır. Daha fazla bilgi için bkz. bağlantı noktası atamaları Visual Studio Uzaktan Hata Ayıklayıcı.|  
|4021||TCP|VS 2015 için. Her Visual Studio sürümü için bağlantı noktası numarası 2 ile artırılır. Daha fazla bilgi için bkz. bağlantı noktası atamaları Visual Studio Uzaktan Hata Ayıklayıcı.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Uzak bilgisayardaki, yönetilen veya yerel uyumluluk moduyla uzaktan hata ayıklamayı etkinleştiren bağlantı noktaları  
  
|**Bağlantı noktaları**|**Gelen/giden**|**Protokol**|**Açıklama**|  
|-|-|-|-|  
|135, 139, 445|Tarafına|TCP|Gereklidir.|  
|137, 138|Tarafına|UDP|Gereklidir.|  
|500, 4500|Tarafına|UDP|Etki alanı ilkeniz, IPSec aracılığıyla ağ iletişimi gerçekleştirilmesini gerektiriyorsa gereklidir.|  
|80|Tarafına|TCP|Web sunucusu hata ayıklaması için gereklidir.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Windows güvenlik duvarında bağlantı noktalarını yapılandırma  
  
1. **Başlat** menüsünde, **Gelişmiş Güvenlik Özellikli Windows Güvenlik Duvarı**' nı arayın.  
  
2. **Gelen kuralları** veya **giden kuralları** ' na tıklayın ve ardından **Eylemler** listesinden **Yeni kural** ' a tıklayın.  
  
3. **Kural türü** sayfasında, **bağlantı noktası** ' nı seçin ve ardından **İleri**' ye tıklayın.  
  
4. **Protokol ve bağlantı noktaları** sayfasında, bağlantı noktası protokolünü (TCP veya UDP) seçin. **Belirli yerel bağlantı noktaları** ' nı seçin ve protokol için etkinleştirmek istediğiniz bir veya daha fazla bağlantı noktası numarası girin. Sayıları virgülle ayırın. Ardından **İleri**'ye tıklayın.  
  
5. **Eylem** sayfasında **bağlantıya izin ver** ' i seçin ve ardından **İleri**' ye tıklayın.  
  
6. **Profil** sayfasında, bağlantı noktası için etkinleştirilecek bir veya daha fazla ağ türünü seçin. Seçtiğiniz tür, uzak bilgisayarın bağlı olduğu ağı içermelidir. Ardından **İleri**'ye tıklayın.  
  
7. **Ad** sayfasında kural için bir ad yazın ve ardından **son**' a tıklayın.  
  
8. Yeni kuralınızı **gelen kurallar** veya **giden kurallar** listesinde görmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
