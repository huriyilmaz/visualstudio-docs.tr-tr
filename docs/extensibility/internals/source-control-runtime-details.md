---
title: Kaynak Denetimi Çalışma Zamanı Detayları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705048"
---
# <a name="source-control-runtime-details"></a>Kaynak Denetimi Çalışma Zamanı Ayrıntıları
Kullanıcı kaynak denetimine veya sihirbaz gibi bir otomasyon denetleyicisi aracılığıyla projeye bir dosya eklendiğinde, proje kaynak denetimine eklenir. Bir proje, kaynak denetimi altında olduğunu kendisi için belirtmez; kaynak denetimini destekler, ancak el ile eklenmesi gerekir.

## <a name="registering-with-a-source-control-package"></a>Kaynak Kontrol Paketi ile Kayıt
 Projenizdeki bir dosya kaynak denetimine eklendiğinde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> ortam, kaynak denetim sistemi tarafından tanımlama bilgisi olarak kullanılan dört opak dize sağlamak için çağırır. Bu dizeleri proje dosyanızda depolayın. Bu dizeleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>proje türünün başlatılmasında Kaynak Denetim Saplaması'na (kaynak denetim paketlerini yöneten Visual Studio bileşeni) iletilmelidir. Bu da uygun kaynak kontrol paketini yükler ve çağrıyı uygulanmasına `IVsSccManager2::RegisterSccProject`iletir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
