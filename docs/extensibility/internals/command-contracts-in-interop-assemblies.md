---
title: Birlikte Çalışma Derlemelerinde Komut Sözleşmeleri | Microsoft Docs
description: Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget arabirimi aracılığıyla komutları işlemeye yönelik temel sözleşme hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f3e0921c37786c3be755f42a477c20465edfe1c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050214"
---
# <a name="command-contracts-in-interop-assemblies"></a>Birlikte çalışma derlemelerinde komut sözleşmeleri
Komutları arabirim üzerinden işlemeye yardımcı olan temel sözleşme, ortamın komutun destekleniyor olup olmadığını belirlemek için yöntemini çağırıp destekleniyorsa durumunu ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metnini belirlemesidir. Ardından, ortam komutunu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yürütmek için yöntemini çağırmaktadır.

 yöntemi, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> tüm komutlar için aynı şekilde ele kullanılır. Gerekirse daha fazla iletişim (örneğin, açılan listelerle) uygun parametrelerle <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi çağrılarak yönetilir. Bu parametrelerin yorumu belirtilen komuta bağlıdır.

 Komut hedefi çıkış parametresinde değerleri döndürürse, çağıranın her zaman ayrılmış olan tüm kaynakları serbest bırakarak sorumluluğu vardır. Bu parametre bir değişken olduğundan, varyantı temizlemek kaynakları serbest bıraktır.

 Komutların hiyerarşi penceresinde çalışması gereken durumlarda <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimi kullanılmalıdır. Arabirimin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> benzer yöntemlerle benzer bir sözleşmesi vardır: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackage'larda komut yönlendirme](../../extensibility/internals/command-routing-in-vspackages.md)
- [Komut uygulaması](../../extensibility/internals/command-implementation.md)
