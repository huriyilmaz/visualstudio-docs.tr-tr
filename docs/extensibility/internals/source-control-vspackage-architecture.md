---
title: Kaynak Kontrol VSPackage Mimarisi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705078"
---
# <a name="source-control-vspackage-architecture"></a>Kaynak Denetimi VSPackage’ı Mimarisi
Kaynak kontrol paketi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE'nin sağladığı hizmetleri kullanan bir VSPackage'dir. Buna karşılık, bir kaynak denetim paketi bir kaynak denetim hizmeti olarak işlevselliğini sağlar. Ayrıca, kaynak kontrol paketi, kaynak denetimini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Kaynak Denetimi Eklentisi API'sini uygulayan bir kaynak denetim eklentisi sıkı bir sözleşmeye uyar. Örneğin, bir eklenti varsayılan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcı arabiriminin (UI) yerini alamaz. Ayrıca, Kaynak Denetimi Eklentisi API'si bir eklentinin kendi kaynak denetim modelini uygulamasına olanak sağlamaz. Ancak bir kaynak denetim paketi, bu sınırlamaların her ikisini de aşar. Kaynak denetim paketi, bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcının kaynak denetim deneyimi üzerinde tam denetime sahiptir. Ayrıca, bir kaynak denetim paketi kendi kaynak denetim modelini ve mantığını kullanabilir ve kaynak denetimiyle ilgili tüm kullanıcı arabirimlerini tanımlayabilir.

## <a name="source-control-package-components"></a>Kaynak Kontrol Paketi Bileşenleri
 Mimari diyagramda gösterildiği gibi, Kaynak Denetim Saplaması adlı bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bileşen, bir kaynak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]denetim paketini .

 Kaynak Denetim Saplama aşağıdaki görevleri işler.

- Kaynak denetimi paketi kaydı için gerekli olan ortak kullanıcı arabirimi sağlar.

- Bir kaynak kontrol paketi yükler.

- Bir kaynak kontrol paketini etkin/etkin olmayan olarak ayarlar.

  Kaynak Kontrol Saplaması, kaynak kontrol paketi için etkin hizmeti arar ve IDE'den gelen tüm servis çağrılarını bu pakete yönlendirir.

  Kaynak Kontrol Bağdaştırıcı Paketi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sağlayan özel bir kaynak kontrol paketidir. Bu paket, Kaynak Denetimi Eklentisi API'sini temel alan kaynak denetimi eklentilerini desteklemek için merkezi bileşendir. Bir kaynak kontrol eklentisi etkin eklenti olduğunda, Kaynak Denetim Saplaması olaylarını Kaynak Denetim Bağdaştırıcı Paketi'ne gönderir. Buna karşılık, Kaynak Denetim Bağdaştırıcı Paketi Kaynak Denetimi Eklentisi API'sini kullanarak kaynak denetimi eklentisi ile iletişim kurar ve ayrıca tüm kaynak denetimi eklentileri için ortak olan varsayılan bir kullanıcı arabirimi sağlar.

  Bir kaynak kontrol paketi etkin paket olduğunda, diğer taraftan, Kaynak Kontrol Saplaması [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Kaynak Kontrol Paketi arabirimlerini kullanarak paketle doğrudan iletişim kurar. Kaynak kontrol paketi, kendi kaynak denetimi uI barındırma sorumludur.

  ![Kaynak Kontrol Mimarisi grafiği](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Kaynak denetim paketi için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetim kodu veya tümleştirme için API sağlamaz. Bunu, kaynak denetim [eklentisinin](../../extensibility/internals/creating-a-source-control-plug-in.md) katı bir işlev ler ve geri çağırmalar kümesi uygulamak zorunda olduğu bir Kaynak Denetim Eklentisi Oluşturma'da özetlenen yaklaşımla karşılaştırın.

  Herhangi bir VSPackage gibi, bir kaynak kontrol paketi kullanılarak `CoCreateInstance`oluşturulabilir bir COM nesnesidir. VSPackage uygulayarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>IDE için kullanılabilir hale getirir. Bir örnek oluşturulduğunda, VSPackage bir site işaretçisi ve IDE'deki kullanılabilir hizmetlere ve arabirimlere VSPackage erişimi sağlayan bir <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> arabirim alır.

  VSPackage tabanlı kaynak kontrol paketi yazmak, Kaynak Denetimi Eklentisi API tabanlı eklenti yazmaktan daha gelişmiş programlama uzmanlığı gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
