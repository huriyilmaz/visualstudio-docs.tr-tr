---
title: Test aracılarını ve test denetleyicilerini yükleme
description: Azure Test Plans veya Team Foundation Server ile testi düzenlemek için Visual Studio aracılarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2ffa3a1006057169d7e4f473922ff2eebbfe7bb
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328892"
---
# <a name="install-test-agents-and-test-controllers"></a>Test aracılarını ve test denetleyicilerini yükleme

Visual Studio ve Azure Test Plans ya da Team Foundation Server (TFS) kullanan test senaryoları için, test denetleyicisine ihtiyacınız yoktur. Azure Test Plans veya TFS ile iletişim kurarak Visual Studio için aracıları düzenleme. Senaryo, Azure Test Plans veya TFS 'de derleme ve yayınlama iş akışları için sürekli testleri çalıştırmanızı sağlayabilir.

Laboratuvar Yönetimi yerine [derleme veya yayın yönetimi](use-build-or-rm-instead-of-lab-management.md) kullanmanın daha iyi olup olmadığını da düşünebilirsiniz.

## <a name="system-requirements"></a>Sistem gereksinimleri

Aşağıdaki tabloda, Visual Studio için test aracısı veya test denetleyicisi yüklemek için sistem gereksinimleri gösterilmektedir:

| Öğe | Gereksinimler |
| ---- | ------------ |
| **Aracı** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard ve Datacenter<br />Windows Server 2012 R2 |
| **Denetleyici** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standard ve Datacenter<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Test denetleyicisini ve test aracılarını yükler

Visual Studio için aracıları [VisualStudio.Microsoft.com](https://visualstudio.microsoft.com/downloads/?q=agents)adresinden indirebilirsiniz. *Visual Studio 2019 Için aracıları* arayın, *Aracı* veya *Denetleyici*' yi seçin ve ardından *İndir*' i seçin. Test aracısını veya denetleyiciyi yüklemek için indirilen yürütülebilir dosyayı çalıştırın.

Visual Studio 2017, Visual Studio 2015 ve Visual Studio 2013 için aracıları [eski indirmeler](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasından indirebilirsiniz.

Bu yükleyiciler, sanal makinelerde kolay yükleme için ISO dosyaları olarak kullanılabilir.

::: moniker range="vs-2017"
## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>TFS, Microsoft Test Yöneticisi, test denetleyicisi ve test aracısının uyumlu sürümleri

Aşağıdaki tabloya göre TFS, Microsoft Test Yöneticisi, test denetleyicisi ve test aracısının farklı sürümlerini karıştırabilirsiniz:

| TFS | Laboratuvar Merkezi ile Microsoft Test Yöneticisi | Denetleyici | Aracı |
| --- | -------------------------------------- | ---------- | ----- |
| 2017:2015 veya yeni yüklemeyi yükseltin | 2017 | 2017 | 2017 |
| 2017:2015 veya yeni yüklemeyi yükseltin | 2017 | 2013 güncelleştirme 5 | 2013 güncelleştirme 5 |
| 2017:2015 veya yeni yüklemeyi yükseltin | 2015 | 2013 güncelleştirme 5 | 2013 güncelleştirme 5 |
| 2015:2013 ' den yükseltme | 2013 | 2013 |2013 |
| 2015: yeni yüklemesi | 2013 | 2013 | 2013 |
| 2015:2013 veya yeni yüklemeyi yükseltin | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="compatible-versions-of-tfs-the-test-controller-and-test-agent"></a>TFS, test denetleyicisi ve test aracısının uyumlu sürümleri

Aşağıdaki tabloya göre TFS, test denetleyicisi ve test aracısının farklı sürümlerini karıştırabilirsiniz:

| TFS | Denetleyici | Aracı |
| --- | -------------------------------------- | ---------- | ----- |
| 2017:2015 veya yeni yüklemeyi yükseltin | 2017 | 2017 |
| 2017:2015 veya yeni yüklemeyi yükseltin | 2013 güncelleştirme 5 | 2013 güncelleştirme 5 |
| 2017:2015 veya yeni yüklemeyi yükseltin | 2013 güncelleştirme 5 | 2013 güncelleştirme 5 |
| 2015:2013 ' den yükseltme | 2013 |2013 |
| 2015: yeni yüklemesi | 2013 | 2013 |
| 2015:2013 veya yeni yüklemeyi yükseltin | 2013 | 2013 |
| 2013 | 2013 | 2013 |
::: moniker-end

> [!NOTE]
> TFS 2018 ve Azure DevOps Services 'de laboratuvar yönetimi senaryoları kullanım dışıdır. Daha fazla bilgi için bkz. [TFS 2018 sürüm notları](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager).

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Visual Studio 2013 test aracılarından yükseltme

Visual Studio için aracıları tüm yeni otomatikleştirilmiş test senaryolarında kullanmanızı öneririz. Test aracılarını makinenize indirmek ve yüklemek için bir yapı ardışık düzeninde *test aracılarını dağıt* görevini kullanabilirsiniz.

Aşağıdaki tabloda, Visual Studio 2013 için aracıların desteklediği senaryolar ve Team Foundation Server (TFS) 2015 ve Azure Test Plans alternatifleri gösterilmektedir:

| Visual Studio 2013 için aracıların desteklediği senaryolar | TFS ve Azure Test Plans alternatifi |
| - | - |
| Visual Studio 'da derleme-dağıtma-test iş akışı | Kullanıcılar, TFS 'deki derleme, dağıtım ve test senaryoları için bir [Yapı işlem hattı](/azure/devops/pipelines/index?view=vsts&preserve-view=true) (XAML derlemesi değil) kullanabilir. |
| Şirket içi uzak makineleri kullanarak yük testi (performans testi) | Şirket içinde yük testlerini çalıştırmak için test denetleyicisi ve test Agents 2013 güncelleştirme 5 ' i kullanın. |
| Laboratuvar ortamı kullanarak Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) otomatik testlerin uzaktan yürütülmesi | Şu anda bu senaryo için alternatif yoktur. Testleri uzaktan yürütmek için derleme ve sürüm tanımlarında (XAML derlemesinde değil) Işlevsel Testleri Çalıştır görevini kullanmanızı öneririz. |
| Visual Studio 'da uzak testler yürüten geliştiriciler | Artık desteklenmiyor. |
