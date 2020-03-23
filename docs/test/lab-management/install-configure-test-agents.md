---
title: Test aracılarını ve test denetleyicilerini yükleme
ms.date: 04/17/2019
ms.topic: conceptual
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27f030fb73629172e0b5a2d5d4cb27cf186bb69f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594272"
---
# <a name="install-test-agents-and-test-controllers"></a>Test aracılarını ve test denetleyicilerini yükleme

Visual Studio ve Azure Test Planları veya Team Foundation Server (TFS) kullanan test senaryoları için bir test denetleyicisi gerekmez. Visual Studio aracıları, Azure Test Planları veya TFS ile iletişim kurarak orkestrasyon işlemini yönetir. Bir senaryo, Azure Test Planları veya TFS'de yapı ve sürüm iş akışları için sürekli testler çalıştırıyor o labilirsiniz.

Laboratuvar yönetimi yerine [yapı veya sürüm yönetimini](use-build-or-rm-instead-of-lab-management.md) kullanmanın daha iyi olup olmadığını da düşünebilirsiniz.

## <a name="system-requirements"></a>Sistem gereksinimleri

Aşağıdaki tablo, Visual Studio için test aracısını veya test denetleyicisini yüklemek için sistem gereksinimlerini gösterir:

| Öğe | Gereksinimler |
| ---- | ------------ |
| **Aracı** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standart ve Veri Merkezi<br />Windows Server 2012 R2 |
| **Denetleyicisi** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standart ve Veri Merkezi<br />Windows Server 2012 R2 |
| **.NET Çerçevesi** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Test denetleyicisini ve test aracılarını yükleme

[Sen visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents)Visual Studio için ajanlar indirebilirsiniz. Visual *Studio 2019 için Aracılar*arayın , *Ya Agent* veya *Controller*seçin , ve sonra *Download*seçin . Test aracısını veya denetleyicisini yüklemek için indirilen çalıştırılabilir'i çalıştırın.

Visual Studio 2017, Visual Studio 2015 ve Visual Studio 2013 [ajanlarını eski indirme](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasından indirebilirsiniz.

Bu yükleyiciler sanal makinelerde kolay kurulum için ISO dosyaları olarak kullanılabilir.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>TFS, Microsoft Test Yöneticisi, test denetleyicisi ve test aracısının uyumlu sürümleri

Aşağıdaki tabloya göre TFS, Microsoft Test Yöneticisi, test denetleyicisi ve test aracısı farklı sürümlerini karıştırabilirsiniz:

| TFS | Lab Center ile Microsoft Test Yöneticisi | Denetleyicisi | Aracı |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: 2015'ten yükseltme veya yeni yükleme | 2017 | 2017 | 2017 |
| 2017: 2015'ten yükseltme veya yeni yükleme | 2017 | 2013 Güncelleme 5 | 2013 Güncelleme 5 |
| 2017: 2015'ten yükseltme veya yeni yükleme | 2015 | 2013 Güncelleme 5 | 2013 Güncelleme 5 |
| 2015: 2013'ten yükseltme | 2013 | 2013 |2013 |
| 2015: yeni yükleme | 2013 | 2013 | 2013 |
| 2015: 2013 veya yeni yükleme yükseltme | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

> [!NOTE]
> TFS 2018 ve Azure DevOps Hizmetleri'ndeki laboratuvar yönetimi senaryoları küçümseniyor. Daha fazla bilgi için [TFS 2018 Yayın Notları'na](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager)bakın.

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Visual Studio 2013 test ajanlarından yükseltme

Tüm yeni otomatik test senaryolarında Visual Studio aracılarını kullanmanızı öneririz. Test aracılarını bilgisayarınıza indirmek ve yüklemek için yapı ardışık yapısındaki *Test Aracılarını Dağıt* görevini kullanabilirsiniz.

Aşağıdaki tablo, Visual Studio 2013 aracıları tarafından desteklenen senaryoları ve Team Foundation Server (TFS) 2015 ve Azure Test Planları için alternatifleri gösterir:

| Visual Studio 2013 için Aracılar tarafından desteklenen senaryolar | TFS ve Azure Test Planlarında Alternatif |
| - | - |
| Visual Studio'da Yap-Dağıt-Test iş akışı | Kullanıcılar, TFS'deki yapı, dağıtma ve test senaryoları için bir [yapı ardışık hattı](/azure/devops/pipelines/index?view=vsts) (XAML yapısı değil) kullanabilir. |
| Şirket içi uzak makineleri kullanarak yük testi (performans testi) | Şirket içinde yük testleri çalıştırmak için Test Denetleyicisi ve Test Aracıları 2013 Güncelleştirme5'i kullanın. |
| Laboratuvar ortamı nı kullanarak Microsoft Test Yöneticisi'nden otomatik testlerin uzaktan yürütülmesi | Şu anda bu senaryo için bir alternatif yoktur. Testleri uzaktan yürütmek için yapı ve sürüm tanımlarında (XAML yapısında değil) İşlevsel Testleri Çalıştır görevini kullanmanızı öneririz. |
| Visual Studio'da uzaktan testler yürüten geliştiriciler | Artık desteklenmiå. |
