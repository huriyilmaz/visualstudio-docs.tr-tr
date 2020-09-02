---
title: Windows Installer Ile VSPackage kaldırılıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a309779850dd33b77b426beb5627f61c40c2c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675236"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer ile VSPackage Kaldırma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çoğu bölüm için Windows Installer VSPackage 'ı yalnızca "geri alma" ile VSPackage 'ı yükleme işlemini kaldırabilir. [Yükleme işleminden sonra çalıştırılması gereken komutlarda](../../extensibility/internals/commands-that-must-be-run-after-installation.md) açıklanan özel eylemler, bir kaldırma işleminden sonra çalıştırılmalıdır. devenv.exe çağrıları hem yükleme hem de kaldırma için InstallFinalize standart eyleminden hemen önce gerçekleştiğinden, CustomAction ve InstallExecuteSequence tablo girdileri her iki durumda da sunar.  
  
> [!NOTE]
> `devenv /setup`BIR MSI paketini kaldırdıktan sonra çalıştırın.  
  
 Genel bir kural olarak, bir Windows Installer paketine özel eylemler eklerseniz, bu işlemleri kaldırma ve geri alma sırasında işlemeniz gerekir. VSPackage 'a kendi kendine kaydolabilmeniz için özel eylemler eklerseniz, örneğin kaydını silmek için özel eylemler eklemeniz gerekir.  
  
> [!NOTE]
> Bir kullanıcının VSPackage 'ı yüklemesi ve ardından tümleşik olduğu sürümlerini kaldırması mümkündür [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Bağımlılıkları olan kodu çalıştıran özel eylemleri ortadan kaldırarak VSPackage 'ın kaldırma işleminin bu senaryoda çalıştığından emin olabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Kaldırma sırasında başlatma koşullarını işleme  
 LaunchConditions standart eylemi, koşullar karşılanmazsa hata iletilerini göstermek için LaunchCondition tablosunun satırlarını okur. Başlatma koşulları genellikle sistem gereksinimlerinin karşılandığından emin olmak için kullanıldığında, kaldırma işlemi sırasında başlatma koşullarını `NOT Installed` LaunchCondition tablosunun LaunchConditions satırına ekleyerek genellikle atlayabilirsiniz.  
  
 Diğer bir seçenek de `OR Installed` kaldırma sırasında önemli olmayan başlatma koşullarına eklemektir. Bu, kaldırma işlemi sırasında koşulun her zaman doğru olmasını sağlar ve bu nedenle başlatma koşulu hata iletisini görüntülemez.  
  
> [!NOTE]
> `Installed` özelliği, VSPackage 'ın sistemde zaten yüklü olduğunu algıladığında ayarlar Windows Installer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Installer](https://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)
