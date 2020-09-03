---
title: Iç Içe projeleri kaldırma ve yeniden yükleme ile ilgili konular | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65145530c8cd6b68b82391a09b395bb8c9a61117
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197009"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>İç İçe Projeleri Kaldırma ve Yeniden Yükleme Konusunda Dikkat Edilmesi Gerekenler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İç içe geçmiş proje türleri uyguladığınızda, projeleri kaldırıp yeniden yüklediğinizde ek adımlar gerçekleştirmeniz gerekir. Dinleyicileri çözüm olaylarına doğru şekilde bildirmek için ve olaylarını doğru şekilde yükseltmeniz gerekir `OnBeforeUnloadProject` `OnAfterLoadProject` .  
  
 Bu olayları bu şekilde yükseltmeniz gerekir, kaynak kodu denetiminin (SCC) sunucudan öğeleri silmesini ve sonra SCC 'ten bir işlem varsa bunları yeni bir şey olarak geri eklemesini istemezsiniz `Get` . Bu durumda, yeni bir dosya SCC 'tan dışarı yüklenir ve farklı olmaları durumunda tüm dosyaları kaldırıp yeniden yüklemeniz gerekir. SCC çağrıları `ReloadItem` . Bu çağrıyı uygulamanız, ve öğesini çağırarak, projeyi silmek ve yeniden oluşturmak için kullanılır `IVsFireSolutionEvents` `OnBeforeUnloadProject` `OnAfterLoadProject` . Bu uygulamayı gerçekleştirdiğinizde, SCC, projenin geçici olarak silindiğini ve yeniden eklendiğini bilgilendirilir. Bu nedenle, proje gerçekten sunucudan silinip daha sonra yeniden eklendiyse, SCC proje üzerinde çalışmaz.  
  
## <a name="reloading-projects"></a>Projeleri yeniden yükleme  
 İç içe projelerin yeniden yüklenmesini desteklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemini uygulayın. Uygulamanızda `ReloadItem` , iç içe geçmiş projeleri kapatıp yeniden oluşturursunuz.  
  
 Genellikle bir proje yeniden yüklendiğinde IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> ve `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` olaylarını başlatır. Ancak, silinecek ve yeniden yüklenecek iç içe projeler için üst proje, IDE değil, işlemi başlatır. Üst proje çözüm olayları yükseltmediğinden ve IDE 'nin işlemin başlatılması hakkında hiçbir bilgisi olmadığından, olaylar çıkarılmaz.  
  
 Bu işlemi işlemek için, üst proje arabirimi `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> devre dışı bırakır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> . `IVsFireSolutionEvents` , IDE 'ye `OnBeforeUnloadProject` iç içe geçmiş projeyi kaldırmak için olayı kullanmasını söyleyen ve sonra `OnAfterLoadProject` aynı projeyi yeniden yüklemek için olayı oluşturan işlevlere sahiptir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Projeleri İç İçe Geçirme](../../extensibility/internals/nesting-projects.md)
