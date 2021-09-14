---
title: Özellikleri Genişletme | Microsoft Docs
description: Uygulamalı ve uygulamalı arabirimler hakkında bilgi edinmek ve uygulamanın özellik listesini genişletmek için Visual Studio Özellikler penceresi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3f631e09287c6d28aa61ea7832d3f4d5241548e1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725069"
---
# <a name="extend-properties"></a>Özellikleri genişletme
Özellikler [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **penceresi** COM ve COM+ bileşenleri için evrensel bir özellik tarayıcısıdır ve tüm ürünleri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] destekler. Özellikler **penceresi,** o anda seçili olan nesnenin tasarım zamanı özelliklerini tümleşik geliştirme ortamındaki (IDE) herhangi bir pencerede listeley etmek için tür bilgileri ve COM+ meta `ITypeInfo` verileriyle çalışır.

  Klavyede **F4** tuşuna basılarak veya Görünüm menüsünde Özellikler Penceresi seçerek açılabilir Özellikler penceresi, seçili nesnelerin yapılandırmadan bağımsız, tasarım zamanı özelliklerini ve olaylarını görüntülemek ve düzenlemek için kullanılır.   Çözümler ve projelerle ilişkili yapılandırmaya bağımlı özellikler, Özellik sayfalarında [görüntülenir.](../../extensibility/internals/property-pages.md) Daha fazla bilgi için, [Yapılandırma seçeneklerini yönetme.](../../extensibility/internals/managing-configuration-options.md)

 ![Özellikler penceresi genel bakış](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Özellikler penceresi

 Bu bölümde Özellikler penceresinin tek tek alanlarıyla ilgili ayrıntılı bilgiler ve pencereyi doldurmak için uygulamalı ve çağırmalısınız arabirimler yer almaktadır. 

## <a name="in-this-section"></a>Bu bölümde
- [Özellikler penceresi genel bakış](../../extensibility/internals/properties-window-overview.md)

 Araç penceresine ve **belge** penceresine göre Özellikler penceresinin amacını açıklar.

- [Şablon ilkesi ve Özellikler penceresi](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Bir projenin bir kurumsal şablon projesinde nasıl yer içerdiğini ve bu kurumsal şablon projesinin ilkeyi nasıl zorlay olduğunu tartışan.

- [Özellikler penceresi alanları ve arabirimleri seçin](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Özellikler penceresinde hangi bilgilerin görüntülenmiyor olduğunu belirleyen seçimin **temelini** açıklar.

- [Özellikler penceresi listesi](../../extensibility/internals/properties-window-object-list.md)

 Özellikler penceresi nesne  listesinin amacını açıklar ve bu listeden farklı bir nesnenin bir çağrıyı tetikleyene kadar ortamda yeni bir nesnenin seç olduğu konusunda bilgi sahibi olduğunu açıklar.

- [Özellikler penceresi düğmeleri](../../extensibility/internals/properties-window-buttons.md)

 Özellikler penceresi araç çubuğunda görüntülenen dört varsayılan düğmenin **amacını** açıklar.

- [Özellikler görüntüleme kılavuzu](../../extensibility/internals/properties-display-grid.md)

 Özellik adlarının ve özellik değerlerinin alanlarının kılavuzda nerede yer alan olduğunu açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Project türleri](../../extensibility/internals/project-types.md)

 Projeleri IDE'nin yapı taşları [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olarak ele almaktadır.

- [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)

 Uygulamaları derleme sırasında sürekli test etmek [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve hata ayıklamak için platformu nasıl kullanabileceğinizi açıklar.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Bir nesnenin yöntemleri ve özellikleri hakkında bilgilere erişmek ve bu bilgileri almak için geç bağlı bir mekanizma sağlayarak, ilk olarak otomasyonu desteklemek `IDispatch` üzere tasarlanmış arabirimini açıklar.

- [Uygulama ayarlarını yönetme (.NET)](../../ide/managing-application-settings-dotnet.md)

 Özellik değerlerinin, uygulamanın derlenmiş kodu yerine bir dış yapılandırma dosyasında depolandığı şekilde, uygulama ayarlarını yapılandırmanıza izin veren bir genel bakış sağlar.

- [Çözümler ve projeler](../../ide/solutions-and-projects-in-visual-studio.md)

 Çözümler ve projeler aracılığıyla geliştirme çalışmanız için gereken başvurular, veri bağlantıları, klasörler ve dosyalar gibi öğeleri ne kadar verimli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir şekilde yönetebilirsiniz?

- [Diğer bölümleri Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Hizmetlerinin geri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kalanıyla eşan kullanıcı arabirimi öğeleri oluşturmak için nasıl kullanılası [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] açıklanmış.
