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
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477058"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Microsoft Visual Studio Uzaktan Hata Ayıklama İzleyicisi'ne Bağlanılamıyor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata iletisi, **Işleme İliştir** iletişim kutusuna geçersiz bir Visual Studio uzaktan hata ayıklama İzleyicisi adı girdiğinizde görüntülenir. Uzaktan Hata Ayıklama İzleyicisi adı genellikle uzaktan hata ayıklama için bağlanmaya çalıştığınız makineyle aynıdır. Bu ileti, uzak makinenin ağda olmaması, uzaktan hata ayıklama izleyicisinin uzak makinede düzgün bir şekilde kurulmadığı veya ağ sorunları veya bir güvenlik duvarının olması nedeniyle uzak makineye erişilemediği için meydana gelebilir.  
  
> [!IMPORTANT]
> Daha fazla yardıma ihtiyacınız varsa bkz. Microsoft 'a başvurmanın yolları için [bize](../ide/talk-to-us.md) danışın.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Yerel olarak debugging sırada bu iletiyi aldım.  
 Yerel olarak hata ayıklarken bu iletiyi alıyorsanız, virüsten koruma yazılımınızı veya bir üçüncü taraf güvenlik duvarı için blame olabilir. Visual Studio 32 bitlik bir uygulama olduğundan, 64 bit uygulamalarda hata ayıklama için uzaktan hata ayıklayıcı 64-bit sürümünü kullanır. İki işlem, yerel bilgisayarın yerel ağda kullanarak iletişim kurar. Bilgisayardan hiçbir ağ trafiği kalmayacak, ancak üçüncü taraf güvenlik yazılımlarının iletişimi engelleyebilen olasıdır.  
  
 Aşağıdaki bölümlerde, neden, bu iletiyi edindiğiniz ve sorunu düzeltmek için yapabilecekleriniz başka bir nedenle listelenmektedir.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Visual Studio Uzaktan Hata Ayıklama İzleyicisi uzak makinede yüklü olduğundan ve çalıştığından emin olun. Uzaktan hata ayıklayıcı ve nasıl yükleneceği hakkında bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).  
  
- Visual Studio 'da proje özelliklerine bakın (**Proje/Özellikler/hata ayıklama**). **Uzak sunucu adının** doğru olduğundan emin olun.  
  
- Uzak makinenin ağ üzerinde erişilebilir olduğunu doğrulayın.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Uzak makineye ulaşılamıyor  
 Uzak makineye [ping işlemi](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) yapmayı deneyin. Ping komutuna yanıt vermezse uzak Araçlar bağlanamaz. Uzak makine yeniden başlatılıyor ve aksi takdirde ağ üzerinde doğru yapılandırıldığından emin deneyin.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Uzaktan hata ayıklayıcının sürümü Visual Studio sürümü ile eşleşmiyor  
 Visual Studio'nun sürümü yerel olarak çalışan uzak makine üzerinde çalışan uzaktan hata ayıklama İzleyicisi sürümüyle eşleşmesi gerekir. Bu sorunu gidermek için indirin ve uzaktan hata ayıklama İzleyicisi'nın eşleşen sürümünün yükleyin. Visual Studio sürümünüz için uzak hata ayıklayıcının doğru sürümünü bulmak üzere [Visual Studio abonelikleri](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) ' ne gidin.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Yerel ve uzak makineler sahip farklı bir kimlik doğrulama modları  

 Yerel ve uzak makineler aynı kimlik doğrulama modunu kullanmanız gerekir. Bu sorunu gidermek için her iki makine aynı kimlik doğrulama modu kullandığınızdan emin olun. Uzaktan hata ayıklayıcı 'daki kimlik doğrulama modunu **Araçlar/Seçenekler** iletişim kutusunda değiştirebilirsiniz.  
  
 Kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulamasına genel bakış](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Uzaktan hata ayıklayıcı farklı bir kullanıcı hesabı altında çalışıyor  
 Bu aşağıdaki yollardan biriyle çözebilirsiniz:  
  
- Uzaktan hata ayıklayıcıyı durdurun ve yerel bilgisayarda kullanmakta olduğunuz hesapla yeniden başlatın.  
  
- Uzaktan hata ayıklayıcıyı komut satırından **/Allow \<username >** parametresiyle başlatabilirsiniz: `msvsmon /allow <username@computer>`  
  
- Kullanıcıyı uzaktan hata ayıklayıcı izinleri (uzaktan hata ayıklayıcı penceresinde, **Araçlar/izinler**) ekleyebilirsiniz.  
  
- Önceki adımlarda yöntemlerini kullanamıyorsanız, uzaktan hata ayıklama yapmak herhangi bir kullanıcı izin verebilirsiniz. Uzaktan hata ayıklayıcı penceresinde, **Araçlar/Seçenekler** iletişim kutusuna gidin. **Kimlik doğrulaması yok**' u seçtiğinizde, **herhangi bir kullanıcının hata ayıklamasına izin ver**' i kontrol edebilirsiniz. Ancak, bu seçeneği yalnızca hiçbir seçenek varsa ya da özel bir ağda olması durumunda kullanmanız gerekir.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Uzak makinedeki güvenlik duvarı uzaktan hata ayıklayıcıya gelen bağlantılara izin vermiyor  
 Visual Studio makinede güvenlik duvarı ve güvenlik duvarı uzak makinede Visual Studio uzaktan hata ayıklayıcı arasındaki iletişime izin verecek şekilde yapılandırılması gerekir. Uzaktan hata ayıklayıcı tarafından kullanılan bağlantı noktaları hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](../debugger/remote-debugger-port-assignments.md). Windows Güvenlik Duvarı 'nı yapılandırma hakkında daha fazla bilgi için bkz. [Uzaktan hata ayıklama Için Windows güvenlik duvarını yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Virüsten koruma yazılımının bağlantıları engelliyor  
 Uzaktan hata ayıklayıcı bağlantıları Windows virüsten koruma yazılımının sağlar, ancak bazı üçüncü taraf virüsten koruma yazılımının engelliyor olabilir. Bu bağlantılara izin verecek şekilde nasıl öğrenmek, virüsten koruma yazılımınızın belgelerine bakın.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Ağ güvenlik ilkesi uzak makinede Visual Studio arasındaki iletişimi engelliyor  
 İletişimi engellemediğinden emin olmak için ağ güvenliği gözden geçirin. Windows ağ güvenlik ilkesi hakkında daha fazla bilgi için bkz. [güvenlik yönetimi](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Ağ uzaktan hata ayıklamayı desteklemek için çok meşgul  
 Farklı bir zamanda uzaktan hata ayıklama yapın veya farklı bir saat için ağ üzerinde işi yeniden zamanlayabilir gerekebilir.  
  
## <a name="more-help"></a>Daha fazla yardım  
 Komut satırı anahtarları dahil olmak üzere daha fazla uzaktan hata ayıklayıcı yardımı almak için, aşağıdakileri bir tarayıcıda açın:  
  
 **Res:/p: \ Program %2 0 dosya \ Microsoft %2 0 görsel %2 0 Studio% 2014.0 \ Common7 \ IDE \ Remote %2 0 Debugger \ x64 \ Msvsmon. exe/help. htm**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
