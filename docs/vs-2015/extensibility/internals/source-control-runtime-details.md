---
title: Kaynak denetimi çalışma zamanı ayrıntıları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183364"
---
# <a name="source-control-runtime-details"></a>Kaynak Denetimi Çalışma Zamanı Ayrıntıları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kullanıcı projeye kaynak denetimine bir dosya eklediğinde veya sihirbaz gibi bir Otomasyon denetleyicisi aracılığıyla kaynak denetimine bir proje eklenir. Proje, kaynak denetimi altında olduğundan kendisi için belirtmez; kaynak denetimini destekler, ancak el ile eklenmesi gerekir.  
  
## <a name="registering-with-a-source-control-package"></a>Kaynak denetim paketiyle kaydetme  
 Projenizdeki bir dosya kaynak denetimine eklendiğinde, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> kaynak denetim sistemi tarafından tanımlama bilgisi olarak kullanılan dört donuk dize sağlamak için çağırır. Bu dizeleri proje dosyanızda depolayın. Bu dizeler, çağırarak proje türünün başlangıcında kaynak denetim saplaması (kaynak denetim paketlerini yöneten Visual Studio bileşeni) olarak geçirilmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Bu, sırasıyla uygun kaynak denetimi paketini yükler ve çağrısını uygulamasının uygulamasına iletir `IVsSccManager2::RegisterSccProject` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Kaynak Denetimini Destekleme](../../extensibility/internals/supporting-source-control.md)
