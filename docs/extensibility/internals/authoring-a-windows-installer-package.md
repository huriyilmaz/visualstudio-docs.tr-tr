---
title: Windows Installer paketi yazma | Microsoft Docs
description: Dosya ve kayıt defteri verilerini içeren veritabanı tablolarından oluşan bir Visual Studio Windows Installer paketini nasıl yazacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82c96bdf8e73f7d40b41220524edef022c216f1b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190128"
---
# <a name="author-a-windows-installer-package"></a>Windows Installer paketi yazma
Veri sürücüleri Windows Installer modeli. Dosyaları kopyalamak ve kayıt defteri girişlerini yazmak için bir yordamsal betik yazmak yerine, dosya ve kayıt defteri verilerini içeren veritabanı tablolarında satır ve sütun yazarınız.

## <a name="database-entries"></a>Veritabanı girdileri
Bir VSPackage yüklemek için, bir Windows Installer paketi aşağıdaki görevleri gerçekleştirmek üzere veritabanı girdileri içermelidir:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage desteklerinizin sürümlerini bulmak için sistemi arayın (AppSearch, CompLocator, RegLocator, DrLocator ve Signature içeren Windows Installer tabloları kullanarak).

- Desteklenen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir sürümü yüklü değilse veya VSPackage için başka bir sistem gereksinimi karşılanmazsa (LaunchCondition tablosu kullanılarak) yüklemeyi iptal edin.

- VSPackage ve bağımlı dosyaları (Dizin, bileşen ve dosya tablolarını kullanarak) yükler.

- Kayıt defterine VSPackage için uygun bilgileri ekleyin (kayıt defteri tablosunu kullanarak).

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **devenv.exe/Setup** ' i çağırarak VSPackage 'ı tümleştirin (CustomAction tablosu kullanarak).

Daha fazla bilgi için bkz. [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Kurulum araçları
Çeşitli üçüncü taraf kurulum araçları, Windows Installer paketlerine yönelik bir geliştirme ortamı sağlar. Aşağıdaki ücretsiz araçlar kullanılabilir:

- InstallShield Limited sürümü

   Visual Studio **Yeni proje** iletişim kutusunu kullanarak, InstallShield 'ın sınırlı bir sürümünü edinebilirsiniz. **Diğer proje türleri** ' ni genişletin ve ardından **Kurulum ve dağıtım '** ı seçin. InstallShield şablonunu seçin.

- Windows Installer XML araç takımı

   Windows Installer XML (WiX) araç takımı, XML kaynak dosyalarından Windows Installer paketleri oluşturur. WiX araç takımı, Microsoft açık kaynaklı bir projem. [WX araç](https://sourceforge.net/projects/wix/)takımından kaynak kodu ve yürütülebilir dosyaları indirebilirsiniz.

   Kullanarak ile tümleşen ticari ürünler için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , bkz. [Visual Studio Market](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer Ile VSPackages 'ı yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
