---
title: Visual Studio'nun Birden Fazla Versiyonunu Destekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699483"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Visual Studio'nun Birden Çok Sürümünü Destekleme
Yan *yana* terim, aynı bilgisayara bir ürünün birden çok sürümü yükleyebileceğiniz ve bakımını yapabileceğiniz anlamına gelir. VSPackages için bu, bir kullanıcının aynı bilgisayarda birkaç Visual Studio sürümü yüklenmiş olabileceği anlamına gelir. Ancak, VSPackages'lerinizin yan yana sürümlerini Visual Studio'nun tek bir sürümüne yükleyemezsiniz.

 VSPackage'ınızı Visual Studio'nun yan yana sürümlerine yüklenebilmeden önce aşağıdakileri göz önünde bulundurun:

- Hangi yan yana uygulama stratejisini izlemek istediğinizi belirlemeniz gerekir.

   Daha fazla bilgi için bkz: [Paylaşılan ve Sürümlü VSPackages Arasında Seçim](../extensibility/choosing-between-shared-and-versioned-vspackages.md)Yapmak.

- Çözüm ve proje dosya biçimleriniz uygulama stratejinize uygun olmalıdır.

   Daha fazla bilgi için bkz: [Özel Projeleri Yükseltme](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) ve Yan Yana [Dağıtımlar için Dosya Adı Uzantılarını Kaydetme.](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)

- Yükleyiciniz, sürümlenmiş bileşenlerin ve ayrıca tüm sürümler arasında paylaşılan bileşenlerin doğru şekilde yüklenmesi ve kaydedilmesi için uygulama stratejinizi işlemelidir.

   Daha fazla bilgi için Windows [Installer ile VSPackages Yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md) ve ayrıca [Bileşen Yönetimi](../extensibility/internals/component-management.md)bakın.

  > [!NOTE]
  > Visual Studio'nun bir sürümünü yüklemek de .NET Framework'ün ilgili bir sürümünü yükler. Örneğin, Visual Studio 2010 ve Visual Studio 2012'yi aynı bilgisayara yüklemek de sırasıyla .NET Framework'ün 4.0 ve 4.5 sürümlerini yükler.

## <a name="in-this-section"></a>Bu Bölümde
- [Paylaşılan ve Sürümlü VSPackages Arasında Seçim](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage'ınızdaki yan yana sorunların nasıl çözüleceğini açıklar.

- [Yan Yana Dağıtımlar için Dosya Adı Uzantılarını Kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage'ınızın dosya ilişkilendirmelerini yan yana senaryoda nasıl kaydedebileceğini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Windows Installer ile VSPackage Yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)
