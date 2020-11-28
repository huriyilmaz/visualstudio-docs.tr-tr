---
title: Otomasyon modeline katkıda bulunma | Microsoft Docs
description: VSPackage tasarlarken bir dizi yönerge izleyerek Visual Studio Automation modeline nasıl katkıda bulunabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab43da108a8d4a3339c54973f60bf1bef6a74780
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305597"
---
# <a name="contribute-to-the-automation-model"></a>Otomasyon modeline katkıda bulunma
Visual Studio, ortamı özelleştirmek için bir Otomasyon arabirimleri kümesi sağlar. Otomasyon modeli, son kullanıcıların Visual Studio eklentileri ve uzantıları oluşturmalarına olanak tanıyan nesne modelidir.

 Ayrıca, Otomasyon modeline katkıda bulunmak için bir VSPackage geliştiricisi olarak size uygundur; Bunu yaparak, VSPackage 'ın son kullanıcılarını eklenti oluşturmak ve genellikle VSPackage 'ı kullandıklarında tutarlı bir kullanıcı modeli deneyimi sağlamak için etkinleştirirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Son Kullanıcı deneyimini tutarlı hale getirmek için VSPackage 'ı tasarlarken bir dizi yönerge izleyerek VSPackage için otomasyon modelinin içindeki fikirleri takip edebilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Bu bölümde
- [Otomasyon modeline genel bakış](../../extensibility/internals/automation-model-overview.md)

 , Ortak ortamın ana modellerini denetleyen ilgili nesne grupları olarak otomasyon modelini tanımlar. Bu nesne kümesi, otomasyon modeli diyagramında görüntülenir.

- [VSPackages için Otomasyon sağlama](../../extensibility/internals/providing-automation-for-vspackages.md)

 VSPackage için Otomasyon sağlamanın iki ana yolunu açıklar.

- [Proje nesnelerini kullanıma sunma](../../extensibility/internals/exposing-project-objects.md)

 VSPackage 'a özgü nesneler oluşturmak için adım adım yönergeler sağlar.

- [Proje modelleme](../../extensibility/internals/project-modeling.md)

 Yeni proje türü için Otomasyon oluşturmak için gereken standart proje nesnelerini açıklar ve proje otomasyonunun izlediği yolu gösterir. Bu konu ayrıca sınıflar için bildirimlerin ve uygulamanın listelerinin listesini de sağlar.

- [Olayları kullanıma sunma](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Otomasyon modelinize yönelik olay oluşturmaya yönelik adım adım yönergeler sağlar.

- [Seçenekler sayfaları için Otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)

 Nesneyi genişleterek **araç** menüsündeki bir VSPackage 'ın özel **Seçenekler** iletişim kutusunun destekleme özelliklerini desteklemek için bir Otomasyon nesnesi döndürmeyi açıklar `DTE.Properties` .

- [Kod için Otomasyon sağlama](../../extensibility/internals/providing-automation-for-code.md)

 Kodunuz için bir otomasyon modeli oluşturmanın gerekli olmadığı açıklanır. Ancak, bu konuda kod modellerine öngörülü bilgiler sağlayan bir bağlantı sağlanmıştır.

- [Nasıl yapılır: Windows için Otomasyon sağlama](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Otomasyon nesnelerini bir pencerede kullanılabilir hale getirmek istediğinizde ve ortam zaten hazır bir Otomasyon nesnesi sağlamıyorsa, Otomasyonu sağlamanın iyi bir fikir olduğunu açıklar. Araç pencereleri ve belge pencereleri için Otomasyonu açıklar.

- [Otomasyon modelini kullanma](../../extensibility/internals/using-the-automation-model.md)

 , Bir Otomasyon tüketicisinin ilk proje otomasyon nesnelerini nasıl alacağını gösteren iki kod örneği sağlar.

- [Yapılandırma ve Selecteditıtem nesneleri için Otomasyon](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Yapılandırma ve Selectedilıtems nesneleri için Otomasyon hakkında bilgi sağlar.

## <a name="reference"></a>Başvuru
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> Bir VSPackage 'ın DTE Otomasyon nesne modeline nasıl katıldığını gösteren bir kod örneği sağlar. Parametreleri, dönüş değerlerini ve seçili açıklamaları listeler.
