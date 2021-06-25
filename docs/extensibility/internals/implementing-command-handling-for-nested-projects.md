---
title: İç İçe Projeler için Komut İşleme | Microsoft Docs
description: Tümleşik geliştirme ortamında (IDE) iç içe projeler için Visual Studio işlemeyi nasıl uygulayacaklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4324e207d7b424295137f9523ed0bed538b3d806
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899992"
---
# <a name="implementing-command-handling-for-nested-projects"></a>İç içe Projeler için Komut İşlemesi Uygulama
IDE, ve arabirimleri aracılığıyla iç içe geçmiş projelere geçirilen komutları geçirebilirsiniz ya da üst projeler komutları filtreleye veya <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> geçersiz kılarak geçirebilirsiniz.

> [!NOTE]
> Yalnızca üst proje tarafından normalde işlenmiş komutlar filtrelenmiş olabilir. IDE **tarafından** **işlenmiş** Build ve Deploy gibi komutlar filtre olamaz.

 Aşağıdaki adımlar, komut işlemeyi uygulama işlemini açıklar.

## <a name="procedures"></a>Yordamlar

#### <a name="to-implement-command-handling"></a>Komut işlemeyi uygulamak için

1. Kullanıcı iç içe bir projeyi veya iç içe geçmiş projedeki bir düğümü seçer:

   1. IDE yöntemini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağırarak.

      — veya —

   2. Komutun kaynağı hiyerarşi penceresinden geliyorsa (örneğin, Çözüm Gezgini menü komutu gibi) IDE, projenin üst <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> öğesinde yöntemini çağırır.

2. Üst proje, üst projenin komutları filtrelemesi gerekip gerek olmadığını belirlemek için ve gibi parametreleri `QueryStatus` `pguidCmdGroup` `prgCmds` inceler. Üst proje komutları filtrelemek için uygulanmışsa şunları ayarlamış olması gerekir:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Daha sonra üst proje , 'ı geri `S_OK` getirsin.

    Üst proje komutu filtreleyene kadar yalnızca dönüş `S_OK` yapar. Bu durumda, IDE komutu otomatik olarak alt projeye yönlendirer.

    Üst projenin komutu alt projeye yönlendirmesi gerek değildir. IDE bu görevi gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
