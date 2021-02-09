---
title: Kaynak denetimi VSPackage mimarisi | Microsoft Docs
description: Kaynak denetimi hizmeti olarak Visual Studio işlevselliği sağlayan bir VSPackage olan kaynak denetimi paketinin mimarisi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e4de5f46746f79e1c7598e1c2a2a6af6ae1d92a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912683"
---
# <a name="source-control-vspackage-architecture"></a>Kaynak Denetimi VSPackage’ı Mimarisi
Kaynak denetimi paketi, IDE 'nin sağladığı Hizmetleri kullanan bir VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Sonuç olarak, kaynak denetimi paketi işlevlerini kaynak denetimi hizmeti olarak sağlar. Ayrıca, kaynak denetimi paketi, kaynak denetimi ile tümleştirme için bir kaynak denetimi eklentisinin daha çok yönlü bir alternatifidir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Katı bir sözleşmeye göre kaynak denetimi eklentisi API 'leri uygulayan bir kaynak denetimi eklentisi. Örneğin, bir eklenti varsayılan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kullanıcı arabirimini (UI) değiştirmez. Üstelik, kaynak denetimi eklentisi API 'SI, bir eklentinin kendi kaynak denetim modelini uygulamasına izin vermez. Ancak, bir kaynak denetimi paketi, bu sınırlamaların her ikisini de içerir. Bir kaynak denetimi paketi, bir kullanıcının kaynak denetimi deneyimi üzerinde tam denetime sahiptir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Ayrıca, bir kaynak denetimi paketi kendi kaynak denetim modelini ve mantığını kullanabilir ve kaynak denetimi ile ilgili tüm kullanıcı arabirimlerini tanımlayabilir.

## <a name="source-control-package-components"></a>Paket bileşenlerini Source-Control
 Mimari diyagramında gösterildiği gibi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi saplaması adlı bir bileşen, ile bir kaynak denetimi paketini tümleştiren bir VSPackage ' dır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Kaynak denetimi saplaması aşağıdaki görevleri gerçekleştirir.

- Kaynak denetimi paket kaydı için gerekli olan ortak kullanıcı arabirimini sağlar.

- Kaynak denetimi paketini yükler.

- Kaynak denetimi paketini etkin/devre dışı olarak ayarlar.

  Kaynak denetimi saplaması, kaynak denetimi paketi için etkin hizmeti arar ve IDE 'deki tüm gelen hizmet çağrılarını bu pakete yönlendirir.

  Kaynak denetim bağdaştırıcısı paketi, sağlayan özel bir kaynak denetimi paketidir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Bu paket, kaynak denetimi eklentisi API 'sine bağlı olarak kaynak denetimi eklentilerini desteklemek için merkezi bileşendir. Bir kaynak denetimi eklentisi etkin eklentidir, kaynak denetimi saplaması, olaylarını kaynak denetimi bağdaştırıcı paketine gönderir. Kaynak denetim bağdaştırıcısı paketi, kaynak denetimi eklentisi API 'sini kullanarak kaynak denetim eklentisi ile iletişim kurar ve ayrıca tüm kaynak denetimi eklentileri için ortak olan varsayılan bir kullanıcı arabirimi sağlar.

  Kaynak denetimi paketi etkin paket olduğunda, diğer yandan kaynak denetimi saplaması, Source-Control paketi arabirimlerini kullanarak doğrudan paketle iletişim kurar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] . Kaynak denetimi paketi kendi kaynak denetimi kullanıcı arabirimini barındırmaktan sorumludur.

  ![Kaynak Denetim Mimarisi grafiği](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Kaynak denetimi paketi için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetim kodu veya tümleştirme için BIR API sağlamaz. Bunu, kaynak denetimi eklentisinin bir grup işlev ve geri çağırma kümesi uygulaması gereken bir [kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md) bölümünde açıklanan yaklaşımla kontrast sağlar.

  Herhangi bir VSPackage gibi, kaynak denetimi paketi kullanılarak oluşturulabilen bir COM nesnesidir `CoCreateInstance` . VSPackage, uygulayarak kendisini IDE için kullanılabilir hale getirir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Bir örnek oluşturulduğunda, VSPackage, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> IDE 'deki kullanılabilir hizmetlere ve arabirimlere VSPackage erişimi sağlayan bir site işaretçisi ve arabirim alır.

  VSPackage tabanlı bir kaynak denetimi paketi yazmak, kaynak denetimi eklentisi API tabanlı eklentisi yazmadan daha gelişmiş programlama uzmanlığını gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
