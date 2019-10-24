---
title: Kaynak denetimi çalışma zamanı ayrıntıları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d2469bc25fabd9659e09d6ca841ebc44a743cca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723402"
---
# <a name="source-control-runtime-details"></a>Kaynak Denetimi Çalışma Zamanı Ayrıntıları
Kullanıcı projeye kaynak denetimine bir dosya eklediğinde veya sihirbaz gibi bir Otomasyon denetleyicisi aracılığıyla kaynak denetimine bir proje eklenir. Proje, kaynak denetimi altında olduğundan kendisi için belirtmez; kaynak denetimini destekler, ancak el ile eklenmesi gerekir.

## <a name="registering-with-a-source-control-package"></a>Kaynak denetim paketiyle kaydetme
 Projenizdeki bir dosya kaynak denetimine eklendiğinde, ortam, kaynak denetim sistemi tarafından tanımlama bilgisi olarak kullanılan dört donuk dize sağlamak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> çağırır. Bu dizeleri proje dosyanızda depolayın. Bu dizeler, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> çağırarak proje türünün başlangıcında kaynak denetimi saplaması (kaynak denetim paketlerini yöneten Visual Studio bileşeni) olarak geçirilmelidir. Bu, sırasıyla uygun kaynak denetimi paketini yükler ve çağrıyı `IVsSccManager2::RegisterSccProject` uygulamasına iletir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)