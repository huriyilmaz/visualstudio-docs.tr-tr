---
title: Özellikleri genişletme | Microsoft Docs
description: Visual Studio Özellikler penceresi Özellikler listesini genişletmek için uygulamanız ve çağırmanız gereken arabirimler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b1006f74cd2de03b4fe74e090d7ffcd1c921e5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069653"
---
# <a name="extend-properties"></a>Özellikleri Genişlet
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Özellikler** penceresi, com ve com+ bileşenleri için bir evrensel Özellik tarayıcısıdır ve tüm [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ürünleri destekler. **Özellikler** penceresi, `ITypeInfo` Tümleşik GELIŞTIRME ortamındaki (IDE) diğer herhangi bir pencerede seçili olan nesnenin tasarım zamanı özelliklerini listelemek için tür bilgileri ve com+ meta verileri ile birlikte kullanılabilir.

 Klavyede **F4** tuşuna basılarak veya **Görünüm** menüsündeki **Özellikler penceresini** seçerek açılabilen **Özellikler** penceresi, yapılandırma bağımsız, tasarım zamanı özelliklerini ve seçili nesnelerin olaylarını görüntülemek ve düzenlemek için kullanılır. Çözümlerle ve projelerle ilişkili yapılandırma bağımlı özellikler, [özellik sayfalarında](../../extensibility/internals/property-pages.md)görüntülenir. Daha fazla bilgi için [yapılandırma seçeneklerini yönetin](../../extensibility/internals/managing-configuration-options.md).

 ![Özellikler penceresi genel bakış](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Özellikler penceresi

 Bu bölümde, **Özellikler** penceresinin bireysel alanlarıyla ilgili ayrıntılı bilgiler ve pencereyi doldurmak için uygulamanız ve çağırmanız gereken arabirimler yer almaktadır.

## <a name="in-this-section"></a>Bu bölümde
- [Özellikler penceresi genel bakış](../../extensibility/internals/properties-window-overview.md)

 Araç penceresi ve belge penceresine göre **Özellikler** penceresinin amacını açıklar.

- [Şablon İlkesi ve Özellikler penceresi](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Projenin bir kurumsal şablon projesinde nasıl dahil olduğunu ve bu kuruluş şablonu projesinin ilkeyi nasıl zorlayacağını açıklar.

- [Özellikler penceresi alanları ve arabirimleri](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 **Özellikler** penceresinde hangi bilgilerin görüntülendiğini belirleyen seçimin temelini açıklar.

- [Özellikler penceresi nesne listesi](../../extensibility/internals/properties-window-object-list.md)

 Bu listedeki farklı bir nesnenin bir çağrıyı tetiklediği, ortamın yeni bir nesne seçilmiş olduğunu bilgilendirdiğini açıklayan **Özellikler** penceresi nesne listesinin amacını açıklar.

- [Özellikler penceresi düğmeleri](../../extensibility/internals/properties-window-buttons.md)

 **Özellikler** penceresi araç çubuğunda görünen dört varsayılan düğmenin amacını açıklar.

- [Özellikler görüntü Kılavuzu](../../extensibility/internals/properties-display-grid.md)

 Özellik adlarının ve özellik değerleri alanlarının kılavuzda nerede bulunduğu açıklanmaktadır.

## <a name="related-sections"></a>İlgili bölümler
- [Proje türleri](../../extensibility/internals/project-types.md)

 Projeleri IDE 'nin yapı taşları olarak açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Derleme ve oluşturma](../../ide/compiling-and-building-in-visual-studio.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Uygulamaları oluştururken sürekli test ve hata ayıklama için platformu nasıl kullanabileceğinizi açıklar.

- [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 `IDispatch`Bir nesnenin yöntemleri ve özellikleri hakkında bilgi almak ve erişmek için bir geç bağlantılı mekanizma sağlamak üzere ilk olarak Otomasyonu destekleyecek şekilde tasarlanan arabirimi açıklar.

- [Uygulama ayarlarını yönetme (.NET)](../../ide/managing-application-settings-dotnet.md)

 Uygulamanızı, özellik değerlerinin uygulamanın derlenmiş kodu yerine bir dış yapılandırma dosyasında depolanması için yapılandırmanıza olanak sağlayan uygulama ayarlarına genel bir bakış sağlar.

- [Çözümler ve projeler](../../ide/solutions-and-projects-in-visual-studio.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Çözümler ve projeler aracılığıyla geliştirme çabalarınız için gereken başvurular, veri bağlantıları, klasörler ve dosyalar gibi öğeleri verimli bir şekilde nasıl yönettiğini açıklar.

- [Visual Studio 'nun diğer kısımlarını genişletme](../../extensibility/extending-other-parts-of-visual-studio.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Hizmetlerin, geri kalanı ile eşleşen kullanıcı arabirimi öğeleri oluşturmak için nasıl kullanılacağını açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
