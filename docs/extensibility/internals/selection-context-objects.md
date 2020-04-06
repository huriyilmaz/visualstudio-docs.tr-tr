---
title: Seçim Bağlam Nesneleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705506"
---
# <a name="selection-context-objects"></a>Seçim Bağlamı Nesneleri
Tümleşik geliştirme ortamı (IDE), IDE'de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne görüntülenmesi gerektiğini belirlemek için genel bir seçim bağlamı nesnesi kullanır. IDE'deki her pencerenin kendi seçim bağlamı nesnesi genel seçim bağlamına itilmiş olabilir. IDE, bu pencere nin odak noktası olduğunda, genel seçim bağlamını bir pencereden gelen değerlerle güncelleştirir. Daha fazla bilgi [için Kullanıcıya Geri Bildirim'e](../../extensibility/internals/feedback-to-the-user.md)bakın.

 IDE'deki her pencere çerçevesi veya <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>sitenin bir hizmeti vardır. VsPackage tarafından oluşturulan ve pencere çerçevesine sited olan `QueryService` nesne, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> arabirime işaretçi almak için yöntemi aramalıdır.

 Çerçeve pencereleri, seçim bağlamı bilgilerinin bazı bölümlerinin başlatıldığında genel seçim bağlamına yayılmasını engelleyebilir. Bu yetenek, boş bir seçimle başlamak zorunda kalabilirsiniz araç pencereleri için yararlıdır.

 Genel seçim bağlamını değiştirmek VSPackages'In izleyebilir olayları tetikler. VSPackages aşağıdaki görevleri uygulayarak `IVsTrackSelectionEx` ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> arabirimleri uygulayarak gerçekleştirebilir:

- Şu anda etkin olan dosyayı bir hiyerarşide güncelleştirin.

- Belirli türdeki öğeleri izleyin. Örneğin, VSPackage'ınız **özel** özellikler penceresi kullanıyorsa, etkin **Özellikler** penceresindeki değişiklikleri izleyebilir ve gerektiğinde sizinkini yeniden başlatabilirsiniz.

  Aşağıdaki sıra, tipik seçim izleme rotasını gösterir.

1. IDE, seçim bağlamını yeni açılan pencereden alır ve genel seçim bağlamına koyar. Seçim bağlamında HIERARCHY_DONTPROPAGATE veya SELCONTAINER_DONTPROPAGATE kullanıyorsa, bu bilgiler genel içeriğe yayılmaz. Daha fazla bilgi [için Kullanıcıya Geri Bildirim'e](../../extensibility/internals/feedback-to-the-user.md)bakın.

2. Bildirim olayları, bunları isteyen herhangi bir VSPackage'a yayınlanır.

3. VSPackage, hiyerarşiyi güncelleştirme, bir aracı yeniden etkinleştirme veya diğer benzer görevleri gerçekleştirme gibi etkinlikler gerçekleştirerek aldığı olaylara göre hareket eder.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE’de Seçim ve Para Birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Proje Türleri](../../extensibility/internals/project-types.md)
