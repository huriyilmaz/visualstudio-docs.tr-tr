---
title: Windows Installer Ile VSPackage kaldırılıyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8e92937e848d124c18dc91b9bdfa0f020f27f20
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722128"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer ile VSPackage Kaldırma
Çoğu bölüm için Windows Installer VSPackage 'ı yalnızca "geri alma" ile VSPackage 'ı yükleme işlemini kaldırabilir. [Yükleme işleminden sonra çalıştırılması gereken komutlarda](../../extensibility/internals/commands-that-must-be-run-after-installation.md) açıklanan özel eylemler, bir kaldırma işleminden sonra çalıştırılmalıdır. Devenv. exe ' ye yapılan çağrılar hem yükleme hem de kaldırma için InstallFinalize standart eyleminden hemen önce bulunduğundan, CustomAction ve InstallExecuteSequence tablo girdileri her iki durumda da servis verir.

> [!NOTE]
> MSI paketini kaldırdıktan sonra `devenv /setup` çalıştırın.

 Genel bir kural olarak, bir Windows Installer paketine özel eylemler eklerseniz, bu işlemleri kaldırma ve geri alma sırasında işlemeniz gerekir. VSPackage 'a kendi kendine kaydolabilmeniz için özel eylemler eklerseniz, örneğin kaydını silmek için özel eylemler eklemeniz gerekir.

> [!NOTE]
> Bir kullanıcının VSPackage 'ı yüklemesi ve ardından tümleştirildiği [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürümlerini kaldırması mümkündür. @No__t_0 bağımlılıklarla kod çalıştıran özel eylemleri ortadan kaldırarak VSPackage 'ın kaldırma işleminin bu senaryoda çalıştığından emin olabilirsiniz.

## <a name="handling-launch-conditions-at-uninstall-time"></a>Kaldırma sırasında başlatma koşullarını işleme
 LaunchConditions standart eylemi, koşullar karşılanmazsa hata iletilerini göstermek için LaunchCondition tablosunun satırlarını okur. Başlatma koşulları genellikle sistem gereksinimlerinin karşılanmasını sağlamak için kullanılır; `NOT Installed` koşulu, LaunchCondition tablosunun LaunchConditions satırına ekleyerek kaldırma sırasında başlatma koşullarını atlayabilirsiniz.

 Alternatif olarak, kaldırma işlemi sırasında önemli olmayan başlatma koşullarına `OR Installed` eklemektir. Bu, kaldırma işlemi sırasında koşulun her zaman doğru olmasını sağlar ve bu nedenle başlatma koşulu hata iletisini görüntülemez.

> [!NOTE]
> `Installed` özelliği, VSPackage 'ın sistemde zaten yüklü olduğunu algıladığında ayarlanır Windows Installer.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer](https://msdn.microsoft.com/library/187d8965-c79d-4ecb-8689-10930fa8b3b5)
- [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)