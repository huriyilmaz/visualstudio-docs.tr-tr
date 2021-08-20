---
title: Windows Installer paketi yazma | Microsoft Docs
description: dosya ve kayıt defteri verilerini içeren veritabanı tablolarından oluşan Visual Studio için Windows Installer paketini nasıl yazacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9b2a279b178a7158db8bde117c3aa1e97ad2925f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086930"
---
# <a name="author-a-windows-installer-package"></a>Windows Installer paketi yazma
veri sürücüleri Windows Installer modeli. Dosyaları kopyalamak ve kayıt defteri girişlerini yazmak için bir yordamsal betik yazmak yerine, dosya ve kayıt defteri verilerini içeren veritabanı tablolarında satır ve sütun yazarınız.

## <a name="database-entries"></a>Veritabanı girdileri
bir vspackage yüklemek için, bir Windows Installer paketi aşağıdaki görevleri gerçekleştirmek üzere veritabanı girdileri içermelidir:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]vspackage desteklerinizin sürümlerini bulmak için sistemi arayın (appsearch, complocator, reglocator, drlocator ve Signature içeren Windows Installer tabloları kullanarak).

- Desteklenen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bir sürümü yüklü değilse veya VSPackage için başka bir sistem gereksinimi karşılanmazsa (LaunchCondition tablosu kullanılarak) yüklemeyi iptal edin.

- VSPackage ve bağımlı dosyaları (Dizin, bileşen ve dosya tablolarını kullanarak) yükler.

- Kayıt defterine VSPackage için uygun bilgileri ekleyin (kayıt defteri tablosunu kullanarak).

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **devenv.exe/Setup** ' i çağırarak VSPackage 'ı tümleştirin (CustomAction tablosu kullanarak).

daha fazla bilgi için bkz. [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Kurulum araçları
çeşitli üçüncü taraf kurulum araçları, Windows Installer paketlerine yönelik bir geliştirme ortamı sağlar. Aşağıdaki ücretsiz araçlar kullanılabilir:

- InstallShield Limited sürümü

   **yeni Visual Studio Project** iletişim kutusu aracılığıyla ınstallshield 'ın sınırlı bir sürümünü edinebilirsiniz. **diğer Project türlerini** genişlettikten sonra **kurulum ve dağıtım '** ı seçin. InstallShield şablonunu seçin.

- Windows Yükleyici XML araç takımı

   Windows Installer xml (wix) araç takımı, xml kaynak dosyalarından Windows Installer paketleri oluşturur. WiX araç takımı, Microsoft açık kaynaklı bir projem. [WX araç](https://sourceforge.net/projects/wix/)takımından kaynak kodu ve yürütülebilir dosyaları indirebilirsiniz.

   kullanarak ile tümleşen ticari ürünler için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , bkz. [Visual Studio marketi](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile vspackages 'i yükler](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
