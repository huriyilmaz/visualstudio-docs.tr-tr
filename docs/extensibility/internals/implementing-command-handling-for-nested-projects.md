---
title: İç içe projeler için Komut Kullanımının Uygulanması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707605"
---
# <a name="implementing-command-handling-for-nested-projects"></a>İç içe Projeler için Komut İşlemesi Uygulama
IDE iç içe geçmiş projelere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimlerden geçirilen komutları geçirebilir veya ana projeler komutları filtreleyebilir veya geçersiz kılabilir.

> [!NOTE]
> Yalnızca ana proje tarafından normalde işlenen komutlar filtrelenebilir. IDE tarafından işlenen **Yapı** ve **Dağıtma** gibi komutlar filtrelenemez.

 Aşağıdaki adımlar, komut işleme yi uygulama işlemini açıklar.

## <a name="procedures"></a>Yordamlar

#### <a name="to-implement-command-handling"></a>Komut işlemeyi uygulamak için

1. Kullanıcı iç içe bir projede iç içe bir proje veya düğüm seçtiğinde:

   1. IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi çağırır.

      — veya —

   2. Komut, Çözüm Gezgini'ndeki kısayol menüsü komutu gibi bir hiyerarşi penceresinden <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> kaynaklanıyorsa, IDE proje nin üst öğesindeki yöntemi çağırır.

2. Ana proje, ana projenin komutları filtreleyip filtrelemeyeceğini belirlemek için `QueryStatus`geçirilecek parametreleri (örneğin) `pguidCmdGroup` `prgCmds`inceleyebilir. Ana proje komutları filtrelemek için uygulanırsa, ayarlanmalıdır:

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    Sonra ana proje `S_OK`dönmelidir.

    Ana proje komutu filtrelemiyorsa, sadece `S_OK`döndürmelidir. Bu durumda, IDE komutu otomatik olarak alt projeye yönlendirir.

    Üst proje, komutu alt projeye yönlendirmek zorunda değildir. IDE bu görevi gerçekleştirir...

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)
- [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
