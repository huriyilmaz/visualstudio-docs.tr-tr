---
title: Kaynak Denetimi VSPackage Mimarisi | Microsoft Docs
description: Kaynak denetimi hizmeti olarak kaynak denetimi hizmeti olarak kullanmak için işlev sağlayan bir VSPackage olan Visual Studio paketi mimarisi hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 02507ef3044e89948b9f852c25f662cb3ad330cd0c94d5fbe3985ff295e28d36
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432155"
---
# <a name="source-control-vspackage-architecture"></a>Kaynak Denetimi VSPackage’ı Mimarisi
Kaynak denetim paketi, IDE'nin sağladığı hizmetleri kullanan bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'dır. Buna karşılık, kaynak denetim paketi, kaynak denetimi hizmeti olarak işlevselliğini sağlar. Ayrıca, kaynak denetimi paketi, kaynak denetimi ile tümleştirerek kaynak denetimi eklentisine göre daha çok yönlü bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alternatiftir.

 Kaynak Denetimi Eklentisi API'sini uygulayan bir kaynak denetimi eklentisi, katı bir sözleşmeye uymalıdır. Örneğin, bir eklenti varsayılan kullanıcı arabiriminin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (UI) yerini aamaz. Ayrıca, Kaynak Denetimi Eklentisi API'si bir eklentinin kendi kaynak denetim modelini uygulamasına olanak tanımaz. Ancak kaynak denetim paketi, bu iki sınırlamanın da üstesinden gelir. Kaynak denetimi paketi, kullanıcının kaynak denetimi deneyimi üzerinde tam denetime [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sahiptir. Ayrıca, kaynak denetim paketi kendi kaynak denetim modelini ve mantığını kullanabilir ve kaynak denetimiyle ilgili tüm kullanıcı arabirimlerini tanımlayabilir.

## <a name="source-control-package-components"></a>Source-Control Paketi Bileşenleri
 Mimari diyagramında gösterildiği gibi Kaynak Denetimi Saplama adlı bir bileşen, ile bir kaynak denetim paketini tümleştiren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir VSPackage'dır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

 Kaynak Denetimi Saplama aşağıdaki görevleri işler.

- Kaynak denetimi paket kaydı için gereken ortak kullanıcı arabirimini sağlar.

- Kaynak denetim paketini yükler.

- Kaynak denetim paketini etkin/etkin değil olarak ayarlar.

  Kaynak Denetimi Saplama, kaynak denetim paketi için etkin hizmeti arar ve IDE'den gelen tüm hizmet çağrılarını bu pakete yönlendirer.

  Kaynak Denetim Bağdaştırıcısı Paketi, sağlayan özel bir kaynak denetim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] paketidir. Bu paket, Kaynak Denetimi Eklentisi API'sini temel alan kaynak denetimi eklentilerini desteklemeye yardımcı olan merkezi bileşendir. Bir kaynak denetimi eklentisi etkin eklenti olduğunda, Kaynak Denetimi Saplama kendi olaylarını Kaynak Denetim Bağdaştırıcısı Paketi'ne gönderir. Buna karşılık, Kaynak Denetim Bağdaştırıcısı Paketi Kaynak Denetimi Eklentisi API'sini kullanarak kaynak denetimi eklentisiyle iletişim kurar ve ayrıca tüm kaynak denetimi eklentileri için ortak olan varsayılan bir kullanıcı arabirimi sağlar.

  Bir kaynak denetim paketi etkin paket olduğunda, Diğer yandan, Kaynak Denetimi Saplama paketi ile Doğrudan Paket [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] arabirimlerini kullanarak Source-Control iletişim kurar. Kaynak denetimi paketi kendi kaynak denetimi kullanıcı arabirimini barındırmadan sorumludur.

  ![Kaynak Denetimi Mimarisi grafiği](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Kaynak denetim paketi için, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleştirme için kaynak denetim kodunu veya API'yi teminz. Bunu, kaynak denetimi eklentisinin katı bir işlev ve geri çağırma kümesi uygulaması gereken Kaynak Denetimi Eklentisi Oluşturma konusunda açıklanan yaklaşımla karşıtlığı kullanın. [](../../extensibility/internals/creating-a-source-control-plug-in.md)

  Tüm VSPackage'lar gibi kaynak denetim paketi de kullanılarak oluşturulacak bir COM `CoCreateInstance` nesnesidir. VSPackage, uygulanarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kendisini IDE'de kullanılabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> yapar. Bir örnek oluşturulduğunda, VSPackage bir site işaretçisi ve IDE'de kullanılabilir hizmetlere ve arabirimlere VSPackage erişimi sağlayan <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> bir arabirim alır.

  VSPackage tabanlı kaynak denetim paketi yazmak, Kaynak Denetimi Eklentisi API'si tabanlı eklenti yazmaktan daha gelişmiş programlama uzmanlığı gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Başlarken](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
