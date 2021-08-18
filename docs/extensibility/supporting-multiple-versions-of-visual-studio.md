---
title: Visual Studio birden çok sürümünü destekleme | Microsoft Docs
description: bazı Visual Studio sürümlerini nasıl destekleyeceğinizi öğrenin ve vspackaları farklı sürümlere yükleyebilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7aa8659754091106cc3f87f13c2e58a14d6b525d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137489"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Visual Studio'nun Birden Çok Sürümünü Destekleme
*Yan yana* terimi, bir ürünün birden çok sürümünü aynı bilgisayara yükleyip koruyabilmeniz anlamına gelir. vspackages için, bir kullanıcının aynı bilgisayarda birden fazla Visual Studio sürümü yüklü olabileceği anlamına gelir. Ancak, Visual Studio tek bir sürümüne yüklenmiş VSPackages 'nin yan yana sürümlerine sahip olabilirsiniz.

 vspackage 'ın Visual Studio yan yana sürümüne yüklenebilmesini sağlamak için önce aşağıdakileri göz önünde bulundurun:

- Hangi yan yana uygulama stratejisini izlemek istediğinizi belirlemelisiniz.

   Daha fazla bilgi için bkz. [paylaşılan ve sürümlü VSPackages arasında seçim yapma](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Çözümünüz ve proje dosyası biçimlerinizin uygulama stratejinize uyması gerekir.

   Daha fazla bilgi için bkz. [özel projeleri yükseltme](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) ve [yan yana dağıtımlar Için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Yükleyicinizin uygulama stratejinizi işlemesi gerekir, böylece sürümlü bileşenler ve ayrıca tüm sürümler genelinde paylaşılan bileşenler doğru şekilde yüklenip kaydedilir.

   daha fazla bilgi için bkz. Windows Installer ve ayrıca [bileşen yönetimi](../extensibility/internals/component-management.md) [ile vspackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md) .

  > [!NOTE]
  > Visual Studio sürümünün yüklenmesi, .NET Framework ilgili bir sürümünü de yüklüyor. örneğin, aynı bilgisayara Visual Studio 2010 ve Visual Studio 2012 ' nin yüklenmesi, sırasıyla .NET Framework ve 4,5 4,0 sürümlerini de yüklüyor.

## <a name="in-this-section"></a>Bu Bölümde
- [Paylaşılan ve sürümlü VSPackages arasında seçim yapma](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage 'inizdeki yan yana sorunların nasıl çözümleneceğini açıklar.

- [Yan yana dağıtımlar Için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage 'ın dosya ilişkilendirmelerini yan yana bir senaryoya nasıl kaydedebileceğinizi açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Windows Installer ile VSPackage Yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md)
