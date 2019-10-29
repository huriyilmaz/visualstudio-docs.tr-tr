---
title: Windows Installer paketi yazma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa967b5f23ff9f4e5afa67b9b1cb4e83707616c6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982236"
---
# <a name="author-a-windows-installer-package"></a>Windows Installer paketi yazma
Veri sürücüleri Windows Installer modeli. Dosyaları kopyalamak ve kayıt defteri girişlerini yazmak için bir yordamsal betik yazmak yerine, dosya ve kayıt defteri verilerini içeren veritabanı tablolarında satır ve sütun yazarınız.

## <a name="database-entries"></a>Veritabanı girdileri
Bir VSPackage yüklemek için, bir Windows Installer paketi aşağıdaki görevleri gerçekleştirmek üzere veritabanı girdileri içermelidir:

- VSPackage 'ın desteklediği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürümlerini bulmak için sistemi arayın (AppSearch, CompLocator, RegLocator, DrLocator ve Signature içeren Windows Installer tabloları kullanarak).

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desteklenen bir sürümü yüklü değilse veya VSPackage 'ın başka bir sistem gereksinimi karşılanmazsa (LaunchCondition tablosu kullanılarak) yüklemeyi iptal edin.

- VSPackage ve bağımlı dosyaları (Dizin, bileşen ve dosya tablolarını kullanarak) yükler.

- Kayıt defterine VSPackage için uygun bilgileri ekleyin (kayıt defteri tablosunu kullanarak).

- **Devenv. exe/Setup** öğesini çağırarak (CustomAction tablosunu kullanarak) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage 'ı tümleştirin.

Daha fazla bilgi için bkz. [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Kurulum araçları
Çeşitli üçüncü taraf kurulum araçları, Windows Installer paketlerine yönelik bir geliştirme ortamı sağlar. Aşağıdaki ücretsiz araçlar kullanılabilir:

- InstallShield Limited sürümü

   Visual Studio **Yeni proje** iletişim kutusunu kullanarak, InstallShield 'ın sınırlı bir sürümünü edinebilirsiniz. **Diğer proje türleri** ' ni genişletin ve ardından **Kurulum ve dağıtım '** ı seçin. InstallShield şablonunu seçin.

- Windows Installer XML araç takımı

   Windows Installer XML (WiX) araç takımı, XML kaynak dosyalarından Windows Installer paketleri oluşturur. WiX araç takımı, Microsoft açık kaynaklı bir projem. [WX araç](https://sourceforge.net/projects/wix/)takımından kaynak kodu ve yürütülebilir dosyaları indirebilirsiniz.

   [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]kullanarak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ile tümleştirilen ticari ürünler için bkz. [Visual Studio Market](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer Ile VSPackages 'ı yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)