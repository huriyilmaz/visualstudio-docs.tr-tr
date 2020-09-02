---
title: Program başlatma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b54250a54960f346f60c5d668755fb5d28ab376e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833011"
---
# <a name="launching-a-program"></a>Program Başlatma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir programda hata ayıklamak isteyen kullanıcılar, hata ayıklayıcıyı IDE 'den çalıştırmak için F5 'e basabilir. Bu, son olarak IDE 'nin bir hata ayıklama altyapısına (DE) bağlanmasına neden olan bir dizi olayı başlatır, bu da aşağıdaki gibi programa bağlı veya bağlı  
  
1. IDE, çözümün etkin proje hata ayıklama ayarlarını almak için ilk olarak proje paketini çağırır. Ayarlar başlangıç dizini, ortam değişkenleri, programın çalıştırılacağı bağlantı noktası ve belirtilmişse programı oluşturmak için kullanılacak olan ' u içerir. Bu ayarlar hata ayıklama paketine geçirilir.  
  
2. Bir DE belirtilmişse, programı başlatmak için işletim sistemini çağırır. Programın başlatılması sonucunda programın çalışma zamanı ortamı yüklenir. Örneğin, bir program MSIL 'de yazılmışsa, programı çalıştırmak için ortak dil çalışma zamanı çağrılır.  
  
    -veya-  
  
    Bir DE belirtilmemişse, bağlantı noktası programı başlatmak için işletim sistemini çağırır, bu da programın çalışma zamanı ortamının yüklenmesine neden olur.  
  
   > [!NOTE]
   > Bir programı başlatmak için bir DE kullanılıyorsa, büyük olasılıkla programa DE aynı şekilde eklenecektir.  
  
3. Ya da bağlantı noktasının programı başlatdığına bağlı olarak, DE veya çalışma zamanı ortamı bir program açıklaması veya düğüm oluşturur ve programın çalıştırdığı bağlantı noktasına bildirir.  
  
   > [!NOTE]
   > Program düğümü, hata ayıklamakta olabilecek bir programın hafif bir gösterimi olduğundan, çalışma zamanı ortamının program düğümünü oluşturması önerilir. Yalnızca bir program düğümü oluşturmak ve kaydetmek için bir DE tamamen yüklenmesi gerekmez. Aynı IDE işleminde çalışmak üzere tasarlanmışsa, ancak aslında hiç IDE çalışmıyorsa, bir program düğümünü bağlantı noktasına ekleyebileceğinden bir bileşen olması gerekir.  
  
   Yeni oluşturulan program, ile ilgili veya ilgisiz, aynı IDE 'den başlatılan veya bağlı olan diğer programlarla birlikte bir hata ayıklama oturumu oluşturabilir.  
  
   Programlı olarak, Kullanıcı **F5**tuşuna bastığında [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hata ayıklama paketi, yöntemi aracılığıyla proje paketini (başlatılan programın türüyle ilişkili) çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> , bu da <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> çözümün etkin proje hata ayıklama ayarlarıyla bir yapıyı doldurur. Bu yapı, yöntemi çağrısıyla hata ayıklama paketine geri geçirilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> . Hata ayıklama paketi daha sonra oturum hata ayıklama Yöneticisi 'ni (SDM) başlatır ve bu, hata ayıklanan programı ve ilişkili hata ayıklama altyapılarını başlatır.  
  
   SDM 'ye geçirilen bağımsız değişkenlerden biri, programı başlatmak için kullanılan DE GUID 'nin GUID 'sidir.  
  
   Aynı GUID değilse `GUID_NULL` , SDM ortak oluşturur ve sonra programı başlatmak Için [launchaskıya alındı](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemini çağırır. Örneğin, bir program yerel kodda yazılmışsa, `IDebugEngineLaunch2::LaunchSuspended` `CreateProcess` programı çalıştırmak için muhtemelen çağrı yapılır ve `ResumeThread` (Win32 işlevleri).  
  
   Programın başlatılması sonucunda programın çalışma zamanı ortamı yüklenir. Daha sonra, veya çalışma zamanı ortamı, programı anlatmak için bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi oluşturur ve bu arabirimi programın çalıştırdığı bağlantı noktasına bildirmek Için [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 'a geçirir.  
  
   `GUID_NULL`Geçirilirse, bağlantı noktası programı başlatır. Program çalışmaya başladıktan sonra çalışma zamanı ortamı, `IDebugProgramNode2` programı tanımlayacak bir arabirim oluşturur ve bunu öğesine geçirir `IDebugPortNotify2::AddProgramNode` . Bu, programın çalıştırdığı bağlantı noktasına bildirir. Sonra, SDM hata ayıklama altyapısını çalışan programa iliştirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Noktasına Bildirme](../../extensibility/debugger/notifying-the-port.md)  
 Bir program başlatıldıktan ve bağlantı noktasına bildirimde bulunulduktan sonra ne olacağını açıklar.  
  
 [Başlatmadan Sonra Ekleme](../../extensibility/debugger/attaching-after-a-launch.md)  
 Hata ayıklama oturumu programa eklemek için hazırsa belgeler.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)  
 Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
