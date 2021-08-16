---
title: Kaynak denetimi çalışma zamanı ayrıntıları | Microsoft Docs
description: Kullanıcı kaynak denetiminde veya bir Otomasyon denetleyicisi aracılığıyla projeye bir dosya eklediğinde, projenin kaynak denetimine nasıl eklendiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 081e4b75644b51539327083b5e51be5f715507b126a59934a429a80cd0cfdd39
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414369"
---
# <a name="source-control-runtime-details"></a>Kaynak Denetimi Çalışma Zamanı Ayrıntıları
Kullanıcı projeye kaynak denetimine bir dosya eklediğinde veya sihirbaz gibi bir Otomasyon denetleyicisi aracılığıyla kaynak denetimine bir proje eklenir. Proje, kaynak denetimi altında olduğundan kendisi için belirtmez; kaynak denetimini destekler, ancak el ile eklenmesi gerekir.

## <a name="registering-with-a-source-control-package"></a>Kaynak denetim paketiyle kaydetme
 Projenizdeki bir dosya kaynak denetimine eklendiğinde, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> kaynak denetim sistemi tarafından tanımlama bilgisi olarak kullanılan dört donuk dize sağlamak için çağırır. Bu dizeleri proje dosyanızda depolayın. bu dizeler, çağırarak proje türünün başlangıcında kaynak denetim saplaması (kaynak denetimi paketlerini yöneten Visual Studio bileşeni) olarak geçirilmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Bu, sırasıyla uygun kaynak denetimi paketini yükler ve çağrısını uygulamasının uygulamasına iletir `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
