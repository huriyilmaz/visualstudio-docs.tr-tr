---
title: Interop Meclislerinde Komuta Sözleşmeleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709682"
---
# <a name="command-contracts-in-interop-assemblies"></a>Interop montajlarında komuta sözleşmeleri
<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Arabirim üzerinden komutları işlemek için temel sözleşme, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ortamın komutun desteklenip desteklenmediğini belirlemek için yöntemi ve desteklenirse durumunu ve metnini belirlemek için çağrılmasıdır. Ardından, ortam komutu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yürütmek için yöntemi çağırır.

 Yöntem, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> tüm komutlar için aynı şekilde işlenir. Daha fazla iletişim, gerekirse (örneğin, açılır listeler ile), <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> uygun parametrelere sahip yöntem çağırArak yönetilir. Bu parametrelerin yorumlanması belirtilen komuta bağlıdır.

 Komut hedefi çıkış parametresindeki değerleri döndürürse, arayan her zaman ayrılan kaynakları serbest bırakmaktan sorumludur. Bu parametre bir varyant olduğundan, varyantı temizlemek kaynakları serbest bırakmaktadır.

 Komutların bir hiyerarşi penceresi içinde çalışması gereken <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> durumlarda, arabirim kullanılmalıdır. Arayüzü benzer yöntemlerle benzer bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>sözleşme vardır: ve . <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackages komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)
- [Komut uygulaması](../../extensibility/internals/command-implementation.md)
