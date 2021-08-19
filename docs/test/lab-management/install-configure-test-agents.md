---
title: Test aracılarını ve test denetleyicilerini yükleme
description: Visual Studio veya Azure Test Plans ile testleri düzenlemeye yönelik Team Foundation Server.
ms.custom: SEO-VS-2020
ms.date: 04/17/2019
ms.topic: how-to
helpviewer_keywords:
- configure test agents, test lab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 709e429a1b131a3c9124c2e182d6b9407da9b23f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156090"
---
# <a name="install-test-agents-and-test-controllers"></a>Test aracılarını ve test denetleyicilerini yükleme

Visual Studio ve Azure Test Plans veya Team Foundation Server (TFS) kullanan test senaryoları için bir test denetleyicisine ihtiyacınız yok. Visual Studio aracıları, Azure Test Plans veya TFS ile iletişim kurarak düzenlemeyi ele almaktadır. Senaryo, derleme ve yayın iş akışları için TFS'de sürekli Azure Test Plans çalıştırma olabilir.

Laboratuvar yönetimi yerine derleme veya yayın yönetimi kullanmanın [daha iyi olup olamayacaklarını](use-build-or-rm-instead-of-lab-management.md) da göz önünde bulundurarak.

## <a name="system-requirements"></a>Sistem Gereksinimleri

Aşağıdaki tabloda, test aracısını veya test denetleyicisini yüklemek için sistem gereksinimleri Visual Studio:

| Öğe | Gereksinimler |
| ---- | ------------ |
| **Aracı** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standart ve Veri Merkezi<br />Windows Server 2012 R2 |
| **Denetleyici** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2016 Standart ve Veri Merkezi<br />Windows Server 2012 R2 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Test denetleyicisini ve test aracılarını yükleme

için aracıları Visual Studio'den [visualstudio.microsoft.com.](https://visualstudio.microsoft.com/downloads/?q=agents) Aracılar için *2019* Visual Studio, Aracı *veya* Denetleyici'yi *seçin ve* ardından İndir'i *seçin.* Test aracısını veya denetleyiciyi yüklemek için indirilen yürütülebilir dosyayı çalıştırın.

Visual Studio 2017, Visual Studio 2015 ve Visual Studio 2013 için [aracıları eski indirmeler sayfasından indirebilirsiniz.](https://visualstudio.microsoft.com/vs/older-downloads/)

Bu yükleyiciler, sanal makinelere kolay yükleme için ISO dosyaları olarak kullanılabilir.

::: moniker range="vs-2017"
## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>TFS, Microsoft Test Yöneticisi, test denetleyicisi ve test aracısını uyumlu sürümleri

TFS, Microsoft Test Yöneticisi, test denetleyicisi ve test aracısını aşağıdaki tabloya göre karıştırabilirsiniz:

| TFS | Microsoft Test Yöneticisi Merkezi ile birlikte | Denetleyici | Aracı |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: 2015 veya yeni yüklemeden yükseltme | 2017 | 2017 | 2017 |
| 2017: 2015 veya yeni yüklemeden yükseltme | 2017 | 2013 Güncelleştirme 5 | 2013 Güncelleştirme 5 |
| 2017: 2015 veya yeni yüklemeden yükseltme | 2015 | 2013 Güncelleştirme 5 | 2013 Güncelleştirme 5 |
| 2015: 2013'den yükseltme | 2013 | 2013 |2013 |
| 2015: yeni yükleme | 2013 | 2013 | 2013 |
| 2015: 2013'den yükseltme veya yeni yükleme | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="compatible-versions-of-tfs-the-test-controller-and-test-agent"></a>TFS, test denetleyicisi ve test aracısını uyumlu sürümleri

TFS'nin farklı sürümlerini, test denetleyicisini ve test aracısını aşağıdaki tabloya göre karıştırabilirsiniz:

| TFS | Denetleyici | Aracı |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: 2015 veya yeni yüklemeden yükseltme | 2017 | 2017 |
| 2017: 2015 veya yeni yüklemeden yükseltme | 2013 Güncelleştirme 5 | 2013 Güncelleştirme 5 |
| 2017: 2015 veya yeni yüklemeden yükseltme | 2013 Güncelleştirme 5 | 2013 Güncelleştirme 5 |
| 2015: 2013'den yükseltme | 2013 |2013 |
| 2015: yeni yükleme | 2013 | 2013 |
| 2015: 2013'den yükseltme veya yeni yükleme | 2013 | 2013 |
| 2013 | 2013 | 2013 |
::: moniker-end

> [!NOTE]
> TFS 2018 ve Azure DevOps Services laboratuvar yönetimi senaryoları kullanım dışıdır. Daha fazla bilgi için [bkz. TFS 2018 Sürüm Notları.](/visualstudio/releasenotes/tfs2018-relnotes#--removing-support-for-lab-center-and-automated-testing-flows-in-microsoft-test-manager)

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Test aracılarından Visual Studio 2013 yükseltme

Tüm yeni otomatikleştirilmiş test senaryolarında Visual Studio aracıları kullanmanız önerilir. Test aracılarını *makinenize indirip* yüklemek için derleme işlem hattında Test Aracılarını Dağıt görevini kullanabilirsiniz.

Aşağıdaki tabloda, Visual Studio 2013 için Aracılar tarafından desteklenen senaryolar ve Team Foundation Server (TFS) 2015 ve sonraki Azure Test Plans:

| Aracılar tarafından desteklenen senaryolar Visual Studio 2013 | TFS ve Azure Test Plans'da alternatif |
| - | - |
| Visual Studio'de Derleme-Dağıtma-Test iş Visual Studio | Kullanıcılar, TFS 'deki derleme, dağıtım ve test senaryoları için bir [Yapı işlem hattı](/azure/devops/pipelines/index?view=vsts&preserve-view=true) (XAML derlemesi değil) kullanabilir. |
| Şirket içi uzak makineleri kullanarak yük testi (performans testi) | Şirket içinde yük testlerini çalıştırmak için test denetleyicisi ve test Agents 2013 güncelleştirme 5 ' i kullanın. |
| laboratuvar ortamı kullanarak Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) otomatik testlerin uzaktan yürütülmesi | Şu anda bu senaryo için alternatif yoktur. Testleri uzaktan yürütmek için derleme ve sürüm tanımlarında (XAML derlemesinde değil) Işlevsel Testleri Çalıştır görevini kullanmanızı öneririz. |
| Visual Studio 'de uzak testleri yürüten geliştiriciler | Artık desteklenmiyor. |
