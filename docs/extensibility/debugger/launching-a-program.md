---
title: Program Başlatma | Microsoft Docs
description: Hata ayıklayıcıyı IDE'den çalıştırmak için F5 kullanarak bir programda hata ayıklarken meydana gelen olay serisi hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 63318d44941784c6613fe35c1f7a405a69cfec48ba10034641c1d2f3b3d2de2e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361099"
---
# <a name="launch-a-program"></a>Programı başlatma
Bir programda hata ayıklamak isteyen kullanıcılar, hata ayıklayıcıyı IDE'den çalıştırmak için **F5'e** basabilirsiniz. Bu, IDE'nin bir hata ayıklama altyapısına (DE) bağlanmasıyla sonuçlandırarak programa sırasıyla bağlı veya bağlı olan bir dizi olayla başlar:

1. IDE, çözümün etkin proje hata ayıklama ayarlarını almak için önce proje paketini arar. Ayarlar başlangıç dizinini, ortam değişkenlerini, programın çalıştıracak olduğu bağlantı noktasını ve belirtilmişse programı oluşturmak için kullanmak üzere DE'i içerir. Bu ayarlar hata ayıklama paketine geçirildi.

2. BIR DE belirtilirse, DE programı başlatmak için işletim sistemini arar. Programı başlatmanın bir sonucu olarak, programın çalışma zamanı ortamı yüklenir. Örneğin, bir program MSIL'de yazılmışsa, programı çalıştırmak için ortak dil çalışma zamanı çağrılır.

    -veya-

    DE belirtilmezse, bağlantı noktası programı başlatmak için işletim sistemini çağırarak programın çalışma zamanı ortamının yüklemesine neden olur.

   > [!NOTE]
   > Bir programı başlatmak için bir DE kullanılıyorsa, büyük olasılıkla aynı DE programa bağlı olur.

3. DE'nin veya bağlantı noktasının programı başlatıp çalıştırmama durumuna bağlı olarak, DE veya çalışma zamanı ortamı bir program açıklaması veya düğümü oluşturur ve programın çalıştırıldı olduğu bağlantı noktasını belirtir.

   > [!NOTE]
   > Program düğümü, hata ayıklanabilir bir programın basit bir gösterimi olduğundan, çalışma zamanı ortamının program düğümünü oluşturması önerilir. Yalnızca bir program düğümü oluşturmak ve kaydetmek için de'nin tamamının yüklenmeye gerek yoktur. DE, IDE sürecinde çalıştıracak şekilde tasarlanmışsa ancak gerçekte çalışan bir IDE yoksa, bağlantı noktasına program düğümü ekleyemeyen bir bileşen olması gerekir.

   Yeni oluşturulan program, ilgili veya ilgisiz, başlatılan veya aynı IDE'den bağlanan diğer programlarla birlikte bir hata ayıklama oturumu oluşturma.

   Program aracılığıyla, kullanıcı **F5'e** ilk kez basıyorsa, hata ayıklama paketi yöntemi aracılığıyla proje paketini (başlatan programın türüyle ilişkilendirilen) çağırarak bir yapıyı çözümün etkin proje hata ayıklama ayarlarıyla [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> doldurur. Bu yapı, yöntemine yapılan bir çağrı aracılığıyla hata ayıklama paketine geri <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> geçirildi. Hata ayıklama paketi daha sonra, hata ayıklanacak programı ve ilişkili hata ayıklama altyapılarını başlatan oturum hata ayıklama yöneticisini (SDM) örneği olarak sunar.

   SDM'ye geçirilen bağımsız değişkenlerden biri, programı başlatmak için kullanılacak DE GUID'idir.

   DE GUID'si yoksa, SDM DE'i birlikte oluşturur ve ardından programı başlatmak için `GUID_NULL` [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) yöntemini çağırarak. Örneğin, bir program yerel kodda yazılmışsa, büyük olasılıkla programı `IDebugEngineLaunch2::LaunchSuspended` çalıştırmak `CreateProcess` için ve `ResumeThread` (Win32 işlevleri) çağırabilir.

   Programı başlatmanın bir sonucu olarak, programın çalışma zamanı ortamı yüklenir. ARDıNDAN DE veya çalışma zamanı ortamı, programı açıklamak için [bir IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) arabirimi oluşturur ve bu arabirimi [AddProgramNode'a](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) iletir ve bağlantı noktasına programın çalıştır olduğunu bildirer.

   `GUID_NULL`geçirirse, bağlantı noktası programı başlatıyor. Program çalıştır edildiktan sonra, çalışma zamanı ortamı programı tanımlamak `IDebugProgramNode2` için bir arabirim oluşturur ve bunu 'ye iletir. `IDebugPortNotify2::AddProgramNode` Bu, programın çalıştır olduğu bağlantı noktasını belirtir. Ardından SDM, hata ayıklama altyapısını çalışan programa iliştirer.

## <a name="in-this-section"></a>Bu bölümde
 [Bağlantı noktasını bildirme](../../extensibility/debugger/notifying-the-port.md) Program başlatıldıktan ve bağlantı noktası bildirdikten sonra ne olacağını açıklar.

 [Başlatmadan sonra ekleme](../../extensibility/debugger/attaching-after-a-launch.md) Hata ayıklama oturumu, DE'i programa eklemeye hazır olduğunda belgeler.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
