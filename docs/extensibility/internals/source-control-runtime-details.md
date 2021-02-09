---
title: Kaynak denetimi çalışma zamanı ayrıntıları | Microsoft Docs
description: Kullanıcı kaynak denetiminde veya bir Otomasyon denetleyicisi aracılığıyla projeye bir dosya eklediğinde, projenin kaynak denetimine nasıl eklendiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 213b0096f2bea541fa55840f8f1ea78e8f195cd8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905757"
---
# <a name="source-control-runtime-details"></a>Kaynak Denetimi Çalışma Zamanı Ayrıntıları
Kullanıcı projeye kaynak denetimine bir dosya eklediğinde veya sihirbaz gibi bir Otomasyon denetleyicisi aracılığıyla kaynak denetimine bir proje eklenir. Proje, kaynak denetimi altında olduğundan kendisi için belirtmez; kaynak denetimini destekler, ancak el ile eklenmesi gerekir.

## <a name="registering-with-a-source-control-package"></a>Kaynak denetim paketiyle kaydetme
 Projenizdeki bir dosya kaynak denetimine eklendiğinde, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> kaynak denetim sistemi tarafından tanımlama bilgisi olarak kullanılan dört donuk dize sağlamak için çağırır. Bu dizeleri proje dosyanızda depolayın. Bu dizeler, çağırarak proje türünün başlangıcında kaynak denetim saplaması (kaynak denetim paketlerini yöneten Visual Studio bileşeni) olarak geçirilmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Bu, sırasıyla uygun kaynak denetimi paketini yükler ve çağrısını uygulamasının uygulamasına iletir `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
