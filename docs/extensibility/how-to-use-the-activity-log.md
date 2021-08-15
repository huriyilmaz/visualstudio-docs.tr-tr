---
title: 'Nasıl yapılır: etkinlik günlüğünü kullanma | Microsoft Docs'
description: VSPackages, etkinlik günlüğüne ileti yazabilir. Perakende ortamlarda VSPackages hata ayıklama için etkinlik günlüğünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: acf0e2d5cd5d72670b00e4cffa05a74c09f8f7e19604edeaabcc82ce834c0afe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401589"
---
# <a name="how-to-use-the-activity-log"></a>Nasıl yapılır: etkinlik günlüğünü kullanma
VSPackages, etkinlik günlüğüne ileti yazabilir. Bu özellik, perakende ortamlarda VSPackages hata ayıklaması için özellikle faydalıdır.

> [!TIP]
> Etkinlik günlüğü her zaman açıktır. Visual Studio, son 100 girişin yanı sıra genel yapılandırma bilgilerine sahip ilk 10 girişin bir sıralı arabelleğini tutar.

## <a name="to-write-an-entry-to-the-activity-log"></a>Etkinlik günlüğüne bir giriş yazmak için

1. Bu kodu <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> yöntemine veya VSPackage Oluşturucusu dışında başka bir yönteme ekleyin:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Bu kod, <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> hizmeti alır ve bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> arabirime yayınlar. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> geçerli kültürel bağlamını kullanarak etkinlik günlüğüne bir bilgilendirme girişi yazar.

2. VSPackage yüklendiğinde (genellikle bir komut çağrıldığında veya pencere açıldığında), metin etkinlik günlüğüne yazılır.

## <a name="to-examine-the-activity-log"></a>Etkinlik günlüğünü incelemek için

1. oturumunuz sırasında ActivityLog.xml diske yazmak için [/log](../ide/reference/log-devenv-exe.md) komut satırı anahtarıyla Visual Studio çalıştırın.

2. Visual Studio kapatıldıktan sonra, Visual Studio verileri için alt klasörde etkinlik günlüğünü bulun:

   <em> *% AppData%</em>\microsoft\visualstudio \\ \<version>\ActivityLog.xml*.

3. Etkinlik günlüğünü herhangi bir metin düzenleyicisiyle açın. Tipik bir giriş aşağıda verilmiştir:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Güçlü programlama

Etkinlik günlüğü bir hizmet olduğundan, VSPackage oluşturucusunda etkinlik günlüğü kullanılamıyor.

Etkinlik günlüğünü kendisine yazmadan hemen önce edinmeniz gerekir. Etkinlik günlüğünü daha sonra kullanmak üzere önbelleğe alma veya kaydetme.

## <a name="see-also"></a>Ayrıca bkz.

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [VSPackage Sorunlarını Giderme](../extensibility/troubleshooting-vspackages.md)
- [VSPackage’lar](../extensibility/internals/vspackages.md)
