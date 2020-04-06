---
title: Program Başlatma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738482"
---
# <a name="launch-a-program"></a>Bir program başlatın
Bir program hata ayıklamak isteyen kullanıcılar IDE hata ayıklayıcı çalıştırmak için **F5** tuşuna basabilirsiniz. Bu, sonuçta IDE'nin programa bağlı veya bağlı olan bir hata ayıklama motoruna (DE) bağlanmasıyla sonuçlanan bir dizi olayı aşağıdaki gibi başlatır:

1. IDE, çözümün etkin proje hata ayıklama ayarlarını almak için önce proje paketini çağırır. Ayarlar, başlangıç dizinini, ortam değişkenlerini, programın çalışacağı bağlantı noktasını ve belirtilmişse programı oluşturmak için kullanılacak DE'yi içerir. Bu ayarlar hata ayıklama paketine aktarılır.

2. De belirtilirse, DE programı başlatmak için işletim sistemini çağırır. Programı başlatmanın bir sonucu olarak, programın çalışma zamanı ortamı yüklenir. Örneğin, bir program MSIL'de yazılmışsa, programı çalıştırmak için ortak dil çalışma süresi çağrılır.

    -veya-

    Bir DE belirtilmemişse, bağlantı noktası programı başlatmak için işletim sistemini çağırır ve bu da programın çalışma zamanı ortamının yüklenmesine neden olur.

   > [!NOTE]
   > Bir program başlatmak için bir DE kullanılırsa, aynı DE programa bağlı olması muhtemeldir.

3. DE veya bağlantı noktası programı başlattı bağlı olarak, DE veya çalışma zamanı ortamı sonra bir program açıklaması veya düğüm oluşturur ve programın çalıştığını bağlantı noktası nı yönetir.

   > [!NOTE]
   > Program düğümü debugged olabilir bir programın hafif bir temsili olduğundan, çalışma zamanı ortamı, program düğümü oluşturmak önerilir. Sadece bir program düğümü oluşturmak ve kaydetmek için tüm de yüklemek için gerek yoktur. DE IDE sürecinde çalışacak şekilde tasarlanmıştır, ancak hiçbir IDE aslında çalışıyorsa, bağlantı noktasına bir program düğümü ekleyecek bir bileşen olması gerekir.

   Yeni oluşturulan program, ilgili veya ilgisiz diğer programlarla birlikte, aynı IDE'den başlatılan veya eklenen bir hata ayıklama oturumu oluşturur.

   Programlı olarak, kullanıcı **F5**tuşuna [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ilk bastığında , 'hata ayıklama paketi proje paketini (başlatılan <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> program türüyle ilişkili olan) <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> yöntem le çağırır ve bu da çözümün etkin proje hata ayıklama ayarlarıyla bir yapıyı doldurur. Bu yapı <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> yönteme yapılan bir çağrı ile hata ayıklama paketine geri aktarılır. Hata ayıklama paketi daha sonra, programın hata ayıklama ve ilişkili hata ayıklama altyapılarını başlatan oturum hata ayıklama yöneticisini (SDM) anında alarır.

   SDM'ye geçirilen argümanlardan biri de guid programı başlatmak için kullanılacak.

   DE GUID değilse, `GUID_NULL`SDM DE'yi birlikte oluşturur ve programı başlatmak için [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemini çağırır. Örneğin, bir program yerel kodla `IDebugEngineLaunch2::LaunchSuspended` yazılmışsa, `ResumeThread` programı çalıştırmak için büyük olasılıkla arama ve (Win32 işlevleri) çağırır. `CreateProcess`

   Programın başlatılması sonucunda, programın çalışma süresi ortamı yüklenir. De veya çalışma zamanı ortamı daha sonra programı açıklamak için bir [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi oluşturur ve bu arabirimi [addProgramNode'ye](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) geçirip programın çalıştığını bağlantı noktasına bildirir.

   Geçirilirse, `GUID_NULL` bağlantı noktası programı başlatır. Program çalıştırıladıktan sonra, çalışma zamanı `IDebugProgramNode2` ortamı programı açıklamak için bir `IDebugPortNotify2::AddProgramNode`arabirim oluşturur ve 'ye geçirir. Bu, programın çalıştığını bağlantı noktasına belirtir. Ardından SDM hata ayıklama altyapısını çalışan programa bağlar.

## <a name="in-this-section"></a>Bu bölümde
 [Bağlantı noktasını bildirme](../../extensibility/debugger/notifying-the-port.md) Bir program başlatıldıktan ve bağlantı noktası bilgilendirildikten sonra neler olduğunu açıklar.

 [Başlatmadan sonra ekleme](../../extensibility/debugger/attaching-after-a-launch.md) Hata ayıklama oturumu PROGRAMA DE eklemeye hazır olduğunda belgeler.

## <a name="related-sections"></a>İlgili bölümler
 [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerine bağlantılar içerir.
