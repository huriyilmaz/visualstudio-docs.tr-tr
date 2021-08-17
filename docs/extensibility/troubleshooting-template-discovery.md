---
title: Visual Studio |'da şablon bulma sorunlarını giderme Microsoft Docs
description: Visual Studio SDK'sı ile özel proje ve şablon dağıtma sorunlarını gidermek için tanılama günlüğünü etkinleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: bda204e4d9b25c5eca7670494e8e1112089b0d5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062595"
---
# <a name="troubleshooting-template-installation"></a>Şablon yükleme sorunlarını giderme

Projenizi veya öğe şablonlarınızı dağıtırken sorun olursa tanılama günlüğünü etkinleştirebilirsiniz.

::: moniker range="vs-2017"

1. Yüklemeniz için *Common7\IDE\CommonExtensions* klasöründe bir pkgdef dosyası oluşturun. Örneğin, *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Yüklemeniz için *Common7\IDE\CommonExtensions* klasöründe bir pkgdef dosyası oluşturun. Örneğin, *C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. pkgdef dosyasına aşağıdakini ekleyin:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Yüklemeniz [Geliştirici Komut İstemi](../ide/reference/command-prompt-powershell.md) bir dosya açın ve `devenv /updateConfiguration` çalıştırın.

::: moniker range="vs-2017"

4. Her Visual Studio ağaçlarını başlatmak için Yeni Project ve Yeni Öğe iletişim kutularını açın.

   Şablon günlüğü artık **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv(instanceid,** Visual Studio örneğinizin yükleme kimliğine karşılık gelen) konumunda görünür. Her şablon ağacı başlatması, bu günlüğe girdi ekler.

::: moniker-end

::: moniker range=">=vs-2019"

4. Her Visual Studio proje oluştur ve **Yeni** Öğe  iletişim kutularını başlatarak her iki şablon ağacını da başlatabilirsiniz.

   Şablon günlüğü artık **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv(instanceid,** Visual Studio örneğinizin yükleme kimliğine karşılık gelen) konumunda görünür. Her şablon ağacı başlatması, bu günlüğe girdi ekler.

::: moniker-end

Günlük dosyası aşağıdaki sütunları içerir:

- **Aşağıdaki değerlere sahip Olan FullPathToTemplate:**

  - Bildirim tabanlı dağıtım için 1

  - Disk tabanlı dağıtım için 0

- **TemplateFileName**

- Diğer şablon özellikleri

> [!NOTE]
> Günlüğü devre dışı bırakmak için pkgdef dosyasını kaldırın veya değerini olarak `EnableTemplateDiscoveryLog` değiştirin `dword:00000000` ve yeniden `devenv /updateConfiguration` çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)
- [Visual Studio giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
