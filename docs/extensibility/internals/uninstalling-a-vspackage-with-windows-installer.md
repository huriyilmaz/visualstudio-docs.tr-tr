---
title: Windows Installer ile VSPackage'ı kaldırma | Microsoft Docs
description: Windows Yükleyici, yüklemeyi geri alınarak VSPackage'nızı kaldırabilirsiniz. Windows Installer paketinizin özel eylemleriyle nasıl Windows öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e1c616b366e18cc6bba0bb9eb2906193022a6289
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627314"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Windows Installer ile VSPackage Kaldırma
Çoğu bölümde, Windows Yükleyicisi VSPackage'nızı yüklemek için ne yaptığını "geri alarak" VSPackage'nızı kaldırabilirsiniz. Yüklemeden Sonra [Çalıştırılacak Komutlar'da tartışılan özel](../../extensibility/internals/commands-that-must-be-run-after-installation.md) eylemler de bir kaldırmadan sonra çalıştırılacaktır. devenv.exe yükleme ve kaldırma için standart InstallFinalize eylemden hemen önce oluştuğu için CustomAction ve InstallExecuteSequence tablo girişleri her iki durum için de kullanılır.

> [!NOTE]
> MSI `devenv /setup` paketini kaldırdikten sonra çalıştırın.

 Genel bir kural olarak, bir Windows Yükleyici paketine özel eylemler eklersiniz, kaldırma ve geri alma sırasında bu eylemleri işlemeniz gerekir. VSPackage'nızı kendi kendine kaydetmek için özel eylemler eklersiniz, örneğin, kaydını silen özel eylemler de eklemeniz gerekir.

> [!NOTE]
> Kullanıcının VSPackage'nızı yüklemesi ve ardından ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleştirilen sürümlerini kaldırması mümkündür. üzerinde bağımlılıklarla kod çalıştıran özel eylemleri ortadan kaldırarak VSPackage kaldırma işleminizin bu senaryoda çalışmalarına yardımcı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] olur.

## <a name="handling-launch-conditions-at-uninstall-time"></a>Kaldırma Zamanında Başlatma Koşullarını İşleme
 LaunchConditions standart eylemi, koşulların karşılanmazsa hata iletilerini göstermek için LaunchCondition tablosu satırlarını okur. Başlatma koşulları genellikle sistem gereksinimlerinin karşı olduğundan emin olmak için kullanılırken, launchCondition tablonun LaunchConditions satırına koşul ekleyerek, kaldırma sırasında başlatma koşullarını `NOT Installed` atlayabilirsiniz.

 Bir alternatif, kaldırma `OR Installed` sırasında önemli olan başlatma koşullarına eklemektir. Bu, kaldırma sırasında koşulun her zaman doğru olması ve bu nedenle başlatma koşulu hata iletisini görüntülemesini sağlar.

> [!NOTE]
> `Installed`, VSPackage Windows nın sistemde zaten yüklü olduğunu algılayan Yükleyici kümelerini ayarlayan özelliğidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer](/previous-versions/ee231230(v=vs.100))
- [Sistem Gereksinimlerini Algılama](../../extensibility/internals/detecting-system-requirements.md)