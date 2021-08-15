---
title: Otomasyon Modeli modeline katkıda | Microsoft Docs
description: VSPackage tasarlarken bir Visual Studio yönergeleri izleerek otomatik otomasyon modeline katkıda bulunun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8c84e07fa5ac2d3fc3afafd1579c8012ad14b06c82eb8a566ecaa28f5904b158
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305834"
---
# <a name="contribute-to-the-automation-model"></a>Otomasyon modeline katkıda bulunun
Visual Studio ortamı özelleştirmek için bir dizi otomasyon arabirimi sağlar. Otomasyon modeli, son kullanıcıların yeni eklentiler ve uzantılar oluşturmalarını Visual Studio nesne modelidir.

 Ayrıca, vsPackage geliştiricisi olarak otomasyon modeline katkıda bulunmak sizin için uygundur; Bunu yaparak, VSPackage'nizin son kullanıcılarının eklenti oluşturmalarını ve vsPackage'larınızı 'de kullandıklarında genellikle tutarlı bir kullanıcı modeli deneyimi sağlamalarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağlarsiniz.

 Son kullanıcı deneyimini tutarlı hale gelecek şekilde, VSPackage'nızı tasarlarken VSPackage'nizin otomasyon modelinin'de fikirleri izlemesi için bir dizi yönergeleri takip [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] edin.

## <a name="in-this-section"></a>Bu bölümde
- [Otomasyon modeline genel bakış](../../extensibility/internals/automation-model-overview.md)

 Otomasyon modelini, ortak ortamın ana modellerini kontrol altına alan ilgili nesne grupları olarak tanımlar. Bu nesne kümesi, otomasyon modelinin diyagramında yer alıyor.

- [VSPackage'lar için otomasyon sağlama](../../extensibility/internals/providing-automation-for-vspackages.md)

 VSPackage'nız için otomasyon sağlamanın iki ana yolu tartışır.

- [Proje nesnelerini açığa çıkarma](../../extensibility/internals/exposing-project-objects.md)

 VSPackage'a özgü nesneler oluşturmak için adım adım yönergeler sağlar.

- [Project modelleme](../../extensibility/internals/project-modeling.md)

 Yeni proje türünüz için otomasyon oluşturmak için gereken standart proje nesnelerini açıklar ve proje otomasyonu'nın takip eden yolunu gösterir. Bu konu, sınıflar için bildirimlerin ve uygulamanın listelerini de sağlar.

- [Olayları ortaya çıkarma](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Otomasyon modeliniz için olay oluşturmaya ilişkin adım adım yönergeler sağlar.

- [Seçenek sayfaları için otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)

 Nesneyi genişleterek VsPackage'ın araç menüsündeki özel Seçenekler  iletişim kutusunun özelliklerini  desteklemek için bir otomasyon nesnesinin nasıl geri getirileceni `DTE.Properties` açıklar.

- [Kod için otomasyon sağlama](../../extensibility/internals/providing-automation-for-code.md)

 Kodunuz için otomasyon modeli oluşturmanın gerekli olmadığını açıklar. Ancak, bu konu başlığında kod modelleri hakkında içgörü sağlayan bir bağlantı verilmektedir.

- [Nasıl Windows: Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Otomasyon sağlamanın, otomasyon nesnelerini bir pencerede kullanılabilir yapmak istediğiniz her durumda iyi bir fikir olduğunu ve ortamın önceden hazır bir otomasyon nesnesi sağlamamış olduğunu açıklar. Araç pencereleri ve belge pencereleri için otomasyonu ele alan.

- [Otomasyon modelini kullanma](../../extensibility/internals/using-the-automation-model.md)

 Otomasyon tüketicisi ilk proje otomasyon nesnelerini nasıl elde eder, iki kod örneği sağlar.

- [Yapılandırma ve SelectedItem nesneleri için Otomasyon](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Yapılandırma ve SelectedItems nesneleri için otomasyon hakkında bilgi sağlar.

## <a name="reference"></a>Başvuru
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> VSPackage'ın DTE otomasyon nesne modeline nasıl katıldığını gösteren bir kod örneği sağlar. Parametreleri, dönüş değerlerini ve seçili açıklamaları listeler.
