---
title: Otomasyon modeline katkıda bulunma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c84ea078f9b7c1268b765111cc400f6e51b783f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196991"
---
# <a name="contributing-to-the-automation-model"></a>Otomasyon Modeline Katkıda Bulunma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio, ortamı özelleştirmek için bir Otomasyon arabirimleri kümesi sağlar. Otomasyon modeli, son kullanıcıların Visual Studio eklentileri ve uzantıları oluşturmalarına olanak tanıyan nesne modelidir.  
  
 Ayrıca, Otomasyon modeline katkıda bulunmak için bir VSPackage geliştiricisi olarak size uygundur; Bunu yaparak, VSPackage 'ın son kullanıcılarını eklenti oluşturmak ve genellikle VSPackage 'ı kullandıklarında tutarlı bir kullanıcı modeli deneyimi sağlamak için etkinleştirirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Son Kullanıcı deneyimini tutarlı hale getirmek için VSPackage 'ı tasarlarken bir dizi yönerge izleyerek VSPackage için otomasyon modelinin içindeki fikirleri takip edebilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Otomasyon Modeline Genel Bakış](../../extensibility/internals/automation-model-overview.md)  
 , Ortak ortamın ana modellerini denetleyen ilgili nesne grupları olarak otomasyon modelini tanımlar. Bu nesne kümesi, otomasyon modeli diyagramında görüntülenir.  
  
 [VSPackage’lar için Otomasyon Sağlama](../../extensibility/internals/providing-automation-for-vspackages.md)  
 VSPackage için Otomasyon sağlamanın iki ana yolunu açıklar.  
  
 [Proje Nesnelerini Kullanıma Sunma](../../extensibility/internals/exposing-project-objects.md)  
 VSPackage 'a özgü nesneler oluşturmak için adım adım yönergeler sağlar.  
  
 [Proje Modelleme](../../extensibility/internals/project-modeling.md)  
 Yeni proje türü için Otomasyon oluşturmak için gereken standart proje nesnelerini açıklar ve proje otomasyonunun izlediği yolu gösterir. Bu konu ayrıca sınıflar için bildirimlerin ve uygulamanın listelerinin listesini de sağlar.  
  
 [Olayları Gösterme](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Otomasyon modelinize yönelik olay oluşturmaya yönelik adım adım yönergeler sağlar.  
  
 [Seçenekler Sayfaları için Otomasyon Desteği](../../extensibility/internals/automation-support-for-options-pages.md)  
 Nesneyi genişleterek **araç** menüsündeki bir VSPackage 'ın özel **Seçenekler** iletişim kutusunun destekleme özelliklerini desteklemek için bir Otomasyon nesnesi döndürmeyi açıklar `DTE.Properties` .  
  
 [Kod için Otomasyon Sağlama](../../extensibility/internals/providing-automation-for-code.md)  
 Kodunuz için bir otomasyon modeli oluşturmanın gerekli olmadığı açıklanır. Ancak, bu konuda kod modellerine öngörülü bilgiler sağlayan bir bağlantı sağlanmıştır.  
  
 [Nasıl Yapılır: Windows için Otomasyon Sağlama](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Otomasyon nesnelerini bir pencerede kullanılabilir hale getirmek istediğinizde ve ortam zaten hazır bir Otomasyon nesnesi sağlamıyorsa, Otomasyonu sağlamanın iyi bir fikir olduğunu açıklar. Araç pencereleri ve belge pencereleri için Otomasyonu açıklar.  
  
 [Otomasyon Modelini Kullanma](../../extensibility/internals/using-the-automation-model.md)  
 , Bir Otomasyon tüketicisinin ilk proje otomasyon nesnelerini nasıl alacağını gösteren iki kod örneği sağlar.  
  
 [Yapılandırma ve SelectedItem Nesneleri için Otomasyon](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Seçilen öğeler için yapılandırma seçenekleri ve otomasyon otomasyonu hakkında bilgi sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Bir VSPackage 'ın DTE Otomasyon nesne modeline nasıl katıldığını gösteren bir kod örneği sağlar. Parametreleri, dönüş değerlerini ve seçili açıklamaları listeler.  
  
## <a name="related-sections"></a>İlgili Bölümler
