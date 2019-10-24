---
title: Kaynak denetimi VSPackage mimarisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9484aabd0080b0a44d75a8a5f6d90d9217d74b8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723358"
---
# <a name="source-control-vspackage-architecture"></a>Kaynak Denetimi VSPackage’ı Mimarisi
Kaynak denetimi paketi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 'nin sağladığı Hizmetleri kullanan VSPackage ' dır. Sonuç olarak, kaynak denetimi paketi işlevlerini kaynak denetimi hizmeti olarak sağlar. Ayrıca, kaynak denetimi paketi, kaynak denetimini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ile tümleştirmek için kaynak denetim eklentisinden daha çok yönlü bir alternatiftir.

 Katı bir sözleşmeye göre kaynak denetimi eklentisi API 'leri uygulayan bir kaynak denetimi eklentisi. Örneğin, bir eklenti varsayılan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kullanıcı arabirimini (UI) değiştirmez. Üstelik, kaynak denetimi eklentisi API 'SI, bir eklentinin kendi kaynak denetim modelini uygulamasına izin vermez. Ancak, bir kaynak denetimi paketi, bu sınırlamaların her ikisini de içerir. Kaynak denetimi paketi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcının kaynak denetimi deneyimi üzerinde tam denetime sahiptir. Ayrıca, bir kaynak denetimi paketi kendi kaynak denetim modelini ve mantığını kullanabilir ve kaynak denetimi ile ilgili tüm kullanıcı arabirimlerini tanımlayabilir.

## <a name="source-control-package-components"></a>Kaynak denetimi paket bileşenleri
 Mimari diyagramında gösterildiği gibi, kaynak denetimi saplaması adlı bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bileşeni, kaynak denetimi paketini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ile tümleştiren bir VSPackage.

 Kaynak denetimi saplaması aşağıdaki görevleri gerçekleştirir.

- Kaynak denetimi paket kaydı için gerekli olan ortak kullanıcı arabirimini sağlar.

- Kaynak denetimi paketini yükler.

- Kaynak denetimi paketini etkin/devre dışı olarak ayarlar.

  Kaynak denetimi saplaması, kaynak denetimi paketi için etkin hizmeti arar ve IDE 'deki tüm gelen hizmet çağrılarını bu pakete yönlendirir.

  Kaynak denetim bağdaştırıcısı paketi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağladığı özel bir kaynak denetimi paketidir. Bu paket, kaynak denetimi eklentisi API 'sine bağlı olarak kaynak denetimi eklentilerini desteklemek için merkezi bileşendir. Bir kaynak denetimi eklentisi etkin eklentidir, kaynak denetimi saplaması, olaylarını kaynak denetimi bağdaştırıcı paketine gönderir. Kaynak denetim bağdaştırıcısı paketi, kaynak denetimi eklentisi API 'sini kullanarak kaynak denetim eklentisi ile iletişim kurar ve ayrıca tüm kaynak denetimi eklentileri için ortak olan varsayılan bir kullanıcı arabirimi sağlar.

  Kaynak denetimi paketi etkin paket olduğunda, diğer yandan kaynak denetimi saplaması, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] kaynak denetimi paket arabirimlerini kullanarak doğrudan paketle iletişim kurar. Kaynak denetimi paketi kendi kaynak denetimi kullanıcı arabirimini barındırmaktan sorumludur.

  ![Kaynak Denetim Mimarisi grafiği](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Kaynak denetimi paketi için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi kodu veya tümleştirme için bir API sağlamaz. Bunu, kaynak denetimi eklentisinin bir grup işlev ve geri çağırma kümesi uygulaması gereken bir [kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md) bölümünde açıklanan yaklaşımla kontrast sağlar.

  Herhangi bir VSPackage gibi, kaynak denetimi paketi, `CoCreateInstance` kullanılarak oluşturulabilen bir COM nesnesidir. VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> uygulayarak kendisini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE için kullanılabilir hale getirir. Bir örnek oluşturulduğunda, VSPackage, IDE 'deki kullanılabilir hizmetlere ve arabirimlere VSPackage erişimi sağlayan bir site işaretçisini ve bir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> arabirimini alır.

  VSPackage tabanlı bir kaynak denetimi paketi yazmak, kaynak denetimi eklentisi API tabanlı eklentisi yazmadan daha gelişmiş programlama uzmanlığını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)