---
title: 'Nasıl Kullanılır: Etkinlik Günlüğü Kullanın | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710577"
---
# <a name="how-to-use-the-activity-log"></a>Nasıl kullanılır: Etkinlik günlüğünü kullanma
VSPackages etkinlik günlüğüne ileti yazabilir. Bu özellik özellikle perakende ortamlarında VSPackages hata ayıklama için yararlıdır.

> [!TIP]
> Etkinlik günlüğü her zaman açık. Visual Studio, genel yapılandırma bilgilerine sahip ilk 10 girişlerin yanı sıra son 100 girişin bir yuvarlanma arabelleği tutar.

## <a name="to-write-an-entry-to-the-activity-log"></a>Etkinlik günlüğüne giriş yazmak için

1. Bu kodu yönteme <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> veya VSPackage oluşturucu dışında başka bir yönteme ekleyin:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Bu kod <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> hizmeti alır ve bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> arabirime atar. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>geçerli kültürel bağlamı kullanarak etkinlik günlüğüne bir bilgi girişi yazar.

2. VSPackage yüklendiğinde (genellikle bir komut çağrıldığında veya bir pencere açıldığında), metin etkinlik günlüğüne yazılır.

## <a name="to-examine-the-activity-log"></a>Etkinlik günlüğünü incelemek için

1. Oturum sırasında ActivityLog.xml'i diske yazmak için [/Log](../ide/reference/log-devenv-exe.md) komut satırı anahtarıyla Visual Studio'yu çalıştırın.

2. Visual Studio'yu kapattıktan sonra Visual Studio verileri için alt klasördeki etkinlik günlüğünü bulun:

   <em> *%AppData%</em>\Microsoft\VisualStudio\\\<sürümü>\ActivityLog.xml*.

3. Herhangi bir metin düzenleyicisi ile etkinlik günlüğünü açın. Burada tipik bir giriş:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Sağlam programlama

Etkinlik günlüğü bir hizmet olduğundan, etkinlik günlüğü VSPackage oluşturucusunda kullanılamaz.

Sadece ona yazmadan önce etkinlik günlüğü elde etmelidir. Etkinlik günlüğünü önbelleğe almayın veya ileride kullanmak üzere kaydetmeyin.

## <a name="see-also"></a>Ayrıca bkz.

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [VSPackage Sorunlarını Giderme](../extensibility/troubleshooting-vspackages.md)
- [VSPackage’lar](../extensibility/internals/vspackages.md)
