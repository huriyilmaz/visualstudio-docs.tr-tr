---
title: Visual Studio 'nun birden çok sürümünü destekleme | Microsoft Docs
description: Vspackaları farklı sürümlere yükleyebilmeleri için Visual Studio 'nun çeşitli sürümlerini nasıl destekleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5d1309c6fcda2b27efdc78e7b31189d3a58edfb8
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715632"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Visual Studio'nun Birden Çok Sürümünü Destekleme
*Yan yana* terimi, bir ürünün birden çok sürümünü aynı bilgisayara yükleyip koruyabilmeniz anlamına gelir. VSPackages için, bir kullanıcının aynı bilgisayarda birçok Visual Studio sürümü yüklü olabileceği anlamına gelir. Ancak, VSPackages 'ın tek bir Visual Studio sürümüne yüklenmiş yan yana sürümlerine sahip olabilirsiniz.

 VSPackage 'ın, Visual Studio 'nun yan yana sürümlerine yüklenebilmesini sağlamak için aşağıdakileri göz önünde bulundurun:

- Hangi yan yana uygulama stratejisini izlemek istediğinizi belirlemelisiniz.

   Daha fazla bilgi için bkz. [paylaşılan ve sürümlü VSPackages arasında seçim yapma](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Çözümünüz ve proje dosyası biçimlerinizin uygulama stratejinize uyması gerekir.

   Daha fazla bilgi için bkz. [özel projeleri yükseltme](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) ve [yan yana dağıtımlar Için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Yükleyicinizin uygulama stratejinizi işlemesi gerekir, böylece sürümlü bileşenler ve ayrıca tüm sürümler genelinde paylaşılan bileşenler doğru şekilde yüklenip kaydedilir.

   Daha fazla bilgi için bkz. Windows Installer ve ayrıca [bileşen yönetimi](../extensibility/internals/component-management.md) [Ile VSPackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md) .

  > [!NOTE]
  > Visual Studio 'nun bir sürümünü yüklemek .NET Framework buna karşılık gelen bir sürümünü de yüklüyor. Örneğin, Visual Studio 2010 ve Visual Studio 2012 'nin aynı bilgisayara yüklenmesi, sırasıyla .NET Framework 4,0 sürümlerini ve 4,5 sürümünü de yüklüyor.

## <a name="in-this-section"></a>Bu Bölümde
- [Paylaşılan ve sürümlü VSPackages arasında seçim yapma](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage 'inizdeki yan yana sorunların nasıl çözümleneceğini açıklar.

- [Yan yana dağıtımlar Için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage 'ın dosya ilişkilendirmelerini yan yana bir senaryoya nasıl kaydedebileceğinizi açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Windows Installer ile VSPackage Yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)
