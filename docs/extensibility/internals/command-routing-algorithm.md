---
title: Komut Yönlendirme Algoritması | Microsoft Docs
description: Komutlar farklı bileşenler tarafından iş Visual Studio ve en içteki bağlamdan en dıştaki bağlama yönlendirildiklerinden, komut çözümlemesi sıralamasını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f99b4e8a4f883d752d217bb1859822c65af07116
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726929"
---
# <a name="command-routing-algorithm"></a>Komut yönlendirme algoritması
Bu Visual Studio komutlar bir dizi farklı bileşen tarafından işlemektedir. Komutlar, geçerli seçimi temel alan en içteki bağlamdan en dıştaki (genel olarak da bilinir) bağlama yönlendirildi. Daha fazla bilgi için bkz. [Komut kullanılabilirliği.](../../extensibility/internals/command-availability.md)

## <a name="order-of-command-resolution"></a>Komut çözümleme sırası
 Komutlar aşağıdaki komut bağlamı düzeyleri aracılığıyla geçirildi:

1. Eklentiler: Ortam ilk olarak mevcut olan tüm eklentilere komutu sunar.

2. Öncelik komutları: Bu komutlar kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> kaydedilir. Bu komutlar, Visual Studio her komut için çağrılır ve kaydedildikleri sırayla çağrılır.

3. Bağlam menüsü komutları: Bağlam menüsünde bulunan bir komut, önce bağlam menüsüne sağlanan komut hedefine, sonra da tipik yönlendirmeye sunulur.

4. Araç çubuğu komut hedeflerini ayarla: Bu komut hedefleri çağrısında <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> kaydedilir. parametresi `pCmdTarget` `null` olabilir. bu yoksa, bu komut hedefi ayar kullanmakta olduğu araç çubuğunda `null` bulunan komutları güncelleştirmek için kullanılır. Kabuk araç çubuğunu ayarıyorsa, araç çubuğundaki komutlara yapılan tüm güncelleştirmelerin odakta yer akan pencere çerçevesi boyunca akmalarını için pencere çerçevesini olarak `pCmdTarget` iletir.

5. Araç penceresi: Genellikle arabirimi uygulayan araç pencereleri, araç penceresi etkin pencere olduğunda Visual Studio hedefini alamayacak şekilde arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de uygulamalı. Ancak odak noktası olan araç penceresi  Project, komut seçilen öğelerin ortak üst öğesi olan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> arabirime yönlendirilecek. Bu seçim birden çok projeye yayıyorsa, komut hiyerarşiye <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> yönlendirildi. arabirimi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> arabirimde karşılık gelen komutlara benzer ve yöntemlerini <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> içerir.

6. Belge penceresi: `RouteToDocs` *Komutta .vsct* dosyasında bayrağı ayarlanmışsa Visual Studio, bir arabirimin örneği veya belge nesnesinin örneği (genellikle bir arabirim veya arabirim) olan belge görünümü nesnesinde bir komut hedefi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> aratır. Belge görünümü nesnesi komutu desteklemezse, Visual Studio döndürülen <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirime yönlendirin. (Bu, belge veri nesneleri için isteğe bağlı bir arabirimdir.)

7. Geçerli hiyerarşi: Geçerli hiyerarşi, etkin belge penceresine sahip olan proje veya içinde seçilen hiyerarşi **Çözüm Gezgini.** Visual Studio, geçerli veya <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> etkin hiyerarşide uygulanan arabirimini aratır. Proje öğesinin belge penceresi odakta olsa bile hiyerarşi etkin olduğunda hiyerarşi geçerli olan komutları desteklemesi gerekir. Ancak, yalnızca Çözüm Gezgini **olduğunda** geçerli olan komutlar, arabirimi ve onun ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> yöntemleri kullanılarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> destekleniyor.

     **Kesme,** **Kopyalama,** **Yapıştırma,** **Silme,** **Yeniden Adlandırma,** **Enter** ve **DoubleClick** komutları özel işleme gerektirir. Hiyerarşilerde Silme ve **Kaldırma komutlarını** işleme hakkında bilgi için arabirimine  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> bakın.

8. Genel: Bir komut daha önce belirtilen bağlamlar tarafından işleniyorsa Visual Studio arabirimi uygulayan bir komutun sahibi olan VSPackage'a yönlendirmeyi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> denemez. VSPackage önceden yüklenmemişse, yöntem çağıran Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yüklenmez. VSPackage yalnızca yöntemi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> çağrıldıktan sonra yüklenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komut tasarımı](../../extensibility/internals/command-design.md)
