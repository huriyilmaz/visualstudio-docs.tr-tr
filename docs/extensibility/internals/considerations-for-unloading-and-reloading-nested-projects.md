---
title: İç Içe Projelerin Boşaltılması ve Yeniden Yüklenmesinde Dikkat Edilecek Hususlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, unloading and reloading
- projects [Visual Studio SDK], unloading and reloading nested
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab705953eea1fcac99883bb4f88c0e95eced108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709296"
---
# <a name="considerations-for-unloading-and-reloading-nested-projects"></a>İç içe olan projelerin boşaltılması ve yeniden yüklenmesi nde dikkat edilmesi gerekenler

İç içe geçirilmiş proje türlerini uyguladığınız zaman, projeleri boşaltıp yeniden yüklerken ek adımlar gerçekleştirmeniz gerekir. Dinleyicileri çözüm olaylarını doğru bir şekilde bilgilendirmek `OnBeforeUnloadProject` için, olayları ve `OnAfterLoadProject` olayları doğru bir şekilde yükseltmeniz gerekir.

Bu olayları yükseltmek için bir neden kaynak kodu denetimi (SCC) içindir. SCC'nin öğeleri sunucudan silmesini ve SCC'den *new* bir `Get` işlem varsa bunları yeni olarak geri eklemesini istemezsiniz. Bu durumda, yeni bir dosya SCC dışına yüklenir. Farklı olmaları ihtimaline karşı tüm dosyaları boşaltmanız ve yeniden yüklemeniz gerekir.

Kaynak kodu `ReloadItem`denetim çağrıları. Arama <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> `OnBeforeUnloadProject` ve projeyi `OnAfterLoadProject` silmek ve yeniden oluşturmak için arabirimi uygulayın. Arabirimi bu şekilde uyguladığınızda, SCC projenin geçici olarak silindiği ve yeniden ekildiği konusunda bilgilendirilir. Bu nedenle, SCC proje üzerinde proje *gerçekten* silinmiş ve yeniden eklenmiştir gibi çalışmaz.

## <a name="reload-projects"></a>Projeleri yeniden yükleme

İç içe geçiren projelerin yeniden yüklenmesini desteklemek için <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> yöntemi uygularsınız. `ReloadItem`Uygulamanızda, iç içe olan projeleri kapatır ve bunları yeniden oluşturursunuz.

Genellikle bir proje yeniden yüklendiğinde, IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> olayları ve olayları yükseltir. Ancak, silinen ve yeniden yüklenen iç içe yönelik projeler için, ana proje Işlemi başlatır, IDE'yi değil. Ana proje çözüm olaylarını yükseltmediği ve IDE'nin işlemin başlatılması hakkında hiçbir bilgisi olmadığından, olaylar yükseltilmemiştir.

Bu işlemi işlemek için, `QueryInterface` ana <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> proje arabirimi çağırır. `IVsFireSolutionEvents`Iç içe geçen projeyi boşaltmak için `OnBeforeUnloadProject` olayı yükseltmesini ve sonra `OnAfterLoadProject` da aynı projeyi yeniden yüklemek için olayı yükseltmesini sağlayan işlevlere sahiptir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- [Nest projeleri](../../extensibility/internals/nesting-projects.md)
