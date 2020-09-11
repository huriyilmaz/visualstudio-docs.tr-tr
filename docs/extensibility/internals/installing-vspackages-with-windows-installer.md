---
title: Windows Installer Ile VSPackages yükleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a7ace9203cd8f21a9e9ab5dc525bf604aeff678
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012210"
---
# <a name="installing-vspackages-with-windows-installer"></a>Windows Installer ile VSPackage Yükleme
VSPackage ile tümleştirme, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dosyaları yalnızca bir kullanıcının bilgisayarına kopyalamaktan daha fazlasını gerektirir. VSPackage yükleyicinizin VSPackage ve bağımlı dosyalarını yüklemesi ve bunları kaydedip tümleştirmeleri gerekir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . VSPackage, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Giriş ekranında ve hakkında iletişim kutusunda bir simge görüntüleme gibi tümleştirme özelliklerinden yararlanabilir.

 Microsoft Windows Installer dosyalar, VSPackages 'leri dağıtmak için önerilen yoldur. Kullanımı kolay Windows Installer paketleri tarafından desteklenen herhangi bir Windows işletim sisteminde çalışabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Daha fazla bilgi için bkz. [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="in-this-section"></a>Bu Bölümde
- [Temel Windows Installer Bilgileri](../../extensibility/internals/windows-installer-basics.md)

 Windows Installer genel bir bakış sağlar.

- [VSPackage Kurulum Senaryoları](../../extensibility/internals/vspackage-setup-scenarios.md)

 Hem VSPackages hem de ' ın yan yana yüklemelerini destekleyebilen farklı yollarını açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Windows Installer Paketi Yazma](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Standart adım yükleyicilerinin, VSPackages 'ı doğru şekilde yüklemek ve bütünleştirmek için izlediği bir genel bakış sunar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)

 Bir yükleyicinin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , VSPackage gereksinimlerine uyulmazsa, onun bileşenlerini algılayıp ve kurulumu iptal edip edebildiğini açıklar.

- [Bileşen Yönetimi](../../extensibility/internals/component-management.md)

 Önceki ürün sürümlerinin bütünlüğünü koruyacak bir yükleyicinin nasıl geliştirileceği açıklanır.

- [VSPackage için Yükleme Dizinini Seçme](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 VSPackages bulma seçeneklerini özetler.

- [VSPackage Kaydı](../../extensibility/internals/vspackage-registration.md)

 VSPackages 'ın yükleme sırasında nasıl kaydedildiğini ve kendi kendine kaydın nasıl kötü bir fikir olduğunu açıklar.

- [Proje Türlerini Dağıtma](../../extensibility/internals/deploying-project-types.md)

 Yönetilen kod proje türleri için yeni proje türü toplayıcısı 'nın nasıl kullanılacağını açıklar.

- [Nasıl Yapılır: Bir Yükleyicinin Kayıt Defteri Bilgilerini Oluşturma](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Yönetilen bir VSPackage için kayıt bildirimi oluşturmak üzere RegPkg.exe nasıl kullanılacağını açıklar.

- [Yükleme Sonrasında çalıştırılması Gereken Komutlar](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 VSPackages ile tümleştirme için yükleme sonrası komutlarının nasıl çalıştırılacağını açıklar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Windows Installer ile VSPackage Kaldırma](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Kullanıcılar VSPackage 'ı kaldırırken yükleyicinizin gerçekleştirmesi gereken adımları açıklar.