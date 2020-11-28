---
title: Birlikte çalışma derlemelerindeki komut sözleşmeleri | Microsoft Docs
description: Microsoft. VisualStudio. OLE. Interop. IOleCommandTarget arabirimi aracılığıyla komutları işlemeye yönelik temel sözleşme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d655bfb3e6f2206156cd3a6d091ea04f18afe91a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304915"
---
# <a name="command-contracts-in-interop-assemblies"></a>Birlikte çalışma derlemelerindeki komut sözleşmeleri
Arabirim aracılığıyla komutları işlemeye yönelik temel sözleşme, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ortamın, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> özelliğin desteklenip desteklenmediğini ve desteklenip desteklenmediğini, durumunu ve metnini belirlemede, desteklenip desteklenmediğini belirlemede metodunu çağırdığı durumdur. Daha sonra ortam, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> komutu yürütmek için yöntemini çağırır.

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Yöntemi tüm komutlar için aynı şekilde işlenir. Gerekirse daha fazla iletişim (örneğin, açılan listelerle), <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi uygun parametrelerle çağırarak yönetilir. Bu parametrelerin yorumu, belirtilen komuta bağlıdır.

 Komut hedefi çıkış parametresindeki değerleri döndürürse, çağıran tüm kaynakları boşaltmaktan her zaman sorumludur. Bu parametre bir değişken olduğundan, varyantın temizlenmesi kaynakları serbest bırakır.

 Komutların bir hiyerarşi penceresi içinde çalışması gereken durumlarda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimin kullanılması gerekir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Arabirim, benzer yöntemlere sahip benzer bir sözleşmeye sahiptir: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackages 'de komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)
- [Komut uygulama](../../extensibility/internals/command-implementation.md)
