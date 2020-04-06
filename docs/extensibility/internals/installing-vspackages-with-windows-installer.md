---
title: Windows Installer ile VSPackages Yükleme | Microsoft Dokümanlar
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
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707455"
---
# <a name="installing-vspackages-with-windows-installer"></a>Windows Installer ile VSPackage Yükleme
VSPackage'ınızı bir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanıcının bilgisayarına kopyalamaktan daha fazlası gerektirir. VSPackage'ınızın yükleyicisi VSPackage'ı ve onun bağımlı dosyalarını [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]yüklemeli ve kaydolmalı ve 'ye entegre etmelidir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage'ınız, sıçrama ekranında bir simge görüntüleme ve Hakkında iletişim kutusu gibi tümleştirme özelliklerinden yararlanabilir.

 Microsoft Windows Installer dosyaları, VSPackages'ınızı dağıtmanın önerilen yoludur. Kullanımı kolay Windows Installer paketleri tarafından [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]desteklenen herhangi bir Windows işletim sisteminde çalıştırılabilir. Daha fazla bilgi için [Windows Installer'a](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)bakın.

## <a name="in-this-section"></a>Bu Bölümde
- [Temel Windows Installer Bilgileri](../../extensibility/internals/windows-installer-basics.md)

 Windows Yükleyici'ye genel bir bakış sağlar.

- [VSPackage Kurulum Senaryoları](../../extensibility/internals/vspackage-setup-scenarios.md)

 Hem VSPackages'lerinizin hem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de .'nüzün yan yana kurulumlarını desteklediğiniz farklı şekillerde tartışır.

- [Windows Installer Paketi Yazma](../../extensibility/internals/authoring-a-windows-installer-package.md)

 VSPackages'i doğru yüklemek ve entegre etmek için yükleyicilerin izlediği tipik adımlara genel bir bakış [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sağlar.

- [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)

 VSPackage gereksinimleri karşılanmazsa yükleyicinin ve bileşenlerinin nasıl algılanabileceğini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve kurulumu nasıl iptal edebildiğini açıklar.

- [Bileşen Yönetimi](../../extensibility/internals/component-management.md)

 Önceki ürün sürümlerinin bütünlüğünü koruyacak bir yükleyicinin nasıl geliştireceğini tartışır.

- [VSPackage için Yükleme Dizinini Seçme](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 VSPackages'ı bulma seçeneklerini özetler.

- [VSPackage Kaydı](../../extensibility/internals/vspackage-registration.md)

 VSPackages'ın yükleme zamanında nasıl kaydolduğunu ve kendi kendine kayıt olmanın neden kötü bir fikir olduğunu tartışır.

- [Proje Türlerini Dağıtma](../../extensibility/internals/deploying-project-types.md)

 Yönetilen kod proje türleri için yeni proje türü toplayıcısının nasıl kullanılacağını tartışır.

- [Nasıl Yapılır: Bir Yükleyicinin Kayıt Defteri Bilgilerini Oluşturma](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Yönetilen bir VSPackage için bir kayıt bildirimi oluşturmak için RegPkg.exe'nin nasıl kullanılacağını açıklar.

- [Yükleme Sonrasında çalıştırılması Gereken Komutlar](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 VSPackages'i tümleştirmek için yükleme sonrası [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]komutların nasıl çalıştırılabildiğini açıklar.

- [Windows Installer ile VSPackage Kaldırma](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Kullanıcılar VSPackage'ınızı kaldırdığında yükleyicinizin gerçekleştirmesi gereken adımları açıklar.
