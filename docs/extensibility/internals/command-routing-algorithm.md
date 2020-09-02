---
title: Komut yönlendirme algoritması | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709545"
---
# <a name="command-routing-algorithm"></a>Komut yönlendirme algoritması
Visual Studio komutları 'nda birkaç farklı bileşen tarafından işlenir. Komutlar, geçerli seçime bağlı olarak en dıştaki (genel olarak da bilinir) bağlam olan en içteki bağlamdan yönlendirilir. Daha fazla bilgi için bkz. [komut kullanılabilirliği](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Komut çözümlemesi sırası
 Komutlar aşağıdaki komut bağlamı düzeylerine geçirilir:

1. Eklentiler: ortam önce mevcut olan tüm eklentilere komutu sunar.

2. Öncelik komutları: Bu komutlar kullanılarak kaydedilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Bunlar, Visual Studio 'daki her komut için çağırılır ve kaydedildikleri sırada çağırılır.

3. Bağlam menüsü komutları: bağlam menüsünde bulunan bir komut, ilk olarak bağlam menüsüne sağlanan komut hedefine ve tipik yönlendirmeye başladıktan sonra sunulur.

4. Araç çubuğu komut hedeflerini ayarla: Bu komut hedefleri, çağırdığınızda kaydedilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . `pCmdTarget`Parametresi olabilir `null` . Değilse `null` , bu komut hedefi, ayarladığınız araç çubuğunda bulunan komutları güncelleştirmek için kullanılır. Kabuk araç çubuğunuzun ayarlarını ayarsa, `pCmdTarget` araç çubuğunuzun içindeki komutlara yönelik tüm güncelleştirmelerin odak altında olmasa bile pencere çerçevesi aracılığıyla akmasını sağlayacak şekilde pencere çerçevesini geçirir.

5. Araç penceresi: genellikle arabirimi uygulayan araç pencereleri, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> araç penceresi etkin pencere olduğunda, Visual Studio 'nun komut hedefini alması için arabirimi de uygulamalıdır. Ancak, odağı olan araç penceresi **Proje** penceresinde ise, komut <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Seçili öğelerin ortak üst öğesi olan arabirime yönlendirilir. Bu seçim birden çok projeye yayılırsa, komut <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> hiyerarşiye yönlendirilir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> arabirimindeki karşılık gelen komutlara benzer ve yöntemlerini içerir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

6. Belge penceresi: komut, `RouteToDocs` *. vsct* dosyasında bayrak kümesine sahipse, Visual Studio bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> arabirim örneği veya bir belge nesnesi örneği (genellikle bir arabirim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> veya arabirim) olan belge görünümü nesnesi üzerinde bir komut hedefi arar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Belge görünümü nesnesi komutunu desteklemiyorsa, Visual Studio komutu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> döndürülen arabirime yönlendirir. (Bu, belge veri nesneleri için isteğe bağlı bir arabirimdir.)

7. Geçerli hiyerarşi: geçerli hiyerarşi, etkin belge penceresine veya **Çözüm Gezgini**seçili hiyerarşiye sahip proje olabilir. Visual Studio, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> geçerli ya da etkin, hiyerarşide uygulanan arabirimi arar. Hiyerarşisi, bir proje öğesinin belge penceresi odağa sahip olsa bile, hiyerarşi etkin olduğunda geçerli olan komutları desteklemelidir. Ancak, yalnızca **Çözüm Gezgini** odağa sahip olduğunda uygulanan komutlar, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirimi ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> ve yöntemleri kullanılarak desteklenmelidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

     **Kesme**, **kopyalama**, **Yapıştırma**, **silme**, **yeniden adlandırma**, **girme**ve **DoubleClick** komutları özel işleme gerektirir. Hiyerarşilerde **silme** ve **kaldırma** komutlarının nasıl ele alınacağını öğrenmek için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> arabirimine bakın.

8. Genel: bir komut daha önce bahsedilen bağlamlar tarafından işlenmezse, Visual Studio onu arabirimini uygulayan bir komuta sahip VSPackage 'a yönlendirmenize çalışır <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . VSPackage henüz yüklenmediyse, Visual Studio yöntemi çağırdığında yüklenmez <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . VSPackage yalnızca <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemi çağrıldığında yüklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut tasarımı](../../extensibility/internals/command-design.md)
