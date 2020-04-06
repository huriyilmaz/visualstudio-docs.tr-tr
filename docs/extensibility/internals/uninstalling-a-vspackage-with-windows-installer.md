---
title: Windows Installer ile VSPackage Kaldırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fee88e895d40d42114eaf53422503524594b485f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704272"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer ile VSPackage Kaldırma
Windows Installer, vspackage'ınızı yüklemek için yaptıklarını "geri alarak" VSPackage'ınızı kaldırabilir. [Yüklemeden Sonra Çalıştırılması Gereken Komutlarda](../../extensibility/internals/commands-that-must-be-run-after-installation.md) tartışılan özel eylemler de bir kaldırma dan sonra çalıştırılmalıdır. devenv.exe çağrıları yükleme ve yükleme yi kaldırmak için InstallFinalize standart eyleminden hemen önce gerçekleştiğinden, CustomAction ve InstallExecuteSequence tablo girişleri her iki servis talebine de hizmet eder.

> [!NOTE]
> MSI paketini kaldırdıktan sonra çalıştırın. `devenv /setup`

 Genel bir kural olarak, bir Windows Installer paketine özel eylemler eklerseniz, bu eylemleri yükleme yi ve geri alma sırasında işlemeniz gerekir. Örneğin, VSPackage'ınızı kendi kendine kaydetmek için özel eylemler eklerseniz, kaydını çıkarmak için de özel eylemler eklemeniz gerekir.

> [!NOTE]
> Bir kullanıcının VSPackage'ınızı yüklemesi ve daha [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sonra entegre olduğu sürümlerini kaldırması mümkündür. VsPackage'ınızın uninstallation'ının bu senaryoda çalıştığından emin [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]olabilirsiniz.

## <a name="handling-launch-conditions-at-uninstall-time"></a>Kaldırma Zamanında Başlatma Koşullarını İşleme
 LaunchConditions standart eylemi, koşullar yerine getirilmezse hata iletilerini göstermek için LaunchCondition tablosunun satırlarını okur. Başlatma koşulları genellikle sistem gereksinimlerinin karşılandığından emin olmak için kullanıldığından, başlatma koşulu tablosunun `NOT Installed`LaunchConditions satırına koşul ekleyerek yüklemeyi kaldırma sırasında genellikle başlatma koşullarını atlayabilirsiniz.

 Alternatif olarak, `OR Installed` yüklemenin boşaltılması sırasında önemli olmayan başlatma koşullarına eklemek de vardır. Bu, yükleme nin boşaltılması sırasında koşulun her zaman doğru olmasını ve bu nedenle başlatma koşulu hata iletisini görüntülememesini sağlar.

> [!NOTE]
> `Installed`VSPackage'ınızın sistemde zaten yüklendiğini algıladığında Windows Installer'ın belirlediği özelliktir.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)
