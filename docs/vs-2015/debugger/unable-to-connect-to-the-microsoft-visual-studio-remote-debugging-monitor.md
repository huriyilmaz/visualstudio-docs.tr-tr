---
title: Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi bağlantı kurulamıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d62e7ce1c419a9c53e40e1ecf2f71497d60d7a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477058"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata iletisi, **Işleme İliştir** iletişim kutusuna geçersiz bir Visual Studio uzaktan hata ayıklama İzleyicisi adı girdiğinizde görüntülenir. Uzaktan Hata Ayıklama İzleyicisi adı genellikle uzaktan hata ayıklama için bağlanmaya çalıştığınız makineyle aynıdır. Bu ileti, uzak makinenin ağda olmaması, uzaktan hata ayıklama izleyicisinin uzak makinede düzgün bir şekilde kurulmadığı veya ağ sorunları veya bir güvenlik duvarının olması nedeniyle uzak makineye erişilemediği için meydana gelebilir.  
  
> [!IMPORTANT]
> Daha fazla yardıma ihtiyacınız varsa bkz. Microsoft 'a başvurmanın yolları için [bize](../ide/talk-to-us.md) danışın.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Yerel olarak hata ayıklarken bu iletiyi aldım  
 Yerel olarak hata ayıklarken bu iletiyi alıyorsanız, virüsten koruma yazılımınız veya üçüncü taraf güvenlik duvarınız önlenebilir. Visual Studio, 32 bitlik bir uygulamadır, bu nedenle 64 bit uygulamalarda hata ayıklamak için uzaktan hata ayıklayıcının 64 bit sürümünü kullanır. İki işlem yerel bilgisayar içindeki yerel ağı kullanarak iletişim kurar. Bilgisayardan hiçbir ağ trafiği kalmayacak, ancak üçüncü taraf güvenlik yazılımlarının iletişimi engelleyebilen olasıdır.  
  
 Aşağıdaki bölümlerde bu iletiyi edinmenizin bazı nedenleri ve sorunu çözebilmeniz için yapabilecekleriniz listelenmektedir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Visual Studio Uzaktan Hata Ayıklama İzleyicisi uzak makinede yüklü olduğundan ve çalıştığından emin olun. Uzaktan hata ayıklayıcı ve nasıl yükleneceği hakkında bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
- Visual Studio 'da proje özelliklerine bakın (**Proje/Özellikler/hata ayıklama**). **Uzak sunucu adının** doğru olduğundan emin olun.  
  
- Uzak makinenin ağ üzerinde erişilebilir olduğunu doğrulayın.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Uzak makineye ulaşılamıyor  
 Uzak makineye [ping işlemi](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) yapmayı deneyin. Ping komutuna yanıt vermezse uzak Araçlar bağlanamaz. Uzak makineyi yeniden başlatmayı deneyin, aksi takdirde ağda doğru yapılandırıldığından emin olun.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcının sürümü Visual Studio sürümü ile eşleşmiyor  
 Yerel olarak çalıştırdığınız Visual Studio sürümünün, uzak makinede çalışan uzaktan hata ayıklama izleyicisinin sürümüyle eşleşmesi gerekir. Bu hatayı gidermek için, uzaktan hata ayıklama izleyicisinin eşleşen sürümünü indirip yükleyin. Visual Studio sürümünüz için uzak hata ayıklayıcının doğru sürümünü bulmak üzere [Visual Studio abonelikleri](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) ' ne gidin.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler farklı kimlik doğrulama modlarına sahiptir  

 Yerel ve uzak makinelerin aynı kimlik doğrulama modunu kullanması gerekir. Bu hatayı onarmak için her iki makinenin da aynı kimlik doğrulama modunu kullanmasını sağlayın. Uzaktan hata ayıklayıcı 'daki kimlik doğrulama modunu **Araçlar/Seçenekler** iletişim kutusunda değiştirebilirsiniz.  
  
 Kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor  
 Bunu, aşağıdaki yollarla çözebilirsiniz:  
  
- Uzaktan hata ayıklayıcıyı durdurabilir ve yerel bilgisayarda kullandığınız hesapla yeniden başlatabilirsiniz.  
  
- Uzaktan hata ayıklayıcıyı komut satırından **/Allow \<username> ** parametresiyle başlatabilirsiniz:`msvsmon /allow <username@computer>`  
  
- Kullanıcıyı uzaktan hata ayıklayıcı izinleri (uzaktan hata ayıklayıcı penceresinde, **Araçlar/izinler**) ekleyebilirsiniz.  
  
- Yukarıdaki adımlarda yöntemleri kullanamıyoruz, herhangi bir kullanıcının uzaktan hata ayıklama yapmasına izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde, **Araçlar/Seçenekler** iletişim kutusuna gidin. **Kimlik doğrulaması yok**' u seçtiğinizde, **herhangi bir kullanıcının hata ayıklamasına izin ver**' i kontrol edebilirsiniz. Ancak, bu seçeneği yalnızca herhangi bir seçiminiz yoksa veya özel bir ağınız üzerinde olduğunuzda kullanmanız gerekir.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcıya gelen bağlantılara izin vermiyor  
 Visual Studio makinesindeki güvenlik duvarının ve uzak makinedeki güvenlik duvarının, Visual Studio ile uzaktan hata ayıklayıcı arasında iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcı tarafından kullanılan bağlantı noktaları hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows Güvenlik Duvarı 'nı yapılandırma hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklama Için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımı bağlantıları engelliyor  
 Windows Anti-Virus yazılımı, uzaktan hata ayıklayıcı bağlantılarına izin verir, ancak bazı üçüncü taraf virüsten koruma yazılımları bunları engelleyebilir. Bu bağlantılara nasıl izin verbileceğinizi öğrenmek için virüsten koruma yazılımınızın belgelerini denetleyin.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi, uzak makine ve Visual Studio arasındaki iletişimi engelliyor  
 İletişimi engellemediğinden emin olmak için ağ güveninizi gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz. [güvenlik yönetimi](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ, uzaktan hata ayıklamayı desteklemeye yönelik çok meşgul  
 Uzaktan hata ayıklamayı farklı bir zamanda yapmanız veya ağdaki çalışmayı farklı bir süre için yeniden zamanlamanız gerekebilir.  
  
## <a name="more-help"></a>Daha fazla yardım  
 Komut satırı anahtarları dahil olmak üzere daha fazla uzaktan hata ayıklayıcı yardımı almak için, aşağıdakileri bir tarayıcıda açın:  
  
 **Res:/\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote% 20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
