---
title: Visual Studio 'nun birden çok sürümünü destekleme 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779419"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Visual Studio'nun Birden Çok Sürümünü Destekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Yan yana* terimi, bir ürünün birden çok sürümünü aynı bilgisayara yükleyip koruyabilmeniz anlamına gelir. VSPackages için, bir kullanıcının aynı bilgisayarda birçok Visual Studio sürümü yüklü olabileceği anlamına gelir. Ancak, VSPackages 'ın tek bir Visual Studio sürümüne yüklenmiş yan yana sürümlerine sahip olabilirsiniz.

 VSPackage 'ın, Visual Studio 'nun yan yana sürümlerine yüklenebilmesini sağlamak için aşağıdakileri göz önünde bulundurun:

- Hangi yan yana uygulama stratejisini izlemek istediğinizi belirlemelisiniz.

     Daha fazla bilgi için bkz. [paylaşılan ve sürümlü VSPackages arasında seçim yapma](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- Çözümünüz ve proje dosyası biçimlerinizin uygulama stratejinize uyması gerekir.

     Daha fazla bilgi için bkz. [özel projeleri yükseltme](../misc/upgrading-custom-projects.md) ve [yan yana dağıtımlar Için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Yükleyicinizin uygulama stratejinizi işlemesi gerekir, böylece sürümlü bileşenler ve ayrıca tüm sürümler genelinde paylaşılan bileşenler doğru şekilde yüklenip kaydedilir.

     Daha fazla bilgi için bkz. Windows Installer ve ayrıca [bileşen yönetimi](../extensibility/internals/component-management.md) [Ile VSPackages yükleme](../extensibility/internals/installing-vspackages-with-windows-installer.md) .

    > [!NOTE]
    > Visual Studio 'nun bir sürümünü yüklemek için de karşılık gelen bir sürümü de yüklenir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Örneğin, Visual Studio 2010 ve Visual Studio 2012 'nin aynı bilgisayara yüklenmesi, sırasıyla 4,0 ve 4,5 sürümlerini de yüklüyor [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="in-this-section"></a>Bu Bölümde
 [Paylaşılan ve sürümlü VSPackages arasında seçim yapma](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage 'inizdeki yan yana sorunların nasıl çözümleneceğini açıklar.

 [Yan yana dağıtımlar Için dosya adı uzantılarını kaydetme](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage 'ın dosya ilişkilendirmelerini yan yana bir senaryoya nasıl kaydedebileceğinizi açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [VSPackages yükleme](../misc/installing-vspackages.md) VSPackages oluşturma ve yüklemeyi ve aynı anda Visual Studio 'nun birden çok sürümünü çalıştıran kullanıcıları desteklemeyi açıklar.
