---
title: Otomasyon Modeline Katkıda Bulunmak | Microsoft Dokümanlar
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
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709265"
---
# <a name="contribute-to-the-automation-model"></a>Otomasyon modeline katkıda bulunmak
Visual Studio, ortamı özelleştirmek için bir dizi otomasyon arabirimi sağlar. Otomasyon modeli, son kullanıcıların Visual Studio eklentileri ve uzantıları oluşturmasını sağlayan nesne modelidir.

 Buna ek olarak, bir VSPackage geliştiricisi olarak otomasyon modeline katkıda bulunmanız uygundur; bunu yaparak, VSPackage'ınızın son kullanıcılarının eklentiler oluşturmasını ve genellikle VSPackage'ınızı 'de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kullandıklarında tutarlı bir kullanıcı modeli deneyimi sağlamasını sağlarsınız.

 Son kullanıcı deneyimini tutarlı kılmak için, VSPackage'ınızı tasarlarken bir dizi yönergeye uyabilirsiniz, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]böylece VSPackage'ınız için otomasyon modeli fikirleri takip edebilirsiniz.

## <a name="in-this-section"></a>Bu bölümde
- [Otomasyon modeline genel bakış](../../extensibility/internals/automation-model-overview.md)

 Otomasyon modelini, ortak ortamın ana yönlerini kontrol eden ilgili nesne grupları olarak tanımlar. Bu nesne kümesi otomasyon modelinin diyagramında resmedilmiştir.

- [VSPackages için otomasyon sağlayın](../../extensibility/internals/providing-automation-for-vspackages.md)

 VSPackage'ınız için otomasyon sağlamanın iki ana yolunu tartışır.

- [Proje nesnelerini açığa çıkarma](../../extensibility/internals/exposing-project-objects.md)

 VSPackage'a özgü nesneler oluşturmak için adım adım yönergeler sağlar.

- [Proje modelleme](../../extensibility/internals/project-modeling.md)

 Yeni proje türünüz için otomasyon oluşturmak için gereken standart proje nesnelerini açıklar ve proje otomasyonunun izlediği yolu gösterir. Bu konu aynı zamanda sınıflar için bildirimlerin ve uygulama listeleri sağlar.

- [Olayları açığa çıkarma](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Otomasyon modeliniz için etkinlik oluşturmak için adım adım yönergeler sağlar.

- [Seçenekler sayfaları için otomasyon desteği](../../extensibility/internals/automation-support-for-options-pages.md)

 Nesneyi genişleterek Araç menüsündeki VSPackage'ın özel **Seçenekler** iletişim kutusunun **Tool** özelliklerini desteklemek için `DTE.Properties` bir otomasyon nesnesinin nasıl döndürüleceklerini açıklar.

- [Kod için otomasyon sağlayın](../../extensibility/internals/providing-automation-for-code.md)

 Kodunuz için bir otomasyon modeli oluşturmanın gerekli olmadığını açıklar. Ancak, kod modelleri içine anlayışlı bilgi sağlayan bu konuda bir bağlantı sağlanır.

- [Nasıl yapilir: Windows için otomasyon sağlama](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Otomasyon sağlamanın, bir pencerede otomasyon nesnelerini kullanılabilir hale getirmek istediğinizde iyi bir fikir olduğunu ve ortamın hazır bir otomasyon nesnesi sağlamadığını açıklar. Takım pencereleri ve belge pencereleri için otomasyonu tartışır.

- [Otomasyon modelini kullanma](../../extensibility/internals/using-the-automation-model.md)

 Otomasyon tüketicisinin ilk proje otomasyon nesnelerini nasıl elde ettiğini gösteren iki kod örneği sağlar.

- [Yapılandırma ve SelectedItem nesneleri için otomasyon](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Yapılandırma ve SelectedItems nesneleri için otomasyon hakkında bilgi sağlar.

## <a name="reference"></a>Başvuru
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>VSPackage'ın DTE otomasyon nesnesi modeline nasıl katıldığını gösteren bir kod örneği sağlar. Parametreleri, iade değerlerini ve seçili açıklamaları listeler.
