---
title: Seçim Bağlamı Nesneleri | Microsoft Docs
description: IDE'de nelerin görüntü Visual Studio belirlemek için IDE'nin genel seçim bağlamı nesnesini nasıl kullandığının içlerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6e6df11b81a48a95d9c401ff801be548923c6f52
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132281"
---
# <a name="selection-context-objects"></a>Seçim Bağlamı Nesneleri
Tümleşik geliştirme ortamı (IDE), IDE'de görüntülenecekleri belirlemek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için genel seçim bağlamı nesnesini kullanır. IDE'de her pencere, genel seçim bağlamına kendi seçim bağlamı nesnesine sahip olabilir. IDE, genel seçim bağlamını bir pencere odağına sahip olduğunda bir pencerede yer alan değerlerle günceller. Daha fazla bilgi için [bkz. Kullanıcıya Geri Bildirim.](../../extensibility/internals/feedback-to-the-user.md)

 IDE'de her pencere çerçevesi veya sitenin adlı bir hizmeti <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> vardır. Pencere çerçevesinde bulunan VSPackage'nız tarafından oluşturulan nesnenin arabirimine bir işaretçi `QueryService` almak için yöntemini çağırmış olması <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> gerekir.

 Çerçeve pencereleri, seçim bağlamı bilgilerini bölümlerinin, başlatıldıklarında genel seçim bağlamına yayılmasını sağlar. Bu özellik, boş bir seçimle başlaması gerektirilen araç pencereleri için kullanışlıdır.

 Genel seçim bağlamının değiştirilmesi, VSPackage'ların izleyesne olayları tetikler. VSPackage'lar ve arabirimlerini kullanarak aşağıdaki `IVsTrackSelectionEx` görevleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> gerçekleştirebilir:

- Bir hiyerarşide o anda etkin olan dosyayı güncelleştirin.

- Belirli öğe türlerine yapılan değişiklikleri izleme. Örneğin, VSPackage'nız özel bir **Özellikler** penceresi kullanıyorsa,  etkin Özellikler penceresindeki değişiklikleri izleyebilir ve gerektiğinde kendi değişikliklerinizi yeniden başlatabilirsiniz.

  Aşağıdaki dizi, tipik seçim izleme kurslarını gösterir.

1. IDE, yeni açılan pencereden seçim bağlamını alan ve genel seçim bağlamına koyar. Seçim bağlamı, HIERARCHY_DONTPROPAGATE veya SELCONTAINER_DONTPROPAGATE kullanıyorsa, bu bilgiler genel bağlama yayılmaz. Daha fazla bilgi için [bkz. Kullanıcıya Geri Bildirim.](../../extensibility/internals/feedback-to-the-user.md)

2. Bildirim olayları, istenen herhangi bir VSPackage'a yayın.

3. VSPackage, hiyerarşiyi güncelleştirme, bir aracı yeniden etkinleştirme veya diğer benzer görevleri gerçekleştirme gibi etkinlikleri gerçekleştirerek aldığı olaylara göre hareket eder.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio’da Hiyerarşiler](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE’de Seçim ve Para Birimi](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Proje Türleri](../../extensibility/internals/project-types.md)
