---
title: Kaynak denetimi VSPackage mimarisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3cca9e39714f87024b01ab2c925189aacbe22785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183403"
---
# <a name="source-control-vspackage-architecture"></a>Kaynak Denetimi VSPackage’ı Mimarisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi paketi, IDE 'nin sağladığı Hizmetleri kullanan bir VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Sonuç olarak, kaynak denetimi paketi işlevlerini kaynak denetimi hizmeti olarak sağlar. Ayrıca, kaynak denetimi paketi, kaynak denetimi ile tümleştirme için bir kaynak denetimi eklentisinin daha çok yönlü bir alternatifidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Katı bir sözleşmeye göre kaynak denetimi eklentisi API 'leri uygulayan bir kaynak denetimi eklentisi. Örneğin, bir eklenti varsayılan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Kullanıcı arabirimini (UI) değiştirmez. Üstelik, kaynak denetimi eklentisi API 'SI, bir eklentinin kendi kaynak denetim modelini uygulamasına izin vermez. Ancak, bir kaynak denetimi paketi, bu sınırlamaların her ikisini de içerir. Bir kaynak denetimi paketi, bir kullanıcının kaynak denetimi deneyimi üzerinde tam denetime sahiptir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Ayrıca, bir kaynak denetimi paketi kendi kaynak denetim modelini ve mantığını kullanabilir ve kaynak denetimi ile ilgili tüm kullanıcı arabirimlerini tanımlayabilir.  
  
## <a name="source-control-package-components"></a>Kaynak denetimi paket bileşenleri  
 Mimari diyagramında gösterildiği gibi, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kaynak denetimi saplaması adlı bir bileşen, ile bir kaynak denetimi paketini tümleştiren bir VSPackage ' dır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Kaynak denetimi saplaması aşağıdaki görevleri gerçekleştirir.  
  
- Kaynak denetimi paket kaydı için gerekli olan ortak kullanıcı arabirimini sağlar.  
  
- Kaynak denetimi paketini yükler.  
  
- Kaynak denetimi paketini etkin/devre dışı olarak ayarlar.  
  
  Kaynak denetimi saplaması, kaynak denetimi paketi için etkin hizmeti arar ve IDE 'deki tüm gelen hizmet çağrılarını bu pakete yönlendirir.  
  
  Kaynak denetim bağdaştırıcısı paketi, sağlayan özel bir kaynak denetimi paketidir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bu paket, kaynak denetimi eklentisi API 'sine bağlı olarak kaynak denetimi eklentilerini desteklemek için merkezi bileşendir. Bir kaynak denetimi eklentisi etkin eklentidir, kaynak denetimi saplaması, olaylarını kaynak denetimi bağdaştırıcı paketine gönderir. Kaynak denetim bağdaştırıcısı paketi, kaynak denetimi eklentisi API 'sini kullanarak kaynak denetim eklentisi ile iletişim kurar ve ayrıca tüm kaynak denetimi eklentileri için ortak olan varsayılan bir kullanıcı arabirimi sağlar.  
  
  Kaynak denetimi paketi etkin paket olduğunda, diğer yandan kaynak denetimi saplaması, kaynak denetimi paket arabirimlerini kullanarak doğrudan paketiyle iletişim kurar [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] . Kaynak denetimi paketi kendi kaynak denetimi kullanıcı arabirimini barındırmaktan sorumludur.  
  
  ![Kaynak Denetim Mimarisi grafiği](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
  Kaynak denetimi paketi için [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kaynak denetim kodu veya tümleştirme için BIR API sağlamaz. Bunu, kaynak denetimi eklentisinin bir grup işlev ve geri çağırma kümesi uygulaması gereken bir [kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md) bölümünde açıklanan yaklaşımla kontrast sağlar.  
  
  Herhangi bir VSPackage gibi, kaynak denetimi paketi kullanılarak oluşturulabilen bir COM nesnesidir `CoCreateInstance` . VSPackage, uygulayarak kendisini IDE için kullanılabilir hale getirir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Bir örnek oluşturulduğunda, VSPackage, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> IDE 'deki kullanılabilir hizmetlere ve arabirimlere VSPackage erişimi sağlayan bir site işaretçisi ve arabirim alır.  
  
  VSPackage tabanlı bir kaynak denetimi paketi yazmak, kaynak denetimi eklentisi API tabanlı eklentisi yazmadan daha gelişmiş programlama uzmanlığını gerektirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
