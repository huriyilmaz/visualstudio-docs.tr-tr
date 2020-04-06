---
title: Windows Yükleyici Paketi Yazma | Microsoft Dokümanlar
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
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710035"
---
# <a name="author-a-windows-installer-package"></a>Windows Installer paketi yazma
Veriler Windows Yükleyici modelini yönlendirir. Dosyaları kopyalamak ve kayıt defteri girişlerini yazmak için bir yordam komut dosyası yazmak yerine, örneğin, dosya ve kayıt defteri verileri içeren veritabanı tablolarında satırlar ve sütunlar yazarsınız.

## <a name="database-entries"></a>Veritabanı girişleri
VSPackage yüklemek için, bir Windows Installer paketi aşağıdaki görevleri gerçekleştirmek için veritabanı girişleri içermelidir:

- VSPackage desteklerinizin sürümlerini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bulmak için sistemde arama yapın (AppSearch, CompLocator, RegLocator, DrLocator ve Signature'ı içeren Windows Installer tablolarını kullanarak).

- Desteklenen bir sürümü yüklü [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] değilse veya VSPackage'ın başka bir sistem gereksinimi karşılanmazsa (LaunchCondition tablosunu kullanarak) yüklemeyi iptal edin.

- VSPackage'ı ve bağımlı dosyaları (dizin, bileşen ve dosya tablolarını kullanarak) yükleyin.

- VSPackage için uygun bilgileri kayıt defterine ekleyin (Kayıt Defteri tablosunu kullanarak).

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Devenv.exe /setup** (CustomAction tablosunu kullanarak) çağırarak VSPackage'ı entegre edin.

Daha fazla bilgi için [Windows Installer'a](/windows/desktop/Msi/windows-installer-portal)bakın.

## <a name="setup-tools"></a>Kurulum araçları
Çeşitli üçüncü taraf kurulum araçları, Windows Installer paketleri için bir geliştirme ortamı sağlar. Aşağıdaki ücretsiz araçlar mevcuttur:

- InstallShield sınırlı sayıda üretilmiştir

   Visual Studio **New Project** iletişim kutusundan InstallShield'in sınırlı bir sürümünü alabilirsiniz. **Diğer Proje Türlerini** Genişletin ve ardından **Kurulum ve Dağıtım'ı**seçin. InstallShield şablonuna seçin.

- Windows Installer XML araç seti

   Windows Installer XML (WiX) araç kümesi, XML kaynak dosyalarından Windows Installer paketleri oluşturur. WiX araç kümesi bir Microsoft açık kaynak projesidir. Kaynak kodu ve çalıştırılabilir leri [Wix araç setinden](https://sourceforge.net/projects/wix/)indirebilirsiniz.

   Kullanarak entegre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ticari ürünler [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]için, [Visual Studio Marketplace](https://marketplace.visualstudio.com/)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer ile VSPackages yükleyin](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
