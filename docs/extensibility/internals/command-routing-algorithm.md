---
title: Komut Yönlendirme Algoritması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709545"
---
# <a name="command-routing-algorithm"></a>Komut yönlendirme algoritması
Visual Studio komutları farklı bileşenleri bir dizi tarafından işlenir. Komutlar, geçerli seçimi temel alan en içteki bağlamdan en dıştaki (genel olarak da bilinir) içeriğe yönlendirilir. Daha fazla bilgi için [Komut kullanılabilirliği'ne](../../extensibility/internals/command-availability.md)bakın.

## <a name="order-of-command-resolution"></a>Komut çözümleme sırası
 Komutlar aşağıdaki komut bağlamından geçirilir:

1. Eklentiler: Ortam ilk olarak mevcut olan eklentilere komut uymaktadır.

2. Öncelik komutları: Bu komutlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>kullanılarak kaydedilir. Visual Studio'daki her komut için çağrılır ve kayıtlı oldukları sırada çağrılır.

3. Bağlam menüsü komutları: Bağlam menüsünde bulunan bir komut önce bağlam menüsüne sağlanan komut hedefine, ondan sonra da tipik yönlendirmeye sunulur.

4. Araç çubuğu komut hedeflerini ayarlar: Bu komut <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>hedefleri, . Parametre `pCmdTarget` olabilir `null`. `null`Değilse, bu komut hedefi, kurmakta olduğunuz araç çubuğunda bulunan komutları güncelleştirmek için kullanılır. Kabuk araç çubuğunuzu ayarlıyorsa, odakta olmasa `pCmdTarget` bile araç çubuğunuzdaki komutların tüm güncelleştirmelerinin pencere çerçevesi üzerinden akması için pencere çerçevesini geçer.

5. Araç penceresi: Genellikle <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirimi uygulayan araç pencereleri, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> araç penceresi etkin pencere olduğunda Visual Studio'nun komut hedefini alabilmesi için arabirimi de uygulamalıdır. Ancak, odak noktası olan araç penceresi **Proje** penceresiise, komut seçili öğelerin <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> ortak üst öğesi olan arabirime yönlendirilir. Bu seçim birden çok projeyi kapsıyorsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> komut hiyerarşiye yönlendirilir. Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimdeki ilgili komutlara benzer ve yöntemleri içerir.

6. Belge penceresi: Komutun `RouteToDocs` *.vsct* dosyasında bayrak kümesi varsa, Visual Studio belge görünümü nesnesinde bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirim veya belge nesnesinin örneği (genellikle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> arabirim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> veya arabirim) olan bir komut hedefi arar. Belge görünümü nesnesi komutu desteklemiyorsa, Visual <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Studio komutu döndürülen arabirime yönlendirir. (Bu, belge veri nesneleri için isteğe bağlı bir arabirimdir.)

7. Geçerli hiyerarşi: Geçerli hiyerarşi, etkin belge penceresinin sahibi olan proje veya **Çözüm Gezgini'nde**seçilen hiyerarşi olabilir. Visual Studio, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> geçerli veya etkin hiyerarşiüzerinde uygulanan arabirimi arar. Hiyerarşi, bir proje öğesinin belge penceresi odak olsa bile, hiyerarşi etkin olduğunda geçerli olan komutları desteklemelidir. Ancak, yalnızca **Solution Explorer'ın** odak noktası olduğunda uygulanan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> komutlar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> arabirimi ve onun ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> yöntemleri kullanılarak desteklenmelidir.

     **Kesme,** **Kopyala,** **Yapıştır,** **Sil,** **Yeniden Adlandır,** **Girin**ve **DoubleClick** komutları özel kullanım gerektirir. Hiyerarşilerde **Sil** ve **Kaldır** komutlarının nasıl işleyeceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> hakkında bilgi için arabirimi görün.

8. Genel: Bir komut daha önce bahsedilen bağlamlar tarafından işlenmemişse, Visual Studio bu komutu arabirimi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> uygulayan bir komuta sahip olan VSPackage'a yönlendirmeye çalışır. VSPackage zaten yüklenmediyse, Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi aradığında yüklenmez. VSPackage yalnızca <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntem çağrıldığında yüklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut tasarımı](../../extensibility/internals/command-design.md)
