---
title: Iç Içe projeler için komut Işlemeyi uygulama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 628fde153441104e4bb504253d96235270b4b8fb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727090"
---
# <a name="implementing-command-handling-for-nested-projects"></a>İç içe Projeler için Komut İşlemesi Uygulama
IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimlerinden geçirilen komutları iç içe projelere geçirebilir veya üst projeler komutları filtreleyebilir veya geçersiz kılabilir.

> [!NOTE]
> Yalnızca üst proje tarafından normalde işlenen komutlar filtrelenebilir. IDE tarafından işlenen **derleme** ve **dağıtım** gibi komutlar filtrelenemez.

 Aşağıdaki adımlarda komut işlemeyi uygulama işlemi açıklanır.

## <a name="procedures"></a>Yordamlar

#### <a name="to-implement-command-handling"></a>Komut işlemeyi uygulamak için

1. Kullanıcı iç içe geçmiş bir proje veya iç içe geçmiş bir projede bir düğüm seçtiğinde:

   1. IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemini çağırır.

      veya

   2. Komut, Çözüm Gezgini içindeki kısayol menü komutu gibi bir hiyerarşi penceresinde başlatıldıysa IDE, projenin üst kısmında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> yöntemini çağırır.

2. Üst proje, ana projenin komutları filtreleyip filtreleyeceğini anlamak için `pguidCmdGroup` ve `prgCmds`gibi `QueryStatus`geçirilecek parametreleri inceleyebilir. Üst proje, filtre komutlarına uygulanmışsa, şu şekilde ayarlanmalıdır:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Sonra ana proje `S_OK`döndürmelidir.

    Üst proje komutu filtrelemez, yalnızca `S_OK`döndürmelidir. Bu durumda IDE, komutu otomatik olarak alt projeye yönlendirir.

    Üst projenin komutu alt projeye yönlendirmesi gerekmez. IDE bu görevi gerçekleştirir...

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)